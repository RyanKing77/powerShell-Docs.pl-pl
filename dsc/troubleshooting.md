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
# <a name="troubleshooting-dsc"></a>Rozwiązywanie problemów z platformą DSC

>Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

W tym temacie opisano sposoby rozwiązywania DSC w przypadku wystąpienia problemów.

## <a name="winrm-dependency"></a>Zależności usługi WinRM

Windows PowerShell Desired State Configuration (DSC) jest zależna od usługi WinRM. Domyślnie w systemie Windows Server 2008 R2 i Windows 7 nie jest włączona usługa WinRM. Uruchom ```Set-WSManQuickConfig```, programu Windows PowerShell z podwyższonym poziomem uprawnień sesji, aby włączyć usługę WinRM.

## <a name="using-get-dscconfigurationstatus"></a>Using Get-DscConfigurationStatus

[Get DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) polecenie cmdlet pobiera informacje o stanie konfiguracji z węzła docelowego.
Rozbudowane obiekt jest zwracany, który zawiera ogólne informacje o czy wykonywania konfiguracji zakończyło się pomyślnie, czy nie. Możesz dowiedzieć się do obiektu, aby odnaleźć szczegółowe informacje o konfiguracji uruchamiania, takich jak:

- Wszystkie zasoby, które nie powiodło się
- Dowolnego zasobu, który zażądał ponownego uruchomienia
- Ustawienia konfiguracji metadanych w czasie konfiguracji uruchamiania
- Etc.

Poniższy zestaw parametrów zwraca informacje o stanie dla ostatniej konfiguracji uruchamiania:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```
Poniższy zestaw parametrów zwraca informacje o stanie dla wszystkich wcześniejszych przebiegów konfiguracji:

```powershell
Get-DscConfigurationStatus  -All
                            [-CimSession <CimSession[]>]
                            [-ThrottleLimit <int>]
                            [-AsJob]
                            [<CommonParameters>]
