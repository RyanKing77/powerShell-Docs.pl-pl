---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Używanie serwera raportów platformy DSC
ms.openlocfilehash: 143e0bdd9b637cee87a676ed327fe6ff3a7fd719
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="using-a-dsc-report-server"></a>Używanie serwera raportów platformy DSC

> Dotyczy: Środowiska Windows PowerShell 5.0

> [!IMPORTANT]
> Ściągnięcia serwera (funkcja Windows *DSC usługi*) jest obsługiwanych składników systemu Windows Server jednak nie ma żadnych planów oferować nowe funkcje lub możliwości. Zaleca się rozpocząć przechodzenie zarządzanych klientów do [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started) (w tym funkcji poza ściągnięcia serwera w systemie Windows Server) lub jednego z rozwiązań społeczności wymienionych [tutaj](pullserver.md#community-solutions-for-pull-service).

>**Uwaga:** serwera raportów w tym temacie opisano nie jest dostępna w programie PowerShell 4.0.

Aby wysyłać raporty o jego stan konfiguracji na serwerze ściągania, które następnie można tworzyć zapytania można pobrać danych można skonfigurować lokalnego Menedżera konfiguracji (LCM) węzła. Każdym węźle sprawdza i ma zastosowanie konfiguracji, wysyła raportu na serwerze raportów. Te raporty są przechowywane w bazie danych na serwerze i mogą zostać pobrane przez wywoływania usługi sieci web raportowania. Każdy raport zawiera informacje, takie jak konfiguracje, jakie zostały zastosowane i czy one zakończyło się pomyślnie, zasoby używane wszystkie błędy, które zostały zgłoszone i rozpoczęcia i zakończenia godzin.

## <a name="configuring-a-node-to-send-reports"></a>Konfigurowanie węzłów na wysyłanie raportów

Poinformuj węzeł, aby wysyłać raporty do serwera przy użyciu **ReportServerWeb** zablokować w węźle LCM konfiguracji (informacji o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md) ). Serwer, z którym węzeł wysyła raporty musi skonfigurować jako serwera sieci web ściągania (do udziału SMB nie można wysyłać raporty). Aby uzyskać informacje dotyczące konfigurowania serwera ściągania, zobacz [ustawienie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md). Serwer raportów mogą być tej samej usługi, z którego węzeł ściąga konfiguracje i pobiera zasobów lub może być innej usługi.

W **ReportServerWeb** bloku, określ adres URL usługi ściągania i klucz rejestracyjny, który jest znany do serwera.

Następująca konfiguracja konfiguruje węzła do ściągania konfiguracje z jedną usługę i wysyłać raporty do usług na innym serwerze.

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
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}
ReportClientConfig
```

Następująca konfiguracja konfiguruje węzła na jednym serwerze do konfiguracji, zasobów i raportów.

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

>**Uwaga:** można określić nazwę usługi sieci web dowolne podczas konfigurowania serwera ściągania, ale **ServerURL** właściwości musi być zgodna z nazwą usługi.

## <a name="getting-report-data"></a>Pobieranie danych raportu

Raporty wysyłane do serwera ściągania są wprowadzane do bazy danych na serwerze. Raporty są dostępne za pośrednictwem połączenia z usługą sieci web. Aby pobrać raporty dla określonego węzła, Wyślij żądanie HTTP z usługą sieci web raport w następującej postaci: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId= 'MyNodeAgentId')/Reports` gdzie `MyNodeAgentId` jest identyfikator agenta węzła, dla którego chcesz uzyskać raporty. Możesz uzyskać identyfikator agenta węzła wywołując [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx) w tym węźle.

Raporty są zwracane jako tablica obiektów JSON.

Poniższy skrypt zwraca raporty dla węzła, na którym jest uruchomiona:

```powershell
function GetReport
{
    param($AgentId = "$((glcm).AgentId)", $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc")
    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a>Wyświetlanie danych raportu

Jeśli ustawisz zmiennej do wyniku **GetReport** funkcji, można wyświetlić poszczególnych pól w elemencie tablicy, która jest zwracana:

```powershell
$reports = GetReport
$reports[1]


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

Domyślnie raporty są sortowane według **JobID**. Aby pobrać najnowszy raport, raporty można sortować według malejącej **StartTime** właściwości, a następnie get pierwszy element tablicy:

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

Zwróć uwagę, że **StatusData** właściwość jest obiekt o wiele właściwości. Jest to, gdzie jest znacznie danych raportowania. Oto poszczególnych pól **StatusData** właściwość najnowszy raport:

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData

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

Między innymi oznacza to najnowszej konfiguracji o nazwie dwa zasoby i że jeden z nich został w żądanym stanie i jeden z nich nie jest. Możesz uzyskać bardziej czytelny wynik tylko **ResourcesNotInDesiredState** właściwości:

```powershell
$statusData.ResourcesInDesiredState

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

Należy pamiętać, że te przykłady są przeznaczone do zapewniają informacje o tym, co można zrobić z danymi raportu. Aby obejrzeć wprowadzenie na temat pracy z JSON w programie PowerShell, zobacz [odtwarzanie z formatami JSON i programu PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie lokalny program Configuration Manager](metaConfig.md)
- [Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md)
- [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](pullClientConfigNames.md)