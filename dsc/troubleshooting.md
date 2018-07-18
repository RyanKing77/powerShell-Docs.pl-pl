---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Rozwiązywanie problemów z platformą DSC
ms.openlocfilehash: 1e8bfdf3540e65e3be94bf6a9b04e7d3b14ff044
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094072"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="b3912-103">Rozwiązywanie problemów z platformą DSC</span><span class="sxs-lookup"><span data-stu-id="b3912-103">Troubleshooting DSC</span></span>

><span data-ttu-id="b3912-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b3912-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b3912-105">W tym temacie opisano sposoby rozwiązywania DSC w przypadku wystąpienia problemów.</span><span class="sxs-lookup"><span data-stu-id="b3912-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="b3912-106">Zależności usługi WinRM</span><span class="sxs-lookup"><span data-stu-id="b3912-106">WinRM Dependency</span></span>

<span data-ttu-id="b3912-107">Windows PowerShell Desired State Configuration (DSC) jest zależna od usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="b3912-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="b3912-108">Domyślnie w systemie Windows Server 2008 R2 i Windows 7 nie jest włączona usługa WinRM.</span><span class="sxs-lookup"><span data-stu-id="b3912-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="b3912-109">Uruchom ```Set-WSManQuickConfig```, programu Windows PowerShell z podwyższonym poziomem uprawnień sesji, aby włączyć usługę WinRM.</span><span class="sxs-lookup"><span data-stu-id="b3912-109">Run ```Set-WSManQuickConfig```, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="b3912-110">Using Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b3912-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="b3912-111">[Get DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) polecenie cmdlet pobiera informacje o stanie konfiguracji z węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="b3912-111">The [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet gets information about configuration status from a target node.</span></span>
<span data-ttu-id="b3912-112">Rozbudowane obiekt jest zwracany, który zawiera ogólne informacje o czy wykonywania konfiguracji zakończyło się pomyślnie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="b3912-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="b3912-113">Możesz dowiedzieć się do obiektu, aby odnaleźć szczegółowe informacje o konfiguracji uruchamiania, takich jak:</span><span class="sxs-lookup"><span data-stu-id="b3912-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="b3912-114">Wszystkie zasoby, które nie powiodło się</span><span class="sxs-lookup"><span data-stu-id="b3912-114">All of the resources that failed</span></span>
- <span data-ttu-id="b3912-115">Dowolnego zasobu, który zażądał ponownego uruchomienia</span><span class="sxs-lookup"><span data-stu-id="b3912-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="b3912-116">Ustawienia konfiguracji metadanych w czasie konfiguracji uruchamiania</span><span class="sxs-lookup"><span data-stu-id="b3912-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="b3912-117">Etc.</span><span class="sxs-lookup"><span data-stu-id="b3912-117">Etc.</span></span>

<span data-ttu-id="b3912-118">Poniższy zestaw parametrów zwraca informacje o stanie dla ostatniej konfiguracji uruchamiania:</span><span class="sxs-lookup"><span data-stu-id="b3912-118">The following parameter set returns the status information for the last configuration run:</span></span>

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```
<span data-ttu-id="b3912-119">Poniższy zestaw parametrów zwraca informacje o stanie dla wszystkich wcześniejszych przebiegów konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="b3912-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```powershell
Get-DscConfigurationStatus  -All
                            [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="b3912-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3912-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :
InDesiredState          :   False
InitialState            :
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="b3912-121">Nie można uruchomić mojego skryptu: DSC przy użyciu dzienników diagnozować błędy skryptu</span><span class="sxs-lookup"><span data-stu-id="b3912-121">My script won’t run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="b3912-122">Podobnie jak oprogramowanie Windows DSC rejestruje błędy i zdarzenia w [dzienniki](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) mogą być wyświetlane z [Podgląd zdarzeń](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span><span class="sxs-lookup"><span data-stu-id="b3912-122">Like all Windows software, DSC records errors and events in [logs](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) that can be viewed from the [Event Viewer](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span></span> <span data-ttu-id="b3912-123">Badanie te dzienniki mogą ułatwić zrozumienie, dlaczego określonej operacji nie powiodło się i jak zapobiec w przyszłości niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="b3912-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="b3912-124">Pisanie skryptów konfiguracji może być trudne ułatwić śledzenie błędów jako autor możesz, użyj zasób DSC dziennika, aby śledzić postęp konfiguracji w DSC analizy dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b3912-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="b3912-125">Gdzie znajdują się dzienniki zdarzeń DSC?</span><span class="sxs-lookup"><span data-stu-id="b3912-125">Where are DSC event logs?</span></span>

<span data-ttu-id="b3912-126">W Podglądzie zdarzeń, zdarzenia DSC znajdują się w: **aplikacji i usług dzienniki/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="b3912-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="b3912-127">Odpowiednie polecenie cmdlet programu PowerShell, [polecenia Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), można również uruchomić na wyświetlanie dzienników zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="b3912-127">The corresponding PowerShell cmdlet, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="b3912-128">Jak wspomniano powyżej, nazwa dziennika podstawowego firmy DSC jest **Microsoft -> Windows -> DSC** (inne nazwy dziennika, w obszarze Windows nie są wyświetlane w tym miejscu dla zwięzłości).</span><span class="sxs-lookup"><span data-stu-id="b3912-128">As shown above, DSC’s primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="b3912-129">Nazwa podstawowa jest dołączany do nazwy kanału, można utworzyć nazwy pełny dziennik.</span><span class="sxs-lookup"><span data-stu-id="b3912-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="b3912-130">Zapisuje aparatu DSC, przede wszystkim na trzy typy dzienników: [dzienniki operacyjne, analityczne i debugowania](https://technet.microsoft.com/library/cc722404.aspx).</span><span class="sxs-lookup"><span data-stu-id="b3912-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](https://technet.microsoft.com/library/cc722404.aspx).</span></span> <span data-ttu-id="b3912-131">Ponieważ analityczne i debugowania dzienniki są domyślnie wyłączone, należy je włączyć w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b3912-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="b3912-132">Aby to zrobić, otwórz Podgląd zdarzeń, wpisując polecenie Pokaż w dzienniku zdarzeń w programie Windows PowerShell; lub kliknij przycisk **Start** przycisku, kliknij przycisk **Panelu sterowania**, kliknij przycisk **narzędzia administracyjne**, a następnie kliknij przycisk **Podgląd zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="b3912-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span> <span data-ttu-id="b3912-133">Na **widoku** kliknij przycisk menu w Podglądzie zdarzeń **Pokaż analityczne i debugowania dzienniki**.</span><span class="sxs-lookup"><span data-stu-id="b3912-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="b3912-134">Nazwa dziennika dla kanału danych analitycznych jest **Microsoft-Windows-Dsc/analityczne**, i kanał debugowania jest **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="b3912-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="b3912-135">Można także użyć [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) narzędzie, aby włączyć dzienniki, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b3912-135">You could also use the [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="b3912-136">Co zawiera dzienniki DSC?</span><span class="sxs-lookup"><span data-stu-id="b3912-136">What do DSC logs contain?</span></span>

<span data-ttu-id="b3912-137">Dzienniki DSC są dzielone za pośrednictwem trzech kanałów dziennika na podstawie ważności komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b3912-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="b3912-138">Dziennik operacji w DSC zawiera wszystkie komunikaty o błędach i może służyć do identyfikowania problemu.</span><span class="sxs-lookup"><span data-stu-id="b3912-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="b3912-139">Dziennik analityczny ma z większą liczbą zdarzeń i można zidentyfikować, których wystąpiły błędy.</span><span class="sxs-lookup"><span data-stu-id="b3912-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="b3912-140">Ten kanał zawiera także pełne komunikaty wyjściowe (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="b3912-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="b3912-141">Dziennik debugowania zawiera dzienniki, które mogą pomóc Ci zrozumieć, jak wystąpienia błędów.</span><span class="sxs-lookup"><span data-stu-id="b3912-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="b3912-142">Komunikaty o zdarzeniach DSC są skonstruowane w taki sposób, że każdy komunikat zdarzenia zaczyna się od Identyfikatora zadania, który unikatowo reprezentuje operację DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="b3912-143">Poniższy przykład próbuje uzyskać komunikat z pierwszym zdarzeniem, które są rejestrowane w dzienniku operational DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="b3912-144">DSC, zdarzenia są rejestrowane w określonej struktury, który umożliwia użytkownikowi w celu agregowania zdarzeń z jednego zadania DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="b3912-145">Struktura jest następująca:</span><span class="sxs-lookup"><span data-stu-id="b3912-145">The structure is as follows:</span></span>

<span data-ttu-id="b3912-146">**Identyfikator zadania: \<Guid\>**
**\<komunikatów o zdarzeniach\>**</span><span class="sxs-lookup"><span data-stu-id="b3912-146">**Job ID : \<Guid\>**
**\<Event Message\>**</span></span>

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="b3912-147">Zbieranie zdarzeń z jednej operacji DSC</span><span class="sxs-lookup"><span data-stu-id="b3912-147">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="b3912-148">DSC, dzienniki zdarzeń zawierają zdarzenia generowane przez różne operacje DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-148">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="b3912-149">Jednak zazwyczaj będzie zajmującym się ze szczegółowymi informacjami o pojedynczej określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="b3912-149">However, you’ll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="b3912-150">Wszystkie dzienniki DSC można grupować według właściwość ID zadania, który jest unikatowy dla każdej operacji DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-150">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="b3912-151">Identyfikator zadania jest wyświetlany jako pierwszy wartość właściwości wszystkich zdarzeń DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-151">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="b3912-152">Poniższe kroki wyjaśniają, jak do wszystkich zdarzeń w strukturze pogrupowanych tablicy.</span><span class="sxs-lookup"><span data-stu-id="b3912-152">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

<span data-ttu-id="b3912-153">Oto, zmienna `$SeparateDscOperations` zawiera dzienniki pogrupowane według identyfikatorów zadań.</span><span class="sxs-lookup"><span data-stu-id="b3912-153">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="b3912-154">Każdy element tablicy tej zmiennej reprezentuje grupę zdarzenia zarejestrowane przez inną operację DSC, zezwalając na dostęp do informacji na temat dzienników.</span><span class="sxs-lookup"><span data-stu-id="b3912-154">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

<span data-ttu-id="b3912-155">Wyodrębnianie danych w zmiennej `$SeparateDscOperations` przy użyciu [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span><span class="sxs-lookup"><span data-stu-id="b3912-155">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span></span> <span data-ttu-id="b3912-156">Poniżej przedstawiono pięciu scenariuszy, w których możesz chcieć wyodrębniania danych do rozwiązywania problemów DSC:</span><span class="sxs-lookup"><span data-stu-id="b3912-156">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="b3912-157">1: niepowodzenia operacji</span><span class="sxs-lookup"><span data-stu-id="b3912-157">1: Operations failures</span></span>

<span data-ttu-id="b3912-158">Wszystkie zdarzenia mają [poziomy ważności](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b3912-158">All events have [severity levels](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span></span> <span data-ttu-id="b3912-159">Te informacje mogą służyć do identyfikowania zdarzenia błędów:</span><span class="sxs-lookup"><span data-stu-id="b3912-159">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="b3912-160">2: szczegóły operacji uruchamiane w ostatnim pół godziny</span><span class="sxs-lookup"><span data-stu-id="b3912-160">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="b3912-161">`TimeCreated`, właściwości dla każdego zdarzenia Windows stany czasie utworzenia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b3912-161">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="b3912-162">Porównywanie tę właściwość za pomocą obiektu określonej daty/godziny może służyć do filtrowania wszystkie zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="b3912-162">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="b3912-163">3: wiadomości od najnowszych operacji</span><span class="sxs-lookup"><span data-stu-id="b3912-163">3: Messages from the latest operation</span></span>

<span data-ttu-id="b3912-164">Najnowsze działania są przechowywane w pierwszy indeks grupy tablic `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="b3912-164">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span> <span data-ttu-id="b3912-165">Wykonywanie zapytań grupowanie komunikatów dla indeksu 0 zwraca wszystkie komunikaty dotyczące najnowszych operacji:</span><span class="sxs-lookup"><span data-stu-id="b3912-165">Querying the group’s messages for index 0 returns all messages for the latest operation:</span></span>

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="b3912-166">4: komunikaty o błędach zarejestrowane dla ostatnich operacje zakończone niepowodzeniem</span><span class="sxs-lookup"><span data-stu-id="b3912-166">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="b3912-167">`$SeparateDscOperations[0].Group` zawiera zestaw zdarzeń dla najnowszych operacji.</span><span class="sxs-lookup"><span data-stu-id="b3912-167">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="b3912-168">Uruchom `Where-Object` polecenia cmdlet, aby filtrować zdarzenia na podstawie ich poziomie wyświetlane nazwy.</span><span class="sxs-lookup"><span data-stu-id="b3912-168">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="b3912-169">Wyniki są przechowywane w `$myFailedEvent` zmiennej, mogą być jeszcze wyizolowana można pobrać komunikatów o zdarzeniach:</span><span class="sxs-lookup"><span data-stu-id="b3912-169">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="b3912-170">5: wszystkie zdarzenia wygenerowane dla identyfikatora określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="b3912-170">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="b3912-171">`$SeparateDscOperations` jest tablicą, grup, z których każdy ma nazwę jako identyfikator unikatowy zadania.</span><span class="sxs-lookup"><span data-stu-id="b3912-171">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="b3912-172">Uruchamiając `Where-Object` polecenia cmdlet, można wyodrębnić te grupy zdarzenia, które mają identyfikator określonego zadania:</span><span class="sxs-lookup"><span data-stu-id="b3912-172">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="b3912-173">Analizowanie DSC przy użyciu xDscDiagnostics dzienników</span><span class="sxs-lookup"><span data-stu-id="b3912-173">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="b3912-174">**xDscDiagnostics** jest moduł programu PowerShell, który składa się z kilku funkcji, które ułatwiają analizowanie błędów DSC na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="b3912-174">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="b3912-175">Te funkcje mogą pomóc w zidentyfikowaniu wszystkie wydarzenia lokalne z ostatnich operacji DSC lub zdarzenia DSC na komputerach zdalnych (z prawidłowymi poświadczeniami).</span><span class="sxs-lookup"><span data-stu-id="b3912-175">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="b3912-176">W tym miejscu termin DSC operacji jest używana do definiowania unikatowy DSC jednorazowym od jego początku do końca.</span><span class="sxs-lookup"><span data-stu-id="b3912-176">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="b3912-177">Na przykład `Test-DscConfiguration` będzie oddzielnych operacji DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-177">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="b3912-178">Podobnie, co inne polecenie cmdlet w DSC (takie jak `Get-DscConfiguration`, `Start-DscConfiguration`, itp.) może zostać każdy zidentyfikowany jako oddzielne operacje DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-178">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="b3912-179">Funkcje zostały wyjaśnione na [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="b3912-179">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span>
<span data-ttu-id="b3912-180">Pomoc jest dostępna, uruchamiając `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="b3912-180">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="b3912-181">Trwa pobieranie szczegółów operacji DSC</span><span class="sxs-lookup"><span data-stu-id="b3912-181">Getting details of DSC operations</span></span>

<span data-ttu-id="b3912-182">`Get-xDscOperation` Funkcja pozwala wyszukiwać wyników operacji DSC, które są uruchamiane na jednym lub wielu komputerach i zwraca obiekt, który zawiera zbiór zdarzenia generowane przez każdej operacji DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-182">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span>
<span data-ttu-id="b3912-183">Na przykład następujące dane wyjściowe trzy polecenia zostały uruchomione.</span><span class="sxs-lookup"><span data-stu-id="b3912-183">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="b3912-184">Pierwsza z nich przekazywane, a druga dwa nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b3912-184">The first one passed, and the other two failed.</span></span> <span data-ttu-id="b3912-185">Te wyniki są podsumowane w danych wyjściowych `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="b3912-185">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="b3912-186">Można również określić mają tylko wyniki dla ostatnich operacji za pomocą `Newest` parametru:</span><span class="sxs-lookup"><span data-stu-id="b3912-186">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="b3912-187">Trwa pobieranie szczegółów zdarzenia DSC</span><span class="sxs-lookup"><span data-stu-id="b3912-187">Getting details of DSC events</span></span>

<span data-ttu-id="b3912-188">`Trace-xDscOperation` Polecenie cmdlet zwraca obiekt zawierający kolekcję zdarzenia i ich typy zdarzeń i komunikat wyjściowy, generowany na podstawie określonej operacji DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-188">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="b3912-189">Zazwyczaj po awarii jest znaleźć w żadnym z operacji za pomocą `Get-xDscOperation`, czy śledzenie tej operacji, aby dowiedzieć się, które zdarzenia spowodowało błąd.</span><span class="sxs-lookup"><span data-stu-id="b3912-189">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="b3912-190">Użyj `SequenceID` parametru, aby pobrać zdarzenia dla określonej operacji dla określonego komputera.</span><span class="sxs-lookup"><span data-stu-id="b3912-190">Use the  `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span> <span data-ttu-id="b3912-191">Na przykład, jeśli określisz `SequenceID` 9, `Trace-xDscOperaion` uzyskać ślad operacji DSC, która została 9 z ostatniej operacji:</span><span class="sxs-lookup"><span data-stu-id="b3912-191">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="b3912-192">Przekaż **GUID** przypisane do określonej operacji DSC (zwrócone przez `Get-xDscOperation` cmldet) można pobrać szczegółów zdarzenia dla tej operacji DSC:</span><span class="sxs-lookup"><span data-stu-id="b3912-192">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmldet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="b3912-193">Należy zauważyć, że ponieważ `Trace-xDscOperation` agreguje analityczne, debugowania, zdarzenia i dzienniki operacyjne, zostanie wyświetlony monit, aby włączyć te dzienniki, jak opisano powyżej.</span><span class="sxs-lookup"><span data-stu-id="b3912-193">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="b3912-194">Alternatywnie można zbierać informacje o zdarzeniach, zapisując dane wyjściowe `Trace-xDscOperation` do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b3912-194">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="b3912-195">Można użyć następujących poleceń do wyświetlenia wszystkich zdarzeń dla określonej operacji DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-195">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="b3912-196">Spowoduje to wyświetlenie takich samych wyników jak `Get-WinEvent` polecenia cmdlet, takich jak danych wyjściowych poniżej:</span><span class="sxs-lookup"><span data-stu-id="b3912-196">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```powershell
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="b3912-197">W idealnym przypadku należy najpierw użyć `Get-xDscOperation` do listy w ciągu ostatnich kilku DSC konfiguracji jest uruchamiane na maszynach.</span><span class="sxs-lookup"><span data-stu-id="b3912-197">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="b3912-198">W związku z tym, można sprawdzić wszelkie jednej operacji (przy użyciu jego identyfikator SequenceID lub JobID) przy użyciu `Trace-xDscOperation` Aby dowiedzieć się, co zostało w tle.</span><span class="sxs-lookup"><span data-stu-id="b3912-198">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="b3912-199">Pobieranie zdarzeń na komputerze zdalnym</span><span class="sxs-lookup"><span data-stu-id="b3912-199">Getting events for a remote computer</span></span>

<span data-ttu-id="b3912-200">Użyj `ComputerName` parametru `Trace-xDscOperation` polecenia cmdlet, aby uzyskać szczegóły zdarzeń na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="b3912-200">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="b3912-201">Przed można to zrobić, należy utworzyć regułę zapory, aby zezwolić na administrację zdalną na komputerze zdalnym:</span><span class="sxs-lookup"><span data-stu-id="b3912-201">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
<span data-ttu-id="b3912-202">Teraz możesz określić danego komputera w wywołania do `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="b3912-202">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="b3912-203">Moje zasoby nie będą aktualizacji: jak zresetować pamięć podręczną</span><span class="sxs-lookup"><span data-stu-id="b3912-203">My resources won’t update: How to reset the cache</span></span>

<span data-ttu-id="b3912-204">Aparat DSC buforuje zaimplementowane jako moduł programu PowerShell dla celów wydajności zasobów.</span><span class="sxs-lookup"><span data-stu-id="b3912-204">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span> <span data-ttu-id="b3912-205">Jednak może to spowodować problemy podczas tworzenia zasobu i testowanie go jednocześnie, ponieważ DSC zostanie załadowany w pamięci podręcznej wersji, dopóki ten proces zostanie uruchomiony ponownie.</span><span class="sxs-lookup"><span data-stu-id="b3912-205">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="b3912-206">Jedynym sposobem, aby wprowadzić DSC załadowanie w nowszej wersji jest jawnie kill proces aparatu DSC hostingu.</span><span class="sxs-lookup"><span data-stu-id="b3912-206">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="b3912-207">Podobnie, po uruchomieniu `Start-DscConfiguration`, po dodaniu i modyfikowania zasobów niestandardowych, modyfikacja nie może być wykonywane chyba że lub do momentu, komputer jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="b3912-207">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="b3912-208">Jest to spowodowane DSC jest uruchamiany w procesie hosta dostawcy WMI (WmiPrvSE), zwykle wiąże się wiele wystąpień WmiPrvSE uruchomionych jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="b3912-208">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="b3912-209">Po ponownym uruchomieniu, proces hosta zostanie ponownie uruchomiony i pamięć podręczna jest czyszczona.</span><span class="sxs-lookup"><span data-stu-id="b3912-209">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="b3912-210">Aby pomyślnie odzyskać konfiguracji i wyczyścić pamięć podręczną bez ponownego rozruchu, należy zatrzymać i ponownie uruchom proces hosta.</span><span class="sxs-lookup"><span data-stu-id="b3912-210">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="b3912-211">Można to zrobić na na podstawie wystąpień, zgodnie z którą można zidentyfikować proces, zatrzymaj ją i uruchom go ponownie.</span><span class="sxs-lookup"><span data-stu-id="b3912-211">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="b3912-212">Alternatywnie można użyć `DebugMode`, jak pokazano poniżej, aby ponownie załadować zasobów DSC programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3912-212">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="b3912-213">Aby zidentyfikować, który proces uruchomiono aparatu DSC i zatrzymaj ją na na podstawie wystąpień, możesz wyświetlić listę identyfikator procesu WmiPrvSE, który jest hostem aparatu DSC.</span><span class="sxs-lookup"><span data-stu-id="b3912-213">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="b3912-214">Następnie, aby zaktualizować dostawcę, Zatrzymaj WmiPrvSE proces, korzystając z poniższych poleceń, a następnie uruchom **Start-DscConfiguration** ponownie.</span><span class="sxs-lookup"><span data-stu-id="b3912-214">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="b3912-215">Za pomocą element DebugMode</span><span class="sxs-lookup"><span data-stu-id="b3912-215">Using DebugMode</span></span>

<span data-ttu-id="b3912-216">Można skonfigurować DSC lokalnego Configuration Manager (LCM) do użycia `DebugMode` zawsze wyczyszczenie pamięci podręcznej, po ponownym uruchomieniu procesu hosta.</span><span class="sxs-lookup"><span data-stu-id="b3912-216">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="b3912-217">Po ustawieniu **TRUE**, sprawia, że aparat zawsze ponownie załaduj zasób DSC programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3912-217">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="b3912-218">Po zakończeniu pisania zasobu, można ustawić go do **FALSE** i aparat powróci do swojego zachowania buforowania modułów.</span><span class="sxs-lookup"><span data-stu-id="b3912-218">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="b3912-219">Oto przykładowa, aby pokazać sposób `DebugMode` automatycznie można odświeżyć pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="b3912-219">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="b3912-220">Najpierw Przyjrzyjmy się domyślnej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="b3912-220">First, let’s look at the default configuration:</span></span>

```
PS C:\> Get-DscLocalConfigurationManager


AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : False
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="b3912-221">Możesz zobaczyć, że `DebugMode` ustawiono **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="b3912-221">You can see that `DebugMode` is set to **FALSE**.</span></span>

<span data-ttu-id="b3912-222">Aby skonfigurować `DebugMode` demonstracyjne, użyj następujących zasobów programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b3912-222">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

<span data-ttu-id="b3912-223">Teraz Tworzenie konfiguracji przy użyciu powyższych zasobu o nazwie `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="b3912-223">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="b3912-224">Zobaczysz, że zawartość pliku: "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" jest **1**.</span><span class="sxs-lookup"><span data-stu-id="b3912-224">You will see that the contents of file: “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” is **1**.</span></span>

<span data-ttu-id="b3912-225">Teraz zaktualizuj kod dostawcy za pomocą następującego skryptu:</span><span class="sxs-lookup"><span data-stu-id="b3912-225">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="b3912-226">Ten skrypt generuje losową liczbę i odpowiednio aktualizuje kod dostawcy.</span><span class="sxs-lookup"><span data-stu-id="b3912-226">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="b3912-227">Za pomocą `DebugMode` wartość false, zawartość pliku "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" nigdy nie są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="b3912-227">With `DebugMode` set to false, the contents of the file “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” are never changed.</span></span>

<span data-ttu-id="b3912-228">Teraz ustaw `DebugMode` do **TRUE** w skrypcie konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="b3912-228">Now, set `DebugMode` to **TRUE** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = $true
}
```

<span data-ttu-id="b3912-229">Po uruchomieniu powyższy skrypt ponownie pojawi się, że zawartość pliku jest inny każdym razem.</span><span class="sxs-lookup"><span data-stu-id="b3912-229">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="b3912-230">(Możesz uruchomić `Get-DscConfiguration` o zaewidencjonowaniu jej).</span><span class="sxs-lookup"><span data-stu-id="b3912-230">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="b3912-231">Poniżej znajduje się wynik dwóch dodatkowych uruchomień (wyniki mogą różnić się po uruchomieniu skryptu):</span><span class="sxs-lookup"><span data-stu-id="b3912-231">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="see-also"></a><span data-ttu-id="b3912-232">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3912-232">See Also</span></span>

### <a name="reference"></a><span data-ttu-id="b3912-233">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="b3912-233">Reference</span></span>

- [<span data-ttu-id="b3912-234">Zasób DSC dziennika</span><span class="sxs-lookup"><span data-stu-id="b3912-234">DSC Log Resource</span></span>](logResource.md)

### <a name="concepts"></a><span data-ttu-id="b3912-235">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="b3912-235">Concepts</span></span>

- [<span data-ttu-id="b3912-236">Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów</span><span class="sxs-lookup"><span data-stu-id="b3912-236">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="b3912-237">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="b3912-237">Other Resources</span></span>

- <span data-ttu-id="b3912-238">[Program Windows PowerShell Desired State Configuration poleceń cmdlet](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="b3912-238">[Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span></span>