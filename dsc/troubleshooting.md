---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Rozwiązywanie problemów z usługi Konfiguracja DSC"
ms.openlocfilehash: 9b1266b9c8923474005760ef78b05d570efdde37
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="troubleshooting-dsc"></a>Rozwiązywanie problemów z usługi Konfiguracja DSC

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

W tym temacie opisano sposoby rozwiązywania DSC w przypadku wystąpienia problemów.

## <a name="winrm-dependency"></a>Zależności usługi WinRM

Windows PowerShell Desired stan konfiguracji (DSC) zależy od usługi WinRM. Usługa WinRM nie jest włączona domyślnie w systemie Windows Server 2008 R2 i Windows 7. Uruchom ```Set-WSManQuickConfig```, w programie Windows PowerShell z podwyższonym poziomem uprawnień sesji, aby włączyć usługę WinRM.

## <a name="using-get-dscconfigurationstatus"></a>Przy użyciu Get DscConfigurationStatus

[Get DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx) polecenie cmdlet pobiera informacje o stanie konfiguracji z węzła docelowego. Sformatowanego obiekt jest zwracany, który zawiera ogólne informacje dotyczące czy Uruchom Konfiguracja zakończyła się powodzeniem. Może odnajdywać się do obiektu, aby odnaleźć szczegółowe informacje o konfiguracji, takie jak uruchamianie:

* Wszystkie zasoby, których nie powiodła się
* Każdy zasób, którego zażądano ponownego rozruchu
* Ustawienia konfiguracji meta w momencie uruchomienia konfiguracji
* itp.

