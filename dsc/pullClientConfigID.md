---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji
ms.openlocfilehash: 93e533fd4e729e1af0124ad69ca7e384e1cb3aa4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="5570c-103">Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5570c-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="5570c-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5570c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5570c-105">Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL, gdzie może się kontaktować z serwerem ściągania można pobrać konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5570c-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="5570c-106">Aby to zrobić, należy skonfigurować lokalne Menedżera konfiguracji (LCM) niezbędne informacje.</span><span class="sxs-lookup"><span data-stu-id="5570c-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="5570c-107">Aby skonfigurować LCM, należy utworzyć specjalny typ konfiguracji ozdobione **DSCLocalConfigurationManager** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5570c-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="5570c-108">Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="5570c-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="5570c-109">**Uwaga**: w tym temacie dotyczą programu PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="5570c-109">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="5570c-110">Aby uzyskać informacje na temat konfigurowania klienta ściągania w programie PowerShell 4.0, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="5570c-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="5570c-111">Poniższy skrypt konfiguruje LCM ściągania konfiguracji z serwera o nazwie "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="5570c-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="5570c-112">W skrypcie **ConfigurationRepositoryWeb** z serwerem ściągania definiuje bloku.</span><span class="sxs-lookup"><span data-stu-id="5570c-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="5570c-113">**ServerURL**</span><span class="sxs-lookup"><span data-stu-id="5570c-113">The **ServerURL**</span></span>

<span data-ttu-id="5570c-114">Po uruchomieniu tego skryptu, tworzy nowy folder wyjściowy o nazwie **PullClientConfigID** i umieszcza metakonfigurację pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="5570c-114">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="5570c-115">W takim przypadku będzie miała nazwę pliku MOF metakonfigurację `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="5570c-115">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="5570c-116">Aby zastosować konfigurację, należy wywołać **DscLocalConfigurationManager zestaw** polecenia cmdlet z **ścieżki** Ustaw lokalizację pliku MOF metakonfigurację.</span><span class="sxs-lookup"><span data-stu-id="5570c-116">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="5570c-117">Na przykład: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="5570c-117">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="5570c-118">Identyfikator konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5570c-118">Configuration ID</span></span>

<span data-ttu-id="5570c-119">Zestawy skryptu **ConfigurationID** właściwości LCM wcześniej utworzony w tym celu identyfikatorem GUID (identyfikator GUID można tworzyć przy użyciu **identyfikator Guid nowego** polecenia cmdlet).</span><span class="sxs-lookup"><span data-stu-id="5570c-119">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="5570c-120">**ConfigurationID** jest LCM używa można znaleźć prawidłowej konfiguracji na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="5570c-120">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="5570c-121">Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania _ConfigurationID_MOF, gdzie _ConfigurationID_ jest wartością **ConfigurationID** właściwości elementu docelowego LCM węzła.</span><span class="sxs-lookup"><span data-stu-id="5570c-121">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="5570c-122">Serwerem ściągania SMB</span><span class="sxs-lookup"><span data-stu-id="5570c-122">SMB pull server</span></span>

<span data-ttu-id="5570c-123">Aby skonfigurować klienta do ściągania konfiguracje z serwerem SMB, użyj **ConfigurationRepositoryShare** bloku.</span><span class="sxs-lookup"><span data-stu-id="5570c-123">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="5570c-124">W **ConfigurationRepositoryShare** bloku, określ ścieżkę do serwera przez ustawienie **Ścieżka_źródłowa** właściwości.</span><span class="sxs-lookup"><span data-stu-id="5570c-124">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="5570c-125">Węzeł docelowy do ściąganie danych z serwera ściągania SMB o nazwie konfiguruje następujące metakonfigurację **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="5570c-125">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="5570c-126">Serwery zasobów i raportów</span><span class="sxs-lookup"><span data-stu-id="5570c-126">Resource and report servers</span></span>

<span data-ttu-id="5570c-127">Jeśli określisz tylko **ConfigurationRepositoryWeb** lub **ConfigurationRepositoryShare** bloków w konfiguracji LCM (tak jak w poprzednim przykładzie), klient ściągania będzie pobierać zasobów z określony serwer, ale nie będą wysyłały raportów do niego.</span><span class="sxs-lookup"><span data-stu-id="5570c-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="5570c-128">Serwer pojedynczego ściągania można używać do konfiguracji, zasobów i raportów, ale należy utworzyć **ReportRepositoryWeb** bloku, aby skonfigurować raportowanie.</span><span class="sxs-lookup"><span data-stu-id="5570c-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

<span data-ttu-id="5570c-129">W poniższym przykładzie przedstawiono metakonfigurację, który konfiguruje klienta w celu ściągania konfiguracje i zasobów i wysyłania raportowania danych, na serwerze ściągania pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="5570c-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }


        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="5570c-130">Można również określić serwery ściągania różnych zasobów i raportowania.</span><span class="sxs-lookup"><span data-stu-id="5570c-130">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="5570c-131">Aby określić serwer zasobów, użyj albo **ResourceRepositoryWeb** (na serwerze ściągania sieci web) lub **ResourceRepositoryShare** bloku (na serwerze ściągania SMB).</span><span class="sxs-lookup"><span data-stu-id="5570c-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="5570c-132">Aby określić serwer raportów, należy użyć **ReportRepositoryWeb** bloku.</span><span class="sxs-lookup"><span data-stu-id="5570c-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="5570c-133">Serwer raportów nie może być serwerem SMB.</span><span class="sxs-lookup"><span data-stu-id="5570c-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="5570c-134">Następujące metakonfigurację konfiguruje klienta ściągania można pobrać jego konfiguracje z **CONTOSO PullSrv** i jej zasobach z **CONTOSO ResourceSrv**i do wysyłania raportów o stanie  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="5570c-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## <a name="see-also"></a><span data-ttu-id="5570c-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5570c-135">See Also</span></span>

* [<span data-ttu-id="5570c-136">Konfigurowanie klienta ściągnięcia z nazwy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5570c-136">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)