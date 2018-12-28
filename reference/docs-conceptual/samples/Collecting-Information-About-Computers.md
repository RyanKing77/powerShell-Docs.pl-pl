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
# <a name="collecting-information-about-computers"></a><span data-ttu-id="91389-103">Zbieranie informacji dotyczących komputerów</span><span class="sxs-lookup"><span data-stu-id="91389-103">Collecting Information About Computers</span></span>

<span data-ttu-id="91389-104">Polecenia cmdlet z **CimCmdlets** moduł są najważniejsze poleceń cmdlet do wykonywania ogólnych zadań zarządzania.</span><span class="sxs-lookup"><span data-stu-id="91389-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="91389-105">Wszystkie ustawienia krytyczny podsystem są udostępniane za pośrednictwem usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="91389-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="91389-106">Ponadto WMI dane są traktowane jako obiekty, które znajdują się w kolekcji jednego lub kilku elementów.</span><span class="sxs-lookup"><span data-stu-id="91389-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="91389-107">Ponieważ środowiska Windows PowerShell również współdziała z obiektami i ma potok, który umożliwia traktowanie jednego lub wielu obiektów w taki sam sposób, ogólny dostęp usługi WMI umożliwia wykonywanie niektórych zaawansowanych zadań przy użyciu bardzo małego wysiłku.</span><span class="sxs-lookup"><span data-stu-id="91389-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="91389-108">Poniższe przykłady pokazują, jak zbierać określone informacje przy użyciu `Get-CimInstance` względem dowolnego komputera.</span><span class="sxs-lookup"><span data-stu-id="91389-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="91389-109">Określamy **ComputerName** parametru z wartością kropka (**.**), który reprezentuje komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="91389-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="91389-110">Można określić nazwę lub adres IP skojarzony z dowolnego komputera, który można osiągnąć za pomocą usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="91389-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="91389-111">Aby pobrać informacje o komputerze lokalnym, można pominąć **ComputerName** parametru.</span><span class="sxs-lookup"><span data-stu-id="91389-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="91389-112">Lista ustawień pulpitu</span><span class="sxs-lookup"><span data-stu-id="91389-112">Listing Desktop Settings</span></span>

<span data-ttu-id="91389-113">Rozpocznie się za pomocą polecenia, które zbiera informacje o komputerach, na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="91389-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="91389-114">Zwraca informacje o wszystkich komputerach, czy są one używane lub nie.</span><span class="sxs-lookup"><span data-stu-id="91389-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="91389-115">Informacje zwrócone przez niektóre klasy WMI może być bardzo szczegółowe i często zawierają metadane dotyczące klasy usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="91389-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="91389-116">Ponieważ większość tych właściwości metadanych mają nazwy rozpoczynające się od **Cim**, można filtrować właściwości, za pomocą `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="91389-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="91389-117">Określ **- ExcludeProperty** "Cim \*" jako wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="91389-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="91389-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="91389-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="91389-119">Aby odfiltrować metadanych, użyj operatora potoku (|) do wysłania wyniki `Get-CimInstance` polecenie `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="91389-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="91389-120">Wyświetlanie informacji o systemie BIOS</span><span class="sxs-lookup"><span data-stu-id="91389-120">Listing BIOS Information</span></span>

<span data-ttu-id="91389-121">WMI **Win32_BIOS** Klasa zwraca stosunkowo małe i kompletne informacje o systemie BIOS komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="91389-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="91389-122">Informacje o procesorze listy</span><span class="sxs-lookup"><span data-stu-id="91389-122">Listing Processor Information</span></span>

