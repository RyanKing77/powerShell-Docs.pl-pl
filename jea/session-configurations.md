---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Konfiguracje sesji JEA
ms.openlocfilehash: 3e5a663be8e7aba09a2592c278224cd892c89a20
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="jea-session-configurations"></a>Konfiguracje sesji JEA

> Dotyczy: środowiska Windows PowerShell 5.0

Punkt końcowy JEA jest zarejestrowany w systemie przez utworzenie i zarejestrowanie plik konfiguracji sesji programu PowerShell w określony sposób.
Określenia konfiguracji sesji *kto* można używać punktu końcowego JEA i role, które będą mają dostęp.
Określają one ustawienia globalne, które są stosowane do użytkowników z dowolnej roli w sesji JEA.

W tym temacie opisano, jak utworzyć plik konfiguracji sesji programu PowerShell i zarejestrować punkt końcowy JEA.

## <a name="create-a-session-configuration-file"></a>Utwórz plik konfiguracji sesji

Aby można było zarejestrować punkt końcowy JEA, należy określić konfiguracji tego punktu końcowego.
Istnieje wiele opcji, należy wziąć pod uwagę w tym miejscu najważniejsze które są kto ma dostęp do punktu końcowego JEA, role będą one można przypisać tożsamość będzie JEA używają i jakie będą Nazwa punktu końcowego JEA.
Są one wszystkie zdefiniowane w pliku konfiguracji sesji programu PowerShell, który plik programu PowerShell danych kończy się rozszerzeniem .pssc.

Aby utworzyć plik konfiguracji sesji szkielet dla punktów końcowych JEA, uruchom następujące polecenie.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Tylko najbardziej typowe opcje konfiguracji są domyślnie dołączone w pliku szkielet.
> Użyj `-Full` przełącznik, aby uwzględnić wszystkie ustawienia mające zastosowanie w wygenerowanym Współpracuje.

Plik konfiguracji sesji można otworzyć w dowolnym edytorze tekstów.
`-SessionType RestrictedRemoteServer` Pole wskazuje używany przez JEA bezpiecznego zarządzania z konfiguracji sesji.
Sesje skonfigurowane w ten sposób będzie działać w [tryb NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) i może zawierać tylko następujące polecenia 8 domyślne (i aliasy) dostępne:

- Wyczyść-Host (ze specyfikacją cls, wyczyść)
- Zakończ-PSSession (exsn, zakończenia)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Miara — obiekt (miary)
- Domyślna wyjściowego
- Select-Object (zaznacz)

Nie dostawcy programu PowerShell są dostępne, ani się, że wszystkie zewnętrzne programy (pliki wykonywalne, skrypty itp.).

Istnieje kilka innych pól, które można skonfigurować dla sesji JEA.
Zostały one omówione w poniższych sekcjach.

### <a name="choose-the-jea-identity"></a>Wybierz tożsamość JEA

W tle JEA musi tożsamości (konto) do użycia podczas uruchamiania polecenia podłączonego użytkownika.
Możesz zdecydować, tożsamość JEA będzie używany w pliku konfiguracji sesji.

#### <a name="local-virtual-account"></a>Lokalne konto wirtualne

Jeśli role obsługiwane przez ten punkt końcowy JEA są używane do zarządzania na komputerze lokalnym, a konto administratora lokalnego jest wystarczająca do uruchomienia polecenia, należy skonfigurować JEA się za pomocą konta lokalnego wirtualnego.
Konta wirtualne są tymczasowego konta, które są unikatowe dla określonego użytkownika i tylko ostatni czas trwania sesji programu PowerShell.
Na serwerze członkowskim lub stacji roboczej, kont wirtualnych należy na komputerze lokalnym **Administratorzy** grupy i mają dostęp do większości zasobów systemowych.
Na kontrolerze domeny usługi Active Directory kont wirtualnych należą do tej domeny **Administratorzy domeny** grupy.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Jeśli role obsługiwany przez konfigurację sesji nie wymagają takiego szerokie uprawnienia, opcjonalnie możesz określić grupy zabezpieczeń, do których będą należeć Konto wirtualne.
Na serwerze członkowskim lub stacji roboczej do określonych grup zabezpieczeń musi być grup lokalnych nie grupy z domeny.

Jeśli określona jest co najmniej jedną grupę zabezpieczeń konta wirtualnego będzie już należy do grupy administratorów lokalnego lub domeny.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Konto usługi zarządzane przez grupę


W scenariuszach wymagających JEA użytkownikowi dostęp do zasobów sieciowych, takich jak inne maszyny lub usługi sieci web konto usługi zarządzane przez grupę (gMSA) jest bardziej odpowiednia tożsamości do użycia.
konta gMSA zapewniają tożsamość domeny, która może służyć do uwierzytelniania względem zasobów na dowolnym komputerze w domenie.
Prawa zapewnia konto usługi zarządzane przez grupę, jest określany przez zasoby masz dostęp.
Nie automatycznie ma prawa administratora na wszystkie maszyny lub usługi, chyba że administrator maszyny/usługi ma jawnie przyznane uprawnienia tego konta gMSA uprawnień administratora.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

