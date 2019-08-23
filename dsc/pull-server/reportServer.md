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
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="2268f-103">Używanie serwera raportów platformy DSC</span><span class="sxs-lookup"><span data-stu-id="2268f-103">Using a DSC report server</span></span>

<span data-ttu-id="2268f-104">Dotyczy: Środowisko Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="2268f-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2268f-105">Serwer ściągania (Windows Feature *DSC-Service*) jest obsługiwanym składnikiem systemu Windows Server, ale nie ma żadnych planów do oferowania nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="2268f-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="2268f-106">Zalecane jest, aby rozpocząć przechodzenie zarządzanych klientów do [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (obejmuje funkcje wykraczające poza serwer ściągający w systemie Windows Server) lub jedno z rozwiązań społecznościowych wymienionych w [tym miejscu](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="2268f-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> [!NOTE]
> <span data-ttu-id="2268f-107">Serwer raportów opisany w tym temacie nie jest dostępny w programie PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="2268f-107">The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="2268f-108">Lokalny Configuration Manager (LCM) węzła można skonfigurować tak, aby raporty o jego stanie konfiguracji były wysyłane do serwera ściągania, który następnie będzie mógł uzyskać zapytanie w celu pobrania tych danych.</span><span class="sxs-lookup"><span data-stu-id="2268f-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="2268f-109">Za każdym razem, gdy węzeł sprawdza i stosuje konfigurację, wysyła raport do serwera raportów.</span><span class="sxs-lookup"><span data-stu-id="2268f-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="2268f-110">Te raporty są przechowywane w bazie danych na serwerze i mogą być pobierane przez wywołanie usługi sieci Web raportowania.</span><span class="sxs-lookup"><span data-stu-id="2268f-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="2268f-111">Każdy raport zawiera informacje, takie jak konfiguracje, które zostały zastosowane i czy zakończyły się powodzeniem, używane zasoby, wszystkie zgłoszone błędy oraz czasy rozpoczęcia i zakończenia.</span><span class="sxs-lookup"><span data-stu-id="2268f-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="2268f-112">Konfigurowanie węzła do wysyłania raportów</span><span class="sxs-lookup"><span data-stu-id="2268f-112">Configuring a node to send reports</span></span>