```

## <a name="example"></a>Przykład

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

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Nie można uruchomić mojego skryptu: DSC przy użyciu dzienników diagnozować błędy skryptu

Podobnie jak oprogramowanie Windows DSC rejestruje błędy i zdarzenia w [dzienniki](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) mogą być wyświetlane z [Podgląd zdarzeń](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). Badanie te dzienniki mogą ułatwić zrozumienie, dlaczego określonej operacji nie powiodło się i jak zapobiec w przyszłości niepowodzenie. Pisanie skryptów konfiguracji może być trudne ułatwić śledzenie błędów jako autor możesz, użyj zasób DSC dziennika, aby śledzić postęp konfiguracji w DSC analizy dziennika zdarzeń.

## <a name="where-are-dsc-event-logs"></a>Gdzie znajdują się dzienniki zdarzeń DSC?

W Podglądzie zdarzeń, zdarzenia DSC znajdują się w: **aplikacji i usług dzienniki/Microsoft/Windows/Desired State Configuration**

Odpowiednie polecenie cmdlet programu PowerShell, [polecenia Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), można również uruchomić na wyświetlanie dzienników zdarzeń:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

Jak wspomniano powyżej, nazwa dziennika podstawowego firmy DSC jest **Microsoft -> Windows -> DSC** (inne nazwy dziennika, w obszarze Windows nie są wyświetlane w tym miejscu dla zwięzłości). Nazwa podstawowa jest dołączany do nazwy kanału, można utworzyć nazwy pełny dziennik. Zapisuje aparatu DSC, przede wszystkim na trzy typy dzienników: [dzienniki operacyjne, analityczne i debugowania](https://technet.microsoft.com/library/cc722404.aspx). Ponieważ analityczne i debugowania dzienniki są domyślnie wyłączone, należy je włączyć w Podglądzie zdarzeń. Aby to zrobić, otwórz Podgląd zdarzeń, wpisując polecenie Pokaż w dzienniku zdarzeń w programie Windows PowerShell; lub kliknij przycisk **Start** przycisku, kliknij przycisk **Panelu sterowania**, kliknij przycisk **narzędzia administracyjne**, a następnie kliknij przycisk **Podgląd zdarzeń**. Na **widoku** kliknij przycisk menu w Podglądzie zdarzeń **Pokaż analityczne i debugowania dzienniki**. Nazwa dziennika dla kanału danych analitycznych jest **Microsoft-Windows-Dsc/analityczne**, i kanał debugowania jest **Microsoft-Windows-Dsc/Debug**. Można także użyć [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) narzędzie, aby włączyć dzienniki, jak pokazano w poniższym przykładzie.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>Co zawiera dzienniki DSC?

Dzienniki DSC są dzielone za pośrednictwem trzech kanałów dziennika na podstawie ważności komunikatu. Dziennik operacji w DSC zawiera wszystkie komunikaty o błędach i może służyć do identyfikowania problemu. Dziennik analityczny ma z większą liczbą zdarzeń i można zidentyfikować, których wystąpiły błędy. Ten kanał zawiera także pełne komunikaty wyjściowe (jeśli istnieje). Dziennik debugowania zawiera dzienniki, które mogą pomóc Ci zrozumieć, jak wystąpienia błędów. Komunikaty o zdarzeniach DSC są skonstruowane w taki sposób, że każdy komunikat zdarzenia zaczyna się od Identyfikatora zadania, który unikatowo reprezentuje operację DSC. Poniższy przykład próbuje uzyskać komunikat z pierwszym zdarzeniem, które są rejestrowane w dzienniku operational DSC.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

DSC, zdarzenia są rejestrowane w określonej struktury, który umożliwia użytkownikowi w celu agregowania zdarzeń z jednego zadania DSC. Struktura jest następująca:

**Identyfikator zadania: \<Guid\>**
**\<komunikatów o zdarzeniach\>**

## <a name="gathering-events-from-a-single-dsc-operation"></a>Zbieranie zdarzeń z jednej operacji DSC

DSC, dzienniki zdarzeń zawierają zdarzenia generowane przez różne operacje DSC. Jednak zazwyczaj będzie zajmującym się ze szczegółowymi informacjami o pojedynczej określonej operacji. Wszystkie dzienniki DSC można grupować według właściwość ID zadania, który jest unikatowy dla każdej operacji DSC. Identyfikator zadania jest wyświetlany jako pierwszy wartość właściwości wszystkich zdarzeń DSC. Poniższe kroki wyjaśniają, jak do wszystkich zdarzeń w strukturze pogrupowanych tablicy.

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

Oto, zmienna `$SeparateDscOperations` zawiera dzienniki pogrupowane według identyfikatorów zadań. Każdy element tablicy tej zmiennej reprezentuje grupę zdarzenia zarejestrowane przez inną operację DSC, zezwalając na dostęp do informacji na temat dzienników.

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

Wyodrębnianie danych w zmiennej `$SeparateDscOperations` przy użyciu [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). Poniżej przedstawiono pięciu scenariuszy, w których możesz chcieć wyodrębniania danych do rozwiązywania problemów DSC:

### <a name="1-operations-failures"></a>1: niepowodzenia operacji

Wszystkie zdarzenia mają [poziomy ważności](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Te informacje mogą służyć do identyfikowania zdarzenia błędów:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: szczegóły operacji uruchamiane w ostatnim pół godziny

`TimeCreated`, właściwości dla każdego zdarzenia Windows stany czasie utworzenia zdarzenia. Porównywanie tę właściwość za pomocą obiektu określonej daty/godziny może służyć do filtrowania wszystkie zdarzenia:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3: wiadomości od najnowszych operacji

Najnowsze działania są przechowywane w pierwszy indeks grupy tablic `$SeparateDscOperations`. Wykonywanie zapytań grupowanie komunikatów dla indeksu 0 zwraca wszystkie komunikaty dotyczące najnowszych operacji:

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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: komunikaty o błędach zarejestrowane dla ostatnich operacje zakończone niepowodzeniem

`$SeparateDscOperations[0].Group` zawiera zestaw zdarzeń dla najnowszych operacji. Uruchom `Where-Object` polecenia cmdlet, aby filtrować zdarzenia na podstawie ich poziomie wyświetlane nazwy. Wyniki są przechowywane w `$myFailedEvent` zmiennej, mogą być jeszcze wyizolowana można pobrać komunikatów o zdarzeniach:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: wszystkie zdarzenia wygenerowane dla identyfikatora określonego zadania.

`$SeparateDscOperations` jest tablicą, grup, z których każdy ma nazwę jako identyfikator unikatowy zadania. Uruchamiając `Where-Object` polecenia cmdlet, można wyodrębnić te grupy zdarzenia, które mają identyfikator określonego zadania:

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Analizowanie DSC przy użyciu xDscDiagnostics dzienników

**xDscDiagnostics** jest moduł programu PowerShell, który składa się z kilku funkcji, które ułatwiają analizowanie błędów DSC na swojej maszynie. Te funkcje mogą pomóc w zidentyfikowaniu wszystkie wydarzenia lokalne z ostatnich operacji DSC lub zdarzenia DSC na komputerach zdalnych (z prawidłowymi poświadczeniami). W tym miejscu termin DSC operacji jest używana do definiowania unikatowy DSC jednorazowym od jego początku do końca. Na przykład `Test-DscConfiguration` będzie oddzielnych operacji DSC. Podobnie, co inne polecenie cmdlet w DSC (takie jak `Get-DscConfiguration`, `Start-DscConfiguration`, itp.) może zostać każdy zidentyfikowany jako oddzielne operacje DSC. Funkcje zostały wyjaśnione na [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).
Pomoc jest dostępna, uruchamiając `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>Trwa pobieranie szczegółów operacji DSC

