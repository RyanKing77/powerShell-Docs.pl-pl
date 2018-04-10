---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea, programu powershell, zabezpieczeń
title: Zagadnienia dotyczące zabezpieczeń JEA
ms.openlocfilehash: 1b83a73c047b056a4cc094d7e4b0bbf31f75f53a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="jea-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń JEA

> Dotyczy: środowiska Windows PowerShell 5.0

JEA pomaga zwiększyć strukturę bezpieczeństwa, zmniejszając liczbę administratorów trwałych na maszynach.
Robi to przez utworzenie nowego punktu wejścia dla użytkowników do zarządzania systemem (Konfiguracja sesji programu PowerShell), który jest ściśle zablokowana domyślnie, aby uniemożliwić nadużycia.
Użytkownicy, którzy potrzebują niektórych, ale nie nieograniczony dostęp do komputera, aby wykonywać zadania administracyjne można udzielić dostępu do punktu końcowego JEA.
Ponieważ JEA pozwala na uruchamianie polecenia administratora bezpośrednio, bez dostępu administratora, możesz usunąć tych użytkowników z grup zabezpieczeń wysoko uprzywilejowane (były użytkownicy standardowi).

W tym temacie opisano model zabezpieczeń JEA i najlepszych rozwiązań bardziej szczegółowo.

## <a name="run-as-account"></a>Konto Uruchom jako

Każdy punkt końcowy JEA ma konto wyznaczonych "Uruchom jako", czyli konta, na którym użytkownik nawiązujący połączenie czynności.
To konto jest konfigurować w [pliku konfiguracji sesji](session-configurations.md), a konto, możesz wybrać ma znaczący wpływ na zabezpieczenia punktu końcowego.

**Kont wirtualnych** to zalecany sposób konfigurowania opcji Uruchom jako konta.
Konta wirtualne są jednorazowe, tymczasowy kont lokalnych, które są tworzone dla użytkownik nawiązujący połączenie do użycia w okresie ich JEA sesji.
Natychmiast po ich sesja została przerwana, konta wirtualnego zostaną usunięte i nie można już używać.
Użytkownik nawiązujący połączenie nie może określić poświadczenia dla konta wirtualnego i nie można użyć konta wirtualnego do uzyskania dostępu do systemu za pomocą innych środków, takich jak Pulpit zdalny lub nieograniczonego punktu końcowego programu PowerShell.

Domyślnie kont wirtualnych należy do lokalnej grupy administratorów na komputerze.
Dzięki temu ich pełnych praw do żadnych czynności w systemie zarządzania, jednak żadne prawa do zarządzania zasobami w sieci.
Podczas uwierzytelniania z innych komputerów, z kontekstu użytkownika będzie konta komputera lokalnego, a nie konta wirtualnego.

Kontrolery domeny są szczególnych przypadkach, ponieważ nie istnieje pojęcie grupy administratorów lokalnych.
Zamiast tego konta wirtualne należą do administratorów domen i mogą zarządzać usługami katalogu na kontrolerze domeny.
Tożsamość domeny jest nadal ograniczone do na kontrolerze domeny, w którym wystąpienia sesji JEA i dostępu do żadnych sieci pojawią się pochodzą z obiektu komputera kontrolera domeny, zamiast tego użyć.

W obu przypadkach można również jawnie definiować które konta wirtualnego powinna należeć do grupy zabezpieczeń.
Jest dobrym rozwiązaniem, gdy zadanie, które są wykonywane mogą być przeprowadzane bez uprawnień administratora lokalnego/domeny.
Jeśli masz już grupę zabezpieczeń zdefiniowane dla administratorów, po prostu można przyznać wirtualnego konto do tej grupy, aby nadać mu uprawnienia, których potrzebuje.
Wirtualne członkostwa grupy konta jest ograniczona do grupy zabezpieczeń lokalnych na stacji roboczej lub na serwerze członkowskim, ale na kontrolerze domeny mogą być tylko członkami grupy zabezpieczeń domeny.
Po określeniu jednej lub więcej grup zabezpieczeń dla konta wirtualnego należy do już będą należeć do grupy domyślne (administratora lokalnego lub administratora domeny).

Poniższa tabela zawiera podsumowanie opcji konfiguracji możliwe i wynikowy uprawnienia dla kont wirtualnych

Typ komputera                | Konfiguracja grupy Konto wirtualne | Kontekst użytkownika lokalnego                                      | Kontekst użytkownika sieci
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Kontroler domeny            | Wartość domyślna                             | Użytkownik domeny, element członkowski "*domeny*\Domain         | Konto komputera
Kontroler domeny            | Grupy w domenie A i B               | Użytkownik domeny, element członkowski "*domeny*\A","*domeny*\B"       | Konto komputera
Serwer członkowski lub stacji roboczej | Wartość domyślna                             | Użytkownika lokalnego, element członkowski "*WBUDOWANE*\Administrators        | Konto komputera
Serwer członkowski lub stacji roboczej | Grupy lokalne C i D                | Użytkownika lokalnego, element członkowski "*komputera*\C" i "*komputera*\D" | Konto komputera

