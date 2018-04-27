---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zbieranie informacji dotyczących komputerów
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: 7f5a5f6accd57a84e2bcb3d20c14640a8e028791
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="51ed7-103">Zbieranie informacji dotyczących komputerów</span><span class="sxs-lookup"><span data-stu-id="51ed7-103">Collecting Information About Computers</span></span>

<span data-ttu-id="51ed7-104">**Get-WmiObject** jest najważniejszych polecenia cmdlet systemu ogólnych zadań zarządzania.</span><span class="sxs-lookup"><span data-stu-id="51ed7-104">**Get-WmiObject** is the most important cmdlet for general system management tasks.</span></span> <span data-ttu-id="51ed7-105">Wszystkie ustawienia podsystemu krytyczne są udostępniane za pośrednictwem usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="51ed7-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="51ed7-106">Ponadto WMI dane są traktowane jako obiekty, które znajdują się w kolekcji jednego lub więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="51ed7-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="51ed7-107">Ponieważ środowisko Windows PowerShell również współpracuje z obiektami i ma potok, który umożliwia traktowanie jednego lub wielu obiektów w taki sam sposób, ogólny dostęp usługi WMI umożliwia wykonywanie niektórych zaawansowanych zadań z bardzo małego wysiłku.</span><span class="sxs-lookup"><span data-stu-id="51ed7-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="51ed7-108">W poniższych przykładach pokazano, jak zbierać określone informacje przy użyciu **Get-WmiObject** względem dowolnego komputera.</span><span class="sxs-lookup"><span data-stu-id="51ed7-108">The following examples demonstrate how to collect specific information by using **Get-WmiObject** against an arbitrary computer.</span></span> <span data-ttu-id="51ed7-109">Określono **ComputerName** parametru z wartością kropka (**.**), która reprezentuje komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="51ed7-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span> <span data-ttu-id="51ed7-110">Można określić nazwę lub adres IP skojarzony z dowolnego komputera, który można otworzyć za pomocą usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="51ed7-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span> <span data-ttu-id="51ed7-111">Aby uzyskać informacje o komputerze lokalnym, można pominąć **- ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="51ed7-111">To retrieve information about the local computer, you could omit the **-ComputerName.**</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="51ed7-112">Wyświetlanie ustawień pulpitu</span><span class="sxs-lookup"><span data-stu-id="51ed7-112">Listing Desktop Settings</span></span>

<span data-ttu-id="51ed7-113">Rozpocznie się za pomocą polecenia, które zbiera informacje o stacji roboczych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="51ed7-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

<span data-ttu-id="51ed7-114">Zwraca informacje dotyczące wszystkich pulpitach, czy są one używane lub nie.</span><span class="sxs-lookup"><span data-stu-id="51ed7-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="51ed7-115">Informacje zwrócone przez niektóre klasy usługi WMI może być bardzo szczegółowe i często zawierają metadane dotyczące klasy usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="51ed7-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span> <span data-ttu-id="51ed7-116">Ponieważ większość tych właściwości metadanych mają nazwy zaczynające się od podkreślenia dwa razy, można filtrować właściwości, za pomocą Select-Object.</span><span class="sxs-lookup"><span data-stu-id="51ed7-116">Because most of these metadata properties have names that begin with a double underscore, you can filter the properties using Select-Object.</span></span> <span data-ttu-id="51ed7-117">Określ tylko właściwości, które rozpoczynają się z alfabetu przy użyciu **[a-z]**\* jako wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="51ed7-117">Specify only properties that begin with alphabetic characters by using **[a-z]**\* as the Property value.</span></span> <span data-ttu-id="51ed7-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="51ed7-118">For example:</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="51ed7-119">Filtrowanie metadanych, użyj operatora potoku (|) aby wysłać wyniki polecenia Get-WmiObject do `Select-Object -Property [a-z]*`.</span><span class="sxs-lookup"><span data-stu-id="51ed7-119">To filter out the metadata, use a pipeline operator (|) to send the results of the Get-WmiObject command to `Select-Object -Property [a-z]*`.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="51ed7-120">Wyświetlanie informacji o systemie BIOS</span><span class="sxs-lookup"><span data-stu-id="51ed7-120">Listing BIOS Information</span></span>

<span data-ttu-id="51ed7-121">Klasa WMI Win32_BIOS zwraca stosunkowo małe i kompletne informacje o systemie BIOS na komputerze lokalnym:</span><span class="sxs-lookup"><span data-stu-id="51ed7-121">The WMI Win32_BIOS class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="51ed7-122">Wyświetlanie informacji o procesora</span><span class="sxs-lookup"><span data-stu-id="51ed7-122">Listing Processor Information</span></span>