`Get-xDscOperation` Funkcja pozwala wyszukiwać wyników operacji DSC, które są uruchamiane na jednym lub wielu komputerach i zwraca obiekt, który zawiera zbiór zdarzenia generowane przez każdej operacji DSC.
Na przykład następujące dane wyjściowe trzy polecenia zostały uruchomione. Pierwsza z nich przekazywane, a druga dwa nie powiodło się. Te wyniki są podsumowane w danych wyjściowych `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

Można również określić mają tylko wyniki dla ostatnich operacji za pomocą `Newest` parametru:

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

### <a name="getting-details-of-dsc-events"></a>Trwa pobieranie szczegółów zdarzenia DSC

`Trace-xDscOperation` Polecenie cmdlet zwraca obiekt zawierający kolekcję zdarzenia i ich typy zdarzeń i komunikat wyjściowy, generowany na podstawie określonej operacji DSC. Zazwyczaj po awarii jest znaleźć w żadnym z operacji za pomocą `Get-xDscOperation`, czy śledzenie tej operacji, aby dowiedzieć się, które zdarzenia spowodowało błąd.

Użyj `SequenceID` parametru, aby pobrać zdarzenia dla określonej operacji dla określonego komputera. Na przykład, jeśli określisz `SequenceID` 9, `Trace-xDscOperaion` uzyskać ślad operacji DSC, która została 9 z ostatniej operacji:

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

Przekaż **GUID** przypisane do określonej operacji DSC (zwrócone przez `Get-xDscOperation` cmldet) można pobrać szczegółów zdarzenia dla tej operacji DSC:

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

Należy zauważyć, że ponieważ `Trace-xDscOperation` agreguje analityczne, debugowania, zdarzenia i dzienniki operacyjne, zostanie wyświetlony monit, aby włączyć te dzienniki, jak opisano powyżej.

Alternatywnie można zbierać informacje o zdarzeniach, zapisując dane wyjściowe `Trace-xDscOperation` do zmiennej. Można użyć następujących poleceń do wyświetlenia wszystkich zdarzeń dla określonej operacji DSC.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Spowoduje to wyświetlenie takich samych wyników jak `Get-WinEvent` polecenia cmdlet, takich jak danych wyjściowych poniżej:

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

W idealnym przypadku należy najpierw użyć `Get-xDscOperation` do listy w ciągu ostatnich kilku DSC konfiguracji jest uruchamiane na maszynach. W związku z tym, można sprawdzić wszelkie jednej operacji (przy użyciu jego identyfikator SequenceID lub JobID) przy użyciu `Trace-xDscOperation` Aby dowiedzieć się, co zostało w tle.

### <a name="getting-events-for-a-remote-computer"></a>Pobieranie zdarzeń na komputerze zdalnym

Użyj `ComputerName` parametru `Trace-xDscOperation` polecenia cmdlet, aby uzyskać szczegóły zdarzeń na komputerze zdalnym. Przed można to zrobić, należy utworzyć regułę zapory, aby zezwolić na administrację zdalną na komputerze zdalnym:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
Teraz możesz określić danego komputera w wywołania do `Trace-xDscOperation`:

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Moje zasoby nie będą aktualizacji: jak zresetować pamięć podręczną

Aparat DSC buforuje zaimplementowane jako moduł programu PowerShell dla celów wydajności zasobów. Jednak może to spowodować problemy podczas tworzenia zasobu i testowanie go jednocześnie, ponieważ DSC zostanie załadowany w pamięci podręcznej wersji, dopóki ten proces zostanie uruchomiony ponownie. Jedynym sposobem, aby wprowadzić DSC załadowanie w nowszej wersji jest jawnie kill proces aparatu DSC hostingu.

Podobnie, po uruchomieniu `Start-DscConfiguration`, po dodaniu i modyfikowania zasobów niestandardowych, modyfikacja nie może być wykonywane chyba że lub do momentu, komputer jest uruchamiany. Jest to spowodowane DSC jest uruchamiany w procesie hosta dostawcy WMI (WmiPrvSE), zwykle wiąże się wiele wystąpień WmiPrvSE uruchomionych jednocześnie. Po ponownym uruchomieniu, proces hosta zostanie ponownie uruchomiony i pamięć podręczna jest czyszczona.

Aby pomyślnie odzyskać konfiguracji i wyczyścić pamięć podręczną bez ponownego rozruchu, należy zatrzymać i ponownie uruchom proces hosta. Można to zrobić na na podstawie wystąpień, zgodnie z którą można zidentyfikować proces, zatrzymaj ją i uruchom go ponownie. Alternatywnie można użyć `DebugMode`, jak pokazano poniżej, aby ponownie załadować zasobów DSC programu PowerShell.

Aby zidentyfikować, który proces uruchomiono aparatu DSC i zatrzymaj ją na na podstawie wystąpień, możesz wyświetlić listę identyfikator procesu WmiPrvSE, który jest hostem aparatu DSC. Następnie, aby zaktualizować dostawcę, Zatrzymaj WmiPrvSE proces, korzystając z poniższych poleceń, a następnie uruchom **Start-DscConfiguration** ponownie.

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

## <a name="using-debugmode"></a>Za pomocą element DebugMode

Można skonfigurować DSC lokalnego Configuration Manager (LCM) do użycia `DebugMode` zawsze wyczyszczenie pamięci podręcznej, po ponownym uruchomieniu procesu hosta. Po ustawieniu **TRUE**, sprawia, że aparat zawsze ponownie załaduj zasób DSC programu PowerShell. Po zakończeniu pisania zasobu, można ustawić go do **FALSE** i aparat powróci do swojego zachowania buforowania modułów.

Oto przykładowa, aby pokazać sposób `DebugMode` automatycznie można odświeżyć pamięć podręczną. Najpierw Przyjrzyjmy się domyślnej konfiguracji:

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

Możesz zobaczyć, że `DebugMode` ustawiono **FALSE**.

Aby skonfigurować `DebugMode` demonstracyjne, użyj następujących zasobów programu PowerShell:

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

Teraz Tworzenie konfiguracji przy użyciu powyższych zasobu o nazwie `TestProviderDebugMode`:

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

Zobaczysz, że zawartość pliku: "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" jest **1**.

Teraz zaktualizuj kod dostawcy za pomocą następującego skryptu:

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

Ten skrypt generuje losową liczbę i odpowiednio aktualizuje kod dostawcy. Za pomocą `DebugMode` wartość false, zawartość pliku "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" nigdy nie są zmieniane.

Teraz ustaw `DebugMode` do **TRUE** w skrypcie konfiguracji:

```powershell
LocalConfigurationManager
{
    DebugMode = $true
}
```

Po uruchomieniu powyższy skrypt ponownie pojawi się, że zawartość pliku jest inny każdym razem. (Możesz uruchomić `Get-DscConfiguration` o zaewidencjonowaniu jej). Poniżej znajduje się wynik dwóch dodatkowych uruchomień (wyniki mogą różnić się po uruchomieniu skryptu):

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

## <a name="see-also"></a>Zobacz też

### <a name="reference"></a>Dokumentacja

- [Zasób DSC dziennika](logResource.md)

### <a name="concepts"></a>Pojęcia

- [Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów](authoringResource.md)

### <a name="other-resources"></a>Inne zasoby

- [Program Windows PowerShell Desired State Configuration poleceń cmdlet](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)