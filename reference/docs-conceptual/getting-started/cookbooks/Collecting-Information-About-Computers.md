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
# <a name="collecting-information-about-computers"></a><span data-ttu-id="09a2f-103">Zbieranie informacji dotyczących komputerów</span><span class="sxs-lookup"><span data-stu-id="09a2f-103">Collecting Information About Computers</span></span>

<span data-ttu-id="09a2f-104">Polecenia cmdlet z **CimCmdlets** modułu są najważniejsze polecenia cmdlet do wykonywania ogólnych zadań zarządzania.</span><span class="sxs-lookup"><span data-stu-id="09a2f-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="09a2f-105">Wszystkie ustawienia podsystemu krytyczne są udostępniane za pośrednictwem usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="09a2f-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="09a2f-106">Ponadto WMI dane są traktowane jako obiekty, które znajdują się w kolekcji jednego lub więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="09a2f-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="09a2f-107">Ponieważ środowisko Windows PowerShell również współpracuje z obiektami i ma potok, który umożliwia traktowanie jednego lub wielu obiektów w taki sam sposób, ogólny dostęp usługi WMI umożliwia wykonywanie niektórych zaawansowanych zadań z bardzo małego wysiłku.</span><span class="sxs-lookup"><span data-stu-id="09a2f-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="09a2f-108">W poniższych przykładach pokazano, jak zbierać określone informacje przy użyciu `Get-CimInstance` względem dowolnego komputera.</span><span class="sxs-lookup"><span data-stu-id="09a2f-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="09a2f-109">Określono **ComputerName** parametru z wartością kropka (**.**), która reprezentuje komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="09a2f-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="09a2f-110">Można określić nazwę lub adres IP skojarzony z dowolnego komputera, który można otworzyć za pomocą usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="09a2f-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="09a2f-111">Aby uzyskać informacje o komputerze lokalnym, można pominąć **ComputerName** parametru.</span><span class="sxs-lookup"><span data-stu-id="09a2f-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="09a2f-112">Wyświetlanie ustawień pulpitu</span><span class="sxs-lookup"><span data-stu-id="09a2f-112">Listing Desktop Settings</span></span>

<span data-ttu-id="09a2f-113">Rozpocznie się za pomocą polecenia, które zbiera informacje o stacji roboczych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="09a2f-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="09a2f-114">Zwraca informacje dotyczące wszystkich pulpitach, czy są one używane lub nie.</span><span class="sxs-lookup"><span data-stu-id="09a2f-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="09a2f-115">Informacje zwrócone przez niektóre klasy usługi WMI może być bardzo szczegółowe i często zawierają metadane dotyczące klasy usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="09a2f-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="09a2f-116">Ponieważ większość tych właściwości metadanych mają nazwy zaczynające się **Cim**, można filtrować przy użyciu właściwości `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="09a2f-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="09a2f-117">Określ **- ExcludeProperty** parametr "Cim \*" jako wartości.</span><span class="sxs-lookup"><span data-stu-id="09a2f-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="09a2f-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="09a2f-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="09a2f-119">Filtrowanie metadanych, należy użyć operatora potoku (|) do wysyłania wyniki `Get-CimInstance` polecenie `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="09a2f-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="09a2f-120">Wyświetlanie informacji o systemie BIOS</span><span class="sxs-lookup"><span data-stu-id="09a2f-120">Listing BIOS Information</span></span>

<span data-ttu-id="09a2f-121">WMI **Win32_BIOS** klasy zwraca stosunkowo małe i kompletne informacje dotyczące systemu BIOS na komputerze lokalnym:</span><span class="sxs-lookup"><span data-stu-id="09a2f-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="09a2f-122">Wyświetlanie informacji o procesora</span><span class="sxs-lookup"><span data-stu-id="09a2f-122">Listing Processor Information</span></span>

