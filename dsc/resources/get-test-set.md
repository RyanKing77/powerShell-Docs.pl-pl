---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Get-Test-Set
ms.openlocfilehash: 6d059518a49926bc5fb56e37e7d3d4d2c66bddec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076603"
---
# <a name="get-test-set"></a>Get-Test-Set

>Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

![Pobieranie, testowanie i ustawianie](/media/get-test-set.png)

PowerShell Desired State Configuration jest konstruowany wokół **uzyskać**, **testu**, i **ustaw** procesu. DSC [zasobów](resources.md) każdy z nich zawiera metody ukończenia każdej z tych operacji. W [konfiguracji](../configurations/configurations.md), należy zdefiniować bloki zasobów, aby wypełnić klucze, które stają się parametry zasobu **uzyskać**, **testu**, i **ustaw** metody.

To jest składnia **usługi** bloku zasobów. **Usługi** zasobów konfiguruje usługi Windows.

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

**Uzyskać**, **testu**, i **ustaw** metody **usługi** zasobów będzie mieć bloków parametrów, które akceptuje te wartości.

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
> Język i metody używane do definiowania zasobu określa sposób, w jaki **uzyskać**, **testu**, i **ustaw** metody zostaną zdefiniowane.

Ponieważ **usługi** zasobu ma tylko jeden klucz wymagany (`Name`), **usługi** bloku zasobów może być tak proste, jak to:

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

Podczas kompilowania konfiguracji powyższych wartości, które określisz dla klucza są przechowywane w pliku "MOF", który jest generowany. Aby uzyskać więcej informacji, zobacz [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

Po zastosowaniu [Local Configuration Manager](../managing-nodes/metaConfig.md) odczytać wartości "Buforu" z pliku "MOF" i przekazać ją do `-Name` parametru **uzyskać**, **testu**, i **ustaw** metod dla wystąpienia "MyService" **usługi** zasobów.

## <a name="get"></a>Pobranie

**Uzyskać** metoda zasobu, pobiera stan zasobu, ponieważ została ona skonfigurowana w docelowym węźle. Ten stan jest zwracana jako [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Klucze **hashtable** będzie można skonfigurować wartości, i parametry akceptuje zasobu.

**Uzyskać** metoda mapuje bezpośrednio do [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) polecenia cmdlet. Podczas wywoływania `Get-DSCConfiguration`, przebiegów LCM **uzyskać** metoda poszczególnych zasobów w konfiguracji obecnie zastosowany. LCM używa wartości kluczy przechowywanych w pliku "MOF" jako parametry do każdego odpowiedniego wystąpienia zasobu.

To przykładowe dane wyjściowe **usługi** zasobu, który konfiguruje usługę "Buforu".

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

Dane wyjściowe zawierają bieżące wartości właściwości można konfigurować przez **usługi** zasobów.

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

## <a name="test"></a>Test

**Testu** metoda zasobu określa, czy węzeł docelowy jest obecnie zgodne z zasobu *żądanego stanu*. **Testu** metoda zwraca `$True` lub `$False` tylko po to, aby wskazać, czy węzeł jest zgodne.
Gdy wywołujesz [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), wywołania LCM **testu** metoda poszczególnych zasobów w konfiguracji obecnie zastosowany. LCM używa wartości kluczy przechowywanych w pliku "MOF" jako parametry do każdego odpowiedniego wystąpienia zasobu.

Jeśli wynik dowolnego pojedynczego zasobu **testu** jest `$False`, `Test-DSCConfiguration` zwraca `$False` wskazujący, że ten węzeł nie jest zgodne. Jeśli wszystkie zasobów **testu** metody zwracają `$True`, `Test-DSCConfiguration` zwraca `$True` do wskazania, że węzeł jest zgodne.

```powershell
Test-DSCConfiguration
```

```output
True
```

Począwszy od programu PowerShell w wersji 5.0 `-Detailed` parametr został dodany. Określanie `-Detailed` powoduje, że `Test-DSCConfiguration` zwracać obiekt zawierający kolekcje wyniki zgodne i niezgodne zasoby.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Aby uzyskać więcej informacji, zobacz [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Ustaw

**Ustaw** metoda zasobu próbuje wymusić węzeł, aby była zgodna z zasobu *żądanego stanu*. **Ustaw** metoda można w dużym **idempotentne**, co oznacza, że **ustaw** można uruchamiać wiele razy i zawsze uzyskać ten sam wynik bez błędów.  Po uruchomieniu [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), cykle LCM za pośrednictwem poszczególnych zasobów w konfiguracji obecnie zastosowany. LCM pobiera wartości kluczy w ramach bieżącego wystąpienia zasobu z pliku "MOF" i są one używane jako parametry dla **testu** metody. Jeśli **testu** metoda zwraca `$True`, węzeł jest zgodne z bieżącego zasobu i **ustaw** metoda zostanie pominięta. Jeśli **testu** zwraca `$False`, węzeł nie jest zgodna.  LCM przekazuje zasób wystąpienia wartości klucza jako parametry do zasobu **ustaw** metodę przywracania węzła zgodności.

Określając `-Verbose` i `-Wait` parametrów, możesz obserwować postęp `Start-DSCConfiguration` polecenia cmdlet. W tym przykładzie ten węzeł jest już zgodne. `Verbose` Dane wyjściowe wskazuje, że **ustaw** metoda została pominięta.

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

## <a name="see-also"></a>Zobacz też

- [Omówienie DSC usługi Azure Automation](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Konfigurowanie serwera ściągania SMB](../pull-server/pullServerSMB.md)
- [Konfigurowanie klienta ściągania](../pull-server/pullClientConfigID.md)
