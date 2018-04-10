---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Pobieranie obiektów WMI pobrać WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 67922426ae3f13ef5f4c70bc70bb3ce1594d3d05
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="7809c-103">Pobieranie obiektów WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="7809c-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="7809c-104">Pobieranie obiektów WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="7809c-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="7809c-105">Instrumentacja zarządzania Windows (WMI) jest technologią podstawową do administrowania systemem Windows, ponieważ ujawnia on również szereg informacji w jednolity sposób.</span><span class="sxs-lookup"><span data-stu-id="7809c-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="7809c-106">Ze względu na ilość WMI sprawia, że to możliwe, polecenia cmdlet programu Windows PowerShell do uzyskiwania dostępu do obiektów WMI **Get-WmiObject**, jest jednym z najbardziej przydatne do wykonywania pracy prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="7809c-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="7809c-107">Zamierzamy omówiono sposób użycia Get-WmiObject dostęp do obiektów WMI, a następnie jak wykonywanie określonych czynności, za pomocą obiektów WMI.</span><span class="sxs-lookup"><span data-stu-id="7809c-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="7809c-108">Listę klas usługi WMI</span><span class="sxs-lookup"><span data-stu-id="7809c-108">Listing WMI Classes</span></span>

<span data-ttu-id="7809c-109">Pierwszy problem napotykanych przez większość użytkowników usługi WMI próbuje sprawdzić, co można zrobić za pomocą usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="7809c-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="7809c-110">Klasy WMI, które opisują zasoby, które mogą być zarządzane.</span><span class="sxs-lookup"><span data-stu-id="7809c-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="7809c-111">Brak setki klas WMI, z których część zawiera dziesiątki właściwości.</span><span class="sxs-lookup"><span data-stu-id="7809c-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="7809c-112">**Get-WmiObject** rozwiązano ten problem, tworząc wykrywalny WMI.</span><span class="sxs-lookup"><span data-stu-id="7809c-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="7809c-113">Można wyświetlić listę dostępnych klas usługi WMI na komputerze lokalnym, wpisując:</span><span class="sxs-lookup"><span data-stu-id="7809c-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="7809c-114">Można pobrać te same informacje z komputera zdalnego za pomocą parametr ComputerName, określając nazwę komputera lub adres IP:</span><span class="sxs-lookup"><span data-stu-id="7809c-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="7809c-115">Na liście klasy zwrócony przez komputery zdalne mogą się różnić z powodu określonego systemu operacyjnego na komputerze jest zainstalowany i określonych rozszerzeń WMI dodane przez zainstalowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7809c-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7809c-116">Podczas nawiązywania połączenia z komputerem zdalnym za pomocą Get-WmiObject, komputer zdalny musi być uruchomiony WMI, a następnie w obszarze Konfiguracja domyślna konta, którego używasz, musi być w lokalnej grupy administratorów na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7809c-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="7809c-117">System zdalny musi mieć zainstalowane środowisko Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7809c-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="7809c-118">Dzięki temu można administrować systemów operacyjnych, które nie są uruchomione środowiska Windows PowerShell, ale masz usługę WMI.</span><span class="sxs-lookup"><span data-stu-id="7809c-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="7809c-119">Właściwość ComputerName można uwzględnić nawet podczas nawiązywania połączenia systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7809c-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="7809c-120">Możesz użyć nazwy komputera lokalnego, adres IP (lub adres sprzężenia zwrotnego 127.0.0.1), lub WMI-style "." jako nazwy komputera.</span><span class="sxs-lookup"><span data-stu-id="7809c-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="7809c-121">Jeśli używasz programu Windows PowerShell na komputerze o nazwie Admin01 o adresie IP 192.168.1.90, następujące polecenia wszystkie zwróci klasy usługi WMI dla tego komputera:</span><span class="sxs-lookup"><span data-stu-id="7809c-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="7809c-122">Get-WmiObject domyślnie używa głównego/cimv2 przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7809c-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="7809c-123">Jeśli chcesz określić inny obszar nazw usługi WMI, użyj **Namespace** parametru i określ odpowiednie ścieżki przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="7809c-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="7809c-124">Wyświetlanie szczegółów klasy usługi WMI</span><span class="sxs-lookup"><span data-stu-id="7809c-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="7809c-125">Jeśli znasz już nazwę klasy usługi WMI, można użyć go można uzyskać informacji o natychmiast.</span><span class="sxs-lookup"><span data-stu-id="7809c-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="7809c-126">Na przykład jednej z klas WMI często używane do pobierania informacji o komputerze jest **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="7809c-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="7809c-127">Mimo że firma Microsoft są wyświetlane wszystkie parametry, polecenie może być wyrażona w sposób bardziej zwięzły.</span><span class="sxs-lookup"><span data-stu-id="7809c-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="7809c-128">**ComputerName** parametru nie jest konieczne, łącząc się z systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7809c-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="7809c-129">Zostanie przedstawiony pokazują przypadku najbardziej ogólnym i przypominać o parametrze.</span><span class="sxs-lookup"><span data-stu-id="7809c-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="7809c-130">**Namespace** domyślnie główny/cimv2 i można również pominąć.</span><span class="sxs-lookup"><span data-stu-id="7809c-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="7809c-131">Na koniec większości poleceń cmdlet umożliwiają pominąć nazwę typowych parametrów.</span><span class="sxs-lookup"><span data-stu-id="7809c-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="7809c-132">Z Get-WmiObject, jeśli nie określono nazwy dla pierwszego parametru środowiska Windows PowerShell traktuje ją jako **klasy** parametru.</span><span class="sxs-lookup"><span data-stu-id="7809c-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="7809c-133">Oznacza to, że ostatnie polecenie może wystawiony przez wpisanie:</span><span class="sxs-lookup"><span data-stu-id="7809c-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="7809c-134">**Win32_OperatingSystem** klasa ma wiele właściwości więcej niż wyświetlone tutaj.</span><span class="sxs-lookup"><span data-stu-id="7809c-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="7809c-135">Aby wyświetlić wszystkie właściwości, można użyć elementu członkowskiego Get.</span><span class="sxs-lookup"><span data-stu-id="7809c-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="7809c-136">Właściwości klasy WMI są automatycznie dostępne, podobnie jak inne właściwości obiektu:</span><span class="sxs-lookup"><span data-stu-id="7809c-136">The properties of a WMI class are automatically available like other object properties:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="7809c-137">Wyświetlanie właściwości innych niż domyślne za pomocą poleceń cmdlet formatu</span><span class="sxs-lookup"><span data-stu-id="7809c-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="7809c-138">Jeśli chcesz, aby informacje zawarte w **Win32_OperatingSystem** klasy, czyli nie jest wyświetlany domyślnie, można je wyświetlić przy użyciu **Format** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7809c-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="7809c-139">Na przykład jeśli chcesz wyświetlić dane dostępnej pamięci, wpisz:</span><span class="sxs-lookup"><span data-stu-id="7809c-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="7809c-140">Symbole wieloznaczne pracować z nazwy właściwości w **Format-Table**, dlatego elementu końcowego potoku można zmniejszyć do **Format-Table-właściwość całkowita*, wolne *</span><span class="sxs-lookup"><span data-stu-id="7809c-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to **Format-Table -Property Total*,Free*</span></span>

<span data-ttu-id="7809c-141">Dane pamięci mogą być bardziej czytelny, jeśli zostanie sformatowany jako listy, wpisując:</span><span class="sxs-lookup"><span data-stu-id="7809c-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```