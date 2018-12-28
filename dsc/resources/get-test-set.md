---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Get-Test-Set
ms.openlocfilehash: e46710954679bf20f4536c6efbcbd4dafd9e629e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404964"
---
# <a name="get-test-set"></a><span data-ttu-id="08887-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="08887-103">Get-Test-Set</span></span>

><span data-ttu-id="08887-104">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="08887-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![GET, testowania i Set](/media/get-test-set.png)

<span data-ttu-id="08887-106">PowerShell Desired State Configuration jest konstruowany wokół **uzyskać**, **testu**, i **ustaw** procesu.</span><span class="sxs-lookup"><span data-stu-id="08887-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="08887-107">DSC [zasobów](resources.md) każdy z nich zawiera metody ukończenia każdej z tych operacji.</span><span class="sxs-lookup"><span data-stu-id="08887-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="08887-108">W [konfiguracji](../configurations/configurations.md), należy zdefiniować bloki zasobów, aby wypełnić klucze, które stają się parametry zasobu **uzyskać**, **testu**, i **ustaw** metody.</span><span class="sxs-lookup"><span data-stu-id="08887-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="08887-109">To jest składnia **usługi** bloku zasobów.</span><span class="sxs-lookup"><span data-stu-id="08887-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="08887-110">**Usługi** zasobów konfiguruje usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="08887-110">The **Service** resource configures Windows services.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="08887-111">**Uzyskać**, **testu**, i **ustaw** metody **usługi** zasobów będzie mieć bloków parametrów, które akceptuje te wartości.</span><span class="sxs-lookup"><span data-stu-id="08887-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> <span data-ttu-id="08887-112">Język i metody używane do definiowania zasobu określa sposób, w jaki **uzyskać**, **testu**, i **ustaw** metody zostaną zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="08887-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="08887-113">Ponieważ **usługi** zasobu ma tylko jeden klucz wymagany (`Name`), **usługi** bloku zasobów może być tak proste, jak to:</span><span class="sxs-lookup"><span data-stu-id="08887-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

<span data-ttu-id="08887-114">Podczas kompilowania konfiguracji powyższych wartości, które określisz dla klucza są przechowywane w pliku "MOF", który jest generowany.</span><span class="sxs-lookup"><span data-stu-id="08887-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="08887-115">Aby uzyskać więcej informacji, zobacz [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="08887-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

<span data-ttu-id="08887-116">Po zastosowaniu [Local Configuration Manager](../managing-nodes/metaConfig.md) odczytać wartości "Buforu" z pliku "MOF" i przekazać ją do `-Name` parametru **uzyskać**, **testu**, i **ustaw** metod dla wystąpienia "MyService" **usługi** zasobów.</span><span class="sxs-lookup"><span data-stu-id="08887-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="08887-117">Pobranie</span><span class="sxs-lookup"><span data-stu-id="08887-117">Get</span></span>

<span data-ttu-id="08887-118">**Uzyskać** metoda zasobu, pobiera stan zasobu, ponieważ została ona skonfigurowana w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="08887-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="08887-119">Ten stan jest zwracana jako [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="08887-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="08887-120">Klucze **hashtable** będzie można skonfigurować wartości, i parametry akceptuje zasobu.</span><span class="sxs-lookup"><span data-stu-id="08887-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="08887-121">**Uzyskać** metoda mapuje bezpośrednio do [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08887-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="08887-122">Podczas wywoływania `Get-DSCConfiguration`, przebiegów LCM **uzyskać** metoda poszczególnych zasobów w konfiguracji obecnie zastosowany.</span><span class="sxs-lookup"><span data-stu-id="08887-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="08887-123">LCM używa wartości kluczy przechowywanych w pliku "MOF" jako parametry do każdego odpowiedniego wystąpienia zasobu.</span><span class="sxs-lookup"><span data-stu-id="08887-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="08887-124">To przykładowe dane wyjściowe **usługi** zasobu, który konfiguruje usługę "Buforu".</span><span class="sxs-lookup"><span data-stu-id="08887-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

<span data-ttu-id="08887-125">Dane wyjściowe zawierają bieżące wartości właściwości można konfigurować przez **usługi** zasobów.</span><span class="sxs-lookup"><span data-stu-id="08887-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a><span data-ttu-id="08887-126">Test</span><span class="sxs-lookup"><span data-stu-id="08887-126">Test</span></span>