<span data-ttu-id="51ed7-123">Informacje o procesorze ogólne można pobrać za pomocą usługi WMI **Win32_Processor** klasy, mimo że będzie prawdopodobnie chcesz filtrować informacje:</span><span class="sxs-lookup"><span data-stu-id="51ed7-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="51ed7-124">Ogólny opis ciągu rodziny procesora, można tylko zwrócić **typem systemu** właściwości:</span><span class="sxs-lookup"><span data-stu-id="51ed7-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="51ed7-125">Lista komputerów producenta i Model</span><span class="sxs-lookup"><span data-stu-id="51ed7-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="51ed7-126">Informacje o komputerze modelu jest również dostępna z **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="51ed7-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="51ed7-127">Standardowa wyświetlanych wyników nie będzie żadnego filtrowania danych OEM:</span><span class="sxs-lookup"><span data-stu-id="51ed7-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem

Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

<span data-ttu-id="51ed7-128">Dane wyjściowe poleceń, takich jak ta, które zwracają informacje bezpośrednio z niektórych urządzeń, jest tylko dane, które masz.</span><span class="sxs-lookup"><span data-stu-id="51ed7-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="51ed7-129">Niektóre informacje nie została poprawnie skonfigurowana przez producentów sprzętu i dlatego mogą być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="51ed7-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="51ed7-130">Lista zainstalowanych poprawek</span><span class="sxs-lookup"><span data-stu-id="51ed7-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="51ed7-131">Wyświetl listę wszystkich zainstalowanych poprawek za pomocą **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="51ed7-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="51ed7-132">Ta klasa zwraca listę poprawek, który wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="51ed7-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
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

<span data-ttu-id="51ed7-133">Bardziej zwięzły danych wyjściowych można wykluczyć niektórych właściwości.</span><span class="sxs-lookup"><span data-stu-id="51ed7-133">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="51ed7-134">Chociaż można używać **właściwości Get-WmiObject** parametr, aby wybrać tylko **HotFixID**, to tak faktycznie zwrócą więcej informacji, ponieważ domyślnie powoduje wyświetlenie wszystkich metadanych:</span><span class="sxs-lookup"><span data-stu-id="51ed7-134">Although you can use the **Get-WmiObject's Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="51ed7-135">Dodatkowe dane są zwracane, ponieważ parametr właściwości w **Get-WmiObject** ogranicza właściwości zwrócony z wystąpień klasy usługi WMI, nie obiekt zwrócił do programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51ed7-135">The additional data is returned, because the Property parameter in **Get-WmiObject** restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span> <span data-ttu-id="51ed7-136">Aby ograniczyć dane wyjściowe, należy użyć **Select-Object**:</span><span class="sxs-lookup"><span data-stu-id="51ed7-136">To reduce the output, use **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId

HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="51ed7-137">Wyświetlanie informacji o wersji systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="51ed7-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="51ed7-138">**Win32_OperatingSystem** właściwości klasy zawierają informacje o pakiecie wersji i usługi.</span><span class="sxs-lookup"><span data-stu-id="51ed7-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="51ed7-139">Jawnie można wybrać tylko te właściwości, aby uzyskać informacje o wersji podsumowanie z **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="51ed7-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="51ed7-140">Można również użyć symboli wieloznacznych z **właściwości Select-Object** parametru.</span><span class="sxs-lookup"><span data-stu-id="51ed7-140">You can also use wildcards with the **Select-Object's Property** parameter.</span></span> <span data-ttu-id="51ed7-141">Ponieważ wszystkie właściwości, począwszy od jednej **kompilacji** lub **z dodatkiem Service Pack** należy użyć w tym miejscu możemy to zmniejszyć do następującej postaci:</span><span class="sxs-lookup"><span data-stu-id="51ed7-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="51ed7-142">Wyświetlanie lokalnych użytkowników i właściciela</span><span class="sxs-lookup"><span data-stu-id="51ed7-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="51ed7-143">Lokalne ogólne informacje o użytkowniku — liczba licencjonowanych użytkowników, bieżąca liczba użytkowników i nazwy właściciela — można znaleźć zestaw **Win32_OperatingSystem** właściwości.</span><span class="sxs-lookup"><span data-stu-id="51ed7-143">Local general user information—number of licensed users, current number of users, and owner name—can be found with a selection of **Win32_OperatingSystem** properties.</span></span> <span data-ttu-id="51ed7-144">Możesz wybrać jawnie właściwości do wyświetlenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="51ed7-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="51ed7-145">Jest bardziej zwięzły wersji przy użyciu symboli wieloznacznych:</span><span class="sxs-lookup"><span data-stu-id="51ed7-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="51ed7-146">Pobieranie dostępnego miejsca na dysku</span><span class="sxs-lookup"><span data-stu-id="51ed7-146">Getting Available Disk Space</span></span>

