---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Konfiguracje sesji JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017881"
---
# <a name="jea-session-configurations"></a>Konfiguracje sesji JEA

Punkt końcowy JEA jest zarejestrowany w systemie przez utworzenie i zarejestrowanie pliku konfiguracji sesji programu PowerShell. Konfiguracje sesji definiują, kto może korzystać z punktu końcowego JEA i jakie role mają do nich dostęp. Definiują one również ustawienia globalne, które mają zastosowanie do wszystkich użytkowników sesji JEA.

## <a name="create-a-session-configuration-file"></a>Utwórz plik konfiguracji sesji

Aby zarejestrować punkt końcowy JEA, należy określić sposób, w jaki ten punkt końcowy jest skonfigurowany. Istnieje wiele opcji, które należy wziąć pod uwagę. Najważniejsze są następujące opcje:

- Kto ma dostęp do punktu końcowego JEA
- Które role są przypisane
- Których tożsamości JEA używa w ramach okładek
- Nazwa punktu końcowego JEA

Te opcje są zdefiniowane w pliku danych programu PowerShell z `.pssc` rozszerzeniem znanym jako plik konfiguracji sesji programu PowerShell. Plik konfiguracji sesji można edytować przy użyciu dowolnego edytora tekstu.

Uruchom następujące polecenie, aby utworzyć plik konfiguracji pustego szablonu.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> W pliku szablonu domyślnie są zawarte tylko najczęściej używane opcje konfiguracji. Użyj przełącznika `-Full` , aby uwzględnić wszystkie odpowiednie ustawienia w wygenerowanym PSSC.

`-SessionType RestrictedRemoteServer` Pole wskazuje, że konfiguracja sesji jest używana przez jea do bezpiecznego zarządzania. Sesje tego typu działają w trybie **NoLanguage** i mają dostęp tylko do następujących poleceń domyślnych (i aliasów):

- Clear-Host (CLS, Clear)
- Exit-PSSession (exsn, Exit)
- Get-Command (GCM)
- Get-FormatData
- Get-Help
- Measure-Object (Measure)
- Out — wartość domyślna
- Select-Object (Select)

Żaden dostawca programu PowerShell nie jest dostępny ani nie ma żadnych programów zewnętrznych (plików wykonywalnych ani skryptów).

