---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Za pomocą serwera raportów konfiguracji DSC"
ms.openlocfilehash: 31b0df7d9baf30d93154d6a28b21f32fc052bc06
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="8048b-103">Za pomocą serwera raportów konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="8048b-103">Using a DSC report server</span></span>

> <span data-ttu-id="8048b-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8048b-104">Applies To: Windows PowerShell 5.0</span></span>

><span data-ttu-id="8048b-105">**Uwaga:** serwera raportów w tym temacie opisano nie jest dostępna w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="8048b-105">**Note:** The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="8048b-106">Aby wysyłać raporty o jego stan konfiguracji na serwerze ściągania, które następnie można tworzyć zapytania można pobrać danych można skonfigurować lokalnego Menedżera konfiguracji (LCM) węzła.</span><span class="sxs-lookup"><span data-stu-id="8048b-106">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="8048b-107">Każdym węźle sprawdza i ma zastosowanie konfiguracji, wysyła raportu na serwerze raportów.</span><span class="sxs-lookup"><span data-stu-id="8048b-107">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="8048b-108">Te raporty są przechowywane w bazie danych na serwerze i mogą zostać pobrane przez wywoływania usługi sieci web raportowania.</span><span class="sxs-lookup"><span data-stu-id="8048b-108">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="8048b-109">Każdy raport zawiera informacje, takie jak konfiguracje, jakie zostały zastosowane i czy one zakończyło się pomyślnie, zasoby używane wszystkie błędy, które zostały zgłoszone i rozpoczęcia i zakończenia godzin.</span><span class="sxs-lookup"><span data-stu-id="8048b-109">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="8048b-110">Konfigurowanie węzłów na wysyłanie raportów</span><span class="sxs-lookup"><span data-stu-id="8048b-110">Configuring a node to send reports</span></span>

<span data-ttu-id="8048b-111">Poinformuj węzeł, aby wysyłać raporty do serwera przy użyciu **ReportServerWeb** zablokować w węźle LCM konfiguracji (informacji o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md) ).</span><span class="sxs-lookup"><span data-stu-id="8048b-111">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md)).</span></span> <span data-ttu-id="8048b-112">Serwer, z którym węzeł wysyła raporty musi skonfigurować jako serwera sieci web ściągania (do udziału SMB nie można wysyłać raporty).</span><span class="sxs-lookup"><span data-stu-id="8048b-112">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="8048b-113">Aby uzyskać informacje dotyczące konfigurowania serwera ściągania, zobacz [ustawienie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="8048b-113">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="8048b-114">Serwer raportów mogą być tej samej usługi, z którego węzeł ściąga konfiguracje i pobiera zasobów lub może być innej usługi.</span><span class="sxs-lookup"><span data-stu-id="8048b-114">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>
 
<span data-ttu-id="8048b-115">W **ReportServerWeb** bloku, określ adres URL usługi ściągania i klucz rejestracyjny, który jest znany do serwera.</span><span class="sxs-lookup"><span data-stu-id="8048b-115">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>
 
<span data-ttu-id="8048b-116">Następująca konfiguracja konfiguruje węzła do ściągania konfiguracje z jedną usługę i wysyłać raporty do usług na innym serwerze.</span><span class="sxs-lookup"><span data-stu-id="8048b-116">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span> 
 
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

<span data-ttu-id="8048b-117">Następująca konfiguracja konfiguruje węzła na jednym serwerze do konfiguracji, zasobów i raportów.</span><span class="sxs-lookup"><span data-stu-id="8048b-117">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

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

><span data-ttu-id="8048b-118">**Uwaga:** można określić nazwę usługi sieci web dowolne podczas konfigurowania serwera ściągania, ale **ServerURL** właściwości musi być zgodna z nazwą usługi.</span><span class="sxs-lookup"><span data-stu-id="8048b-118">**Note:** You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="8048b-119">Pobieranie danych raportu</span><span class="sxs-lookup"><span data-stu-id="8048b-119">Getting report data</span></span>

<span data-ttu-id="8048b-120">Raporty wysyłane do serwera ściągania są wprowadzane do bazy danych na serwerze.</span><span class="sxs-lookup"><span data-stu-id="8048b-120">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="8048b-121">Raporty są dostępne za pośrednictwem połączenia z usługą sieci web.</span><span class="sxs-lookup"><span data-stu-id="8048b-121">The reports are available through calls to the web service.</span></span> <span data-ttu-id="8048b-122">Aby pobrać raporty dla określonego węzła, Wyślij żądanie HTTP z usługą sieci web raport w następującej postaci: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId= 'MyNodeAgentId')/Reports` gdzie `MyNodeAgentId` jest identyfikator agenta węzła, dla którego chcesz uzyskać raporty.</span><span class="sxs-lookup"><span data-stu-id="8048b-122">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId= 'MyNodeAgentId')/Reports` where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="8048b-123">Możesz uzyskać identyfikator agenta węzła wywołując [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) w tym węźle.</span><span class="sxs-lookup"><span data-stu-id="8048b-123">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) on that node.</span></span>

