---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Zagadnienia dotyczące zabezpieczeń usługi JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726583"
---
# <a name="jea-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń usługi JEA

JEA pomaga zwiększyć poziom bezpieczeństwa dzięki zmniejszeniu liczby administratorów trwałych na maszynach. JEA używa konfiguracji sesji programu PowerShell, aby utworzyć nowy punkt wejścia dla użytkowników do zarządzania systemem. Użytkownicy, którzy muszą z podwyższonym poziomem uprawnień, ale nie nieograniczony dostęp do maszyny, aby wykonywać zadania administracyjne można udzielić dostępu do punktu końcowego JEA. Ponieważ JEA umożliwia Ci użytkownicy uruchamiać polecenia administratora bez dostępu administratora pełnego, możesz usunąć tych użytkowników z grup zabezpieczeń o wysokim poziomie uprawnień.

## <a name="run-as-account"></a>Konto Uruchom jako

Każdy punkt końcowy usługi JEA ma wyznaczonych **Uruchom jako** konta. To jest konto w ramach której użytkownik nawiązujący połączenie akcje są wykonywane. To konto jest konfigurowane w [plik konfiguracji sesji](session-configurations.md), i konta, możesz wybrać ma istotny wpływ na zabezpieczenia punktu końcowego usługi.

**Kont wirtualnych** to zalecany sposób konfigurowania **Uruchom jako** konta. Kont wirtualnych są jednorazowe, tymczasowy kont lokalnych, które są tworzone dla użytkownik nawiązujący połączenie do użycia w czasie trwania sesji JEA. Zaraz po ich sesja została przerwana, wirtualne konto zostanie zniszczony i nie można już używać. Użytkownik nawiązujący połączenie nie może ustalić poświadczenia dla konta wirtualnego. Konta wirtualnego nie można uzyskać dostępu do systemu za pomocą innych metod, takich jak pulpitu zdalnego lub nieograniczonego punktu końcowego programu PowerShell.

Domyślnie kont wirtualnych należeć do lokalnej **Administratorzy** grupy na komputerze. To daje im pełne prawa do niczego w systemie zarządzania, ale żadnych praw do zarządzania zasobami w sieci.
Podczas uwierzytelniania z innymi maszynami, kontekst użytkownika jest konto komputera lokalnego konta wirtualnego.

Kontrolery domeny są szczególny przypadek, ponieważ nie istnieje lokalnie **Administratorzy** grupy. Zamiast tego konta wirtualne należą do **Administratorzy domeny** i może zarządzać usługi katalogowe na kontrolerze domeny. Tożsamość domeny jest nadal może być używana na kontrolerze domeny, w której utworzono wystąpienie sesji JEA. Pojawia się, że dostęp do dowolnej sieci pochodzą z obiektu komputera kontrolera domeny, zamiast tego.

W obu przypadkach może być jawnie zdefiniować wirtualnego konto należy do grupy zabezpieczeń. Jest dobrą praktyką, gdy zadanie może odbywać się bez uprawnień administratora lokalnego lub domeny. Jeśli masz już grupę zabezpieczeń zdefiniowane dla administratorów, należy udzielić członkostwa wirtualnego konta do tej grupy. Członkostwo w grupie kont wirtualnych jest ograniczona do lokalnych grup zabezpieczeń na stacji roboczej i elementów członkowskich serwerach. Na kontrolerach domeny kont wirtualnych musi być członkami grupy zabezpieczeń domeny.
Po dodaniu co najmniej jedną grupę zabezpieczeń konta wirtualnego nie jest już należy do grup domyślnych (lokalnego lub domeny Administratorzy).

Poniższa tabela zawiera podsumowanie możliwych opcji konfiguracji i wynikowy uprawnienia dla kont wirtualnych:

|        Typ komputera         | Konfiguracja grupy konta wirtualnego |                   Kontekst użytkownika lokalnego                    | Kontekst użytkownika sieci |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Kontroler domeny            | Wartość domyślna                             | Użytkownik domeny, członek "*domeny*\Domain         | Konto komputera     |
| Kontroler domeny            | Grupy w domenie A i B               | Użytkownik domeny, członek "*domeny*\A","*domeny*\B"       | Konto komputera     |
| Serwera członkowskiego lub stacji roboczej | Wartość domyślna                             | Użytkownik lokalny, członek "*BUILTIN*\Administrators        | Konto komputera     |
| Serwera członkowskiego lub stacji roboczej | Grupy lokalne, C i D                | Użytkownik lokalny, członek "*komputera*\C" i "*komputera*\D" | Konto komputera     |

