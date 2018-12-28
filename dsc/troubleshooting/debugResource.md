---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Debugowanie zasobów DSC
ms.openlocfilehash: 9b2e7dd9b42332b869c4d7fabb21bd4b5a6b8800
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404916"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="ab19e-103">Debugowanie zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="ab19e-103">Debugging DSC resources</span></span>

> <span data-ttu-id="ab19e-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ab19e-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ab19e-105">W programie PowerShell 5.0 nowa funkcja została wprowadzona w żądany stan elementy (DSC) umożliwiający debugowanie zasobów DSC, ponieważ konfiguracja jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="ab19e-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="ab19e-106">Włączanie debugowania DSC</span><span class="sxs-lookup"><span data-stu-id="ab19e-106">Enabling DSC debugging</span></span>
<span data-ttu-id="ab19e-107">Przed można debugować zasobu, musisz włączyć debugowanie przez wywołanie metody [DscDebug Włącz](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab19e-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span>
<span data-ttu-id="ab19e-108">To polecenie cmdlet przyjmuje to parametr obowiązkowy **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="ab19e-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="ab19e-109">Możesz sprawdzić, czy debugowanie zostało włączone, analizując wynik wywołania do [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="ab19e-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="ab19e-110">Następujące dane wyjściowe programu PowerShell pokazuje wynik włączenie debugowania:</span><span class="sxs-lookup"><span data-stu-id="ab19e-110">The following PowerShell output shows the result of enabling debugging:</span></span>


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


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="ab19e-111">Począwszy od debugowania włączone konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ab19e-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="ab19e-112">Debugowanie zasobów DSC, możesz uruchomić konfiguracji, który wywołuje tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="ab19e-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="ab19e-113">W tym przykładzie przyjrzymy prostej konfiguracji, który wywołuje **WindowsFeature** zasobów, aby upewnić się, czy zainstalowana jest funkcja "WindowsPowerShellWebAccess":</span><span class="sxs-lookup"><span data-stu-id="ab19e-113">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

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
<span data-ttu-id="ab19e-114">Po kompilacji konfiguracji, uruchom ją, wywołując [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="ab19e-114">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span>
<span data-ttu-id="ab19e-115">Konfiguracja zostanie zatrzymana, gdy lokalne Configuration Manager (LCM) wywoła pierwszy zasób w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ab19e-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="ab19e-116">Jeśli używasz `-Verbose` i `-Wait` parametrów, wyświetla dane wyjściowe wierszy, należy wprowadzić, aby rozpocząć debugowanie.</span><span class="sxs-lookup"><span data-stu-id="ab19e-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

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
<span data-ttu-id="ab19e-117">W tym momencie LCM o nazwie zasobu, zakończyła się pierwszy punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="ab19e-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="ab19e-118">Trzy ostatnie wiersze w dane wyjściowe pokazują, jak dołączyć do procesu, a następnie rozpocząć debugowanie skryptu zasobu.</span><span class="sxs-lookup"><span data-stu-id="ab19e-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="ab19e-119">Debugowanie skryptu zasobu</span><span class="sxs-lookup"><span data-stu-id="ab19e-119">Debugging the resource script</span></span>

<span data-ttu-id="ab19e-120">Uruchom nowe wystąpienie programu PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ab19e-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="ab19e-121">W okienku konsoli, wprowadź ostatnie trzy wiersze danych wyjściowych z `Start-DscConfiguration` dane wyjściowe jako polecenia, zastępując `<credentials>` ważne poświadczenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ab19e-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="ab19e-122">Powinien zostać wyświetlony monit, która wygląda podobnie do:</span><span class="sxs-lookup"><span data-stu-id="ab19e-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="ab19e-123">Skrypt zasobów zostanie otwarty w okienku skryptów i Debuger jest zatrzymywany w pierwszym wierszu **TargetResource testu** — funkcja ( **Test()** metody oparte na klasach zasobów).</span><span class="sxs-lookup"><span data-stu-id="ab19e-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="ab19e-124">Teraz możesz używać poleceń debugowania w środowisku ISE, aby przejść przez skrypt zasobu, Przyjrzyj się wartości zmiennych, przejrzyj stos wywołań i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ab19e-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="ab19e-125">Należy pamiętać, że każdy wiersz w skrypt zasobu (lub klasy) jest ustawiony jako punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="ab19e-125">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="ab19e-126">Wyłączenie debugowania DSC</span><span class="sxs-lookup"><span data-stu-id="ab19e-126">Disabling DSC debugging</span></span>

<span data-ttu-id="ab19e-127">Po wywołaniu [DscDebug Włącz](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), wszystkie wywołania do [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) spowoduje konfiguracji przerwanie w debugerze.</span><span class="sxs-lookup"><span data-stu-id="ab19e-127">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="ab19e-128">Aby zezwolić na konfiguracje normalne działanie, należy wyłączyć debugowanie przez wywołanie metody [DscDebug Wyłącz](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab19e-128">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

><span data-ttu-id="ab19e-129">**Uwaga:** Ponowne uruchamianie nie zmienia stanu LCM debugowania.</span><span class="sxs-lookup"><span data-stu-id="ab19e-129">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="ab19e-130">Jeśli włączone jest debugowanie, uruchamianie konfiguracji będzie nadal wkroczenia do debugera po ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="ab19e-130">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab19e-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab19e-131">See Also</span></span>

- [<span data-ttu-id="ab19e-132">Pisanie zasobu DSC niestandardowych z pliku MOF</span><span class="sxs-lookup"><span data-stu-id="ab19e-132">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="ab19e-133">Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab19e-133">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
