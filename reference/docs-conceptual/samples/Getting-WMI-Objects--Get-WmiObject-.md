---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Pobieranie obiektów WMI Pobierz WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404699"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="a6b84-103">Pobieranie obiektów WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="a6b84-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="a6b84-104">Pobieranie obiektów WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="a6b84-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="a6b84-105">Instrumentacja zarządzania Windows (WMI) jest technologią podstawową do administrowania systemem Windows, ponieważ ujawnia on szerokiej gamy informacji w jednolity sposób.</span><span class="sxs-lookup"><span data-stu-id="a6b84-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="a6b84-106">Ze względu na ilość WMI sprawia, że to możliwe, polecenia cmdlet programu Windows PowerShell do uzyskiwania dostępu do obiektów WMI **Get-WmiObject**, jest jednym z najbardziej przydatne do wykonywania faktyczną pracę.</span><span class="sxs-lookup"><span data-stu-id="a6b84-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="a6b84-107">Firma Microsoft zamierza omówiono sposób używania Get-WmiObject dostępu do obiektów WMI, a następnie sposób wykorzystania obiektów WMI do wykonywania określonych czynności.</span><span class="sxs-lookup"><span data-stu-id="a6b84-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="a6b84-108">Lista klas usługi WMI</span><span class="sxs-lookup"><span data-stu-id="a6b84-108">Listing WMI Classes</span></span>

