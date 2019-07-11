---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Konfiguracje sesji usługi JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726550"
---
# <a name="jea-session-configurations"></a>Konfiguracje sesji usługi JEA

Punkt końcowy usługi JEA jest zarejestrowany w systemie, tworząc i rejestrowanie w pliku konfiguracji sesji programu PowerShell. Konfiguracje sesji zdefiniować, kto może korzystać z punktu końcowego JEA i które role mają dostęp. Mogą również określać ustawienia globalne, które są stosowane do wszystkich użytkowników sesji JEA.

## <a name="create-a-session-configuration-file"></a>Utwórz plik konfiguracji sesji

Rejestrowanie punktu końcowego JEA, należy określić, jak ten punkt końcowy został skonfigurowany. Istnieje wiele opcji, należy wziąć pod uwagę. Najważniejsze opcje są następujące:

- Kto ma dostęp do punktu końcowego JEA
- Role można przypisać
- Tożsamość usługi JEA używa w tle
- Nazwa punktu końcowego usługi JEA

Te opcje są zdefiniowane w pliku danych programu PowerShell przy użyciu `.pssc` rozszerzenia znany jako plik konfiguracji sesji programu PowerShell. Plik konfiguracji sesji można edytować za pomocą dowolnego edytora tekstów.

Uruchom następujące polecenie, aby utworzyć pusty szablon pliku konfiguracji.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Tylko najbardziej typowe opcje konfiguracji są domyślnie dołączone w pliku szablonu. Użyj `-Full` przełącznik, aby uwzględnić wszystkie ustawienia mające zastosowanie w wygenerowanym Współpracuje.

`-SessionType RestrictedRemoteServer` Pole wskazuje, że konfiguracja sesji jest używany przez usługi JEA do bezpiecznego zarządzania. Sesje tego typu działają w **NoLanguage** tryb i mieć dostęp tylko do następujących domyślnych poleceń (i aliasy):

- Clear-Host (zgodne ze specyfikacją, usuń zaznaczenie)
- PSSession zakończenia (exsn, zakończenia)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- (Środek) dla obiektu w miary
- Wyewidencjonowanie i domyślne
- Select-Object (wybór)

Żaden dostawca programu PowerShell są dostępne, podobnie jak wszelkie zewnętrznych programów (plików wykonywalnych i skryptów).