konta gMSA należy używać tylko podczas dostępu do zasobów sieciowych są wymagane do kilku powodów:

- Jest trudniej wywodzić akcje użytkownika, gdy za pomocą konta gMSA, ponieważ każdy użytkownik udostępnia tej samej tożsamości Uruchom jako. Należy zapoznać się dzienniki służące do skorelowania użytkowników z ich działania i zapisy sesji programu PowerShell.

- Konta gMSA mogą mieć dostęp do wielu zasobów sieciowych, które użytkownik nawiązujący połączenie nie potrzebują dostępu do. Zawsze spróbuj ograniczyć czynnych uprawnień w sesji JEA postępuj zgodnie z zasadą najniższych uprawnień.

> [!NOTE]
> Konta usług zarządzane przez grupę tylko są dostępne w programie Windows PowerShell 5.1 lub nowszej i na komputerach przyłączonych do domeny.


#### <a name="more-information-about-run-as-users"></a>Więcej informacji na temat uruchamiania jako użytkowników

Dodatkowe informacje na temat uruchamiania jako tożsamości i jak uwzględnić ich bezpieczeństwo sesji JEA znajdują się w [zagadnienia dotyczące zabezpieczeń](security-considerations.md) artykułu.

### <a name="session-transcripts"></a>Zapisy sesji

Zalecane jest skonfigurowanie plik konfiguracji sesji JEA automatyczne rejestrowanie zapisy sesji użytkowników.
Zapisy sesji programu PowerShell zawierają informacje o użytkownik nawiązujący połączenie, Uruchom jako tożsamość przypisana, i polecenia uruchamiane przez użytkownika.
Mogą być przydatne do inspekcji zespołu, który wymaga, aby zrozumieć, kto wykonał określonej zmiany do systemu.

Aby skonfigurować automatyczne zapisu w pliku konfiguracji sesji, należy podać ścieżkę do folderu przechowywania zapisów.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Określony folder należy skonfigurować tak, aby uniemożliwić użytkownikom modyfikacja lub usunięcie wszystkich danych w ramach tego.
Zapisy są zapisywane w folderze przy użyciu konta systemu lokalnego, uprawnienia do odczytu i zapisu do katalogu.
Użytkownicy standardowi powinien nie masz dostępu do folderu, a ograniczony zestaw zabezpieczeń Administratorzy powinni mieć dostęp do inspekcji zapisów.

### <a name="user-drive"></a>Stacji użytkownika

Łączącego użytkownicy muszą do kopiowania plików z punktu końcowego JEA, aby można było uruchomić polecenie, po włączeniu dysku użytkownika w pliku konfiguracji sesji.
Dysk użytkownika jest [elementu PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) który jest mapowany do unikatowego folderu dla każdego użytkownika łączącego.
Ten folder pełni miejsca, aby skopiować pliki z systemu, bez udzielania dostępu do systemu plików pełnego lub udostępnianie dostawcy FileSystem.
Zawartość dysku użytkownika są trwałe między sesjami, aby zmieścił się w sytuacjach, w którym można przerwać połączenie sieciowe.

```powershell
MountUserDrive = $true
```

Domyślnie dysku użytkownika umożliwia przechowywanie maksymalnie 50MB danych dla poszczególnych użytkowników.
Można ograniczyć ilość danych, które użytkownik może korzystać z *UserDriveMaximumSize* pola.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Jeśli nie chcesz, aby dane na dysku użytkownika były trwałe, zaplanowane zadanie można skonfigurować w systemie, aby wyczyścić automatycznie folderze każdej nocy.

> [!NOTE]
> Dysku użytkownika jest dostępne wyłącznie w programie Windows PowerShell 5.1 lub nowszej.

### <a name="role-definitions"></a>Definicje ról

Definicje ról w pliku konfiguracji sesji zdefiniować mapowanie *użytkowników* do *ról*.
Każdy użytkownik lub grupa zawarte w tym polu będzie automatycznie mieć uprawnienie do punktu końcowego JEA gdy jest on zarejestrowany.
Każdy użytkownik lub grupa może być uwzględniana jako klucz w tablicy skrótów tylko raz, ale można przypisać wiele ról.
Nazwa roli możliwości powinna być nazwa pliku możliwości roli, bez rozszerzenia .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Jeśli użytkownik należy do więcej niż jednej grupy w definicji roli, otrzyma dostęp do poszczególnych ról.
Jeśli dwie role udzielić dostępu do tych samych poleceń cmdlet, najbardziej ograniczająca zestaw parametrów zostaną przyznane użytkownikowi.

