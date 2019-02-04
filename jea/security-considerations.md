---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Zagadnienia dotyczące zabezpieczeń usługi JEA
ms.openlocfilehash: ede727f0f30412d520712d6ba855ba2008375d9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687244"
---
# <a name="jea-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń usługi JEA

> Dotyczy: Windows PowerShell 5.0

JEA pomaga zwiększyć poziom bezpieczeństwa dzięki zmniejszeniu liczby administratorów trwałych na maszynach.
Robi to przez utworzenie nowego punktu wejścia dla użytkowników do zarządzania systemem (Konfiguracja sesji programu PowerShell), który jest ściśle zablokowana domyślnie, aby uniemożliwić nadużycia.
Użytkownicy, którzy muszą niektóre, ale nie nieograniczony dostęp do komputera, aby wykonywać zadania administracyjne można udzielić dostępu do punktu końcowego JEA.
Ponieważ JEA umożliwia ich wykonywania polecenia administratora bezpośrednio, bez dostępu administratora, możesz usunąć tych użytkowników z grup zabezpieczeń o wysokim poziomie uprawnień (były użytkownicy standardowi).

W tym temacie opisano model zabezpieczeń usługi JEA i najlepsze rozwiązania, które bardziej szczegółowo.

## <a name="run-as-account"></a>Konto Uruchom jako

Każdy punkt końcowy usługi JEA ma konto wyznaczonym "Uruchom jako", czyli konta, w którym użytkownik nawiązujący połączenie czynności.
To konto jest konfigurowane w [plik konfiguracji sesji](session-configurations.md), i konta, możesz wybrać ma istotny wpływ na zabezpieczenia punktu końcowego usługi.

**Kont wirtualnych** to zalecany sposób konfigurowania opcji Uruchom jako konta.
Kont wirtualnych są jednorazowe, tymczasowy kont lokalnych, które są tworzone dla użytkownik nawiązujący połączenie do użycia w czasie trwania sesji JEA.
Zaraz po ich sesja została przerwana, wirtualnego konta zostaną usunięte i nie można już używać.
Użytkownik nawiązujący połączenie nie może określić poświadczenia dla konta wirtualnego i nie można używać konta wirtualnej dostęp do systemu za pomocą innych środków, takich jak pulpitu zdalnego lub nieograniczonego punktu końcowego programu PowerShell.

Domyślnie kont wirtualnych należeć do lokalnej grupy administratorów na komputerze.
To daje im pełne prawa do niczego w systemie zarządzania, ale żadnych praw do zarządzania zasobami w sieci.
Podczas uwierzytelniania z innymi maszynami, kontekst użytkownika będzie z konta komputera lokalnego konta wirtualnego.

Kontrolery domeny są szczególny przypadek, ponieważ nie obowiązuje koncepcja lokalnej grupy administratorów.
Zamiast kont wirtualnych należą administratorzy domeny i zarządzać usługi katalogowe na kontrolerze domeny.
Tożsamość domeny jest nadal ograniczona do użycia na kontrolerze domeny, której wystąpienia sesji JEA i dostępu do żadnych sieci pojawią się pochodzić z obiektu komputera kontrolera domeny, zamiast tego.

W obu przypadkach można także jawnie zdefiniować grupy zabezpieczeń, które konta wirtualnej powinny należeć do.
Jest dobrą praktyką, gdy zadanie, które wykonujesz, możesz zrobić bez uprawnień administratora lokalnego/domeny.
Jeśli masz już grupę zabezpieczeń zdefiniowane dla administratorów, można po prostu udzielić członkostwa wirtualnego konta do tej grupy w celu nadania mu uprawnień, których potrzebuje.
Wirtualny, członkostwo w grupie kont jest ograniczona do lokalnych grup zabezpieczeń na stacji roboczej i elementów członkowskich serwerach, ale na kontrolerze domeny mogą być tylko członkowie grupy zabezpieczeń domeny.
Po określeniu jednego lub więcej grup zabezpieczeń dla konta wirtualnej należy do, już nie będą należeć do grup domyślnych (administratora lokalnego lub administratora domeny).

W poniższej tabeli podsumowano możliwych opcji konfiguracji i wynikowy uprawnienia dla kont wirtualnych

Typ komputera                | Konfiguracja grupy konta wirtualnego | Kontekst użytkownika lokalnego                                      | Kontekst użytkownika sieci
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Kontroler domeny            | Wartość domyślna                             | Użytkownik domeny, członek "*domeny*\Domain         | Konto komputera
Kontroler domeny            | Grupy w domenie A i B               | Użytkownik domeny, członek "*domeny*\A","*domeny*\B"       | Konto komputera
Serwera członkowskiego lub stacji roboczej | Wartość domyślna                             | Użytkownik lokalny, członek "*BUILTIN*\Administrators        | Konto komputera
Serwera członkowskiego lub stacji roboczej | Grupy lokalne, C i D                | Użytkownik lokalny, członek "*komputera*\C" i "*komputera*\D" | Konto komputera