<span data-ttu-id="09a2f-123">Informacje o procesorze ogólne można pobrać za pomocą usługi WMI **Win32_Processor** klasy, mimo że będzie prawdopodobnie chcesz filtrować informacje:</span><span class="sxs-lookup"><span data-stu-id="09a2f-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="09a2f-124">Ogólny opis ciągu rodziny procesora, można tylko zwrócić **typem systemu** właściwości:</span><span class="sxs-lookup"><span data-stu-id="09a2f-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="09a2f-125">Lista komputerów producenta i Model</span><span class="sxs-lookup"><span data-stu-id="09a2f-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="09a2f-126">Informacje o komputerze modelu jest również dostępna z **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="09a2f-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="09a2f-127">Standardowa wyświetlanych wyników nie będzie żadnego filtrowania danych OEM:</span><span class="sxs-lookup"><span data-stu-id="09a2f-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="09a2f-128">Dane wyjściowe poleceń, takich jak ta, które zwracają informacje bezpośrednio z niektórych urządzeń, jest tylko dane, które masz.</span><span class="sxs-lookup"><span data-stu-id="09a2f-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="09a2f-129">Niektóre informacje nie została poprawnie skonfigurowana przez producentów sprzętu i dlatego mogą być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="09a2f-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="09a2f-130">Lista zainstalowanych poprawek</span><span class="sxs-lookup"><span data-stu-id="09a2f-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="09a2f-131">Wyświetl listę wszystkich zainstalowanych poprawek za pomocą **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="09a2f-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="09a2f-132">Ta klasa zwraca listę poprawek, który wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="09a2f-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="09a2f-133">Bardziej zwięzły danych wyjściowych można wykluczyć niektórych właściwości.</span><span class="sxs-lookup"><span data-stu-id="09a2f-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="09a2f-134">Chociaż można używać `Get-CimInstance`w **właściwości** parametr, aby wybrać tylko **HotFixID**, to tak faktycznie zwrócą więcej informacji, ponieważ domyślnie powoduje wyświetlenie wszystkich metadanych:</span><span class="sxs-lookup"><span data-stu-id="09a2f-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="09a2f-135">Dodatkowe dane są zwracane, ponieważ parametr właściwości w `Get-CimInstance` ogranicza właściwości zwrócony z wystąpień klasy usługi WMI, nie obiekt zwrócił do programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09a2f-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="09a2f-136">Aby ograniczyć dane wyjściowe, należy użyć `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="09a2f-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="09a2f-137">Wyświetlanie informacji o wersji systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="09a2f-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="09a2f-138">**Win32_OperatingSystem** właściwości klasy zawierają informacje o pakiecie wersji i usługi.</span><span class="sxs-lookup"><span data-stu-id="09a2f-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="09a2f-139">Jawnie można wybrać tylko te właściwości, aby uzyskać informacje o wersji podsumowanie z **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="09a2f-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="09a2f-140">Można również użyć symboli wieloznacznych z `Select-Object`w **właściwości** parametru.</span><span class="sxs-lookup"><span data-stu-id="09a2f-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="09a2f-141">Ponieważ wszystkie właściwości, począwszy od jednej **kompilacji** lub **z dodatkiem Service Pack** należy użyć w tym miejscu możemy to zmniejszyć do następującej postaci:</span><span class="sxs-lookup"><span data-stu-id="09a2f-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="09a2f-142">Wyświetlanie lokalnych użytkowników i właściciela</span><span class="sxs-lookup"><span data-stu-id="09a2f-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="09a2f-143">Lokalne ogólne informacje o użytkowniku — liczba licencjonowanych użytkowników, bieżąca liczba użytkowników i nazwy właściciela — można znaleźć zestaw **Win32_OperatingSystem** właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="09a2f-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="09a2f-144">Możesz wybrać jawnie właściwości do wyświetlenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="09a2f-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="09a2f-145">Jest bardziej zwięzły wersji przy użyciu symboli wieloznacznych:</span><span class="sxs-lookup"><span data-stu-id="09a2f-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="09a2f-146">Pobieranie dostępnego miejsca na dysku</span><span class="sxs-lookup"><span data-stu-id="09a2f-146">Getting Available Disk Space</span></span>

<span data-ttu-id="09a2f-147">Aby wyświetlić miejsca na dysku i wolnego miejsca na dyskach lokalnych, służy klasy Win32_LogicalDisk usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="09a2f-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="09a2f-148">Należy sprawdzić tylko wystąpienia o DriveType 3 — wartość używa usługi WMI stałe dyski twarde.</span><span class="sxs-lookup"><span data-stu-id="09a2f-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

### <a name="getting-logon-session-information"></a><span data-ttu-id="09a2f-149">Trwa pobieranie informacji o sesji logowania</span><span class="sxs-lookup"><span data-stu-id="09a2f-149">Getting Logon Session Information</span></span>

<span data-ttu-id="09a2f-150">Można uzyskać ogólne informacje dotyczące sesji logowania skojarzone z użytkownikami za pomocą **Win32_LogonSession** klasy usługi WMI:</span><span class="sxs-lookup"><span data-stu-id="09a2f-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="09a2f-151">Pobieranie użytkownika zalogowanego na komputerze</span><span class="sxs-lookup"><span data-stu-id="09a2f-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="09a2f-152">Użytkownik zalogowany do określonego systemu komputerowego przy użyciu Win32_ComputerSystem można wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="09a2f-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="09a2f-153">To polecenie zwraca tylko użytkownika zalogowanego na pulpicie systemu:</span><span class="sxs-lookup"><span data-stu-id="09a2f-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="09a2f-154">Pobieranie czasu lokalnego na komputerze</span><span class="sxs-lookup"><span data-stu-id="09a2f-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="09a2f-155">Bieżący czas lokalny na określonym komputerze można pobrać za pomocą **Win32_LocalTime** klasy usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="09a2f-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

### <a name="displaying-service-status"></a><span data-ttu-id="09a2f-156">Wyświetlanie stanu usługi</span><span class="sxs-lookup"><span data-stu-id="09a2f-156">Displaying Service Status</span></span>

<span data-ttu-id="09a2f-157">Aby wyświetlić stan wszystkich usług na określonym komputerze, lokalnie służy `Get-Service` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="09a2f-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="09a2f-158">Dla systemów zdalnych, możesz użyć **Win32_Service** klasy usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="09a2f-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="09a2f-159">Jeśli używasz również `Select-Object` mają być filtrowane wyniki do **stan**, **nazwa**, i **DisplayName**, format danych wyjściowych będzie niemal identyczne z `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="09a2f-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="09a2f-160">Umożliwia wyświetlanie pełne nazwy okazjonalne usługi z bardzo długie nazwy, warto użyć `Format-Table` z **AutoSize** i **zawijanie** parametrów, aby zoptymalizować szerokość kolumny i Zezwalaj na długie nazwy opakowywać zamiast obcięcie:</span><span class="sxs-lookup"><span data-stu-id="09a2f-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
