---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Zbieranie informacji o komputerach
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: c0b7ec9ed7d2b07c66d2b1cf3342f971d71da481
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="collecting-information-about-computers"></a>Zbieranie informacji o komputerach
**Get-WmiObject** jest najważniejszych polecenia cmdlet systemu ogólnych zadań zarządzania. Wszystkie ustawienia podsystemu krytyczne są udostępniane za pośrednictwem usługi WMI. Ponadto WMI dane są traktowane jako obiekty, które znajdują się w kolekcji jednego lub więcej elementów. Ponieważ środowisko Windows PowerShell również współpracuje z obiektami i ma potok, który umożliwia traktowanie jednego lub wielu obiektów w taki sam sposób, ogólny dostęp usługi WMI umożliwia wykonywanie niektórych zaawansowanych zadań z bardzo małego wysiłku.

W poniższych przykładach pokazano, jak zbierać określone informacje przy użyciu **Get-WmiObject** względem dowolnego komputera. Określono **ComputerName** parametru z wartością kropka (**.**), która reprezentuje komputer lokalny. Można określić nazwę lub adres IP skojarzony z dowolnego komputera, który można otworzyć za pomocą usługi WMI. Aby uzyskać informacje o komputerze lokalnym, można pominąć **- ComputerName.**

### <a name="listing-desktop-settings"></a>Wyświetlanie ustawień pulpitu
Rozpocznie się za pomocą polecenia, które zbiera informacje o stacji roboczych na komputerze lokalnym.

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

Zwraca informacje dotyczące wszystkich pulpitach, czy są one używane lub nie.

> [!NOTE]
> Informacje zwrócone przez niektóre klasy usługi WMI może być bardzo szczegółowe i często zawierają metadane dotyczące klasy usługi WMI. Ponieważ większość tych właściwości metadanych mają nazwy zaczynające się od podkreślenia dwa razy, można filtrować właściwości, za pomocą Select-Object. Określ tylko właściwości, które rozpoczynają się z alfabetu przy użyciu **[a-z]*** jako wartość właściwości. Przykład:

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

Filtrowanie metadanych, użyj operatora potoku (|) aby wysłać wyniki polecenia Get-WmiObject do **Select-Object - właściwości [a-z]***.

### <a name="listing-bios-information"></a>Wyświetlanie informacji o systemie BIOS
Klasa WMI Win32_BIOS zwraca stosunkowo małe i kompletne informacje o systemie BIOS na komputerze lokalnym:

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Wyświetlanie informacji o procesora
Informacje o procesorze ogólne można pobrać za pomocą usługi WMI **Win32_Processor** klasy, mimo że będzie prawdopodobnie chcesz filtrować informacje:

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

Ogólny opis ciągu rodziny procesora, można tylko zwrócić **typem systemu** właściwości:

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Lista komputerów producenta i Model
Informacje o komputerze modelu jest również dostępna z **Win32_ComputerSystem**. Standardowa wyświetlanych wyników nie będzie żadnego filtrowania danych OEM:

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

Dane wyjściowe poleceń, takich jak ta, które zwracają informacje bezpośrednio z niektórych urządzeń, jest tylko dane, które masz. Niektóre informacje nie została poprawnie skonfigurowana przez producentów sprzętu i dlatego mogą być niedostępne.

### <a name="listing-installed-hotfixes"></a>Lista zainstalowanych poprawek
Wyświetl listę wszystkich zainstalowanych poprawek za pomocą **Win32_QuickFixEngineering**:

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

Ta klasa zwraca listę poprawek, który wygląda następująco:

```
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

Bardziej zwięzły danych wyjściowych można wykluczyć niektórych właściwości. Chociaż można używać **właściwości Get-WmiObject** parametr, aby wybrać tylko **HotFixID**, to tak faktycznie zwrócą więcej informacji, ponieważ domyślnie powoduje wyświetlenie wszystkich metadanych:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID
HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

Dodatkowe dane są zwracane, ponieważ parametr właściwości w **Get-WmiObject** ogranicza właściwości zwrócony z wystąpień klasy usługi WMI, nie obiekt zwrócił do programu Windows PowerShell. Aby ograniczyć dane wyjściowe, należy użyć **Select-Object**:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a>Wyświetlanie informacji o wersji systemu operacyjnego
**Win32_OperatingSystem** właściwości klasy zawierają informacje o pakiecie wersji i usługi. Jawnie można wybrać tylko te właściwości, aby uzyskać informacje o wersji podsumowanie z **Win32_OperatingSystem**:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Można również użyć symboli wieloznacznych z **właściwości Select-Object** parametru. Ponieważ wszystkie właściwości, począwszy od jednej **kompilacji** lub **z dodatkiem Service Pack** należy użyć w tym miejscu możemy to zmniejszyć do następującej postaci:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Wyświetlanie lokalnych użytkowników i właściciela
Lokalne ogólne informacje o użytkowniku — liczba licencjonowanych użytkowników, bieżąca liczba użytkowników i nazwy właściciela — można znaleźć zestaw **Win32_OperatingSystem** właściwości. Możesz wybrać jawnie właściwości do wyświetlenia w następujący sposób:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Jest bardziej zwięzły wersji przy użyciu symboli wieloznacznych:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Pobieranie dostępnego miejsca na dysku
Aby wyświetlić miejsca na dysku i wolnego miejsca na dyskach lokalnych, służy klasy WMI Win32_LogicalDisk. Należy sprawdzić tylko wystąpienia o DriveType 3 — wartość używa usługi WMI stałe dyski twarde.

```
Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### <a name="getting-logon-session-information"></a>Trwa pobieranie informacji o sesji logowania
Aby uzyskać ogólne informacje dotyczące sesji logowania skojarzone z użytkownikami za pośrednictwem klasy WMI Win32_LogonSession:

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Pobieranie użytkownika zalogowanego na komputerze
Użytkownik zalogowany do określonego systemu komputerowego przy użyciu Win32_ComputerSystem można wyświetlić. To polecenie zwraca tylko użytkownika zalogowanego na pulpicie systemu:

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Pobieranie czasu lokalnego na komputerze
Za pomocą klasy WMI Win32_LocalTime można pobrać bieżącego czasu lokalnego na określonym komputerze. Ponieważ ta klasa domyślnie wyświetla wszystkie metadane, można filtrować przy użyciu **Select-Object**:

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### <a name="displaying-service-status"></a>Wyświetlanie stanu usługi
Aby wyświetlić stan wszystkich usług na określonym komputerze, lokalnie służy **Get-Service** polecenia cmdlet, jak wspomniano wcześniej. Dla systemów zdalnych można użyć klasy WMI Win32_Service. Jeśli używasz również **Select-Object** mają być filtrowane wyniki do **stan**, **nazwa**, i **DisplayName**, format danych wyjściowych będzie niemal identyczny z **Get-Service**:

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Umożliwia wyświetlanie pełne nazwy okazjonalne usługi z bardzo długie nazwy, warto użyć **Format-Table** z **AutoSize** i **zawijanie** parametrów , można zoptymalizować szerokość kolumny oraz umożliwić długie nazwy opakowywać zamiast obcięcie:

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```

