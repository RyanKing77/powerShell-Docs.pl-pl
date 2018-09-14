---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Konfiguracje sesji usługi JEA
ms.openlocfilehash: bdf3659357045203d90e8083613e51cce657da1a
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522966"
---
# <a name="jea-session-configurations"></a>Konfiguracje sesji usługi JEA

> Dotyczy: Windows PowerShell 5.0

Punkt końcowy usługi JEA jest zarejestrowany w systemie, tworząc i rejestrowanie pliku konfiguracji sesji programu PowerShell w określony sposób.
Określenia konfiguracji sesji *kto* można używać punktu końcowego JEA i role, które będzie miał dostęp do.
Mogą również określać ustawienia globalne, które mają zastosowanie do użytkowników każdej roli w sesji JEA.

W tym temacie opisano, jak utworzyć plik konfiguracji sesji programu PowerShell i zarejestrować punktu końcowego JEA.

## <a name="create-a-session-configuration-file"></a>Utwórz plik konfiguracji sesji

Aby można było zarejestrować punkt końcowy usługi JEA, należy określić, jak skonfigurować punkt końcowy.
Istnieje wiele opcji, należy wziąć pod uwagę w tym miejscu najważniejsze które bycia kto powinien mieć dostęp do punktu końcowego JEA, które role będzie ich można przypisać tożsamość usługi JEA użyje w sposób niewidoczny i co to jest nazwa punktu końcowego JEA.
Te są definiowane w pliku konfiguracji sesji programu PowerShell, który plik danych programu PowerShell kończy się rozszerzeniem .pssc.

Aby utworzyć plik konfiguracji sesji szkielet dla punktów końcowych JEA, uruchom następujące polecenie.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Tylko najbardziej typowe opcje konfiguracji są domyślnie dołączone w szkielet pliku.
> Użyj `-Full` przełącznik, aby uwzględnić wszystkie ustawienia mające zastosowanie w wygenerowanym Współpracuje.

Plik konfiguracji sesji można otworzyć w dowolnym edytorze tekstów.
`-SessionType RestrictedRemoteServer` Pole wskazuje, używane przez usługi JEA do bezpiecznego zarządzania z konfiguracji sesji.
Sesje skonfigurowane w ten sposób będzie działał w [tryb NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) i może zawierać tylko następujące polecenia 8 domyślne (i aliasy) dostępne:

- Clear-Host (zgodne ze specyfikacją, usuń zaznaczenie)
- PSSession zakończenia (exsn, zakończenia)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- (Środek) dla obiektu w miary
- Wyewidencjonowanie i domyślne
- Select-Object (wybór)

Żaden dostawca programu PowerShell są dostępne, podobnie jak wszelkie zewnętrznych programów (plików wykonywalnych, skryptów, itp.).

Istnieje kilka innych pól, które można skonfigurować dla sesji JEA.
Zostały one omówione w poniższych sekcjach.

### <a name="choose-the-jea-identity"></a>Wybierz tożsamość usługi JEA

Za kulisami usługi JEA musi tożsamość (konto), aby używać podczas uruchamiania polecenia połączonych użytkowników.
Możesz zdecydować, tożsamość usługi JEA zostaną użyte w pliku konfiguracji sesji.

#### <a name="local-virtual-account"></a>Konto wirtualne

Jeśli role obsługiwane przez ten punkt końcowy usługi JEA są używane do zarządzania na komputerze lokalnym, a konto administratora lokalnego jest wystarczające do uruchomienia pomyślnie poleceń, należy skonfigurować usługi JEA do używania konta lokalnego wirtualnego.
Kont wirtualnych są tymczasowego konta, które są unikatowe dla określonego użytkownika i tylko ostatni czas trwania sesji programu PowerShell.
Na serwerze członkowskim lub stacji roboczej, kont wirtualnych należy na komputerze lokalnym **Administratorzy** grupy i mieć dostęp do większości zasobów systemowych.
Na kontrolerze domeny usługi Active Directory kont wirtualnych należą do tej domeny **Administratorzy domeny** grupy.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Role obsługiwane przez tę konfigurację sesji nie wymagają takiego szerokie uprawnienia, opcjonalnie możesz określić grupy zabezpieczeń, do których będą należeć konta wirtualnego.
Dla serwera członkowskiego lub stacji roboczej do określonych grup zabezpieczeń musi być grupy lokalne, a nie grupy z domeny.

Gdy określona jest co najmniej jedną grupę zabezpieczeń, konta wirtualnej już nie będą należeć do grupy administratorów lokalnego lub domeny.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Konto usługi zarządzane przez grupę


W scenariuszach wymagających JEA użytkownikowi dostęp do zasobów sieciowych, takich jak innych maszyn lub usług sieci web konto usługi zarządzanych przez grupę (gMSA) jest bardziej odpowiednia tożsamość do użycia.
konta gMSA zapewniają tożsamość domeny, która może służyć do uwierzytelniania względem zasobów na dowolnym komputerze w domenie.
Prawa zapewnia konta gMSA, który jest określany przez zasoby uzyskujesz dostęp do usługi.
Nie będziesz automatycznie mieć uprawnienia administratora na wszystkich maszynach lub usługi, chyba że administrator komputera/usługi ma jawnie przyznane uprawnienia konta gMSA uprawnień administratora.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

