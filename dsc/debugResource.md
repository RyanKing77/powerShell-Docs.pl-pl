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
# <a name="debugging-dsc-resources"></a><span data-ttu-id="65448-103">Debugowanie zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="65448-103">Debugging DSC resources</span></span>

> <span data-ttu-id="65448-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="65448-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="65448-105">W programie PowerShell 5.0 nowa funkcja została wprowadzona w żądany stan konfiguracji (DSC), która umożliwia debugowanie zasobów DSC, ponieważ konfiguracja jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="65448-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="65448-106">Włączanie debugowania DSC</span><span class="sxs-lookup"><span data-stu-id="65448-106">Enabling DSC debugging</span></span>
<span data-ttu-id="65448-107">Przed debugowaniem zasobu, należy włączyć debugowanie wywołując [DscDebug Włącz](https://technet.microsoft.com/library/mt517870.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65448-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span></span>
<span data-ttu-id="65448-108">To polecenie cmdlet przyjmuje to parametr obowiązkowy, **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="65448-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="65448-109">Możesz sprawdzić, czy sprawdzając wynik wywołania włączono debugowanie [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="65448-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span></span>

<span data-ttu-id="65448-110">Następujące dane wyjściowe programu PowerShell pokazuje wynik włączenie debugowania:</span><span class="sxs-lookup"><span data-stu-id="65448-110">The following PowerShell output shows the result of enabling debugging:</span></span>


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


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="65448-111">Uruchamianie konfiguracji z włączoną debugowania</span><span class="sxs-lookup"><span data-stu-id="65448-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="65448-112">Aby debugować zasobów DSC, możesz uruchomić konfiguracji, który wywołuje tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="65448-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="65448-113">Na przykład przyjrzymy prostą konfigurację, która wywołuje [WindowsFeature](windowsfeatureResource.md) zasobów, aby upewnić się, że zainstalowano funkcję "WindowsPowerShellWebAccess":</span><span class="sxs-lookup"><span data-stu-id="65448-113">For this example, we'll look at a simple configuration that calls the [WindowsFeature](windowsfeatureResource.md) resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

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
<span data-ttu-id="65448-114">Po kompilacji konfiguracji, aby uruchomić przez wywołanie metody [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="65448-114">After compiling the configuration, start it by calling [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span></span>
<span data-ttu-id="65448-115">Konfiguracja zostanie zatrzymana, gdy lokalnego Menedżera konfiguracji (LCM) wywołuje pierwszy zasób w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="65448-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="65448-116">Jeśli używasz `-Verbose` i `-Wait` parametrów, dane wyjściowe wyświetla wiersze, musisz wprowadzić można rozpocząć debugowania.</span><span class="sxs-lookup"><span data-stu-id="65448-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

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
<span data-ttu-id="65448-117">W tym momencie LCM ma nazywane zasobu i się pierwszy punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="65448-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="65448-118">Trzy ostatnie wiersze w danych wyjściowych pokazują, jak dołączyć do procesu i Rozpocznij debugowanie skryptu zasobu.</span><span class="sxs-lookup"><span data-stu-id="65448-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="65448-119">Debugowanie skryptów zasobów</span><span class="sxs-lookup"><span data-stu-id="65448-119">Debugging the resource script</span></span>

<span data-ttu-id="65448-120">Uruchom nowe wystąpienie programu PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="65448-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="65448-121">W okienku konsoli, wprowadź ostatnie trzy wiersze danych wyjściowych z `Start-DscConfiguration` dane wyjściowe jako polecenia, zastępując `<credentials>` ważne poświadczenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="65448-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="65448-122">Powinien zostać wyświetlony monit, która wygląda podobnie do:</span><span class="sxs-lookup"><span data-stu-id="65448-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="65448-123">Skrypt zasobów zostanie otwarty w okienku skryptów i debuger został zatrzymany w pierwszym wierszu **TargetResource testu** — funkcja ( **Test()** metody klasy zasobu).</span><span class="sxs-lookup"><span data-stu-id="65448-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="65448-124">Teraz można używać w ISE polecenia debugowania do wykonania kroków opisanych skrypt zasobu, należy przyjrzeć się wartości zmiennych, wyświetlić stosu wywołań i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="65448-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span>
<span data-ttu-id="65448-125">Informacje dotyczące debugowania w programie PowerShell ISE, zobacz [jak debugowanie skryptów w środowisku Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span><span class="sxs-lookup"><span data-stu-id="65448-125">For information about debugging in the PowerShell ISE, see [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span></span>
<span data-ttu-id="65448-126">Należy pamiętać, że każdy wiersz w skrypt zasobu (lub klasy) jest ustawiony jako punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="65448-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="65448-127">Wyłączanie debugowania DSC</span><span class="sxs-lookup"><span data-stu-id="65448-127">Disabling DSC debugging</span></span>

<span data-ttu-id="65448-128">Po wywołaniu [DscDebug Włącz](https://technet.microsoft.com/library/mt517870.aspx), wszystkie wywołania [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) spowoduje przerwanie w debugerze konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="65448-128">After calling [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), all calls to [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="65448-129">Aby umożliwić konfiguracji, aby działać normalnie, należy wyłączyć debugowanie przez wywołanie metody [DscDebug Wyłącz](https://technet.microsoft.com/en-us/library/mt517872.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65448-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span></span>

><span data-ttu-id="65448-130">**Uwaga:** ponowne uruchomienie nie zmienia stanu debugowania LCM.</span><span class="sxs-lookup"><span data-stu-id="65448-130">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="65448-131">Jeśli włączone jest debugowanie, uruchamianie konfiguracji będą nadal przerwanie w debugerze po ponownym rozruchu.</span><span class="sxs-lookup"><span data-stu-id="65448-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>


## <a name="see-also"></a><span data-ttu-id="65448-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65448-132">See Also</span></span>
- [<span data-ttu-id="65448-133">Pisanie niestandardowych zasobów DSC z MOF</span><span class="sxs-lookup"><span data-stu-id="65448-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="65448-134">Pisanie niestandardowych zasobów DSC z klasami programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="65448-134">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)