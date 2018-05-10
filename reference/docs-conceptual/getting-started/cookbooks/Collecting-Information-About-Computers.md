---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zbieranie informacji dotyczących komputerów
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: ca92474eaf6fa546c3d6450f5a282e45157018a8
ms.sourcegitcommit: 4a841ebda3339ae2477e0f5f5be8c01740221232
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="collecting-information-about-computers"></a>Zbieranie informacji dotyczących komputerów

Polecenia cmdlet z **CimCmdlets** modułu są najważniejsze polecenia cmdlet do wykonywania ogólnych zadań zarządzania.
Wszystkie ustawienia podsystemu krytyczne są udostępniane za pośrednictwem usługi WMI.
Ponadto WMI dane są traktowane jako obiekty, które znajdują się w kolekcji jednego lub więcej elementów.
Ponieważ środowisko Windows PowerShell również współpracuje z obiektami i ma potok, który umożliwia traktowanie jednego lub wielu obiektów w taki sam sposób, ogólny dostęp usługi WMI umożliwia wykonywanie niektórych zaawansowanych zadań z bardzo małego wysiłku.

W poniższych przykładach pokazano, jak zbierać określone informacje przy użyciu `Get-CimInstance` względem dowolnego komputera.
Określono **ComputerName** parametru z wartością kropka (**.**), która reprezentuje komputer lokalny.
Można określić nazwę lub adres IP skojarzony z dowolnego komputera, który można otworzyć za pomocą usługi WMI.
Aby uzyskać informacje o komputerze lokalnym, można pominąć **ComputerName** parametru.

### <a name="listing-desktop-settings"></a>Wyświetlanie ustawień pulpitu

Rozpocznie się za pomocą polecenia, które zbiera informacje o stacji roboczych na komputerze lokalnym.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Zwraca informacje dotyczące wszystkich pulpitach, czy są one używane lub nie.

> [!NOTE]
> Informacje zwrócone przez niektóre klasy usługi WMI może być bardzo szczegółowe i często zawierają metadane dotyczące klasy usługi WMI.
Ponieważ większość tych właściwości metadanych mają nazwy zaczynające się **Cim**, można filtrować przy użyciu właściwości `Select-Object`.
Określ **- ExcludeProperty** parametr "Cim *" jako wartości.
Przykład:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Filtrowanie metadanych, należy użyć operatora potoku (|) do wysyłania wyniki `Get-CimInstance` polecenie `Select-Object -ExcludeProperty "CIM*"`.

### <a name="listing-bios-information"></a>Wyświetlanie informacji o systemie BIOS

WMI **Win32_BIOS** klasy zwraca stosunkowo małe i kompletne informacje dotyczące systemu BIOS na komputerze lokalnym:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Wyświetlanie informacji o procesora

Informacje o procesorze ogólne można pobrać za pomocą usługi WMI **Win32_Processor** klasy, mimo że będzie prawdopodobnie chcesz filtrować informacje:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Ogólny opis ciągu rodziny procesora, można tylko zwrócić **typem systemu** właściwości:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Lista komputerów producenta i Model

Informacje o komputerze modelu jest również dostępna z **Win32_ComputerSystem**.
Standardowa wyświetlanych wyników nie będzie żadnego filtrowania danych OEM:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

Dane wyjściowe poleceń, takich jak ta, które zwracają informacje bezpośrednio z niektórych urządzeń, jest tylko dane, które masz.
Niektóre informacje nie została poprawnie skonfigurowana przez producentów sprzętu i dlatego mogą być niedostępne.

### <a name="listing-installed-hotfixes"></a>Lista zainstalowanych poprawek

Wyświetl listę wszystkich zainstalowanych poprawek za pomocą **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Ta klasa zwraca listę poprawek, który wygląda następująco:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Bardziej zwięzły danych wyjściowych można wykluczyć niektórych właściwości.
Chociaż można używać `Get-CimInstance`w **właściwości** parametr, aby wybrać tylko **HotFixID**, to tak faktycznie zwrócą więcej informacji, ponieważ domyślnie powoduje wyświetlenie wszystkich metadanych:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Dodatkowe dane są zwracane, ponieważ parametr właściwości w `Get-CimInstance` ogranicza właściwości zwrócony z wystąpień klasy usługi WMI, nie obiekt zwrócił do programu Windows PowerShell.
Aby ograniczyć dane wyjściowe, należy użyć `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a>Wyświetlanie informacji o wersji systemu operacyjnego

**Win32_OperatingSystem** właściwości klasy zawierają informacje o pakiecie wersji i usługi.
Jawnie można wybrać tylko te właściwości, aby uzyskać informacje o wersji podsumowanie z **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Można również użyć symboli wieloznacznych z `Select-Object`w **właściwości** parametru.
Ponieważ wszystkie właściwości, począwszy od jednej **kompilacji** lub **z dodatkiem Service Pack** należy użyć w tym miejscu możemy to zmniejszyć do następującej postaci:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Wyświetlanie lokalnych użytkowników i właściciela

Lokalne ogólne informacje o użytkowniku — liczba licencjonowanych użytkowników, bieżąca liczba użytkowników i nazwy właściciela — można znaleźć zestaw **Win32_OperatingSystem** właściwości klasy.
Możesz wybrać jawnie właściwości do wyświetlenia w następujący sposób:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Jest bardziej zwięzły wersji przy użyciu symboli wieloznacznych:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Pobieranie dostępnego miejsca na dysku

Aby wyświetlić miejsca na dysku i wolnego miejsca na dyskach lokalnych, służy klasy Win32_LogicalDisk usługi WMI.
Należy sprawdzić tylko wystąpienia o DriveType 3 — wartość używa usługi WMI stałe dyski twarde.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a>Trwa pobieranie informacji o sesji logowania

Można uzyskać ogólne informacje dotyczące sesji logowania skojarzone z użytkownikami za pomocą **Win32_LogonSession** klasy usługi WMI:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Pobieranie użytkownika zalogowanego na komputerze

Użytkownik zalogowany do określonego systemu komputerowego przy użyciu Win32_ComputerSystem można wyświetlić.
To polecenie zwraca tylko użytkownika zalogowanego na pulpicie systemu:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Pobieranie czasu lokalnego na komputerze

Bieżący czas lokalny na określonym komputerze można pobrać za pomocą **Win32_LocalTime** klasy usługi WMI.

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a>Wyświetlanie stanu usługi

Aby wyświetlić stan wszystkich usług na określonym komputerze, lokalnie służy `Get-Service` polecenia cmdlet.
Dla systemów zdalnych, możesz użyć **Win32_Service** klasy usługi WMI.
Jeśli używasz również `Select-Object` mają być filtrowane wyniki do **stan**, **nazwa**, i **DisplayName**, format danych wyjściowych będzie niemal identyczne z `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Umożliwia wyświetlanie pełne nazwy okazjonalne usługi z bardzo długie nazwy, warto użyć `Format-Table` z **AutoSize** i **zawijanie** parametrów, aby zoptymalizować szerokość kolumny i Zezwalaj na długie nazwy opakowywać zamiast obcięcie:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