Następujący zestaw parametrów zwraca informacje o stanie dla ostatniej konfiguracji uruchamiania:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```
Następujący zestaw parametrów zwraca informacje o stanie dla wszystkich wcześniejszych przebiegów konfiguracji:

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

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>Nie można uruchomić skryptu moje: diagnozowanie błędów skryptów logowania przy użyciu usługi Konfiguracja DSC

Podobnie jak wszystkie oprogramowanie systemu Windows, DSC rejestruje błędy i zdarzenia w [dzienniki](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) mogą być wyświetlane z [Podgląd zdarzeń](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). Badanie te dzienniki mogą ułatwić zrozumienie, dlaczego określonej operacji nie powiodło się i jak zapobiec błędu w przyszłości. Pisanie skryptów konfiguracji może być trudne, tak ułatwić śledzenie błędów jako autor możesz, użyj zasobu dziennika DSC aby śledzić postęp konfiguracji DSC analityczne dziennik zdarzeń.

## <a name="where-are-dsc-event-logs"></a>Gdzie są dzienniki zdarzeń usługi Konfiguracja DSC?

W Podglądzie zdarzeń, DSC zdarzeń znajdują się w: **aplikacji i usług dzienników/Microsoft/Windows/żądany stan konfiguracji**

Odpowiednie polecenie cmdlet programu PowerShell [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), można również uruchomić na wyświetlanie dzienników zdarzeń:

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

Jak pokazano powyżej, nazwa dziennika podstawowego DSC jest **Microsoft -> okna -> Konfiguracja DSC** (inne nazwy dziennika w systemie Windows nie są wyświetlane tutaj w celu jego skrócenia). Nazwa podstawowa jest dołączany do nazwę kanału, aby utworzyć pełny dziennik nazwy. Aparat DSC zapisuje przede wszystkim na trzy typy dzienników: [dzienniki działa, analityczne i debugowania](https://technet.microsoft.com/library/cc722404.aspx). Ponieważ analityczne i debugowania dzienniki są domyślnie wyłączone, należy je włączyć w Podglądzie zdarzeń. Aby to zrobić, otwórz Podgląd zdarzeń, wpisując EventLog Pokaż w programie Windows PowerShell; lub kliknij przycisk **Start** , kliknij **Panelu sterowania**, kliknij przycisk **narzędzia administracyjne**, a następnie kliknij przycisk **Podgląd zdarzeń**. Na **widoku** menu w Podglądzie zdarzeń, kliknij przycisk **dzienniki Pokaż analityczne i debugowania**. Nazwa dziennika dla kanału danych analitycznych jest **Microsoft-Windows-Dsc/analityczne**, i kanał debugowania jest **Microsoft-Windows-Dsc/Debug**. Można także użyć [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) narzędzie, aby włączyć dzienniki, jak pokazano w poniższym przykładzie.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>Co zawierają dzienniki DSC?

Dzienniki usługi Konfiguracja DSC są podzielone na trzy kanały dzienników oparciu ważności wiadomości. Dziennik operacji w DSC zawiera wszystkie komunikaty o błędach i może służyć do identyfikowania problem. Dziennik analityczny ma większą ilość zdarzeń i może zidentyfikować, których wystąpiły błędy. Ten kanał zawiera także komunikaty pełne (jeśli istnieje). Dziennik debugowania zawiera dzienniki, które mogą ułatwić zrozumienie sposobu wystąpienia błędów. Komunikaty o zdarzeniach usługi Konfiguracja DSC są struktury w taki sposób, że każdy komunikat zdarzenia zaczyna się od Identyfikatora zadania, który unikatowo reprezentuje operację DSC. W poniższym przykładzie próbuje uzyskać komunikatu z pierwszego zdarzenia rejestrowane w dzienniku operational DSC.

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

DSC zdarzenia są rejestrowane w szczególności struktury, który umożliwia użytkownikowi w celu agregowania zdarzeń z jednego zadania konfiguracji DSC. Struktura jest następujący:

**Identyfikator zadania:<Guid>**
**<Event Message>**

## <a name="gathering-events-from-a-single-dsc-operation"></a>Zbieranie zdarzeń z jednej operacji DSC

Dzienniki zdarzeń usługi Konfiguracja DSC zawierają zdarzenia generowane przez różne operacje usługi Konfiguracja DSC. Jednak zazwyczaj będziesz zajmującym się ze szczegółowymi informacjami o pojedynczej określonej operacji. Wszystkie dzienniki DSC można przedstawić w rozbiciu właściwość Identyfikatora zadania, która jest unikatowa dla każdej operacji usługi Konfiguracja DSC. Identyfikator zadania jest wyświetlana jako pierwsza wartość właściwości wszystkich zdarzeń usługi Konfiguracja DSC. Poniższe kroki opisano gromadzone wszystkie zdarzenia w strukturze grupowanych tablicy.

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

Tutaj, zmienna `$SeparateDscOperations` zawiera dzienniki pogrupowane według identyfikatorów zadań. Każdy element tablicy tej zmiennej reprezentuje grupę zdarzenia zarejestrowane przez inną operację DSC zezwalania na dostęp do dodatkowych informacji o dziennikach.

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

Wyodrębnianie danych w zmiennej `$SeparateDscOperations` przy użyciu [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). Poniżej przedstawiono pięć scenariuszy, w których można wyodrębnić danych do rozwiązywania problemów DSC:

### <a name="1-operations-failures"></a>1: niepowodzenia operacji

Wszystkie zdarzenia mają [poziomy ważności](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Te informacje można zidentyfikować zdarzenia błędów:

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2: szczegóły operacji uruchomione w ostatnich pół godziny

`TimeCreated`, czas utworzenia zdarzenia stany właściwości każdego zdarzenia systemu Windows. Porównanie tej właściwości z obiektem określonej daty i godziny może służyć do filtrowania wszystkich zdarzeń:

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### <a name="3-messages-from-the-latest-operation"></a>3: komunikaty z najnowszą operacji

Najnowsze operacji są przechowywane w indeks pierwszego grupy tablicy `$SeparateDscOperations`. Kwerendy komunikatów grupy dla indeksu 0 zwraca wszystkie komunikaty o najnowsze operacji:

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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4: komunikaty o błędach zarejestrowane dla ostatnich operacji nie powiodło się

`$SeparateDscOperations[0].Group`zawiera zestaw zdarzeń najnowsze operacji. Uruchom `Where-Object` polecenia cmdlet, aby filtrować zdarzenia na podstawie ich poziomu wyświetlanej nazwy. Wyniki są przechowywane w `$myFailedEvent` zmiennej, którego można dodatkowo rozcięta można uzyskać komunikaty o zdarzeniach:

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5: wszystkie zdarzenia wygenerowane identyfikatora określonego zadania.

`$SeparateDscOperations`jest tablicą grup, z których każdy ma nazwę jako identyfikator unikatowy zadania. Uruchamiając `Where-Object` polecenia cmdlet, można wyodrębnić te grupy zdarzeń o identyfikatorze określonego zadania:

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>Loguje się przy użyciu xDscDiagnostics do analizowania DSC

**xDscDiagnostics** jest moduł programu PowerShell, który składa się z kilku funkcji, które ułatwiają analizowanie błędów DSC na tym komputerze. Te funkcje mogą pomóc w zidentyfikowaniu wszystkie lokalne z poprzednich operacji DSC, lub zdarzenia DSC na komputerach zdalnych (z prawidłowymi poświadczeniami). W tym miejscu termin operacji DSC umożliwia definiowanie unikatowy DSC jednorazowym od jej początku do końca. Na przykład `Test-DscConfiguration` byłoby oddzielne operacji usługi Konfiguracja DSC. Podobnie, co inne polecenie cmdlet w konfiguracji DSC (takich jak `Get-DscConfiguration`, `Start-DscConfiguration`, itd.) może być identyfikowanych jako osobne operacje usługi Konfiguracja DSC. Funkcje zostały wyjaśnione w [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics). Pomoc jest dostępna, uruchamiając `Get-Help <cmdlet name>`.

### <a name="getting-details-of-dsc-operations"></a>Pobieranie szczegółów operacji DSC 

`Get-xDscOperation` Funkcji można znaleźć wyniki operacji DSC, na jednym lub wielu komputerach z systemem i zwraca obiekt, który zawiera kolekcję zdarzenia generowane przez każdej operacji DSC. Na przykład w następujących danych wyjściowych polecenia trzy zostały uruchomione. Pierwszy przekazany, a druga dwa nie powiodło się. Te wyniki są podsumowane w danych wyjściowych `Get-xDscOperation`.

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents            
------------   ---------- -----------           ------   -----                                 ---------            
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...

```