Aby uzyskać więcej informacji na temat trybów języka, zobacz [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Wybierz tożsamość usługi JEA

Za kulisami usługi JEA musi tożsamość (konto), aby używać podczas uruchamiania polecenia połączonych użytkowników.
Należy zdefiniować tożsamości, które korzysta z technologii JEA w pliku konfiguracji sesji.

#### <a name="local-virtual-account"></a>Konto wirtualne

Lokalnych kont wirtualnych są przydatne, gdy wszystkie role zdefiniowane dla punktu końcowego JEA są używane do zarządzania na komputerze lokalnym i konta administratora lokalnego jest wystarczająca do uruchomienia poleceń pomyślnie.
Kont wirtualnych są tymczasowego konta, które są unikatowe dla określonego użytkownika i tylko ostatni czas trwania sesji programu PowerShell. Na serwerze członkowskim lub stacji roboczej, kont wirtualnych należy na komputerze lokalnym **Administratorzy** grupy. Na kontrolerze domeny usługi Active Directory kont wirtualnych należą do tej domeny **Administratorzy domeny** grupy.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Jeśli role zdefiniowane przez konfigurację sesji nie wymagają pełnymi uprawnieniami administracyjnymi, można określić grupy zabezpieczeń, do których będą należeć konta wirtualnego. Dla serwera członkowskiego lub stacji roboczej do określonych grup zabezpieczeń musi być grupy lokalne, a nie grupy z domeny.

Jeśli określono co najmniej jedną grupę zabezpieczeń konta wirtualnego nie jest przypisany do grupy administratorów lokalnego lub domeny.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Kont wirtualnych tymczasowo są przyznawane logowanie w trybie usługi w zasadach zabezpieczeń serwera lokalnego. Jeśli jeden z VirtualAccountGroups określone zostało już udzielone tego prawa w zasadach, pojedyncze konto wirtualnego nie jest już będą dodawane i usuwane z zasad. Może to być przydatne w scenariuszach takich jak kontrolery domeny, w których poprawki, zasady zabezpieczeń kontrolera domeny są ściśle poddawane inspekcji. To jest dostępna tylko w systemu Windows Server 2016 z listopada 2018 r lub nowszy pakiet zbiorczy i 2019 serwera systemu Windows za pomocą 2019 stycznia lub nowszej.

#### <a name="group-managed-service-account"></a>Konto usługi zarządzane przez grupę

Konto usługi zarządzane przez grupę (GMSA) jest odpowiedniej tożsamości do użycia podczas JEA użytkownicy potrzebują dostępu do zasobów sieciowych, takich jak udziały plików i usług sieci web. Konta Gmsa zapewniają tożsamość domeny, który jest używany do uwierzytelniania przy użyciu zasobów na dowolnym komputerze w domenie. Prawa, które zapewnia GMSA, są określane przez zasoby uzyskiwany jest dostęp. Nie masz uprawnień administratora na wszystkich maszynach lub usługi, chyba że administrator usługi lub maszynowo ma jawnie przyznane uprawnienia te prawa do opcją GMSA

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

Konta Gmsa należy używać tylko w przypadku, gdy jest to konieczne:

- Trudno wywodzić akcje użytkownika, korzystając z GMSA. Każdy użytkownik udostępnia taką samą tożsamość Uruchom jako. Należy przejrzeć zapisy sesji programu PowerShell i dzienniki, aby skorelować poszczególnych użytkowników z ich działania.

- Opcją GMSA może mieć dostęp do wielu zasobów sieciowych, które użytkownik nawiązujący połączenie nie wymaga dostępu do. Zawsze próbuje ograniczyć czynne uprawnienia w ramach sesji usługi JEA do wykonania zasadę najmniejszych uprawnień.

> [!NOTE]
> Konta usług zarządzane przez grupę tylko są dostępne na komputerach przyłączonych do domeny, przy użyciu programu PowerShell 5.1 lub nowszej.

Aby uzyskać więcej informacji na temat zabezpieczania sesji JEA temacie [zagadnienia dotyczące zabezpieczeń](security-considerations.md) artykułu.

### <a name="session-transcripts"></a>Zapisy sesji

Zaleca się konfigurowania punktu końcowego JEA, aby automatycznie rejestrował transkrypcji sesje użytkowników. Zapisy sesji programu PowerShell zawierają informacje o użytkownik nawiązujący połączenie Uruchom jako tożsamość przypisaną do nich, i polecenia są uruchamiane przez użytkownika. Może być przydatne do inspekcji zespołu, która musi wiedzieć, kto wprowadził zmianę określonych w systemie.

Aby skonfigurować transkrypcje automatyczne w pliku konfiguracji sesji, należy podać ścieżkę do folderu przechowywania transkrypcji.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Zapisy są zapisywane w folderze przez **systemu lokalnego** konta, które wymaga dostępu odczytu i zapisu do katalogu. Użytkownicy standardowi powinna nie mają dostępu do folderu. Ogranicz liczbę administratorów zabezpieczeń, mających dostęp do inspekcji transkrypcji.

### <a name="user-drive"></a>Dysku użytkownika

Połączenie użytkownicy potrzebują do kopiowania plików do / z punktu końcowego JEA, po włączeniu dysku użytkownika w pliku konfiguracji sesji. Dysk użytkownika jest **PSDrive** który jest mapowany do unikatowego folderu dla każdego użytkownika nawiązującego połączenie. Ten folder umożliwia użytkownikom do kopiowania plików do / z systemu bez udzielania dostępu do systemu plików pełnej lub udostępnianie dostawcy FileSystem. Zawartość dysku użytkownika są trwałe dla wszystkich sesji, aby dopasować sytuacje, w którym mogą zostać przerwane połączenie sieciowe.

```powershell
MountUserDrive = $true
```

Domyślnie dysku użytkownika pozwala przechowywać maksymalnie 50MB danych dla poszczególnych użytkowników. Można ograniczyć ilość danych, użytkownik może zużywać z *UserDriveMaximumSize* pola.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Jeśli nie chcesz, aby dane na dysku użytkownika były trwałe, można skonfigurować zaplanowane zadanie w systemie, aby automatycznie oczyścić folderu każdej nocy.

> [!NOTE]
> Dysku użytkownika jest dostępne tylko w programie PowerShell 5.1 lub nowszej.

Aby uzyskać więcej informacji na temat PSDrives zobacz [dyski Zarządzanie PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Definicje ról

Definicje ról w pliku konfiguracji sesji zdefiniować mapowanie **użytkowników** do **role**. Każdego użytkownika lub grupy uwzględnione w tym polu jest uprawnienie do punktu końcowego JEA po jej zarejestrowaniu.
Każdy użytkownik lub grupa może być uwzględniany jako klucz w tablicy skrótów tylko raz, ale można przypisać wiele ról. Nazwa możliwości roli powinna być nazwa pliku możliwości roli, bez `.psrc` rozszerzenia.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Jeśli użytkownik należy do więcej niż jednej grupy w definicji roli, uzyska dostęp do ról każdego z nich. Jeśli dwie role udzielić dostępu do tego samego polecenia cmdlet, restrykcyjny zestaw parametrów jest udzielany użytkownikowi.

Podczas określania lokalnych użytkowników lub grupy w polu definicji roli, należy użyć nazwy komputera nie **localhost** ani symboli wieloznacznych. Sprawdź nazwę komputera, sprawdzając `$env:COMPUTERNAME` zmiennej.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Kolejność wyszukiwania możliwości roli

Jak pokazano w powyższym przykładzie, możliwości roli odwołuje się nazwa podstawowa pliku możliwości roli. Nazwa podstawowa pliku jest nazwa pliku bez rozszerzenia. Jeśli wiele możliwości roli są dostępne w systemie o takiej samej nazwie, programu PowerShell używa jej kolejność wyszukiwania niejawne, aby wybrać plik możliwości skutecznego roli. JEA jest **nie** udzielić dostępu do wszystkich plików możliwości rolę o takiej samej nazwie.

Korzysta z technologii JEA `$env:PSModulePath` zmiennej środowiskowej, aby określić, które ścieżki do skanowania w poszukiwaniu plików możliwości roli. W ramach każdej z tych ścieżek JEA szuka prawidłowe moduły programu PowerShell, które zawierają podfolder "RoleCapabilities". Podobnie jak w przypadku importowania modułów, JEA preferuje możliwości roli, które są dostarczane z programem Windows z funkcjami rola niestandardowa o takiej samej nazwie.

Dla wszystkich innych nazw powoduje konflikt pierwszeństwo zależy od kolejności, w którym Windows wylicza pliki w katalogu. Kolejność nie jest musi być znakiem alfabetycznym. Pierwszy plik możliwości roli znaleziono, który jest zgodny z określonym nazwa jest używana jako użytkownik nawiązujący połączenie. Ponieważ wyszukiwanie możliwości roli kolejność nie jest deterministyczna, jest **zdecydowanie zaleca się** czy możliwości roli mają unikatowych nazw plików.

### <a name="conditional-access-rules"></a>Zasady dostępu warunkowego

Wszyscy użytkownicy i grupy objęte **RoleDefinitions** pola automatycznie uzyskają dostęp do punktów końcowych JEA. Zasady dostępu warunkowego pozwalają dostosować ten dostęp i Wymagaj od użytkowników należą do grup zabezpieczeń, które nie miały wpływu na role, do których masz przypisaną. Jest to przydatne, gdy chcesz zintegrować to rozwiązanie do zarządzania uprzywilejowany dostęp just in time, uwierzytelnianie karty inteligentnej lub innego rozwiązania do uwierzytelniania wieloskładnikowego za pomocą technologii JEA.

Zasady dostępu warunkowego są definiowane w polu RequiredGroups w pliku konfiguracji sesji.
Tam możesz podać hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do konstruowania reguły. Poniżej przedstawiono kilka przykładów sposobu użycia tego pola:

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
> Zasady dostępu warunkowego są tylko dostępne w programie PowerShell 5.1 lub nowszej.

### <a name="other-properties"></a>Inne właściwości

Pliki konfiguracji sesji można robić wszystko, co można zrobić plik możliwości roli, po prostu bez możliwości daje łączącego się użytkownikom dostęp do różnych poleceń. Jeśli chcesz umożliwić wszystkim użytkownikom dostępu do określonych poleceń cmdlet, funkcji lub dostawców, możesz to zrobić bezpośrednio w pliku konfiguracji sesji.
Aby uzyskać pełną listę obsługiwanych właściwości w pliku konfiguracji sesji, należy uruchomić `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Plik konfiguracji sesji testowania

Możesz przetestować konfiguracji sesji przy użyciu [PSSessionConfigurationFile testu](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) polecenia cmdlet. Zalecane jest, sprawdzić plik konfiguracji sesji, czy można ręcznie edytować `.pssc` pliku. Testowanie gwarantuje, że składnia jest poprawna. W przypadku pliku konfiguracji sesji niepowodzenia tego testu nie można zarejestrować w systemie.

## <a name="sample-session-configuration-file"></a>Przykładowy plik konfiguracji sesji

Poniższy przykład pokazuje, jak utworzyć i zweryfikować konfigurację sesji dla usługi JEA. Definicje ról są tworzone i przechowywane w `$roles` zmiennej dla wygody i czytelności. Nie jest to wymagane, aby to zrobić.

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

Aby zmienić właściwości konfiguracji sesji, JEA, w tym mapowanie użytkowników do ról, należy najpierw [wyrejestrować](register-jea.md#unregistering-jea-configurations). Następnie [ponownie zarejestrować](register-jea.md) JEA konfiguracji sesji przy użyciu pliku konfiguracji sesji zaktualizowane.

## <a name="next-steps"></a>Następne kroki

- [Rejestruj konfigurację usługi JEA](register-jea.md)
- [Role usługi JEA autora](role-capabilities.md)