Jeśli przyjrzymy się zdarzenia inspekcji zabezpieczeń i dzienniki zdarzeń aplikacji, zobaczysz, czy każdej sesji użytkownika JEA ma unikatowe konto wirtualne.
Dzięki temu można śledzić akcje użytkownika w punkcie końcowym usługi JEA dla oryginalnego użytkownika, który uruchomił polecenie.
Konta wirtualnej nazwy zgodne z formatem "Użytkownicy usługi WinRM wirtualnej\\WinRM\_oceny luk w zabezpieczeniach\_*ACCOUNTNUMBER*\_*domeny* \_ *sAMAccountName*"na przykład, jeśli użytkownik"Alicja"w domenie"Contoso"ponowne uruchomienie usługi w punktu końcowego JEA, nazwę użytkownika skojarzoną z dowolnego zdarzenia Menedżera sterowania usługami będzie" użytkowników wirtualnych WinRM\\WinRM\_ Oceny luk w zabezpieczeniach\_1\_contoso\_Alicja ".


**Grupa kont usług zarządzanych (kont Gmsa)** są przydatne, gdy serwer członkowski musi mieć dostęp do zasobów sieciowych w sesji JEA.
Przykład przypadek użycia to jest JEA punktu końcowego, który służy do kontrolowania dostępu do interfejsu API REST hostowany na innym komputerze.
To ułatwia pisanie funkcji dzięki żądaną wywołań interfejsu API REST, ale w celu uwierzytelnienia przy użyciu interfejsu API potrzebne tożsamości sieciowej.
Za pomocą konta usługi zarządzanych przez grupę pozwala "drugiego przeskoku" przy zachowaniu kontroli nad tym, którzy komputery można używać tego konta.
Czynne uprawnienia opcją gMSA są definiowane przez grupy zabezpieczeń (lokalnego lub domeny) do którego należy dane konta gMSA.

Gdy punkt końcowy usługi JEA jest skonfigurowany do używania konta gMSA, akcje dla wszystkich użytkowników usługi JEA pojawi się pochodzić z tej samej grupy zarządzane konto usługi.
Jest to jedyny sposób, można śledzić akcje do określonego użytkownika do identyfikowania zestawów polecenia uruchamiane w wykazie sesji programu PowerShell.