Można również określić mają tylko wyniki ostatniej operacji za pomocą `Newest` parametru:

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

### <a name="getting-details-of-dsc-events"></a>Pobieranie szczegółów zdarzenia DSC

`Trace-xDscOperation` Polecenie cmdlet zwraca obiekt zawierający zbierania zdarzeń, ich typów zdarzeń i komunikat wyjściowe, generowane na podstawie określonej operacji usługi Konfiguracja DSC. Zazwyczaj gdy możesz znaleźć awarii w każdej operacji za pomocą `Get-xDscOperation`, czy śledzenie tej operacji, aby dowiedzieć się, które zdarzenia spowodowała awarię.

Użyj `SequenceID` parametr, aby pobrać zdarzenia dla określonej operacji dla określonego komputera. Na przykład jeśli określisz `SequenceID` 9, `Trace-xDscOperaion` uzyskać śledzenia dla operacji DSC, który był 9 z ostatniej operacji:

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

Przekaż **GUID** przypisane do określonej operacji usługi Konfiguracja DSC (zwrócony przez `Get-xDscOperation` cmldet) można pobrać szczegółów zdarzenia dla tej operacji DSC:

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

Należy pamiętać, że, ponieważ `Trace-xDscOperation` agreguje z analityczne, debugowania i działa w dziennikach, zostanie wyświetlony monit, aby włączyć te dzienniki, zgodnie z powyższym opisem.

Alternatywnie można zbierać informacje o zdarzenia przez zapisanie danych wyjściowych `Trace-xDscOperation` do zmiennej. Następujące polecenia służy do wyświetlenia wszystkich zdarzeń dla określonej operacji usługi Konfiguracja DSC.

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

Spowoduje to wyświetlenie takie same wyniki jak `Get-WinEvent` polecenia cmdlet, taki jak danych wyjściowych poniżej:

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

Najlepszym rozwiązaniem, należy najpierw użyć `Get-xDscOperation` do listy limit ostatniego DSC kilka konfiguracji działa na maszynach. W związku z tym, można sprawdzić wszelkie jednej operacji (przy użyciu jego identyfikator sekwencji: lub JobID) z `Trace-xDscOperation` Aby dowiedzieć się, co zostało w tle.

### <a name="getting-events-for-a-remote-computer"></a>Pobieranie zdarzeń na komputerze zdalnym