Przyjrzyj się zdarzeń inspekcji zabezpieczeń i dzienniki zdarzeń aplikacji, zobacz, że każda sesja użytkownika JEA ma unikatowe konto wirtualne. Unikatowe konto ułatwia śledzenie działań użytkownika w punktu końcowego JEA dla oryginalnego użytkownika, który uruchomił polecenie. Konta wirtualnej nazwy zgodne z formatem `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` na przykład, jeśli użytkownik **Alicja** w domenie **Contoso** powoduje ponowne uruchomienie usługi JEA punkt końcowy, nazwę użytkownika skojarzoną z dowolnym Menedżera sterowania usługami zdarzenia będą `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

**Konta usług zarządzane przez grupę (konta Gmsa)** są przydatne, gdy serwer członkowski musi mieć dostęp do zasobów sieciowych w sesji JEA. Na przykład, gdy punktu końcowego JEA służy do kontrolowania dostępu do interfejsu API REST usługi hostowanej na innym komputerze. Ułatwia pisanie funkcji do wywołania interfejsów API REST, ale należy tożsamości sieciowej, do uwierzytelniania za pomocą interfejsu API. Używane konto usługi zarządzane przez grupę pozwala drugiego przeskoku przy jednoczesnym zachowaniu kontroli nad tym, którzy komputery można używać tego konta. Czynne uprawnienia opcją gMSA są definiowane przez grupy zabezpieczeń (lokalnego lub domeny) do którego należy dane konta gMSA.

Gdy punkt końcowy usługi JEA jest skonfigurowany do używania gMSA, akcje wszystkich użytkowników usługi JEA pojawią się pochodzić z tej samej gMSA. Jest to jedyny sposób działania śledzenia do określonego użytkownika do identyfikowania zestawów polecenia uruchamiane w wykazie sesji programu PowerShell.

**Poświadczenia — dostęp próbny do** są używane, jeśli nie określisz **Uruchom jako** konta. Program PowerShell używa poświadczeń użytkownik nawiązujący połączenie, aby uruchamiać polecenia na serwerze zdalnym. Wymaga to przyznania łączące bezpośredni dostęp użytkowników do grup uprzywilejowanych zarządzania. Ta konfiguracja jest **nie** zalecane w przypadku technologii JEA. Jeśli użytkownik nawiązujący połączenie ma już uprawnienia administratora, mogą uniknąć JEA i zarządzania systemem za pośrednictwem oznacza, że inne, nieograniczone. Aby uzyskać więcej informacji, zobacz sekcję poniżej na temat [JEA nie chroni przed Administratorzy](#jea-doesnt-protect-against-admins).

**Standardowe konta Uruchom jako** pozwalają na określenie dowolnego konta użytkownika, na którym działa podczas całej sesji programu PowerShell. Konfiguracje sesji przy użyciu stałej **Uruchom jako** konta (za pomocą `-RunAsCredential` parametr) nie jestes świadomy JEA. Definicje ról nie będą działać zgodnie z oczekiwaniami. Każdy użytkownik autoryzowany do dostępu do punktu końcowego przypisano tę samą rolę.

Nie używaj **RunAsCredential** w punkcie końcowym usługi JEA jest trudne do śledzenia działania do określonych użytkowników nie ma Obsługa i mapowanie użytkowników do ról.

## <a name="winrm-endpoint-acl"></a>Listy ACL punktów końcowych usługi WinRM

Za pomocą regularnego punkty końcowe komunikacji zdalnej programu PowerShell, każdego punktu końcowego JEA ma oddzielne listy kontroli dostępu (ACL), który kontroluje kto może uwierzytelniać przy użyciu punktu końcowego JEA. Jeśli skonfigurowana niepoprawnie, Zaufani użytkownicy może nie być mogli korzystać z punktu końcowego JEA i niezaufanych użytkownicy mogą uzyskiwać dostęp. Listy ACL usługi WinRM nie ma wpływu na mapowanie użytkowników do ról usługi JEA. Mapowanie jest kontrolowana przez **RoleDefinitions** pole w pliku konfiguracji sesji używane do zarejestrowania punktu końcowego.

Domyślnie gdy punkt końcowy usługi JEA ma wiele możliwości roli, listy ACL usługi WinRM jest skonfigurowany do Zezwalaj na dostęp do wszystkich zamapowanych użytkowników. Na przykład sesję JEA skonfigurowany przy użyciu następujących poleceń przyznaje pełny dostęp do `CONTOSO\JEA_Lev1` i `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Można przeprowadzać ich inspekcje uprawnień użytkownika za pomocą [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet.

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Aby zmienić, którzy użytkownicy mają dostęp, uruchom `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` dla monitu interakcyjnego lub `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` można zaktualizować uprawnień. Użytkownicy muszą się przynajmniej *Invoke* praw dostępu do punktu końcowego JEA.

Istnieje możliwość tworzenia punktu końcowego JEA, który nie jest mapowany zdefiniowanej roli każdemu użytkownikowi, który ma dostęp. Tacy użytkownicy można rozpocząć sesję JEA, ale tylko mają dostęp do poleceń cmdlet domyślne. Można przeprowadzać ich inspekcje uprawnienia użytkownika w punkcie końcowym usługi JEA, uruchamiając `Get-PSSessionCapability`. Aby uzyskać więcej informacji, zobacz [inspekcji i raporty dotyczące technologii JEA](audit-and-report.md).

## <a name="least-privilege-roles"></a>Co najmniej role uprawnień

Podczas projektowania technologii JEA ról, to należy pamiętać, że konta wirtualne zarządzane przez grupę usługi uruchomione w tle mogą mają nieograniczony dostęp do komputera lokalnego. Możliwości roli JEA ograniczyć polecenia i aplikacje, które mogą być uruchamiane w tym kontekście uprzywilejowanych.
Nieprawidłowo zaprojektowane role można zezwolić na poleceń niebezpiecznych, które może zezwolić użytkownikowi zerwać granice JEA lub uzyskać dostępu do poufnych informacji.

Na przykład rozważmy następujący wpis możliwości roli:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Ta funkcja roli umożliwia użytkownikom uruchamianie każdego polecenia cmdlet programu PowerShell z rzeczownikiem **procesu** z **Microsoft.PowerShell.Management** modułu. Użytkownicy może być konieczne dostęp do poleceń cmdlet, takich jak `Get-Process` co aplikacje są uruchomione w systemie i `Stop-Process` do zatrzymania aplikacji, które nie odpowiada. Jednak ten wpis umożliwia także `Start-Process`, który może służyć do uruchamiania dowolnego programu z uprawnieniami administrator o pełnych uprawnieniach. Program nie musi być zainstalowana lokalnie w systemie. Program można uruchomić połączonego użytkownika z udziału plików, która przyznaje użytkownikowi uprawnienia administratora lokalnego, uruchamia złośliwego oprogramowania i innych.

Bardziej bezpieczna wersja ta sama funkcja roli będzie wyglądać:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Należy unikać używania symboli wieloznacznych w możliwości roli. Pamiętaj, aby regularnie [inspekcji uprawnienia obowiązująca nazwa użytkownika](audit-and-report.md#check-effective-rights-for-a-specific-user) zrozumieć, jakie polecenia są dostępne dla użytkownika.

## <a name="jea-doesnt-protect-against-admins"></a>JEA nie chroni przed administratorów

Jedną z podstawowych zasad JEA jest możliwość użytkowników innych niż administratorzy w celu niektórych zadań administracyjnych. JEA nie chroni przed użytkownikami, którzy już mają uprawnienia administratora. Użytkownicy, którzy należą **Administratorzy domeny**lokalny **Administratorzy**, lub inne wysoce uprzywilejowanych grup mogą omijać zabezpieczenia JEA firmy za pomocą innych metod. Na przykład ich można zalogować się przy użyciu protokołu RDP, użyj zdalnych konsol programu MMC lub nawiązać połączenie z użyciem środowiska PowerShell punktów końcowych. Ponadto administratorzy lokalni w systemie można zmodyfikować JEA konfiguracje, aby umożliwić dodatkowych użytkowników lub zmienić możliwości roli, aby rozszerzyć zakres co użytkownik może zrobić w ich sesji usługi JEA. Należy ocenić użytkowników usługi JEA rozszerzone uprawnienia, aby zobaczyć, czy istnieją inne sposoby na uzyskanie uprzywilejowanego dostępu do systemu.

Powszechną praktyką jest JEA na użytek codziennej konserwacji i just-in-time, rozwiązanie do zarządzania dostępem uprzywilejowanym, które umożliwia użytkownikom tymczasowo stają się administratorami lokalnymi w sytuacjach awaryjnych. Dzięki temu użytkownicy nie są trwałe Administratorzy w systemie, ale można uzyskać te prawa, jeśli i tylko wtedy, gdy ich zakończeniu przepływu pracy, która dokumentuje ich użycie tych uprawnień.