<span data-ttu-id="08887-127">**Testu** metoda zasobu określa, czy węzeł docelowy jest obecnie zgodne z zasobu *żądanego stanu*.</span><span class="sxs-lookup"><span data-stu-id="08887-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="08887-128">**Testu** metoda zwraca `$True` lub `$False` tylko po to, aby wskazać, czy węzeł jest zgodne.</span><span class="sxs-lookup"><span data-stu-id="08887-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="08887-129">Gdy wywołujesz [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), wywołania LCM **testu** metoda poszczególnych zasobów w konfiguracji obecnie zastosowany.</span><span class="sxs-lookup"><span data-stu-id="08887-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="08887-130">LCM używa wartości kluczy przechowywanych w pliku "MOF" jako parametry do każdego odpowiedniego wystąpienia zasobu.</span><span class="sxs-lookup"><span data-stu-id="08887-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="08887-131">Jeśli wynik dowolnego pojedynczego zasobu **testu** jest `$False`, `Test-DSCConfiguration` zwraca `$False` wskazujący, że ten węzeł nie jest zgodne.</span><span class="sxs-lookup"><span data-stu-id="08887-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="08887-132">Jeśli wszystkie zasobów **testu** metody zwracają `$True`, `Test-DSCConfiguration` zwraca `$True` do wskazania, że węzeł jest zgodne.</span><span class="sxs-lookup"><span data-stu-id="08887-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="08887-133">Począwszy od programu PowerShell w wersji 5.0 `-Detailed` parametr został dodany.</span><span class="sxs-lookup"><span data-stu-id="08887-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="08887-134">Określanie `-Detailed` powoduje, że `Test-DSCConfiguration` zwracać obiekt zawierający kolekcje wyniki zgodne i niezgodne zasoby.</span><span class="sxs-lookup"><span data-stu-id="08887-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="08887-135">Aby uzyskać więcej informacji, zobacz [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="08887-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="08887-136">Ustaw</span><span class="sxs-lookup"><span data-stu-id="08887-136">Set</span></span>

<span data-ttu-id="08887-137">**Ustaw** metoda zasobu próbuje wymusić węzeł, aby była zgodna z zasobu *żądanego stanu*.</span><span class="sxs-lookup"><span data-stu-id="08887-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="08887-138">**Ustaw** metoda można w dużym **idempotentne**, co oznacza, że **ustaw** można uruchamiać wiele razy i zawsze uzyskać ten sam wynik bez błędów.</span><span class="sxs-lookup"><span data-stu-id="08887-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="08887-139">Po uruchomieniu [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), cykle LCM za pośrednictwem poszczególnych zasobów w konfiguracji obecnie zastosowany.</span><span class="sxs-lookup"><span data-stu-id="08887-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="08887-140">LCM pobiera wartości kluczy w ramach bieżącego wystąpienia zasobu z pliku "MOF" i są one używane jako parametry dla **testu** metody.</span><span class="sxs-lookup"><span data-stu-id="08887-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="08887-141">Jeśli **testu** metoda zwraca `$True`, węzeł jest zgodne z bieżącego zasobu i **ustaw** metoda zostanie pominięta.</span><span class="sxs-lookup"><span data-stu-id="08887-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="08887-142">Jeśli **testu** zwraca `$False`, węzeł nie jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="08887-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="08887-143">LCM przekazuje zasób wystąpienia wartości klucza jako parametry do zasobu **ustaw** metodę przywracania węzła zgodności.</span><span class="sxs-lookup"><span data-stu-id="08887-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="08887-144">Określając `-Verbose` i `-Wait` parametrów, możesz obserwować postęp `Start-DSCConfiguration` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08887-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="08887-145">W tym przykładzie ten węzeł jest już zgodne.</span><span class="sxs-lookup"><span data-stu-id="08887-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="08887-146">`Verbose` Dane wyjściowe wskazuje, że **ustaw** metoda została pominięta.</span><span class="sxs-lookup"><span data-stu-id="08887-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a><span data-ttu-id="08887-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08887-147">See also</span></span>

- [<span data-ttu-id="08887-148">Omówienie DSC usługi Azure Automation</span><span class="sxs-lookup"><span data-stu-id="08887-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="08887-149">Konfigurowanie serwera ściągania SMB</span><span class="sxs-lookup"><span data-stu-id="08887-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="08887-150">Konfigurowanie klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="08887-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