<span data-ttu-id="2268f-113">Poinformujesz węzeł, aby wysyłał raporty do serwera przy użyciu bloku **ReportServerWeb** w konfiguracji LCM węzła (Aby uzyskać informacje o konfigurowaniu LCM), zobacz [Konfigurowanie Configuration Manager lokalnego](../managing-nodes/metaConfig.md)).</span><span class="sxs-lookup"><span data-stu-id="2268f-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)).</span></span> <span data-ttu-id="2268f-114">Serwer, do którego węzeł wysyła raporty, musi być skonfigurowany jako serwer ściągania w sieci Web (nie można wysyłać raportów do udziału SMB).</span><span class="sxs-lookup"><span data-stu-id="2268f-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="2268f-115">Aby uzyskać informacje na temat konfigurowania serwera ściągania, zobacz [Konfigurowanie serwera ściągania sieci Web](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="2268f-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="2268f-116">Serwer raportów może być tą samą usługą, z której węzeł ściąga konfiguracje i pobiera zasoby, lub może być inną usługą.</span><span class="sxs-lookup"><span data-stu-id="2268f-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="2268f-117">W bloku **ReportServerWeb** Określ adres URL usługi ściągania i klucz rejestracji znany serwerowi.</span><span class="sxs-lookup"><span data-stu-id="2268f-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="2268f-118">Poniższa konfiguracja konfiguruje węzeł do ściągania konfiguracji z jednej usługi i wysyła raporty do usługi na innym serwerze.</span><span class="sxs-lookup"><span data-stu-id="2268f-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

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

<span data-ttu-id="2268f-119">Poniższa konfiguracja konfiguruje węzeł do korzystania z jednego serwera na potrzeby konfiguracji, zasobów i raportowania.</span><span class="sxs-lookup"><span data-stu-id="2268f-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

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
> <span data-ttu-id="2268f-120">Usługę sieci Web można nazwać w dowolny sposób podczas konfigurowania serwera ściągania, ale właściwość **ServerURL** musi być zgodna z nazwą usługi.</span><span class="sxs-lookup"><span data-stu-id="2268f-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="2268f-121">Pobieranie danych raportu</span><span class="sxs-lookup"><span data-stu-id="2268f-121">Getting report data</span></span>

<span data-ttu-id="2268f-122">Raporty wysyłane do serwera ściągania są wprowadzane do bazy danych na serwerze.</span><span class="sxs-lookup"><span data-stu-id="2268f-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="2268f-123">Raporty są dostępne za pomocą wywołań usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2268f-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="2268f-124">Aby pobrać raporty dla określonego węzła, Wyślij żądanie HTTP do usługi sieci Web raportów w następującej postaci:`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span><span class="sxs-lookup"><span data-stu-id="2268f-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span></span>
<span data-ttu-id="2268f-125">gdzie `MyNodeAgentId` to identyfikator agenta węzła, dla którego chcesz uzyskać raporty.</span><span class="sxs-lookup"><span data-stu-id="2268f-125">where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="2268f-126">Możesz uzyskać identyfikator agenta dla węzła, wywołując metodę [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) w tym węźle.</span><span class="sxs-lookup"><span data-stu-id="2268f-126">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="2268f-127">Raporty są zwracane jako tablica obiektów JSON.</span><span class="sxs-lookup"><span data-stu-id="2268f-127">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="2268f-128">Poniższy skrypt zwraca raporty dla węzła, na którym jest uruchamiany:</span><span class="sxs-lookup"><span data-stu-id="2268f-128">The following script returns the reports for the node on which it is run:</span></span>

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

## <a name="viewing-report-data"></a><span data-ttu-id="2268f-129">Wyświetlanie danych raportu</span><span class="sxs-lookup"><span data-stu-id="2268f-129">Viewing report data</span></span>

<span data-ttu-id="2268f-130">W przypadku ustawienia zmiennej do wyniku funkcji GetReport można wyświetlić poszczególne pola w elemencie tablicy, która jest zwracana:</span><span class="sxs-lookup"><span data-stu-id="2268f-130">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

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

<span data-ttu-id="2268f-131">Domyślnie raporty są sortowane według identyfikatora **zadania**.</span><span class="sxs-lookup"><span data-stu-id="2268f-131">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="2268f-132">Aby uzyskać najnowszy raport, można posortować raporty według właściwości **StartTime** , a następnie uzyskać pierwszy element tablicy:</span><span class="sxs-lookup"><span data-stu-id="2268f-132">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="2268f-133">Zauważ, że właściwość **StatusData** jest obiektem z liczbą właściwości.</span><span class="sxs-lookup"><span data-stu-id="2268f-133">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="2268f-134">Jest to miejsce, w którym jest dużo danych raportowania.</span><span class="sxs-lookup"><span data-stu-id="2268f-134">This is where much of the reporting data is.</span></span> <span data-ttu-id="2268f-135">Przyjrzyjmy się poszczególnym polom właściwości **StatusData** dla najnowszego raportu:</span><span class="sxs-lookup"><span data-stu-id="2268f-135">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

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

<span data-ttu-id="2268f-136">W ten sposób pokazuje, że najnowsza konfiguracja o nazwie dwa zasoby i że jedna z nich była w żądanym stanie, a jeden z nich nie był.</span><span class="sxs-lookup"><span data-stu-id="2268f-136">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="2268f-137">Można uzyskać bardziej czytelny wynik tylko dla właściwości **ResourcesNotInDesiredState** :</span><span class="sxs-lookup"><span data-stu-id="2268f-137">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

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

<span data-ttu-id="2268f-138">Należy zauważyć, że te przykłady mają na celu zakoncepcję tego, co można zrobić z danymi raportu.</span><span class="sxs-lookup"><span data-stu-id="2268f-138">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="2268f-139">Aby zapoznać się z wprowadzeniem do pracy z kodem JSON w programie PowerShell, zobacz [odtwarzanie za pomocą kodu JSON i programu PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="2268f-139">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="2268f-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2268f-140">See Also</span></span>

[<span data-ttu-id="2268f-141">Konfigurowanie Configuration Manager lokalnego</span><span class="sxs-lookup"><span data-stu-id="2268f-141">Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="2268f-142">Konfigurowanie serwera ściągania sieci Web DSC</span><span class="sxs-lookup"><span data-stu-id="2268f-142">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="2268f-143">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2268f-143">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