<span data-ttu-id="51ed7-147">Aby wyświetlić miejsca na dysku i wolnego miejsca na dyskach lokalnych, służy klasy WMI Win32_LogicalDisk.</span><span class="sxs-lookup"><span data-stu-id="51ed7-147">To see the disk space and free space for local drives, you can use the WMI Win32_LogicalDisk class.</span></span> <span data-ttu-id="51ed7-148">Należy sprawdzić tylko wystąpienia o DriveType 3 — wartość używa usługi WMI stałe dyski twarde.</span><span class="sxs-lookup"><span data-stu-id="51ed7-148">You need to see only instances with a DriveType of 3—the value WMI uses for fixed hard disks.</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

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

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="51ed7-149">Trwa pobieranie informacji o sesji logowania</span><span class="sxs-lookup"><span data-stu-id="51ed7-149">Getting Logon Session Information</span></span>

<span data-ttu-id="51ed7-150">Aby uzyskać ogólne informacje dotyczące sesji logowania skojarzone z użytkownikami za pośrednictwem klasy WMI Win32_LogonSession:</span><span class="sxs-lookup"><span data-stu-id="51ed7-150">You can get general information about logon sessions associated with users through the WMI Win32_LogonSession class:</span></span>

```powershell
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="51ed7-151">Pobieranie użytkownika zalogowanego na komputerze</span><span class="sxs-lookup"><span data-stu-id="51ed7-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="51ed7-152">Użytkownik zalogowany do określonego systemu komputerowego przy użyciu Win32_ComputerSystem można wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="51ed7-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="51ed7-153">To polecenie zwraca tylko użytkownika zalogowanego na pulpicie systemu:</span><span class="sxs-lookup"><span data-stu-id="51ed7-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="51ed7-154">Pobieranie czasu lokalnego na komputerze</span><span class="sxs-lookup"><span data-stu-id="51ed7-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="51ed7-155">Za pomocą klasy WMI Win32_LocalTime można pobrać bieżącego czasu lokalnego na określonym komputerze.</span><span class="sxs-lookup"><span data-stu-id="51ed7-155">You can retrieve the current local time on a specific computer by using the WMI Win32_LocalTime class.</span></span> <span data-ttu-id="51ed7-156">Ponieważ ta klasa domyślnie wyświetla wszystkie metadane, można filtrować przy użyciu **Select-Object**:</span><span class="sxs-lookup"><span data-stu-id="51ed7-156">Because this class by default displays all metadata, you may want to filter it using **Select-Object**:</span></span>

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

### <a name="displaying-service-status"></a><span data-ttu-id="51ed7-157">Wyświetlanie stanu usługi</span><span class="sxs-lookup"><span data-stu-id="51ed7-157">Displaying Service Status</span></span>

<span data-ttu-id="51ed7-158">Aby wyświetlić stan wszystkich usług na określonym komputerze, lokalnie służy **Get-Service** polecenia cmdlet, jak wspomniano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="51ed7-158">To view the status of all services on a specific computer, you can locally use the **Get-Service** cmdlet as mentioned earlier.</span></span> <span data-ttu-id="51ed7-159">Dla systemów zdalnych można użyć klasy WMI Win32_Service.</span><span class="sxs-lookup"><span data-stu-id="51ed7-159">For remote systems, you can use the WMI Win32_Service class.</span></span> <span data-ttu-id="51ed7-160">Jeśli używasz również **Select-Object** mają być filtrowane wyniki do **stan**, **nazwa**, i **DisplayName**, format danych wyjściowych będzie niemal identyczny z **Get-Service**:</span><span class="sxs-lookup"><span data-stu-id="51ed7-160">If you also use **Select-Object** to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from **Get-Service**:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="51ed7-161">Umożliwia wyświetlanie pełne nazwy okazjonalne usługi z bardzo długie nazwy, warto użyć **Format-Table** z **AutoSize** i **zawijanie** parametrów , można zoptymalizować szerokość kolumny oraz umożliwić długie nazwy opakowywać zamiast obcięcie:</span><span class="sxs-lookup"><span data-stu-id="51ed7-161">To allow the complete display of names for the occasional services with extremely long names, you may want to use **Format-Table** with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