Po wyświetleniu zdarzenia inspekcji zabezpieczeń i dzienniki zdarzeń aplikacji, zobaczysz, że każdej sesji użytkownika JEA ma unikatowe konto wirtualnego.
Ułatwia to śledzenie działań użytkownika w punkt końcowy JEA dla oryginalnego użytkownika, który uruchomił polecenie.
Konto wirtualne nazwy zgodne format "Użytkownicy usługi WinRM wirtualnej\\WinRM\_VA\_*ACCOUNTNUMBER*\_*domeny* \_ *sAMAccountName*"na przykład, jeśli użytkownika"Alicja"w domenie"Contoso"ponowne uruchomienie usługi w punkt końcowy JEA, nazwę użytkownika skojarzoną z żadnych zdarzeń z Menedżera kontroli usług będzie" Użytkownicy wirtualnej WinRM\\WinRM\_ VA\_1\_contoso\_Alicja ".


**Grupa kont usług zarządzanych (Gmsa)** są przydatne, gdy serwer członkowski musi mieć dostęp do zasobów sieciowych w sesji JEA.
Przykład przypadek użycia tego jest JEA punktu końcowego, który służy do kontrolowania dostępu do interfejsu API REST hostowany na innym komputerze.
Jest łatwy do zapisania tożsamości sieciowej potrzebne funkcje wprowadzić odpowiednie wywołania na interfejsu API REST, ale w celu uwierzytelnienia przy użyciu interfejsu API.
Za pomocą konta usługi zarządzane przez grupę pozwala "drugi przeskok" przy zachowaniu kontroli nad którym komputery mogą używać konta.
Czynnych uprawnień przez grupę są definiowane przez grup zabezpieczeń (lokalnego lub domeny), do której należy konto usługi zarządzane przez grupę.

Gdy punkt końcowy JEA jest skonfigurowany do używania konta gMSA, akcje wszyscy użytkownicy JEA pojawi się pochodzą z tej samej grupy zarządzane konto usługi.
Jedynym sposobem można śledzić akcje do określonego użytkownika jest ustalenie zestaw poleceń, uruchom w wykazie sesji programu PowerShell.