Aby uzyskać więcej informacji na temat trybów języka, zobacz [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Wybieranie tożsamości JEA

W tle JEA potrzebuje tożsamości (konta) do użycia podczas uruchamiania poleceń połączonego użytkownika.
Należy określić, której tożsamości JEA używać w pliku konfiguracji sesji.

#### <a name="local-virtual-account"></a>Lokalne konto wirtualne

Lokalne konta wirtualne są przydatne, gdy wszystkie role zdefiniowane dla punktu końcowego JEA są używane do zarządzania komputerem lokalnym, a konto administratora lokalnego jest wystarczające do pomyślnego uruchomienia poleceń.
Konta wirtualne są kontami tymczasowymi, które są unikatowe dla określonego użytkownika i tylko przez czas trwania sesji programu PowerShell. Na serwerze członkowskim lub stacji roboczej konta wirtualne należą do grupy **administratorów** komputera lokalnego. Na kontrolerze domena usługi Active Directory konta wirtualne należą do grupy **Administratorzy domeny** domeny.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Jeśli role zdefiniowane przez konfigurację sesji nie wymagają pełnego uprawnienia administratora, można określić grupy zabezpieczeń, do których będzie należało konto wirtualne. W przypadku serwera członkowskiego lub stacji roboczej określone grupy zabezpieczeń muszą być grupami lokalnymi, a nie grupami z domeny.

W przypadku określenia co najmniej jednej grupy zabezpieczeń konto wirtualne nie jest przypisane do grupy Administratorzy lokalni lub domeny.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Kontom wirtualnym tymczasowo przyznano Logowanie jako usługa bezpośrednio w zasadach zabezpieczeń serwera lokalnego. Jeśli jeden z określonych VirtualAccountGroups został już udzielony w zasadach, indywidualne konto wirtualne nie zostanie już dodane i usunięte z zasad. Może to być przydatne w scenariuszach takich jak kontrolery domeny, w których zmiany zasad zabezpieczeń kontrolera domeny są ściśle poddawane inspekcji. Jest to możliwe tylko w systemie Windows Server 2016 z pakietem zbiorczym z listopada 2018 lub nowszym oraz systemem Windows Server 2019 z pakietem zbiorczym z stycznia 2019 lub nowszym.

#### <a name="group-managed-service-account"></a>Konto usługi zarządzane przez grupę

Konto usługi zarządzane przez grupę (GMSA) jest odpowiednią tożsamością używaną, gdy użytkownicy JEA muszą uzyskać dostęp do zasobów sieciowych, takich jak udziały plików i usługi sieci Web. Kont gMSA zapewniają tożsamość domeny, która jest używana do uwierzytelniania za pomocą zasobów na dowolnym komputerze w domenie. Prawa, które zapewnia GMSA, są określane przez zasoby, do których uzyskujesz dostęp. Nie masz uprawnień administratora na żadnych maszynach lub usługach, chyba że administrator maszyny lub usługi jawnie udzielił tych praw do GMSA.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

Kont gMSA powinny być używane tylko wtedy, gdy jest to konieczne:

- Trudno jest śledzić działania z powrotem do użytkownika podczas korzystania z GMSA. Każdy użytkownik ma tę samą tożsamość Uruchom jako. Należy przejrzeć transkrypcje i dzienniki sesji programu PowerShell w celu skorelowania poszczególnych użytkowników z ich działaniami.

- GMSA może mieć dostęp do wielu zasobów sieciowych, do których użytkownik łączący nie potrzebuje dostępu. Zawsze należy próbować ograniczyć czynne uprawnienia w sesji JEA, aby były zgodne z zasadą najniższych uprawnień.

> [!NOTE]
> Konta usług zarządzane przez grupę są dostępne tylko na komputerach przyłączonych do domeny przy użyciu programu PowerShell 5,1 lub nowszego.

Aby uzyskać więcej informacji na temat zabezpieczania sesji JEA, zobacz artykuł dotyczący [zagadnień dotyczących zabezpieczeń](security-considerations.md) .

### <a name="session-transcripts"></a>Transkrypcje sesji

Zaleca się skonfigurowanie punktu końcowego JEA, aby automatycznie rejestrować transkrypcje sesji użytkowników. Transkrypcje sesji programu PowerShell zawierają informacje o połączonym użytkowniku, przypisanej tożsamości Uruchom jako i poleceniach uruchamianych przez użytkownika. Mogą być przydatne dla zespołu ds. inspekcji, który musi zrozumieć, kto wprowadził konkretną zmianę w systemie.

Aby skonfigurować automatyczne transkrypcję w pliku konfiguracji sesji, podaj ścieżkę do folderu, w którym powinny być przechowywane transkrypcje.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Transkrypcje są zapisywane w folderze przez konto **systemu lokalnego** , które wymaga dostępu do odczytu i zapisu do katalogu. Użytkownicy standardowi nie powinni mieć dostępu do folderu. Ogranicz liczbę administratorów zabezpieczeń, którzy mają dostęp do inspekcji transkrypcji.

### <a name="user-drive"></a>Dysk użytkownika

Jeśli łączący się użytkownicy muszą kopiować pliki do lub z punktu końcowego JEA, można włączyć dysk użytkownika w pliku konfiguracji sesji. Dysk użytkownika to **PSDrive** , który jest mapowany do unikatowego folderu dla każdego łączącego się użytkownika. Ten folder umożliwia użytkownikom kopiowanie plików do lub z systemu bez udzielania im dostępu do pełnego systemu plików ani udostępniania dostawcy plików. Zawartość dysku użytkownika jest trwała między sesjami, aby uwzględnić sytuacje, w których można przerwać łączność sieciową.

```powershell
MountUserDrive = $true
```

Domyślnie dysk użytkownika umożliwia przechowywanie maksymalnie 50 MB danych na użytkownika. Można ograniczyć ilość danych, które użytkownik może wykorzystać w polu *UserDriveMaximumSize* .

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Jeśli nie chcesz, aby dane na dysku użytkownika były trwałe, możesz skonfigurować zaplanowane zadanie w systemie, aby automatycznie czyścić folder w każdej nocy.

> [!NOTE]
> Dysk użytkownika jest dostępny tylko w programie PowerShell w wersji 5,1 lub nowszej.

Aby uzyskać więcej informacji na temat PSDrives, zobacz [Zarządzanie dyskami programu PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Definicje ról

Definicje ról w pliku konfiguracji sesji definiują mapowanie **użytkowników** do **ról**. Każdy użytkownik lub Grupa uwzględniona w tym polu uzyskuje uprawnienia do punktu końcowego JEA, gdy jest on zarejestrowany.
Każdy użytkownik lub Grupa może być dołączana jako klucz w elemencie Hashtable tylko raz, ale można przypisać wiele ról. Nazwa funkcji roli powinna być nazwą pliku możliwości roli bez `.psrc` rozszerzenia.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Jeśli użytkownik należy do więcej niż jednej grupy w definicji roli, uzyskuje dostęp do ról każdego z nich. Gdy dwie role udzielą dostępu do tych samych poleceń cmdlet, zestaw parametrów z największą liczbą jest przyznawany użytkownikowi.

W przypadku określania lokalnych użytkowników lub grup w polu definicje ról należy użyć nazwy komputera, a nie od **localhost** lub symboli wieloznacznych. Nazwę komputera można sprawdzić, sprawdzając `$env:COMPUTERNAME` zmienną.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Kolejność wyszukiwania możliwości roli

Jak pokazano w powyższym przykładzie, możliwości roli są przywoływane przez podstawową nazwę pliku możliwości roli. Nazwa podstawowa pliku to nazwa pliku bez rozszerzenia. Jeśli w systemie jest dostępnych wiele możliwości roli o tej samej nazwie, program PowerShell użyje niejawnej kolejności wyszukiwania, aby wybrać skuteczny plik możliwości roli. JEA nie udziela dostępu do wszystkich plików możliwości roli o tej samej nazwie.

JEA używa `$env:PSModulePath` zmiennej środowiskowej w celu określenia ścieżek do skanowania dla plików możliwości roli. W ramach każdej z tych ścieżek JEA szuka prawidłowych modułów programu PowerShell zawierających podfolder "RoleCapabilities". Podobnie jak w przypadku importowania modułów, JEA preferuje możliwości roli, które są dostarczane z systemem Windows, do możliwości roli niestandardowej o tej samej nazwie.

W przypadku wszystkich innych konfliktów nazewnictwa pierwszeństwo zależy od kolejności, w której system Windows wylicza pliki w katalogu. Kolejność nie jest gwarantowana w porządku alfabetycznym. Dla użytkownika łączącego jest używany pierwszy plik możliwości roli, który jest zgodny z określoną nazwą. Ponieważ kolejność wyszukiwania możliwości roli nie jest deterministyczna, **zdecydowanie** zalecamy, aby możliwości roli miały unikatowe nazwy plików.

### <a name="conditional-access-rules"></a>Reguły dostępu warunkowego

Wszyscy użytkownicy i grupy uwzględnione w polu **RoleDefinitions** mają automatycznie udzielony dostęp do punktów końcowych jea. Reguły dostępu warunkowego umożliwiają ograniczenie dostępu i wymaganie, aby użytkownicy należały do dodatkowych grup zabezpieczeń, które nie mają wpływu na role, do których są przypisane. Jest to przydatne, gdy chcesz zintegrować rozwiązanie do zarządzania dostępem uprzywilejowanym w trybie just-in-Time, uwierzytelniania karty inteligentnej lub innego rozwiązania do uwierzytelniania wieloskładnikowego z JEA.

Reguły dostępu warunkowego są zdefiniowane w polu RequiredGroups w pliku konfiguracji sesji.
Tam można podać tablicę skrótów (opcjonalnie zagnieżdżoną), która używa kluczy "i" i "lub" do konstruowania reguł. Poniżej przedstawiono kilka przykładów użycia tego pola:

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
> Reguły dostępu warunkowego są dostępne tylko w programie PowerShell w wersji 5,1 lub nowszej.

### <a name="other-properties"></a>Inne właściwości

Pliki konfiguracji sesji mogą również wykonywać wszystko, co może zrobić plik możliwości roli, bez możliwości nadawania użytkownikom dostępu do różnych poleceń. Jeśli chcesz zezwolić wszystkim użytkownikom na dostęp do określonych poleceń cmdlet, funkcji lub dostawców, możesz to zrobić bezpośrednio w pliku konfiguracji sesji.
Aby uzyskać pełną listę obsługiwanych właściwości w pliku konfiguracji sesji, uruchom `Get-Help New-PSSessionConfigurationFile -Full`polecenie.

## <a name="testing-a-session-configuration-file"></a>Testowanie pliku konfiguracji sesji

Konfigurację sesji można testować za pomocą polecenia cmdlet [test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) . Zaleca się przetestowanie pliku konfiguracji sesji, jeśli `.pssc` plik został ręcznie edytowany. Testowanie zapewnia poprawną składnię. Jeśli ten test zakończy się niepowodzeniem, nie można zarejestrować go w systemie.

## <a name="sample-session-configuration-file"></a>Przykładowy plik konfiguracji sesji

Poniższy przykład pokazuje, jak utworzyć i zweryfikować konfigurację sesji dla JEA. Definicje ról są tworzone i przechowywane w `$roles` zmiennej dla wygody i czytelności. Nie jest to wymagane.

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

Aby zmienić właściwości konfiguracji sesji JEA, z uwzględnieniem mapowania użytkowników do ról, należy wyrejestrować. [](register-jea.md#unregistering-jea-configurations) Następnie [zarejestruj ponownie](register-jea.md) konfigurację sesji jea przy użyciu zaktualizowanego pliku konfiguracji sesji.

## <a name="next-steps"></a>Następne kroki

- [Rejestrowanie konfiguracji JEA](register-jea.md)
- [Tworzenie ról JEA](role-capabilities.md)
