---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Debugowanie zasobów DSC
ms.openlocfilehash: 30d49768fc2301b5306d0001e157d60e2e991883
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="debugging-dsc-resources"></a>Debugowanie zasobów DSC

> Dotyczy: Środowiska Windows PowerShell 5.0

W programie PowerShell 5.0 nowa funkcja została wprowadzona w żądany stan konfiguracji (DSC), która umożliwia debugowanie zasobów DSC, ponieważ konfiguracja jest stosowany.

## <a name="enabling-dsc-debugging"></a>Włączanie debugowania DSC
Przed debugowaniem zasobu, należy włączyć debugowanie wywołując [DscDebug Włącz](https://technet.microsoft.com/library/mt517870.aspx) polecenia cmdlet.
To polecenie cmdlet przyjmuje to parametr obowiązkowy, **BreakAll**.

Możesz sprawdzić, czy sprawdzając wynik wywołania włączono debugowanie [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).

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


## <a name="starting-a-configuration-with-debug-enabled"></a>Uruchamianie konfiguracji z włączoną debugowania
Aby debugować zasobów DSC, możesz uruchomić konfiguracji, który wywołuje tego zasobu.
Na przykład przyjrzymy prostą konfigurację, która wywołuje [WindowsFeature](windowsfeatureResource.md) zasobów, aby upewnić się, że zainstalowano funkcję "WindowsPowerShellWebAccess":

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
Po kompilacji konfiguracji, aby uruchomić przez wywołanie metody [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).
Konfiguracja zostanie zatrzymana, gdy lokalnego Menedżera konfiguracji (LCM) wywołuje pierwszy zasób w konfiguracji.
Jeśli używasz `-Verbose` i `-Wait` parametrów, dane wyjściowe wyświetla wiersze, musisz wprowadzić można rozpocząć debugowania.

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
W tym momencie LCM ma nazywane zasobu i się pierwszy punkt przerwania.
Trzy ostatnie wiersze w danych wyjściowych pokazują, jak dołączyć do procesu i Rozpocznij debugowanie skryptu zasobu.

## <a name="debugging-the-resource-script"></a>Debugowanie skryptów zasobów

Uruchom nowe wystąpienie programu PowerShell ISE.
W okienku konsoli, wprowadź ostatnie trzy wiersze danych wyjściowych z `Start-DscConfiguration` dane wyjściowe jako polecenia, zastępując `<credentials>` ważne poświadczenia użytkownika.
Powinien zostać wyświetlony monit, która wygląda podobnie do:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Skrypt zasobów zostanie otwarty w okienku skryptów i debuger został zatrzymany w pierwszym wierszu **TargetResource testu** — funkcja ( **Test()** metody klasy zasobu).
Teraz można używać w ISE polecenia debugowania do wykonania kroków opisanych skrypt zasobu, należy przyjrzeć się wartości zmiennych, wyświetlić stosu wywołań i tak dalej.
Informacje dotyczące debugowania w programie PowerShell ISE, zobacz [jak debugowanie skryptów w środowisku Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).
Należy pamiętać, że każdy wiersz w skrypt zasobu (lub klasy) jest ustawiony jako punkt przerwania.

## <a name="disabling-dsc-debugging"></a>Wyłączanie debugowania DSC

Po wywołaniu [DscDebug Włącz](https://technet.microsoft.com/library/mt517870.aspx), wszystkie wywołania [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) spowoduje przerwanie w debugerze konfiguracji. Aby umożliwić konfiguracji, aby działać normalnie, należy wyłączyć debugowanie przez wywołanie metody [DscDebug Wyłącz](https://technet.microsoft.com/en-us/library/mt517872.aspx) polecenia cmdlet.

>**Uwaga:** ponowne uruchomienie nie zmienia stanu debugowania LCM. Jeśli włączone jest debugowanie, uruchamianie konfiguracji będą nadal przerwanie w debugerze po ponownym rozruchu.


## <a name="see-also"></a>Zobacz też
- [Pisanie niestandardowych zasobów DSC z MOF](authoringResourceMOF.md)
- [Pisanie niestandardowych zasobów DSC z klasami programu PowerShell](authoringResourceClass.md)