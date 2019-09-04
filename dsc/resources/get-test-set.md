---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Get-test-Set
ms.openlocfilehash: 68738107cd4a222a13dd4afa158f0370953158ad
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215426"
---
# <a name="get-test-set"></a><span data-ttu-id="c8ed3-103">Get-test-Set</span><span class="sxs-lookup"><span data-stu-id="c8ed3-103">Get-Test-Set</span></span>

><span data-ttu-id="c8ed3-104">Dotyczy: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="c8ed3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Pobieranie, testowanie i ustawianie](../media/get-test-set.png)

<span data-ttu-id="c8ed3-106">Konfiguracja żądanego stanu programu PowerShell jest zbudowana wokół procesu **Get**, **test**i **Set** .</span><span class="sxs-lookup"><span data-stu-id="c8ed3-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="c8ed3-107">[Zasoby](resources.md) DSC zawierają metody umożliwiające wykonanie każdej z tych operacji.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="c8ed3-108">W [konfiguracji](../configurations/configurations.md)definiuje się bloki zasobów, aby wypełnić klucze, które stają się parametrami dla metod **Get**, **test**i **Set** zasobu.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="c8ed3-109">Jest to składnia bloku zasobów **usługi** .</span><span class="sxs-lookup"><span data-stu-id="c8ed3-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="c8ed3-110">Zasób **usługi służy** do konfigurowania usług systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="c8ed3-111">Metody **Get**, **test**i **Set** zasobu **usługi** będą mieć bloki parametrów, które akceptują te wartości.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="c8ed3-112">Język i Metoda używane do definiowania zasobów określają sposób definiowania metod **Get**, **test**i **Set** .</span><span class="sxs-lookup"><span data-stu-id="c8ed3-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="c8ed3-113">Ponieważ zasób **usługi** ma tylko jeden wymagany klucz (`Name`), zasób bloku **usługi** może być prosty w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c8ed3-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="c8ed3-114">Po skompilowaniu powyższej konfiguracji wartości podane dla klucza są przechowywane w generowanym pliku "MOF".</span><span class="sxs-lookup"><span data-stu-id="c8ed3-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="c8ed3-115">Aby uzyskać więcej informacji, zobacz [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="c8ed3-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="c8ed3-116">W przypadku zastosowania [Configuration Manager lokalny](../managing-nodes/metaConfig.md) (LCM) odczyta wartość "bufor" z pliku ". MOF `-Name` " i przekaże go do parametru metod **Get**, **test**i **Set** dla wystąpienia **"Moja usługa" Zasób usługi** .</span><span class="sxs-lookup"><span data-stu-id="c8ed3-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="c8ed3-117">Pobranie</span><span class="sxs-lookup"><span data-stu-id="c8ed3-117">Get</span></span>

<span data-ttu-id="c8ed3-118">Metoda **Get** zasobu Pobiera stan zasobu w miarę jego konfiguracji w węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="c8ed3-119">Ten stan jest zwracany jako obiekt [Hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="c8ed3-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="c8ed3-120">Klucze obiektu **Hashtable** będą konfigurowalne wartości lub parametry, które zaakceptuje zasób.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="c8ed3-121">Metoda **Get** mapuje się bezpośrednio do polecenia cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="c8ed3-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="c8ed3-122">Po wywołaniu `Get-DSCConfiguration`, LCM uruchamia metodę **Get** każdego zasobu w aktualnie stosowanej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="c8ed3-123">LCM używa wartości klucza przechowywanych w pliku ". MOF" jako parametrów do każdego odpowiadającego wystąpienia zasobu.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="c8ed3-124">Jest to przykładowe dane wyjściowe z zasobu **usługi** , który konfiguruje usługę "bufor".</span><span class="sxs-lookup"><span data-stu-id="c8ed3-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="c8ed3-125">Dane wyjściowe przedstawiają bieżące właściwości wartości konfigurowalne przez zasób **usługi** .</span><span class="sxs-lookup"><span data-stu-id="c8ed3-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="c8ed3-126">Test</span><span class="sxs-lookup"><span data-stu-id="c8ed3-126">Test</span></span>

<span data-ttu-id="c8ed3-127">Metoda **testowa** zasobu określa, czy węzeł docelowy jest aktualnie zgodny z *żądanym stanem*zasobu.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="c8ed3-128">Metoda **testowa** zwraca `$True` lub `$False` tylko wskazuje, czy węzeł jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="c8ed3-129">Po wywołaniu [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), LCM wywołuje metodę **testową** każdego zasobu w aktualnie stosowanej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="c8ed3-130">LCM używa wartości klucza przechowywanych w pliku ". MOF" jako parametrów do każdego odpowiadającego wystąpienia zasobu.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="c8ed3-131">Jeśli wynik **testu** pojedynczego zasobu to `$False`, `Test-DSCConfiguration` zwraca `$False` informację o tym, że węzeł nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="c8ed3-132">Jeśli wszystkie metody **testowe** zasobu zwracają `$True`, zwraca `Test-DSCConfiguration` `$True` , aby wskazać, że węzeł jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="c8ed3-133">Począwszy od programu PowerShell 5,0, `-Detailed` parametr został dodany.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="c8ed3-134">Określenie `-Detailed` przyczyn`Test-DSCConfiguration` zwrócenia obiektu zawierającego kolekcje wyników dla zgodnych i niezgodnych zasobów.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="c8ed3-135">Aby uzyskać więcej informacji, zobacz [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="c8ed3-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="c8ed3-136">Ustaw</span><span class="sxs-lookup"><span data-stu-id="c8ed3-136">Set</span></span>

<span data-ttu-id="c8ed3-137">Metoda **Set** zasobu próbuje wymusić zgodność węzła z *żądanym stanem*zasobu.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="c8ed3-138">Metoda **Set** ma być **idempotentne**, co oznacza, że **zestaw** może być uruchamiany wiele razy i zawsze uzyskać ten sam wynik bez błędów.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="c8ed3-139">Po uruchomieniu [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), LCM przeprowadzi cykl przez każdy zasób w aktualnie stosowanej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="c8ed3-140">LCM pobiera wartości klucza dla bieżącego wystąpienia zasobu z pliku ". MOF" i używa ich jako parametrów dla metody **testowej** .</span><span class="sxs-lookup"><span data-stu-id="c8ed3-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="c8ed3-141">Jeśli metoda **testowa** zwraca `$True`, węzeł jest zgodny z bieżącym zasobem, a Metoda **Set** jest pomijana.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="c8ed3-142">Jeśli **test** zwraca `$False`, węzeł nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="c8ed3-143">LCM przekazuje wartości klucza wystąpienia zasobu jako parametry do metody **Set** zasobu, przywracając węzeł do zgodności.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="c8ed3-144">Określając `-Verbose` parametry i `-Wait` , można `Start-DSCConfiguration` obserwować postęp polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="c8ed3-145">W tym przykładzie węzeł jest już zgodny.</span><span class="sxs-lookup"><span data-stu-id="c8ed3-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="c8ed3-146">Dane wyjściowe wskazują, że Metoda Set została pominięta. `Verbose`</span><span class="sxs-lookup"><span data-stu-id="c8ed3-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c8ed3-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8ed3-147">See also</span></span>

- [<span data-ttu-id="c8ed3-148">Azure Automation DSC — Omówienie</span><span class="sxs-lookup"><span data-stu-id="c8ed3-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="c8ed3-149">Konfigurowanie serwera ściągania SMB</span><span class="sxs-lookup"><span data-stu-id="c8ed3-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="c8ed3-150">Konfigurowanie klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="c8ed3-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