konta gMSA powinny być używane tylko podczas dostępu do zasobów sieciowych wymaganych kilka powodów:

- Jest trudniejsze wywodzić akcje użytkownika, gdy przy użyciu konta gMSA, ponieważ każdy użytkownik udostępnia taką samą tożsamość Uruchom jako. Należy zapoznać się z zapisy sesji programu PowerShell i dzienniki, aby skorelować użytkowników z ich działania.

- Dane konta gMSA mogą mieć dostęp do wielu zasobów sieciowych, których należy użytkownik nawiązujący połączenie nie wymaga dostępu do. Zawsze próbuje ograniczyć czynne uprawnienia w ramach sesji usługi JEA do wykonania zasadę najmniejszych uprawnień.

> [!NOTE]
> Konta usług zarządzane przez grupę tylko są dostępne w programie Windows PowerShell 5.1 lub nowszej i na komputerach przyłączonych do domeny.


#### <a name="more-information-about-run-as-users"></a>Więcej informacji na temat uruchamiania jako użytkownicy

Dodatkowe informacje na temat wykonywania jako tożsamości i jak mogą wziąć pod uwagę w zabezpieczenia sesji JEA znajdują się w [zagadnienia dotyczące zabezpieczeń](security-considerations.md) artykułu.

### <a name="session-transcripts"></a>Zapisy sesji

Zalecane jest, aby skonfigurować plik konfiguracji usługi JEA sesji, aby automatycznie rejestrował transkrypcji sesje użytkowników.
Zapisy sesji programu PowerShell zawierają informacje o użytkownik nawiązujący połączenie Uruchom jako tożsamość przypisaną do nich, i polecenia są uruchamiane przez użytkownika.
Może być przydatne do inspekcji zespołu, która musi wiedzieć, kto wykonał określonej zmiany w systemie.

Aby skonfigurować transkrypcje automatyczne w pliku konfiguracji sesji, należy podać ścieżkę do folderu przechowywania transkrypcji.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Aby uniemożliwić użytkownikom modyfikowanie lub usuwanie żadnych danych, należy skonfigurować określonego folderu.
Zapisy są zapisywane w folderze, konto System lokalny, który wymaga dostępu odczytu i zapisu do katalogu.
Użytkownicy standardowi nie powinny mieć dostępu do folderu, a ograniczony zestaw zabezpieczeń Administratorzy powinni mieć dostęp do inspekcji transkrypcji.

### <a name="user-drive"></a>Dysku użytkownika

Połączenie użytkownicy muszą kopiować pliki z punktu końcowego JEA w celu uruchomienia polecenia, po włączeniu dysku użytkownika w pliku konfiguracji sesji.
Dysk użytkownika jest [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) który jest mapowany do unikatowego folderu dla każdego użytkownika nawiązującego połączenie.
Ten folder służy jako miejsce dla nich skopiować pliki z systemu, bez udzielania dostępu do systemu plików pełnej lub udostępnianie dostawcy FileSystem.
Zawartość dysku użytkownika są trwałe dla wszystkich sesji, aby dopasować sytuacje, w którym mogą zostać przerwane połączenie sieciowe.

```powershell
MountUserDrive = $true
```

Domyślnie dysku użytkownika pozwala przechowywać maksymalnie 50MB danych dla poszczególnych użytkowników.
Można ograniczyć ilość danych, użytkownik może zużywać z *UserDriveMaximumSize* pola.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Jeśli chcesz, aby dane na dysku użytkownika były trwałe, można skonfigurować zaplanowane zadanie w systemie, aby automatycznie oczyścić folderu każdej nocy.

> [!NOTE]
> Dysku użytkownika jest dostępne tylko w programie Windows PowerShell 5.1 lub nowszej.

### <a name="role-definitions"></a>Definicje ról

Definicje ról w pliku konfiguracji sesji zdefiniować mapowanie *użytkowników* do *role*.
Każdego użytkownika lub grupy uwzględnione w tym polu będzie automatycznie otrzymuje uprawnienie do punktu końcowego JEA po jej zarejestrowaniu.
Każdy użytkownik lub grupa może być uwzględniany jako klucz w tablicy skrótów tylko raz, ale można przypisać wiele ról.
Nazwa możliwości roli powinna być nazwą pliku możliwości roli, bez rozszerzenia .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Jeśli użytkownik należy do więcej niż jednej grupy w definicji roli, uzyskują dostęp do ról każdego z nich.
Jeśli dwie role udzielić dostępu do tego samego polecenia cmdlet, restrykcyjny zestaw parametrów zostaną przyznane użytkownikowi.