<span data-ttu-id="a6b84-109">Pierwszy problem, który wystąpi większość użytkowników usługi WMI próbuje sprawdzić, co można zrobić z usługą WMI.</span><span class="sxs-lookup"><span data-stu-id="a6b84-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="a6b84-110">Klasy usługi WMI Opisz zasoby, które mogą być zarządzane.</span><span class="sxs-lookup"><span data-stu-id="a6b84-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="a6b84-111">Istnieją setki klasy usługi WMI, z których część zawiera dziesiątek, jak właściwości.</span><span class="sxs-lookup"><span data-stu-id="a6b84-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="a6b84-112">**Get-WmiObject** rozwiązuje ten problem, wprowadzając wykrywalny WMI.</span><span class="sxs-lookup"><span data-stu-id="a6b84-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="a6b84-113">Można wyświetlić listę dostępnych klas usługi WMI na komputerze lokalnym, wpisując:</span><span class="sxs-lookup"><span data-stu-id="a6b84-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="a6b84-114">Możesz pobrać te same informacje z komputera zdalnego za pomocą parametru ComputerName określania nazwy komputera lub adres IP:</span><span class="sxs-lookup"><span data-stu-id="a6b84-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="a6b84-115">Lista klas zwrócony przez komputer zdalny mogą się różnić od określonego systemu operacyjnego, który komputer działa i określonych rozszerzeń usługi WMI, dodane przez zainstalowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a6b84-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="a6b84-116">Podczas nawiązywania połączenia z komputerem zdalnym za pomocą Get-WmiObject, komputer zdalny musi działać usługa WMI, a następnie w domyślnej konfiguracji konta, którego używasz, musi być w lokalnej grupy administratorów na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="a6b84-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="a6b84-117">W systemie zdalnym nie trzeba mieć program Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6b84-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="a6b84-118">Dzięki temu można administrować systemy operacyjne, które nie jest uruchomiony program Windows PowerShell, ale mają usługę WMI.</span><span class="sxs-lookup"><span data-stu-id="a6b84-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="a6b84-119">Można nawet dołączyć nazwa_komputera podczas nawiązywania połączenia z systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a6b84-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="a6b84-120">Można użyć nazwy komputera lokalnego, jego adres IP (lub na adres sprzężenia zwrotnego 127.0.0.1), lub stylu WMI "." jako nazwę komputera.</span><span class="sxs-lookup"><span data-stu-id="a6b84-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="a6b84-121">Jeśli używasz programu Windows PowerShell na komputerze o nazwie Admin01 za pomocą adresu IP 192.168.1.90, następujące polecenia wszystkie zwróci klasy usługi WMI dla tego komputera:</span><span class="sxs-lookup"><span data-stu-id="a6b84-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="a6b84-122">Get-WmiObject używa przestrzeni nazw root/cimv2 domyślnie.</span><span class="sxs-lookup"><span data-stu-id="a6b84-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="a6b84-123">Jeśli chcesz określić inny przestrzeni nazw usługi WMI, użyj **Namespace** parametru i określ odpowiednie ścieżki przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="a6b84-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="a6b84-124">Wyświetlanie szczegółów klasy usługi WMI</span><span class="sxs-lookup"><span data-stu-id="a6b84-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="a6b84-125">Jeśli znasz już nazwę klasy usługi WMI, można użyć go można pobrać informacji o natychmiast.</span><span class="sxs-lookup"><span data-stu-id="a6b84-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="a6b84-126">Na przykład jeden z najczęściej używanych do odzyskiwania informacji o komputerze klasy usługi WMI jest **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="a6b84-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="a6b84-127">Mimo że firma Microsoft są wyświetlane wszystkie parametry, polecenia mogą być wyrażone w sposób bardziej zwięzły.</span><span class="sxs-lookup"><span data-stu-id="a6b84-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="a6b84-128">**ComputerName** parametr nie jest konieczne, łącząc się z systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a6b84-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="a6b84-129">Pokazujemy pokazują przypadek najbardziej ogólny i przypominać o parametrze.</span><span class="sxs-lookup"><span data-stu-id="a6b84-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="a6b84-130">**Namespace** wartość domyślna to root/cimv2, a także można pominąć.</span><span class="sxs-lookup"><span data-stu-id="a6b84-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="a6b84-131">Większość poleceń cmdlet pozwalają na koniec pominąć nazwy wspólnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="a6b84-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="a6b84-132">Przy użyciu Get-WmiObject, jeśli nazwa nie jest określony jako pierwszy parametr środowiska Windows PowerShell traktuje je jako **klasy** parametru.</span><span class="sxs-lookup"><span data-stu-id="a6b84-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="a6b84-133">Oznacza to, że ostatnie polecenie może został wystawiony przez wpisanie:</span><span class="sxs-lookup"><span data-stu-id="a6b84-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="a6b84-134">**Win32_OperatingSystem** klasa ma wiele właściwości więcej niż te są wyświetlane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="a6b84-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="a6b84-135">Get-Member można użyć, aby wyświetlić wszystkie właściwości.</span><span class="sxs-lookup"><span data-stu-id="a6b84-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="a6b84-136">Właściwości klasy WMI są automatycznie dostępne, podobnie jak inne właściwości obiektu:</span><span class="sxs-lookup"><span data-stu-id="a6b84-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="a6b84-137">Wyświetlanie właściwości innych niż domyślne za pomocą poleceń cmdlet Format</span><span class="sxs-lookup"><span data-stu-id="a6b84-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="a6b84-138">Jeśli chcesz, aby uzyskać informacje zawarte w **Win32_OperatingSystem** klasy, to znaczy nie są wyświetlane domyślnie, możesz wyświetlić ją za pomocą **Format** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6b84-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="a6b84-139">Na przykład jeśli chcesz wyświetlić dane dostępnej pamięci, wpisz:</span><span class="sxs-lookup"><span data-stu-id="a6b84-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="a6b84-140">Symbole wieloznaczne pracować nazwy właściwości w **Format-Table**, więc elementu końcowego potoku można ograniczyć do `Format-Table -Property Total,Free`</span><span class="sxs-lookup"><span data-stu-id="a6b84-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="a6b84-141">Dane pamięci może być bardziej czytelny, jeśli należy sformatować jako listę, wpisując:</span><span class="sxs-lookup"><span data-stu-id="a6b84-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