**Do przekazywania poświadczeń** są używane, gdy nie określać Uruchom jako konta i chcesz programu PowerShell na potrzeby uruchamiania poleceń na serwerze zdalnym poświadczeń użytkownik nawiązujący połączenie.
Ta konfiguracja jest *nie* zalecane dla JEA, ponieważ wymagałoby przyznania łączącego bezpośredni dostęp użytkownika do grupy zarządzania uprzywilejowanym.
Jeśli użytkownik nawiązujący połączenie ma już uprawnień administratora, mogą uniknąć JEA całkowicie i zarządzanie systemu za pośrednictwem innych nieograniczonego oznaczają.
Zobacz poniższą sekcję na temat [JEA nie chroni przed Administratorzy](#jea-does-not-protect-against-admins) Aby uzyskać więcej informacji.

**Standardowa Uruchom jako konta** umożliwiają określenie dowolnego konta użytkownika, na którym będzie uruchamiana całej sesji programu PowerShell.
Jest to ważna różnica, ponieważ zestaw konfiguracyjny sesji do użycia jako konto Uruchom stałego (z `-RunAsCredential` parametru) nie jest JEA-aware.
Oznacza to, czy definicje ról przestaną działać zgodnie z oczekiwaniami i każdego użytkownika uprawnień dostępu punkt końcowy będzie można przypisać tego samego elementu role.

Nie należy używać RunAsCredential na punkt końcowy JEA z powodu trudności w śledzeniu akcje do konkretnych użytkowników i brak obsługi mapowanie użytkowników do ról.

## <a name="winrm-endpoint-acl"></a>Listę ACL punktów końcowych usługi WinRM

Z regularnych punktów końcowych usługi zdalne środowiska PowerShell, każdy punkt końcowy JEA ma osobne listy kontroli dostępu (ACL) w konfiguracji usługi WinRM, która kontroluje, który może uwierzytelniać z punktem końcowym JEA.
Jeśli niepoprawnie skonfigurowany Zaufani użytkownicy nie mogą mieć możliwość dostępu JEA punktu końcowego i/lub niezaufanych użytkownicy mogą uzyskać dostęp.
Listy ACL usługi WinRM nie dotyczy jednak mapowanie użytkowników do ról JEA.
Który jest kontrolowany przez *RoleDefinitions* w pliku konfiguracji sesji, który został zarejestrowany w systemie.

Domyślnie podczas rejestrowania punktu końcowego JEA przy użyciu pliku konfiguracji sesji i jeden lub więcej możliwości roli WinRM ACL zostanie skonfigurowana w celu zezwala wszystkim użytkownikom mapowanie na co najmniej jeden dostępu ról do punktu końcowego.
Na przykład sesji JEA skonfigurowany za pomocą następujących poleceń będzie zezwalał na dostęp do *CONTOSO\JEA\_Lev1* i *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Można przeprowadzić inspekcję uprawnienia użytkownika z [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Aby zmienić, którzy użytkownicy mają dostęp, uruchom `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` dla monitu interakcyjnego lub `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` można zaktualizować uprawnienia.
Użytkownicy muszą mieć co najmniej *Invoke* prawa dostępu JEA punktu końcowego.

Jeśli dodatkowym użytkownikom udzielany jest dostęp do punktu końcowego JEA, ale nie należą do żadnych ról, zdefiniowanych w pliku konfiguracji sesji, będą oni mogli rozpocząć sesję JEA, ale tylko dostęp do poleceń cmdlet programu domyślnego.
Uprawnienia użytkownika w punkcie końcowym JEA można inspekcji, uruchamiając `Get-PSSessionCapability`.
Zapoznaj się z [inspekcji i raportowania JEA](audit-and-report.md) artykule Aby uzyskać więcej informacji o inspekcji, które polecenia użytkownika ma dostęp do w punkt końcowy JEA.

## <a name="least-privilege-roles"></a>Co najmniej uprawnień ról

Podczas projektowania JEA ról, jest pamiętać, że wirtualne lub grupy usługi zarządzanej konta uruchomione w tle często ma nieograniczony dostęp do zarządzania na komputerze lokalnym.
Możliwości roli JEA ograniczyć co tego konta może służyć do dzięki ograniczeniu liczby poleceń i aplikacje, które mogą być uruchamiane przy użyciu tego kontekstu uprzywilejowanych.
Nieprawidłowo zaprojektowane role umożliwiają niebezpiecznych polecenia do uruchomienia, które może zezwolić użytkownikowi na break poza granice JEA lub uzyskać dostępu do poufnych informacji.

Rozważmy na przykład następujący wpis możliwości roli:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Ta możliwość roli pozwala użytkownikom na uruchamianie każdego polecenia cmdlet programu PowerShell z rzeczownik "Proces" z modułu Microsoft.PowerShell.Management.
Użytkownicy mogą potrzebować dostępu do poleceń cmdlet, takich jak do `Get-Process` zrozumieć, jakie aplikacje są uruchomione w systemie i `Stop-Process` do żadnego kill zawiesił aplikacji.
Jednak umożliwia też ten wpis `Start-Process`, które mogą służyć do uruchomienia dowolnego programu z uprawnieniami administratora pełnego.
Program nie wymaga lokalnie był zainstalowany w systemie, aby Atakujący dokonuje po prostu można uruchomić programu w udziale plików, zapewniająca łączącego użytkownikowi uprawnienia administratora lokalnego, uruchamia złośliwego oprogramowania i inne. "

Bezpieczniejsza wersja ta sama funkcja roli wyglądałyby tak jak:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Unikaj używania symboli wieloznacznych w roli możliwości i upewnij się, [inspekcji efektywne uprawnienia](audit-and-report.md#check-effective-rights-for-a-specific-user) regularnie, aby zrozumieć, które polecenia użytkownik ma dostęp do.

## <a name="jea-does-not-protect-against-admins"></a>JEA nie chroni przed Administratorzy

Jeden z podstawowych zasad JEA jest możliwość z systemem innym niż administratorzy przeprowadzić *niektórych* zadania administracyjne.
JEA nie chroni przed tych, którzy już mają uprawnienia administratora.
Użytkownicy należącymi "Administratorzy domeny," "Administratorzy lokalni" lub innych grup wysoce uprzywilejowane w środowisku nadal będzie uda się rozwiązać przez JEA ochrony po zalogowaniu się do komputera za pośrednictwem innymi sposobami.
One można na przykład, zaloguj się przy użyciu protokołu RDP, Użyj zdalnego konsoli MMC lub Połącz z nieograniczonego punkty końcowe programu PowerShell.
Administratorzy lokalni na komputerze można również zmodyfikować konfiguracje JEA umożliwia innym użytkownikom do zarządzania systemem lub zmień możliwość roli rozszerzyć zakres użytkownika czynności w ich JEA sesji.
W związku z tym należy ocenić użytkowników JEA uprawnienia rozszerzone aby zobaczyć, czy istnieją inne sposoby ich może uzyskać uprzywilejowany dostęp do systemu.

Popularną praktyką jest JEA dla codziennej konserwacji i mieć "tylko w czasie" uprzywilejowany dostęp do rozwiązania do zarządzania umożliwiają użytkownikom tymczasowo stają się Administratorzy lokalni sytuacji awaryjnych.
Dzięki temu użytkownicy nie są trwałe Administratorzy na komputerze, ale można uzyskać te prawa, jeśli i tylko wtedy, gdy ich zakończeniu przepływu pracy, który dokumentów ich użycie tych uprawnień.