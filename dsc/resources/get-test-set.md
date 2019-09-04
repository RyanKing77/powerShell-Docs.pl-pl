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
# <a name="get-test-set"></a>Get-test-Set

>Dotyczy: Windows PowerShell 4,0, Windows PowerShell 5,0

![Pobieranie, testowanie i ustawianie](../media/get-test-set.png)

Konfiguracja żądanego stanu programu PowerShell jest zbudowana wokół procesu **Get**, **test**i **Set** . [Zasoby](resources.md) DSC zawierają metody umożliwiające wykonanie każdej z tych operacji. W [konfiguracji](../configurations/configurations.md)definiuje się bloki zasobów, aby wypełnić klucze, które stają się parametrami dla metod **Get**, **test**i **Set** zasobu.

Jest to składnia bloku zasobów **usługi** . Zasób **usługi służy** do konfigurowania usług systemu Windows.

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

Metody **Get**, **test**i **Set** zasobu **usługi** będą mieć bloki parametrów, które akceptują te wartości.

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
> Język i Metoda używane do definiowania zasobów określają sposób definiowania metod **Get**, **test**i **Set** .

Ponieważ zasób **usługi** ma tylko jeden wymagany klucz (`Name`), zasób bloku **usługi** może być prosty w następujący sposób:

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

Po skompilowaniu powyższej konfiguracji wartości podane dla klucza są przechowywane w generowanym pliku "MOF". Aby uzyskać więcej informacji, zobacz [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

W przypadku zastosowania [Configuration Manager lokalny](../managing-nodes/metaConfig.md) (LCM) odczyta wartość "bufor" z pliku ". MOF `-Name` " i przekaże go do parametru metod **Get**, **test**i **Set** dla wystąpienia **"Moja usługa" Zasób usługi** .

## <a name="get"></a>Pobranie

Metoda **Get** zasobu Pobiera stan zasobu w miarę jego konfiguracji w węźle docelowym. Ten stan jest zwracany jako obiekt [Hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Klucze obiektu **Hashtable** będą konfigurowalne wartości lub parametry, które zaakceptuje zasób.

Metoda **Get** mapuje się bezpośrednio do polecenia cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) . Po wywołaniu `Get-DSCConfiguration`, LCM uruchamia metodę **Get** każdego zasobu w aktualnie stosowanej konfiguracji. LCM używa wartości klucza przechowywanych w pliku ". MOF" jako parametrów do każdego odpowiadającego wystąpienia zasobu.

Jest to przykładowe dane wyjściowe z zasobu **usługi** , który konfiguruje usługę "bufor".

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

Dane wyjściowe przedstawiają bieżące właściwości wartości konfigurowalne przez zasób **usługi** .

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

Metoda **testowa** zasobu określa, czy węzeł docelowy jest aktualnie zgodny z *żądanym stanem*zasobu. Metoda **testowa** zwraca `$True` lub `$False` tylko wskazuje, czy węzeł jest zgodny.
Po wywołaniu [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), LCM wywołuje metodę **testową** każdego zasobu w aktualnie stosowanej konfiguracji. LCM używa wartości klucza przechowywanych w pliku ". MOF" jako parametrów do każdego odpowiadającego wystąpienia zasobu.

Jeśli wynik **testu** pojedynczego zasobu to `$False`, `Test-DSCConfiguration` zwraca `$False` informację o tym, że węzeł nie jest zgodny. Jeśli wszystkie metody **testowe** zasobu zwracają `$True`, zwraca `Test-DSCConfiguration` `$True` , aby wskazać, że węzeł jest zgodny.

```powershell
Test-DSCConfiguration
```

```output
True
```

Począwszy od programu PowerShell 5,0, `-Detailed` parametr został dodany. Określenie `-Detailed` przyczyn`Test-DSCConfiguration` zwrócenia obiektu zawierającego kolekcje wyników dla zgodnych i niezgodnych zasobów.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Aby uzyskać więcej informacji, zobacz [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Ustaw

Metoda **Set** zasobu próbuje wymusić zgodność węzła z *żądanym stanem*zasobu. Metoda **Set** ma być **idempotentne**, co oznacza, że **zestaw** może być uruchamiany wiele razy i zawsze uzyskać ten sam wynik bez błędów.  Po uruchomieniu [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), LCM przeprowadzi cykl przez każdy zasób w aktualnie stosowanej konfiguracji. LCM pobiera wartości klucza dla bieżącego wystąpienia zasobu z pliku ". MOF" i używa ich jako parametrów dla metody **testowej** . Jeśli metoda **testowa** zwraca `$True`, węzeł jest zgodny z bieżącym zasobem, a Metoda **Set** jest pomijana. Jeśli **test** zwraca `$False`, węzeł nie jest zgodny.  LCM przekazuje wartości klucza wystąpienia zasobu jako parametry do metody **Set** zasobu, przywracając węzeł do zgodności.

Określając `-Verbose` parametry i `-Wait` , można `Start-DSCConfiguration` obserwować postęp polecenia cmdlet. W tym przykładzie węzeł jest już zgodny. Dane wyjściowe wskazują, że Metoda Set została pominięta. `Verbose`

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

- [Azure Automation DSC — Omówienie](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Konfigurowanie serwera ściągania SMB](../pull-server/pullServerSMB.md)
- [Konfigurowanie klienta ściągania](../pull-server/pullClientConfigID.md)
