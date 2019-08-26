---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Zagadnienia dotyczące zabezpieczeń JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017909"
---
# <a name="jea-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń JEA

JEA pomaga zwiększyć bezpieczeństwo stan, zmniejszając liczbę trwałych administratorów na Twoich komputerach. JEA używa konfiguracji sesji programu PowerShell w celu utworzenia nowego punktu wejścia dla użytkowników w celu zarządzania systemem. Użytkownicy wymagający podwyższonego poziomu uprawnień, ale nie z ograniczeniami, dostęp do maszyny do zadań administracyjnych można udzielić do punktu końcowego JEA. Ponieważ JEA zezwala tym użytkownikom na uruchamianie poleceń administracyjnych bez posiadania pełnego dostępu administratora, można następnie usunąć tych użytkowników z wysoce uprzywilejowanych grup zabezpieczeń.

## <a name="run-as-account"></a>Konto Uruchom jako

Każdy punkt końcowy JEA ma określone konto **Uruchom jako** . Jest to konto, pod którym wykonywane są akcje łączące użytkownika. To konto można skonfigurować w [pliku konfiguracji sesji](session-configurations.md), a wybrane konto ma znaczący wpływ na bezpieczeństwo punktu końcowego.

**Konta wirtualne** są zalecaną metodą konfigurowania konta **Uruchom jako** . Konta wirtualne są jednorazowymi, tymczasowymi kontami lokalnymi utworzonymi dla połączonego użytkownika w czasie trwania sesji JEA. Gdy tylko sesja zostanie zakończona, konto wirtualne zostanie zniszczone i nie można go już używać. Użytkownik nawiązujący połączenie nie wie o poświadczeniach dla konta wirtualnego. Nie można użyć konta wirtualnego, aby uzyskać dostęp do systemu za pośrednictwem innych metod, takich jak Pulpit zdalny lub nieograniczonego punktu końcowego programu PowerShell.

Domyślnie konta wirtualne należą do lokalnej grupy **administratorów** na komputerze. Dzięki temu są one pełnymi prawami do zarządzania wszystkimi elementami w systemie, ale nie mają uprawnień do zarządzania zasobami w sieci.
Podczas uwierzytelniania przy użyciu innych maszyn kontekst użytkownika to konto komputera lokalnego, a nie konto wirtualne.

Kontrolery domeny są szczególnym przypadkiem, ponieważ nie ma lokalnej grupy **administratorów** . Zamiast tego konta wirtualne należą do **administratorów domeny** i mogą zarządzać usługami katalogowymi na kontrolerze domeny. Tożsamość domeny jest nadal ograniczona do użycia na kontrolerze domeny, w którym utworzono wystąpienie sesji JEA. Każdy dostęp do sieci jest wyświetlany zamiast obiektu komputera kontrolera domeny.

W obu przypadkach można jawnie zdefiniować grupy zabezpieczeń, do których należy konto wirtualne. Jest to dobre rozwiązanie, gdy zadanie można wykonać bez uprawnień administratora lokalnego lub domeny. Jeśli masz już zdefiniowaną grupę zabezpieczeń dla administratorów, przypisz do niej członkostwo konta wirtualnego. Członkostwo w grupie kont wirtualnych jest ograniczone do lokalnych grup zabezpieczeń na stacjach roboczych i serwerach członkowskich. Na kontrolerach domeny konta wirtualne muszą należeć do grupy zabezpieczeń domeny.
Po dodaniu konta wirtualnego do co najmniej jednej grupy zabezpieczeń nie należy ono już do grup domyślnych (administratorów lokalnych lub domen).

Poniższa tabela zawiera podsumowanie możliwych opcji konfiguracji i wynikających z nich uprawnień dla kont wirtualnych:

|        Typ komputera         | Konfiguracja grupy kont wirtualnych |                   Kontekst użytkownika lokalnego                    | Kontekst użytkownika sieci |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Kontroler domeny            | Wartość domyślna                             | Użytkownik domeny, członek grupy "Administratorzy*domeny*\Domain"         | Konto komputera     |
| Kontroler domeny            | Grupy domen A i B               | Użytkownik domeny, członek "*domena*\a", "*domena*\b"       | Konto komputera     |
| Serwer członkowski lub stacja robocza | Wartość domyślna                             | Użytkownik lokalny, członek elementu "\Administrators*wbudowane*"        | Konto komputera     |
| Serwer członkowski lub stacja robocza | Grupy lokalne C i D                | Użytkownik lokalny, członek "*Computer*\c" i "*Computer*\d" | Konto komputera     |