<span data-ttu-id="91389-123">Informacje o procesorze ogólne można pobrać za pomocą usługi WMI **Win32_Processor** klasy, chociaż prawdopodobnie będziesz filtrować informacje:</span><span class="sxs-lookup"><span data-stu-id="91389-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="91389-124">Ogólny opis ciągu rodziny procesorów, można po prostu zwrócić **typem systemu** właściwości:</span><span class="sxs-lookup"><span data-stu-id="91389-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="91389-125">Lista komputerów producent i Model</span><span class="sxs-lookup"><span data-stu-id="91389-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="91389-126">Informacje o komputerze modelu jest również dostępna z **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="91389-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="91389-127">Standardowe dane wyjściowe wyświetlane nie wymaga żadnego filtrowania do dostarczania danych OEM:</span><span class="sxs-lookup"><span data-stu-id="91389-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="91389-128">Dane wyjściowe za pomocą poleceń takich jak ta, które zwracają informacje bezpośrednio w sprzęt, jest tylko jako dane, do których masz.</span><span class="sxs-lookup"><span data-stu-id="91389-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="91389-129">Niektóre informacje nie jest poprawnie skonfigurowana przez producentów sprzętu i dlatego może być niedostępna.</span><span class="sxs-lookup"><span data-stu-id="91389-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="91389-130">Lista zainstalowanych poprawek</span><span class="sxs-lookup"><span data-stu-id="91389-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="91389-131">Możesz wyświetlić listę wszystkich zainstalowanych poprawek za pomocą **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="91389-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="91389-132">Ta klasa zwraca listę poprawek, które wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="91389-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="91389-133">Dla bardziej zwięzłą danych wyjściowych można wykluczyć niektóre właściwości.</span><span class="sxs-lookup"><span data-stu-id="91389-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="91389-134">Chociaż można używać `Get-CimInstance`firmy **właściwość** parametru, aby wybrać tylko **HotFixID**, wykonanie tej tak, faktycznie zwrócą więcej informacji, ponieważ domyślnie powoduje wyświetlenie wszystkich metadanych:</span><span class="sxs-lookup"><span data-stu-id="91389-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="91389-135">Dodatkowe dane są zwracane, ponieważ parametr właściwości w `Get-CimInstance` ogranicza właściwości zwrócone w wyniku wystąpienia klasy WMI, nie obiekt zwrócony do programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91389-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="91389-136">Aby ograniczyć dane wyjściowe, należy użyć `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="91389-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="91389-137">Wyświetlanie informacji o wersji systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="91389-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="91389-138">**Win32_OperatingSystem** właściwości klas, które zawierają informacje o pakiecie wersji i usługi.</span><span class="sxs-lookup"><span data-stu-id="91389-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="91389-139">Można jawnie wybrać tylko te właściwości, aby uzyskać informacje o wersji podsumowanie z **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="91389-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="91389-140">Możesz również użyć symboli wieloznacznych przy użyciu `Select-Object`firmy **właściwość** parametru.</span><span class="sxs-lookup"><span data-stu-id="91389-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="91389-141">Ponieważ wszystkie właściwości, począwszy od albo **kompilacji** lub **z dodatkiem Service Pack** są ważne do użycia w tym miejscu możemy to skrócić do następującej postaci:</span><span class="sxs-lookup"><span data-stu-id="91389-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="91389-142">Wyświetlanie listy lokalnych użytkowników i właściciela</span><span class="sxs-lookup"><span data-stu-id="91389-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="91389-143">Lokalne ogólne informacje o użytkowniku — liczbę objętych licencją użytkowników, bieżąca liczba użytkowników i nazwy właściciela — można znaleźć szereg **Win32_OperatingSystem** właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="91389-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="91389-144">Można jawnie wybrać właściwości do wyświetlenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="91389-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="91389-145">Nieco bardziej zwięzłą przy użyciu symboli wieloznacznych jest:</span><span class="sxs-lookup"><span data-stu-id="91389-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="91389-146">Wprowadzenie dostępnego miejsca na dysku</span><span class="sxs-lookup"><span data-stu-id="91389-146">Getting Available Disk Space</span></span>

<span data-ttu-id="91389-147">Aby zobaczyć miejsce na dysku i wolnego miejsca na dyskach lokalnych, można użyć klasy Win32_LogicalDisk WMI.</span><span class="sxs-lookup"><span data-stu-id="91389-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="91389-148">Chcesz zobaczyć tylko wystąpienia z DriveType 3 — wartość WMI używa stałej dysków twardych.</span><span class="sxs-lookup"><span data-stu-id="91389-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

### <a name="getting-logon-session-information"></a><span data-ttu-id="91389-149">Pobieranie informacji o sesji logowania</span><span class="sxs-lookup"><span data-stu-id="91389-149">Getting Logon Session Information</span></span>

<span data-ttu-id="91389-150">Zawiera ogólne informacje o sesjach logowania skojarzone z użytkownikami za pomocą **Win32_LogonSession** klasy usługi WMI:</span><span class="sxs-lookup"><span data-stu-id="91389-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="91389-151">Pobieranie użytkownika zalogowanego na komputerze</span><span class="sxs-lookup"><span data-stu-id="91389-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="91389-152">Użytkownik zalogowany do określonego systemu komputerowego przy użyciu Win32_ComputerSystem można wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="91389-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="91389-153">To polecenie zwraca tylko użytkownika zalogowanego na pulpicie systemu:</span><span class="sxs-lookup"><span data-stu-id="91389-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="91389-154">Pobieranie czasu lokalnego na komputerze</span><span class="sxs-lookup"><span data-stu-id="91389-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="91389-155">Bieżący czas lokalny na określonym komputerze można pobrać za pomocą **Win32_LocalTime** klasy WMI.</span><span class="sxs-lookup"><span data-stu-id="91389-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

### <a name="displaying-service-status"></a><span data-ttu-id="91389-156">Wyświetlanie stanu usługi</span><span class="sxs-lookup"><span data-stu-id="91389-156">Displaying Service Status</span></span>

<span data-ttu-id="91389-157">Aby wyświetlić stan wszystkich usług na określonym komputerze, lokalnie służy `Get-Service` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91389-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="91389-158">W przypadku systemów zdalnych, można użyć **Win32_Service** klasy WMI.</span><span class="sxs-lookup"><span data-stu-id="91389-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="91389-159">Gdy również użyć `Select-Object` do odfiltrowania wyników do **stan**, **nazwa**, i **DisplayName**, format danych wyjściowych będzie niemal identyczne, z `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="91389-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="91389-160">Aby zezwolić na pełne wyświetlanie nazw okazjonalnych o bardzo długich nazwach, warto użyć `Format-Table` z **AutoSize** i **opakować** parametrów w celu optymalizacji szerokość kolumny i Zezwalaj na długich nazwach zawijać zamiast obcinania:</span><span class="sxs-lookup"><span data-stu-id="91389-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