**Przekaż do poświadczeń** są używane, gdy nie określaj Uruchom jako konto się i nie ma programu PowerShell, Uruchom polecenia na serwerze zdalnym za pomocą poświadczeń użytkownik nawiązujący połączenie.
Ta konfiguracja jest *nie* zalecane dla usługi JEA, ponieważ wymagałoby przyznania łączące bezpośredni dostęp użytkowników do grup uprzywilejowanych zarządzania.
Jeśli użytkownik nawiązujący połączenie ma już uprawnienia administratora, są całkowicie uniknąć JEA i zarządzania systemem za pośrednictwem oznacza, że inne, nieograniczone.
Zobacz w poniższym rozdziale na temat [JEA nie chroni przed Administratorzy](#jea-does-not-protect-against-admins) Aby uzyskać więcej informacji.

**Standardowa Uruchom jako konta** pozwalają na określenie dowolnego konta użytkownika, na którym będzie uruchamiana podczas całej sesji programu PowerShell.
Jest to ważna różnica, ponieważ konfiguracja sesji skonfigurowany do używania stały Uruchom jako konto (przy użyciu `-RunAsCredential` parametr) nie są znane JEA.
Oznacza to, że definicje ról przestaną działać zgodnie z oczekiwaniami, a każdy użytkownik autoryzowany do dostępu do punktu końcowego zostanie przypisany tę samą rolę.

Nie należy używać RunAsCredential w punkcie końcowym usługi JEA ze względu na problemy w śledzeniu akcje do konkretnych użytkowników i brak obsługi mapowanie użytkowników do ról.

## <a name="winrm-endpoint-acl"></a>Listy ACL punktów końcowych usługi WinRM

Za pomocą regularnego punkty końcowe komunikacji zdalnej programu PowerShell, każdego punktu końcowego JEA ma oddzielne listy kontroli dostępu (ACL) w konfiguracji usługi WinRM, który kontroluje kto może uwierzytelniać przy użyciu punktu końcowego JEA.
Jeśli skonfigurowana niepoprawnie, zaufanych użytkownicy mogą nie mieć możliwość dostępu do punktu końcowego JEA i/lub niezaufanym użytkownikom może uzyskać dostęp.
Listy ACL usługi WinRM nie dotyczy jednak mapowanie użytkowników do ról usługi JEA.
Który jest kontrolowany przez *RoleDefinitions* pola w pliku konfiguracji sesji, który został zarejestrowany w systemie.

Domyślnie podczas rejestracji, punktu końcowego JEA przy użyciu pliku konfiguracji sesji i jedną lub kilkoma funkcjami roli listy ACL usługi WinRM zostaną skonfigurowane aby umożliwić wszystkim użytkownikom mapowanie na jeden lub więcej ról uprawnieniami do punktu końcowego.
Na przykład sesję JEA skonfigurowany przy użyciu następujących poleceń spowoduje przyznanie pełnego dostępu do *CONTOSO\JEA\_Lev1* i *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Można przeprowadzać ich inspekcje uprawnień użytkownika za pomocą [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) polecenia cmdlet.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Aby zmienić, którzy użytkownicy mają dostęp, uruchom `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` dla monitu interakcyjnego lub `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` można zaktualizować uprawnień.
Użytkownicy muszą się przynajmniej *Invoke* praw dostępu do punktu końcowego JEA.

Jeśli dodatkowi użytkownicy uzyskują dostęp do punktu końcowego JEA, ale nie należą do żadnych ról zdefiniowane w pliku konfiguracji sesji, będą mogli rozpocząć sesję JEA, ale tylko mają dostęp do poleceń cmdlet programu domyślnego.
Można przeprowadzać ich inspekcje uprawnienia użytkownika w punkcie końcowym usługi JEA, uruchamiając `Get-PSSessionCapability`.
Zapoznaj się z [inspekcji i raporty dotyczące technologii JEA](audit-and-report.md) artykuł, aby uzyskać więcej informacji na temat inspekcji polecenia użytkownika, które ma dostęp do w punktu końcowego JEA.

## <a name="least-privilege-roles"></a>Co najmniej role uprawnień

Podczas projektowania technologii JEA ról, to należy pamiętać, że wirtualny lub grupy usługi zarządzanej konta działa w tle często ma nieograniczony dostęp do funkcji zarządzania na komputerze lokalnym.
Możliwości roli JEA pomagają ograniczyć, jakie to konto może służyć do, ograniczając polecenia i aplikacje, które mogą być uruchamiane przy użyciu tego kontekstu uprzywilejowanych.
Nieprawidłowo zaprojektowane role można zezwolić na niebezpiecznych uruchamiania poleceń, które umożliwiają użytkownikowi zerwać granice JEA lub uzyskać dostępu do poufnych informacji.

Na przykład rozważmy następujący wpis możliwości roli:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Ta funkcja roli umożliwia użytkownikom uruchamianie każdego polecenia cmdlet programu PowerShell przy użyciu rzeczownik "Procesu" z modułu Microsoft.PowerShell.Management.
Użytkownicy może być konieczne dostęp do poleceń cmdlet, takich jak `Get-Process` Aby zrozumieć, jakie aplikacje działają w systemie i `Stop-Process` kill dowolne zawiesiła się w aplikacji.
Jednak ten wpis umożliwia także `Start-Process`, który może służyć do uruchamiania dowolnego programu z uprawnieniami administrator o pełnych uprawnieniach.
Program nie musi być zainstalowana lokalnie w systemie, dzięki czemu osoba atakująca może po prostu uruchomić program w udziale plików, zapewniającej połączenia użytkownikowi uprawnienia administratora lokalnego, uruchomienia złośliwego oprogramowania i nie tylko. "

Bardziej bezpieczna wersja ta sama funkcja roli będzie wyglądać:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Unikaj używania symboli wieloznacznych w możliwości roli i pamiętaj, aby [inspekcji uprawnienia obowiązująca nazwa użytkownika](audit-and-report.md#check-effective-rights-for-a-specific-user) regularnie, aby zrozumieć, które polecenia użytkownik ma dostęp do.

## <a name="jea-does-not-protect-against-admins"></a>JEA nie chroni przed administratorów

Jedną z podstawowych zasad JEA jest możliwość użytkowników innych niż administratorzy w celu wykonania *niektóre* zadań administracyjnych.
JEA nie chroni przed tych, którzy już mają uprawnienia administratora.
Użytkownicy którzy należą "Administratorzy domeny," "Administratorzy lokalni" lub innych wysoce uprzywilejowanych grup w danym środowisku nadal będzie można obejść zabezpieczenia JEA firmy, logując się do komputera za pomocą innych metod.
One można na przykład, zaloguj się przy użyciu protokołu RDP, użyj zdalnych konsol programu MMC lub nawiązać połączenie z użyciem środowiska PowerShell punktów końcowych.
Administratorzy lokalni w systemie można również zmodyfikować konfiguracje JEA, aby umożliwić innym użytkownikom do zarządzania systemem lub zmienić możliwości roli, aby rozszerzyć zakres co użytkownik może zrobić w ich sesji usługi JEA.
W związku z tym jest ważne, aby ocenić użytkowników usługi JEA rozszerzone uprawnienia, aby zobaczyć, czy istnieją inne sposoby ich może uzyskać uprzywilejowany dostęp do systemu.

Powszechną praktyką jest korzystają z technologii JEA dla codziennej konserwacji i mają "dokładnie na czas" uprzywilejowany rozwiązania do zarządzania dostępem Zezwalaj użytkownikom na tymczasowo stają się administratorami lokalnymi sytuacji awaryjnych.
Dzięki temu użytkownicy nie są trwałe Administratorzy w systemie, ale można uzyskać te prawa, jeśli i tylko wtedy, gdy ich zakończeniu przepływu pracy, która dokumentuje ich użycie tych uprawnień.