Podczas przeglądania zdarzeń inspekcji zabezpieczeń i dzienników zdarzeń aplikacji zobaczysz, że każda sesja użytkownika JEA ma unikatowe konto wirtualne. To unikatowe konto pomaga śledzić akcje użytkownika w punkcie końcowym JEA z powrotem do oryginalnego użytkownika, który uruchomił polecenie. Nazwy kont wirtualnych są zgodne z `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` formatem, na przykład jeśli **Alicja** użytkownika w domenie **contoso** ponownie uruchomi usługę w punkcie końcowym jea, nazwa użytkownika skojarzona z dowolnym zdarzeniem Menedżera `WinRM Virtual Users\WinRM_VA_1_contoso_alice`kontroli usług będzie mieć wartość.

**Konta usług zarządzane przez grupę (kont gMSA)** są przydatne, gdy serwer członkowski musi mieć dostęp do zasobów sieciowych w sesji jea. Na przykład, gdy punkt końcowy JEA jest używany do kontrolowania dostępu do usługi interfejsu API REST hostowanej na innym komputerze. Można łatwo pisać funkcje do wywoływania interfejsów API REST, ale potrzebna jest tożsamość sieciowa do uwierzytelniania za pomocą interfejsu API. Użycie konta usługi zarządzanego przez grupę sprawia, że drugi przeskok jest możliwy do zapewnienia kontroli nad tym, które komputery mogą korzystać z tego konta. Czynne uprawnienia gMSA są definiowane przez grupy zabezpieczeń (lokalne lub domeny), do których należy konto gMSA.

Gdy punkt końcowy JEA jest skonfigurowany do korzystania z gMSA, akcje wszystkich użytkowników JEA pojawiają się z tego samego gMSA. Jedynym sposobem śledzenia akcji z powrotem do określonego użytkownika jest zidentyfikowanie zestawu poleceń uruchamianych w transkrypcji sesji programu PowerShell.

**Poświadczenia przekazywania** są używane, jeśli nie określono konta **Uruchom jako** . Program PowerShell używa poświadczeń łączącego użytkownika do uruchamiania poleceń na serwerze zdalnym. Wymaga to przyznania użytkownikom bezpośredniego dostępu do uprzywilejowanych grup zarządzania. Ta konfiguracja **nie** jest zalecana w przypadku jea. Jeśli użytkownik nawiązujący połączenie ma już uprawnienia administratora, może uniknąć JEA i zarządzać systemem za pośrednictwem innych, nieograniczonych środków. Aby uzyskać więcej informacji, zapoznaj się z sekcją poniżej, w jaki sposób [jea nie chroni przed administratorami](#jea-doesnt-protect-against-admins).

**Standardowe konta Uruchom jako** umożliwiają określenie dowolnego konta użytkownika, w ramach którego działa cała sesja programu PowerShell. Konfiguracje sesji przy użyciu stałych kont **Uruchom jako** (z parametrem) nie są oparte na `-RunAsCredential` jea. Definicje ról nie działają dłużej niż oczekiwano. Każdy użytkownik autoryzowany do uzyskiwania dostępu do punktu końcowego ma przypisaną tę samą rolę.

Nie należy używać **RunAsCredential** w punkcie KOŃCOWYm jea, ponieważ trudno jest śledzić akcje z powrotem do określonych użytkowników i brak obsługi mapowania użytkowników do ról.

## <a name="winrm-endpoint-acl"></a>Lista ACL punktu końcowego usługi WinRM

Podobnie jak w przypadku zwykłych punktów końcowych komunikacji zdalnej programu PowerShell każdy punkt końcowy JEA ma osobną listę kontroli dostępu (ACL), która kontroluje, kto może uwierzytelniać się za pomocą punktu końcowego JEA. W przypadku nieprawidłowej konfiguracji zaufane użytkownicy mogą nie być w stanie uzyskać dostępu do punktu końcowego JEA, a niezaufani użytkownicy mogą mieć dostęp. Lista ACL usługi WinRM nie ma wpływu na Mapowanie użytkowników na role JEA. Mapowanie jest kontrolowane przez pole **RoleDefinitions** w pliku konfiguracyjnym sesji używanym do rejestrowania punktu końcowego.

Domyślnie, gdy punkt końcowy JEA ma wiele możliwości roli, lista ACL usługi WinRM jest skonfigurowana tak, aby zezwalać na dostęp wszystkim zamapowanym użytkownikom. Na przykład sesja jea skonfigurowana przy użyciu następujących poleceń daje pełny dostęp do `CONTOSO\JEA_Lev1` i. `CONTOSO\JEA_Lev2`

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Uprawnienia użytkownika można poddać inspekcji za pomocą polecenia cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) .

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Aby zmienić użytkowników, którzy mają do nich dostęp `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` , uruchom dla interakcyjnego `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` monitu lub zaktualizuj uprawnienia. Użytkownicy muszą mieć co najmniej uprawnienia umożliwiające dostęp do punktu końcowego jea.