Podczas określania lokalnych użytkowników lub grupy w polu definicji roli, należy użyć nazwy komputera (nie *localhost* lub *.*) przed ukośnik odwrotny.
Sprawdź nazwę komputera, sprawdzając `$env:computername` zmiennej.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Kolejność wyszukiwania możliwości roli
Jak pokazano w powyższym przykładzie, możliwości roli odwołuje się płaskiej nazwy (nazwa pliku bez rozszerzenia) pliku możliwości roli.
Jeśli wiele możliwości roli są dostępne w systemie o takiej samej nazwie prostego, programu PowerShell użyje jej kolejność wyszukiwania niejawne aby wybrać plik możliwości roli.
Będzie ono **nie** udzielić dostępu do wszystkich plików możliwości rolę o takiej samej nazwie.

Korzysta z technologii JEA `$env:PSModulePath` zmiennej środowiskowej, aby określić, które ścieżki do skanowania w poszukiwaniu plików możliwości roli.
W ramach każdej z tych ścieżek JEA będzie szukał prawidłowe moduły programu PowerShell, które zawierają podfolder "RoleCapabilities".
Podobnie jak w przypadku importowania modułów, JEA preferuje możliwości roli, które są dostarczane z programem Windows z funkcjami rola niestandardowa o takiej samej nazwie.
Wszystkie inne konflikty nazewnictwa pierwszeństwo zależy od kolejności, w którym Windows wylicza pliki w katalogu (nie musi być w kolejności alfabetycznej).
Pierwszy plik możliwości roli znaleziono żądany nazwa będzie używana dla użytkownik nawiązujący połączenie.

Ponieważ kolejność wyszukiwania funkcja ról nie jest jednoznaczny. gdy dwie lub więcej możliwości roli ma taką samą nazwę, jest **zdecydowanie zaleca się** zapewnienia możliwości roli mają unikatowe nazwy na swojej maszynie.

### <a name="conditional-access-rules"></a>Zasady dostępu warunkowego

Wszyscy użytkownicy i grupy w polu RoleDefinitions automatycznie uzyskają dostęp do punktów końcowych JEA.
Zasady dostępu warunkowego pozwalają dostosować ten dostęp i Wymagaj od użytkowników należą do grup zabezpieczeń, które nie wpływają na role, które są przypisane.
Może to być przydatne, jeśli chcesz zintegrować "dokładnie na czas" uprzywilejowany dostęp do rozwiązania do zarządzania, uwierzytelnianie karty inteligentnej lub innego rozwiązania do uwierzytelniania wieloskładnikowego za pomocą technologii JEA.

Zasady dostępu warunkowego są definiowane w polu RequiredGroups w pliku konfiguracji sesji.
Tam możesz podać hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do konstruowania reguły.
Poniżej przedstawiono kilka przykładów jak korzystać z tego pola:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> Zasady dostępu warunkowego są tylko dostępne w programie Windows PowerShell 5.1 lub nowszej.

### <a name="other-properties"></a>Inne właściwości
Pliki konfiguracji sesji można robić wszystko, co można zrobić plik możliwości roli, po prostu bez możliwości daje łączącego się użytkownikom dostęp do różnych poleceń.
Jeśli chcesz umożliwić wszystkim użytkownikom dostępu do określonych poleceń cmdlet, funkcji lub dostawców, możesz to zrobić bezpośrednio w pliku konfiguracji sesji.
Aby uzyskać pełną listę obsługiwanych właściwości w pliku konfiguracji sesji, należy uruchomić `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Plik konfiguracji sesji testowania

Możesz przetestować konfiguracji sesji przy użyciu [PSSessionConfigurationFile testu](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) polecenia cmdlet.
Zdecydowanie zaleca się przetestowanie pliku konfiguracji sesji, jeśli edytowano plik współpracuje ręcznie za pomocą edytora tekstów, aby upewnić się, że składnia jest poprawna.
Jeśli plik konfiguracji sesji nie zakończy się pomyślnie tego testu, nie można pomyślnie można zarejestrować w systemie.

## <a name="sample-session-configuration-file"></a>Przykładowy plik konfiguracji sesji

Poniżej znajduje się pełny przykład przedstawiający sposób tworzenia i sprawdzania poprawności konfiguracji sesji dla usługi JEA.
Należy pamiętać, że definicje ról są tworzone i przechowywane w `$roles` zmiennej dla wygody i czytelności.
Nie jest to wymagane, aby to zrobić.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Aktualizowanie plików konfiguracji sesji

Jeśli zachodzi potrzeba zmiany właściwości konfiguracji sesji, JEA, w tym mapowanie użytkowników do ról, musisz najpierw [wyrejestrować](register-jea.md#unregistering-jea-configurations) i [ponownie zarejestrować](register-jea.md) JEA konfiguracji sesji.
Gdy ponownie zarejestrować JEA konfiguracji sesji, użyj zaktualizowanych zawierający potrzebne zmiany pliku konfiguracji sesji programu PowerShell.

## <a name="next-steps"></a>Następne kroki

- [Rejestruj konfigurację usługi JEA](register-jea.md)
- [Role usługi JEA autora](role-capabilities.md)