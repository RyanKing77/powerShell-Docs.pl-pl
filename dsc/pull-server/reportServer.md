---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Używanie serwera raportów platformy DSC
ms.openlocfilehash: 1ccd4f96b782b41b7d7c953735cb41b3ba3d2bce
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986562"
---
# <a name="using-a-dsc-report-server"></a>Używanie serwera raportów platformy DSC

Dotyczy: Środowisko Windows PowerShell 5,0

> [!IMPORTANT]
> Serwer ściągania (Windows Feature *DSC-Service*) jest obsługiwanym składnikiem systemu Windows Server, ale nie ma żadnych planów do oferowania nowych funkcji. Zalecane jest, aby rozpocząć przechodzenie zarządzanych klientów do [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (obejmuje funkcje wykraczające poza serwer ściągający w systemie Windows Server) lub jedno z rozwiązań społecznościowych wymienionych w [tym miejscu](pullserver.md#community-solutions-for-pull-service).
>
> [!NOTE]
> Serwer raportów opisany w tym temacie nie jest dostępny w programie PowerShell 4,0.

Lokalny Configuration Manager (LCM) węzła można skonfigurować tak, aby raporty o jego stanie konfiguracji były wysyłane do serwera ściągania, który następnie będzie mógł uzyskać zapytanie w celu pobrania tych danych. Za każdym razem, gdy węzeł sprawdza i stosuje konfigurację, wysyła raport do serwera raportów. Te raporty są przechowywane w bazie danych na serwerze i mogą być pobierane przez wywołanie usługi sieci Web raportowania. Każdy raport zawiera informacje, takie jak konfiguracje, które zostały zastosowane i czy zakończyły się powodzeniem, używane zasoby, wszystkie zgłoszone błędy oraz czasy rozpoczęcia i zakończenia.

## <a name="configuring-a-node-to-send-reports"></a>Konfigurowanie węzła do wysyłania raportów

Poinformujesz węzeł, aby wysyłał raporty do serwera przy użyciu bloku **ReportServerWeb** w konfiguracji LCM węzła (Aby uzyskać informacje o konfigurowaniu LCM), zobacz [Konfigurowanie Configuration Manager lokalnego](../managing-nodes/metaConfig.md)). Serwer, do którego węzeł wysyła raporty, musi być skonfigurowany jako serwer ściągania w sieci Web (nie można wysyłać raportów do udziału SMB). Aby uzyskać informacje na temat konfigurowania serwera ściągania, zobacz [Konfigurowanie serwera ściągania sieci Web](pullServer.md). Serwer raportów może być tą samą usługą, z której węzeł ściąga konfiguracje i pobiera zasoby, lub może być inną usługą.

W bloku **ReportServerWeb** Określ adres URL usługi ściągania i klucz rejestracji znany serwerowi.

Poniższa konfiguracja konfiguruje węzeł do ściągania konfiguracji z jednej usługi i wysyła raporty do usługi na innym serwerze.

```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCPullServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

Poniższa konfiguracja konfiguruje węzeł do korzystania z jednego serwera na potrzeby konfiguracji, zasobów i raportowania.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }



        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

> [!NOTE]
> Usługę sieci Web można nazwać w dowolny sposób podczas konfigurowania serwera ściągania, ale właściwość **ServerURL** musi być zgodna z nazwą usługi.

## <a name="getting-report-data"></a>Pobieranie danych raportu

Raporty wysyłane do serwera ściągania są wprowadzane do bazy danych na serwerze. Raporty są dostępne za pomocą wywołań usługi sieci Web. Aby pobrać raporty dla określonego węzła, Wyślij żądanie HTTP do usługi sieci Web raportów w następującej postaci:`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`
gdzie `MyNodeAgentId` to identyfikator agenta węzła, dla którego chcesz uzyskać raporty. Możesz uzyskać identyfikator agenta dla węzła, wywołując metodę [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) w tym węźle.

Raporty są zwracane jako tablica obiektów JSON.

Poniższy skrypt zwraca raporty dla węzła, na którym jest uruchamiany:

```powershell
function GetReport
{
    param
    (
        $AgentId = "$((glcm).AgentId)", 
        $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc"
    )

    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a>Wyświetlanie danych raportu

W przypadku ustawienia zmiennej do wyniku funkcji GetReport można wyświetlić poszczególne pola w elemencie tablicy, która jest zwracana:

```powershell
$reports = GetReport
$reports[1]
```

```output
JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name:
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

Domyślnie raporty są sortowane według identyfikatora **zadania**. Aby uzyskać najnowszy raport, można posortować raporty według właściwości **StartTime** , a następnie uzyskać pierwszy element tablicy:

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

Zauważ, że właściwość **StatusData** jest obiektem z liczbą właściwości. Jest to miejsce, w którym jest dużo danych raportowania. Przyjrzyjmy się poszczególnym polom właściwości **StatusData** dla najnowszego raportu:

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData
```

```output
StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost:
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking;
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall;
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration;
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive;
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[];
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle;
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0;
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull;
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

W ten sposób pokazuje, że najnowsza konfiguracja o nazwie dwa zasoby i że jedna z nich była w żądanym stanie, a jeden z nich nie był. Można uzyskać bardziej czytelny wynik tylko dla właściwości **ResourcesNotInDesiredState** :

```powershell
$statusData.ResourcesInDesiredState
```

```output
SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

Należy zauważyć, że te przykłady mają na celu zakoncepcję tego, co można zrobić z danymi raportu. Aby zapoznać się z wprowadzeniem do pracy z kodem JSON w programie PowerShell, zobacz [odtwarzanie za pomocą kodu JSON i programu PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).

## <a name="see-also"></a>Zobacz też

[Konfigurowanie Configuration Manager lokalnego](../managing-nodes/metaConfig.md)

[Konfigurowanie serwera ściągania sieci Web DSC](pullServer.md)

[Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](pullClientConfigNames.md)
