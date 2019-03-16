---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Debugowanie zasobów DSC
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055584"
---
# <a name="debugging-dsc-resources"></a>Debugowanie zasobów DSC

> Dotyczy: Windows PowerShell 5.0

W programie PowerShell 5.0 nowa funkcja została wprowadzona w Desired State Configuration (DSC) umożliwiający debugowanie zasobów DSC, ponieważ konfiguracja jest stosowana.

## <a name="enabling-dsc-debugging"></a>Włączanie debugowania DSC
Przed można debugować zasobu, musisz włączyć debugowanie przez wywołanie metody [DscDebug Włącz](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) polecenia cmdlet.
To polecenie cmdlet przyjmuje to parametr obowiązkowy **BreakAll**.

Możesz sprawdzić, czy debugowanie zostało włączone, analizując wynik wywołania do [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

Następujące dane wyjściowe programu PowerShell pokazuje wynik włączenie debugowania:


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a>Począwszy od debugowania włączone konfiguracji
Debugowanie zasobów DSC, możesz uruchomić konfiguracji, który wywołuje tego zasobu.
W tym przykładzie przyjrzymy prostej konfiguracji, który wywołuje **WindowsFeature** zasobów, aby upewnić się, czy zainstalowana jest funkcja "WindowsPowerShellWebAccess":

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
Po kompilacji konfiguracji, uruchom ją, wywołując [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).
Konfiguracja zostanie zatrzymana, gdy lokalne Configuration Manager (LCM) wywoła pierwszy zasób w konfiguracji.
Jeśli używasz `-Verbose` i `-Wait` parametrów, wyświetla dane wyjściowe wierszy, należy wprowadzić, aby rozpocząć debugowanie.

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
W tym momencie LCM o nazwie zasobu, zakończyła się pierwszy punkt przerwania.
Trzy ostatnie wiersze w dane wyjściowe pokazują, jak dołączyć do procesu, a następnie rozpocząć debugowanie skryptu zasobu.

## <a name="debugging-the-resource-script"></a>Debugowanie skryptu zasobu

Uruchom nowe wystąpienie programu PowerShell ISE.
W okienku konsoli, wprowadź ostatnie trzy wiersze danych wyjściowych z `Start-DscConfiguration` dane wyjściowe jako polecenia, zastępując `<credentials>` ważne poświadczenia użytkownika.
Powinien zostać wyświetlony monit, która wygląda podobnie do:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Skrypt zasobów zostanie otwarty w okienku skryptów i Debuger jest zatrzymywany w pierwszym wierszu **TargetResource testu** — funkcja ( **Test()** metody oparte na klasach zasobów).
Teraz możesz używać poleceń debugowania w środowisku ISE, aby przejść przez skrypt zasobu, Przyjrzyj się wartości zmiennych, przejrzyj stos wywołań i tak dalej. Należy pamiętać, że każdy wiersz w skrypt zasobu (lub klasy) jest ustawiony jako punkt przerwania.

## <a name="disabling-dsc-debugging"></a>Wyłączenie debugowania DSC

Po wywołaniu [DscDebug Włącz](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), wszystkie wywołania do [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) spowoduje konfiguracji przerwanie w debugerze. Aby zezwolić na konfiguracje normalne działanie, należy wyłączyć debugowanie przez wywołanie metody [DscDebug Wyłącz](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) polecenia cmdlet.

>**Uwaga:** Ponowne uruchamianie nie zmienia stanu LCM debugowania. Jeśli włączone jest debugowanie, uruchamianie konfiguracji będzie nadal wkroczenia do debugera po ponownym uruchomieniu.

## <a name="see-also"></a>Zobacz też

- [Pisanie zasobu DSC niestandardowych z pliku MOF](../resources/authoringResourceMOF.md)
- [Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell](../resources/authoringResourceClass.md)