<span data-ttu-id="8048b-124">Raporty są zwracane jako tablica obiektów JSON.</span><span class="sxs-lookup"><span data-stu-id="8048b-124">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="8048b-125">Poniższy skrypt zwraca raporty dla węzła, na którym jest uruchomiona:</span><span class="sxs-lookup"><span data-stu-id="8048b-125">The following script returns the reports for the node on which it is run:</span></span>

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
    
## <a name="viewing-report-data"></a><span data-ttu-id="8048b-126">Wyświetlanie danych raportu</span><span class="sxs-lookup"><span data-stu-id="8048b-126">Viewing report data</span></span>

<span data-ttu-id="8048b-127">Jeśli ustawisz zmiennej do wyniku **GetReport** funkcji, można wyświetlić poszczególnych pól w elemencie tablicy, która jest zwracana:</span><span class="sxs-lookup"><span data-stu-id="8048b-127">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

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

<span data-ttu-id="8048b-128">Domyślnie raporty są sortowane według **JobID**.</span><span class="sxs-lookup"><span data-stu-id="8048b-128">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="8048b-129">Aby pobrać najnowszy raport, raporty można sortować według malejącej **StartTime** właściwości, a następnie get pierwszy element tablicy:</span><span class="sxs-lookup"><span data-stu-id="8048b-129">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="8048b-130">Zwróć uwagę, że **StatusData** właściwość jest obiekt o wiele właściwości.</span><span class="sxs-lookup"><span data-stu-id="8048b-130">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="8048b-131">Jest to, gdzie jest znacznie danych raportowania.</span><span class="sxs-lookup"><span data-stu-id="8048b-131">This is where much of the reporting data is.</span></span> <span data-ttu-id="8048b-132">Oto poszczególnych pól **StatusData** właściwość najnowszy raport:</span><span class="sxs-lookup"><span data-stu-id="8048b-132">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

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

<span data-ttu-id="8048b-133">Między innymi oznacza to najnowszej konfiguracji o nazwie dwa zasoby i że jeden z nich został w żądanym stanie i jeden z nich nie jest.</span><span class="sxs-lookup"><span data-stu-id="8048b-133">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="8048b-134">Możesz uzyskać bardziej czytelny wynik tylko **ResourcesNotInDesiredState** właściwości:</span><span class="sxs-lookup"><span data-stu-id="8048b-134">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

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

<span data-ttu-id="8048b-135">Należy pamiętać, że te przykłady są przeznaczone do zapewniają informacje o tym, co można zrobić z danymi raportu.</span><span class="sxs-lookup"><span data-stu-id="8048b-135">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="8048b-136">Aby obejrzeć wprowadzenie na temat pracy z JSON w programie PowerShell, zobacz [odtwarzanie z formatami JSON i programu PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="8048b-136">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="8048b-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8048b-137">See Also</span></span>
- [<span data-ttu-id="8048b-138">Konfigurowanie lokalny program Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="8048b-138">Configuring the Local Configuration Manager</span></span>](metaConfig.md)
- [<span data-ttu-id="8048b-139">Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web</span><span class="sxs-lookup"><span data-stu-id="8048b-139">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="8048b-140">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8048b-140">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)