Użyj `ComputerName` parametr `Trace-xDscOperation` polecenia cmdlet, aby uzyskać szczegóły zdarzeń na komputerze zdalnym. Zanim można to zrobić, należy utworzyć regułę zapory, aby zezwolić na administrację zdalną na komputerze zdalnym:

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```
Teraz możesz określić danego komputera wywołania do `Trace-xDscOperation`:

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>Nie Aktualizuj moje zasoby: sposób resetowania pamięci podręcznej

Aparat DSC buforuje zaimplementowane jako moduł programu PowerShell dla celów wydajności zasobów. Jednak może to spowodować problemy podczas tworzenia zasobu i testowanie go równocześnie, ponieważ DSC załaduje wersja buforowana do momentu ponownego uruchomienia procesu. Jedynym sposobem, aby załadować nowsza wersja usługi Konfiguracja DSC jest jawnie kasowanie procesu hostingu aparat DSC.

Podobnie, po uruchomieniu `Start-DscConfiguration`, po dodaniu i modyfikowania zasobów niestandardowych, modyfikacja nie może wykonać chyba że lub do momentu, komputer jest uruchamiany. To dlatego DSC jest uruchamiany w ramach procesu hosta dostawcy usługi WMI (WmiPrvSE) i zwykle, istnieje wiele wystąpień WmiPrvSE uruchomionych jednocześnie. Po ponownym uruchomieniu, proces hosta zostanie ponownie uruchomiony i pamięci podręcznej jest wyczyszczone.

Pomyślnie Odtwórz konfiguracji i wyczyść pamięć podręczną bez ponownego uruchamiania komputera, należy zatrzymać i ponownie uruchomić proces hosta. Można to zrobić na podstawie na wystąpienie, zgodnie z którymi możesz zidentyfikować proces, zatrzymaj ją i uruchom go ponownie. Możesz też użyć `DebugMode`, jak pokazano poniżej, aby ponownie załadować zasobów DSC środowiska PowerShell.

Aby zidentyfikować procesu, który jest hostem aparat DSC i zatrzymaj ją dla poszczególnych wystąpień, można wyświetlić listę identyfikator procesu WmiPrvSE, który jest hostem aparat DSC. Następnie, aby uaktualnić dostawcę, Zatrzymaj WmiPrvSE proces, korzystając z poniższych poleceń, a następnie uruchom **Start DscConfiguration** ponownie.

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

## <a name="using-debugmode"></a>Przy użyciu DebugMode

Można skonfigurować DSC lokalnego Configuration Manager (LCM) do użycia `DebugMode` zawsze Wyczyść pamięć podręczną po ponownym uruchomieniu procesu hosta. Jeśli wartość **TRUE**, ta powoduje, że aparat zawsze ponownie załaduj zasób DSC środowiska PowerShell. Po zakończeniu zapisu zasobu, można ją ustawić do **FALSE** i aparat powróci do jego zachowanie buforowania modułów.

Poniżej znajduje się przykładowa pokazanie sposobu `DebugMode` automatycznie można odświeżyć pamięci podręcznej. Po pierwsze Przyjrzyjmy się domyślnej konfiguracji:

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

Można stwierdzić, że `DebugMode` ustawiono **FALSE**.

Aby skonfigurować `DebugMode` demonstracyjnych, użyj następujących zasobów programu PowerShell:

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

Teraz, Tworzenie konfiguracji przy użyciu powyższego zasobu o nazwie `TestProviderDebugMode`:

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

Teraz zaktualizuj kod dostawcy przy użyciu następującego skryptu:

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

Ten skrypt generuje losową liczbę i odpowiednio aktualizowany kod dostawcy. Z `DebugMode` wartość false, zawartość pliku "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" nigdy nie są zmieniane.

Teraz, `DebugMode` do **TRUE** skryptu konfiguracji:

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

Gdy powyższy skrypt można uruchomić ponownie, zobaczysz, że zawartość pliku różni się zawsze. (Możesz uruchomić `Get-DscConfiguration` wyewidencjonuj go). Poniżej znajduje się wynik dwa przebiegi dodatkowe (wyniki mogą być w innej, po uruchomieniu skryptu):

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
* [Zasób dziennika DSC](logResource.md)

### <a name="concepts"></a>Pojęcia
* [Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów](authoringResource.md)

### <a name="other-resources"></a>Inne zasoby
* [Polecenia cmdlet stanu konfiguracji żądanego programu Windows PowerShell](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)