Podczas określania lokalnych użytkowników lub grupy w polu definicji roli, należy użyć nazwy komputera (nie *localhost* lub *.*) przed ukośniku odwrotnym.
Sprawdź nazwę komputera, sprawdzając `$env:computername` zmiennej.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Kolejność wyszukiwania możliwości roli
Jak pokazano w przykładzie powyżej, możliwości roli odwołuje się płaskiej nazwy (nazwa pliku bez rozszerzenia) pliku możliwości roli.
Jeśli wiele możliwości roli są dostępne w systemie o takiej samej nazwie prosty, programu PowerShell użyje ich kolejność niejawnego wyszukiwania i wybierz plik możliwości roli.
Będzie on **nie** zapewniają dostęp do wszystkich plików możliwości Rola o tej samej nazwie.

Używa JEA `$env:PSModulePath` zmiennej środowiskowej, aby określić, które ścieżki do skanowania w poszukiwaniu plików możliwości roli.
W każdej z tych ścieżek JEA będzie szukać prawidłowy moduły programu PowerShell zawierających podfolder "RoleCapabilities".
Podobnie jak w przypadku importowania modułów, JEA preferuje możliwości roli, które są dostarczane z systemem Windows do funkcji rola niestandardowa o takiej samej nazwie.
Dla wszystkich innych konfliktów nazw pierwszeństwo jest określana przez kolejność, w którym system Windows wylicza pliki w katalogu (nie gwarantuje to w kolejności alfabetycznej).
Znaleziono plik możliwości roli, które odpowiadają żądaną nazwa będzie używana dla użytkownik nawiązujący połączenie.

Ponieważ kolejność wyszukiwania możliwości rola nie jest deterministyczna, gdy dwie lub więcej możliwości Rola o tej samej nazwie, jest **zdecydowanie zalecane** zapewnienia możliwości roli mają unikatowe nazwy na tym komputerze.

### <a name="conditional-access-rules"></a>Zasady dostępu warunkowego

Wszyscy użytkownicy i grupy w polu RoleDefinitions automatycznie otrzymują dostęp do punktów końcowych JEA.
Zasady dostępu warunkowego umożliwiają uściślić dostęp i wymaganie od użytkowników należą do grup zabezpieczeń, które nie wpływają na role, które są przypisane.
Może to być przydatne, jeśli chcesz zintegrować "tylko w czasie" uprzywilejowany dostęp do rozwiązania do zarządzania, uwierzytelnienie karty inteligentnej lub innego rozwiązania do uwierzytelniania wieloskładnikowego z JEA.

Zasady dostępu warunkowego są definiowane w polu RequiredGroups w pliku konfiguracji sesji.
Istnieje, możesz podać hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do utworzenia reguły.
Oto kilka przykładów sposób korzystania z tego pola:

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
Pliki konfiguracji sesji można również wszystkiego plik możliwości roli można wykonać, tylko bez możliwości daje łączącego użytkownikom dostęp do różnych poleceń.
Jeśli chcesz zezwolić wszystkim użytkownikom dostępu do określonych poleceń cmdlet, funkcji lub dostawców, możesz to zrobić bezpośrednio w pliku konfiguracji sesji.
Aby uzyskać pełną listę obsługiwanych właściwości w pliku konfiguracji sesji, uruchom `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Plik konfiguracji sesji testowania

Można przetestować konfiguracji sesji przy użyciu [PSSessionConfigurationFile testu](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) polecenia cmdlet.
Zdecydowanie zaleca się przetestowanie pliku konfiguracji sesji, edytując plik współpracuje ręcznie przy użyciu edytora tekstów, aby upewnić się, że składnia jest poprawna.
Jeśli plik konfiguracji sesji tego testu nie zostały spełnione, nie można pomyślnie można zarejestrować w systemie.

## <a name="sample-session-configuration-file"></a>Przykładowy plik konfiguracji sesji

Poniżej znajduje się pełny przykład przedstawiający sposób tworzenia i weryfikowanie konfiguracji sesji dla JEA.
Należy pamiętać, że definicje ról są tworzone i przechowywane w `$roles` zmiennej dla wygody i czytelności.
Nie jest wymagane w tym celu.

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

Jeśli musisz zmienić właściwości konfiguracji sesji, JEA, w tym mapowanie użytkowników do ról, należy najpierw [wyrejestrować](register-jea.md#unregistering-jea-configurations) i [ponownie zarejestrować](register-jea.md) JEA konfiguracji sesji.
Gdy ponownie zarejestrować JEA konfiguracji sesji, użyj zaktualizowane zawierającego odpowiednie zmiany pliku konfiguracji sesji programu PowerShell.

## <a name="next-steps"></a>Następne kroki

- [Rejestruj konfigurację JEA](register-jea.md)
- [Autor JEA ról](role-capabilities.md)