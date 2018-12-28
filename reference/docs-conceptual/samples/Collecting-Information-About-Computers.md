---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zbieranie informacji dotyczących komputerów
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: 99125ef701705c20d4e955c79eaa3469ce4d58fb
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404802"
---
# <a name="collecting-information-about-computers"></a>Zbieranie informacji dotyczących komputerów

Polecenia cmdlet z **CimCmdlets** moduł są najważniejsze poleceń cmdlet do wykonywania ogólnych zadań zarządzania.
Wszystkie ustawienia krytyczny podsystem są udostępniane za pośrednictwem usługi WMI.
Ponadto WMI dane są traktowane jako obiekty, które znajdują się w kolekcji jednego lub kilku elementów.
Ponieważ środowiska Windows PowerShell również współdziała z obiektami i ma potok, który umożliwia traktowanie jednego lub wielu obiektów w taki sam sposób, ogólny dostęp usługi WMI umożliwia wykonywanie niektórych zaawansowanych zadań przy użyciu bardzo małego wysiłku.

Poniższe przykłady pokazują, jak zbierać określone informacje przy użyciu `Get-CimInstance` względem dowolnego komputera.
Określamy **ComputerName** parametru z wartością kropka (**.**), który reprezentuje komputer lokalny.
Można określić nazwę lub adres IP skojarzony z dowolnego komputera, który można osiągnąć za pomocą usługi WMI.
Aby pobrać informacje o komputerze lokalnym, można pominąć **ComputerName** parametru.

### <a name="listing-desktop-settings"></a>Lista ustawień pulpitu

Rozpocznie się za pomocą polecenia, które zbiera informacje o komputerach, na komputerze lokalnym.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Zwraca informacje o wszystkich komputerach, czy są one używane lub nie.

> [!NOTE]
> Informacje zwrócone przez niektóre klasy WMI może być bardzo szczegółowe i często zawierają metadane dotyczące klasy usługi WMI.
Ponieważ większość tych właściwości metadanych mają nazwy rozpoczynające się od **Cim**, można filtrować właściwości, za pomocą `Select-Object`.
Określ **- ExcludeProperty** "Cim *" jako wartość parametru.
Przykład:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Aby odfiltrować metadanych, użyj operatora potoku (|) do wysłania wyniki `Get-CimInstance` polecenie `Select-Object -ExcludeProperty "CIM*"`.

### <a name="listing-bios-information"></a>Wyświetlanie informacji o systemie BIOS

WMI **Win32_BIOS** Klasa zwraca stosunkowo małe i kompletne informacje o systemie BIOS komputera lokalnego:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Informacje o procesorze listy

Informacje o procesorze ogólne można pobrać za pomocą usługi WMI **Win32_Processor** klasy, chociaż prawdopodobnie będziesz filtrować informacje:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Ogólny opis ciągu rodziny procesorów, można po prostu zwrócić **typem systemu** właściwości:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Lista komputerów producent i Model

Informacje o komputerze modelu jest również dostępna z **Win32_ComputerSystem**.
Standardowe dane wyjściowe wyświetlane nie wymaga żadnego filtrowania do dostarczania danych OEM:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

Dane wyjściowe za pomocą poleceń takich jak ta, które zwracają informacje bezpośrednio w sprzęt, jest tylko jako dane, do których masz.
Niektóre informacje nie jest poprawnie skonfigurowana przez producentów sprzętu i dlatego może być niedostępna.

### <a name="listing-installed-hotfixes"></a>Lista zainstalowanych poprawek

Możesz wyświetlić listę wszystkich zainstalowanych poprawek za pomocą **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Ta klasa zwraca listę poprawek, które wyglądają następująco:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Dla bardziej zwięzłą danych wyjściowych można wykluczyć niektóre właściwości.
Chociaż można używać `Get-CimInstance`firmy **właściwość** parametru, aby wybrać tylko **HotFixID**, wykonanie tej tak, faktycznie zwrócą więcej informacji, ponieważ domyślnie powoduje wyświetlenie wszystkich metadanych:

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

Dodatkowe dane są zwracane, ponieważ parametr właściwości w `Get-CimInstance` ogranicza właściwości zwrócone w wyniku wystąpienia klasy WMI, nie obiekt zwrócony do programu Windows PowerShell.
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

**Win32_OperatingSystem** właściwości klas, które zawierają informacje o pakiecie wersji i usługi.
Można jawnie wybrać tylko te właściwości, aby uzyskać informacje o wersji podsumowanie z **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Możesz również użyć symboli wieloznacznych przy użyciu `Select-Object`firmy **właściwość** parametru.
Ponieważ wszystkie właściwości, począwszy od albo **kompilacji** lub **z dodatkiem Service Pack** są ważne do użycia w tym miejscu możemy to skrócić do następującej postaci:

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

### <a name="listing-local-users-and-owner"></a>Wyświetlanie listy lokalnych użytkowników i właściciela

Lokalne ogólne informacje o użytkowniku — liczbę objętych licencją użytkowników, bieżąca liczba użytkowników i nazwy właściciela — można znaleźć szereg **Win32_OperatingSystem** właściwości klasy.
Można jawnie wybrać właściwości do wyświetlenia w następujący sposób:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Nieco bardziej zwięzłą przy użyciu symboli wieloznacznych jest:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Wprowadzenie dostępnego miejsca na dysku

Aby zobaczyć miejsce na dysku i wolnego miejsca na dyskach lokalnych, można użyć klasy Win32_LogicalDisk WMI.
Chcesz zobaczyć tylko wystąpienia z DriveType 3 — wartość WMI używa stałej dysków twardych.

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

### <a name="getting-logon-session-information"></a>Pobieranie informacji o sesji logowania

Zawiera ogólne informacje o sesjach logowania skojarzone z użytkownikami za pomocą **Win32_LogonSession** klasy usługi WMI:

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

Bieżący czas lokalny na określonym komputerze można pobrać za pomocą **Win32_LocalTime** klasy WMI.

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
W przypadku systemów zdalnych, można użyć **Win32_Service** klasy WMI.
Gdy również użyć `Select-Object` do odfiltrowania wyników do **stan**, **nazwa**, i **DisplayName**, format danych wyjściowych będzie niemal identyczne, z `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Aby zezwolić na pełne wyświetlanie nazw okazjonalnych o bardzo długich nazwach, warto użyć `Format-Table` z **AutoSize** i **opakować** parametrów w celu optymalizacji szerokość kolumny i Zezwalaj na długich nazwach zawijać zamiast obcinania:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