Istnieje możliwość utworzenia punktu końcowego JEA, który nie mapuje zdefiniowanej roli na wszystkich użytkowników, którzy mają dostęp. Ci użytkownicy mogą uruchomić sesję JEA, ale ma tylko dostęp do domyślnych poleceń cmdlet. Aby przeprowadzić inspekcję uprawnień użytkowników w punkcie końcowym JEA `Get-PSSessionCapability`, należy uruchomić program. Aby uzyskać więcej informacji, zobacz [Inspekcja i raportowanie w witrynie jea](audit-and-report.md).

## <a name="least-privilege-roles"></a>Role najniższych uprawnień

Podczas projektowania ról JEA należy pamiętać, że wirtualne i zarządzane przez grupę konta usług działające w tle mogą mieć nieograniczony dostęp do komputera lokalnego. Możliwości roli JEA pomagają ograniczyć liczbę poleceń i aplikacji, które mogą być uruchamiane w kontekście uprzywilejowanym.
Nieprawidłowo zaprojektowane role mogą zezwalać na używanie niebezpiecznych poleceń, które mogą pozwolić użytkownikowi na przerwanie granic JEA lub uzyskanie dostępu do poufnych informacji.

Rozważmy na przykład następujący wpis możliwości roli:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Ta funkcja umożliwia użytkownikom uruchamianie dowolnego polecenia cmdlet programu PowerShell z **procesem** rzeczowników z modułu **Microsoft. PowerShell. Management** . Użytkownicy mogą potrzebować dostępu do poleceń cmdlet, `Get-Process` takich jak aby zobaczyć, jakie aplikacje są uruchomione w `Stop-Process` systemie, i aby skasować aplikacje, które nie odpowiadają. Ten wpis umożliwia `Start-Process`jednak również uruchamianie dowolnego programu z pełnymi uprawnieniami administratora. Program nie musi być zainstalowany lokalnie w systemie. Połączony użytkownik może uruchomić program z udziału plików, który nadaje użytkownikowi uprawnienia administratora lokalnego, uruchamia złośliwe oprogramowanie i nie tylko.

Bardziej bezpieczna wersja tej samej funkcji roli będzie wyglądać następująco:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Unikaj używania symboli wieloznacznych w możliwościach roli. Należy regularnie przeprowadzać [inspekcję uprawnień użytkowników](audit-and-report.md#check-effective-rights-for-a-specific-user) , aby zrozumieć, które polecenia są dostępne dla użytkownika.

## <a name="jea-doesnt-protect-against-admins"></a>JEA nie chroni przed administratorami

Jedną z podstawowych zasad JEA jest możliwość wykonywania niektórych zadań administracyjnych, które nie są administratorami. JEA nie chroni użytkowników, którzy mają już uprawnienia administratora. Użytkownicy należący do grup **Administratorzy domeny**, **administratorzy**lokalni lub inne wysoce uprzywilejowane grupy mogą ominąć ochronę jea za pomocą innych środków. Na przykład mogą logować się przy użyciu protokołu RDP, używać zdalnych konsol programu MMC lub łączyć się z nieograniczone punkty końcowe programu PowerShell. Ponadto administratorzy lokalni w systemie mogą modyfikować konfiguracje JEA, aby umożliwić dodatkowym użytkownikom lub zmienić możliwości roli w celu zwiększenia zakresu działania użytkownika w sesji JEA. Ważne jest, aby oszacować rozszerzone uprawnienia użytkowników JEA, aby sprawdzić, czy istnieją inne sposoby uzyskania uprzywilejowanego dostępu do systemu.

Typowym rozwiązaniem jest użycie JEA do regularnej konserwacji codziennej i posiadanie rozwiązania do zarządzania dostępem uprzywilejowanym w trybie just-in-Time, które pozwala użytkownikom tymczasowo stać się administratorami lokalnymi w sytuacjach awaryjnych. Pozwala to zagwarantować, że użytkownicy nie są stałymi administratorami systemu, ale mogą uzyskać te prawa, jeśli tylko wtedy, gdy ukończyją one przepływ pracy, który dokumentują te uprawnienia.
