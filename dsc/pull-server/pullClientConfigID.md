---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji w programie PowerShell 5.0 lub nowszy
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055720"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="a161f-103">Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji w programie PowerShell 5.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="a161f-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="a161f-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a161f-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a161f-105">Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno.</span><span class="sxs-lookup"><span data-stu-id="a161f-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="a161f-106">Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="a161f-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="a161f-107">Przed rozpoczęciem konfigurowania klienta ściągania, należy skonfigurować serwer ściągania.</span><span class="sxs-lookup"><span data-stu-id="a161f-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="a161f-108">Chociaż ta kolejność nie jest wymagane, pomaga w rozwiązywaniu problemów i pomaga zagwarantować, że rejestracja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a161f-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="a161f-109">Aby skonfigurować serwer ściągania, można użyć następujących przewodników:</span><span class="sxs-lookup"><span data-stu-id="a161f-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="a161f-110">Konfigurowanie serwera ściągania SMB DSC</span><span class="sxs-lookup"><span data-stu-id="a161f-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a161f-111">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="a161f-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="a161f-112">Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu.</span><span class="sxs-lookup"><span data-stu-id="a161f-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="a161f-113">Poniższe sekcje pokazują, jak konfigurowanie klienta ściągania przy użyciu udziału SMB lub protokołu HTTP DSC Pull Server.</span><span class="sxs-lookup"><span data-stu-id="a161f-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="a161f-114">Podczas odświeżania LCM węzła, jej skontaktuje się skonfigurowanej lokalizacji, aby pobrać wszystkie przypisane konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="a161f-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="a161f-115">Jeśli wszystkie wymagane zasoby, które nie istnieją w węźle, zostaną automatycznie pobrane je ze skonfigurowanej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a161f-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="a161f-116">Jeśli węzeł jest skonfigurowana z [serwera raportów](reportServer.md), następnie zgłasza stan operacji.</span><span class="sxs-lookup"><span data-stu-id="a161f-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="a161f-117">Ten temat dotyczy programu PowerShell w wersji 5.0.</span><span class="sxs-lookup"><span data-stu-id="a161f-117">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="a161f-118">Aby uzyskać informacje na temat konfigurowania klienta ściągania w programie PowerShell 4.0, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="a161f-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="a161f-119">Konfigurowanie klienta ściągania LCM</span><span class="sxs-lookup"><span data-stu-id="a161f-119">Configure the pull client LCM</span></span>

<span data-ttu-id="a161f-120">Wykonanie wszystkich poniższych przykładach tworzy nowy folder wyjściowy o nazwie **PullClientConfigID** i umieszcza plik MOF metaconfiguration istnieje.</span><span class="sxs-lookup"><span data-stu-id="a161f-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="a161f-121">W tym przypadku będzie miała nazwę pliku MOF metaconfiguration `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="a161f-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="a161f-122">Aby zastosować konfigurację, należy wywołać **Set-DscLocalConfigurationManager** polecenia cmdlet, za pomocą **ścieżki** Ustaw lokalizację pliku MOF metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="a161f-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="a161f-123">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a161f-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="a161f-124">Identyfikator konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a161f-124">Configuration ID</span></span>

<span data-ttu-id="a161f-125">Przykłady poniżej zestawów **ConfigurationID** właściwość LCM do **Guid** które było wcześniej utworzone w tym celu.</span><span class="sxs-lookup"><span data-stu-id="a161f-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="a161f-126">**ConfigurationID** jest LCM używa można odnaleźć odpowiedniej konfiguracji na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="a161f-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="a161f-127">Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania `ConfigurationID.mof`, gdzie *ConfigurationID* jest wartością **ConfigurationID** właściwość LCM węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="a161f-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="a161f-128">Aby uzyskać więcej informacji, zobacz [publikowania konfiguracje serwera ściągania (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="a161f-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="a161f-129">Można utworzyć losowej **Guid** w przykładzie poniżej lub za pomocą [nowy Guid](/powershell/module/microsoft.powershell.utility/new-guid) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a161f-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="a161f-130">Aby uzyskać więcej informacji o korzystaniu z **identyfikatorów GUID** w danym środowisku, zobacz [planowanie identyfikatorów GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="a161f-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="a161f-131">Konfigurowanie klienta ściągania można pobrać konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a161f-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="a161f-132">Każdy klient musi być skonfigurowany w **ściągnięcia** tryb i adres url serwera ściągania przechowywania jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a161f-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="a161f-133">Aby to zrobić, należy skonfigurować lokalne Configuration Manager (LCM) niezbędne informacje.</span><span class="sxs-lookup"><span data-stu-id="a161f-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="a161f-134">Aby skonfigurować LCM, należy utworzyć specjalny rodzaj konfiguracji ozdobione **DSCLocalConfigurationManager** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a161f-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="a161f-135">Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="a161f-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="a161f-136">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="a161f-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="a161f-137">Poniższy skrypt konfiguruje LCM ściągania konfiguracje z serwerem o nazwie "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="a161f-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="a161f-138">W skrypcie **ConfigurationRepositoryWeb** bloku definiuje serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="a161f-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="a161f-139">**ServerUrl** Określa adres url ściągnięcia DSC</span><span class="sxs-lookup"><span data-stu-id="a161f-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="a161f-140">Udział SMB</span><span class="sxs-lookup"><span data-stu-id="a161f-140">SMB Share</span></span>

<span data-ttu-id="a161f-141">Poniższy skrypt konfiguruje LCM ściągania konfiguracje z udziału SMB `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="a161f-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="a161f-142">W skrypcie **ConfigurationRepositoryShare** bloku definiuje serwera ściągania, w tym przypadku jest po prostu udziału SMB.</span><span class="sxs-lookup"><span data-stu-id="a161f-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="a161f-143">Konfigurowanie klienta ściągania można pobrać zasobów</span><span class="sxs-lookup"><span data-stu-id="a161f-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="a161f-144">Jeśli określisz tylko **ConfigurationRepositoryWeb** lub **ConfigurationRepositoryShare** blokuje w konfiguracji LCM (tak jak w poprzednich przykładach), klienta ściągania będzie pobierać zasoby z tej samej Lokalizacja pobierania jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a161f-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="a161f-145">Można również określić oddzielne lokalizacje dla zasobów.</span><span class="sxs-lookup"><span data-stu-id="a161f-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="a161f-146">Aby określić lokalizację zasobu jako oddzielny serwer, użyj **ResourceRepositoryWeb** bloku.</span><span class="sxs-lookup"><span data-stu-id="a161f-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="a161f-147">Aby określić lokalizację zasobu jako udziału SMB, użyj **ResourceRepositoryShare** bloku.</span><span class="sxs-lookup"><span data-stu-id="a161f-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="a161f-148">Można połączyć **ConfigurationRepositoryWeb** z **ResourceRepositoryShare** lub **ConfigurationRepositoryShare** z **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="a161f-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="a161f-149">Przykłady tego nie zostały wymienione poniżej.</span><span class="sxs-lookup"><span data-stu-id="a161f-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="a161f-150">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="a161f-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="a161f-151">Następujące metaconfiguration konfiguruje klienta ściągania, aby uzyskać jego konfiguracji z **CONTOSO PullSrv** i jej zasobach z **CONTOSO ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="a161f-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="a161f-152">Udział SMB</span><span class="sxs-lookup"><span data-stu-id="a161f-152">SMB Share</span></span>

<span data-ttu-id="a161f-153">W poniższym przykładzie pokazano metaconfiguration, który konfiguruje klienta do ściągania konfiguracji z udziału SMB `\\SMBPullServer\Configurations`i zasoby z udziału SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="a161f-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="a161f-154">Automatycznie pobieraj zasobami w trybie Push</span><span class="sxs-lookup"><span data-stu-id="a161f-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="a161f-155">Począwszy od programu PowerShell w wersji 5.0 klientów ściągnięcia można pobrać modułów z udziału SMB nawet wtedy, gdy są one konfigurowane na potrzeby **wypychania** trybu.</span><span class="sxs-lookup"><span data-stu-id="a161f-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="a161f-156">Jest to szczególnie przydatne w scenariuszach, w których nie chcesz skonfigurować serwer ściągania.</span><span class="sxs-lookup"><span data-stu-id="a161f-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="a161f-157">**ResourceRepositoryShare** bloku mogą być używane bez określania **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="a161f-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="a161f-158">W poniższym przykładzie pokazano metaconfiguration, który konfiguruje klienta do ściągnięcia zasobów z udziału SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="a161f-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="a161f-159">Gdy węzeł zostaje **PUSHED** konfiguracji automatycznie pobierze wszystkie wymagane zasoby z udziału określonego.</span><span class="sxs-lookup"><span data-stu-id="a161f-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="a161f-160">Konfigurowanie klienta ściągania raportowanie stanu</span><span class="sxs-lookup"><span data-stu-id="a161f-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="a161f-161">Domyślnie węzły nie będą wysyłały raporty do skonfigurowanego serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="a161f-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="a161f-162">Serwer pojedynczego ściągania można użyć do konfiguracji, zasobów i raportów, ale należy utworzyć **ReportRepositoryWeb** bloku, aby skonfigurować raportowanie.</span><span class="sxs-lookup"><span data-stu-id="a161f-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="a161f-163">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="a161f-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="a161f-164">Poniższy przykład pokazuje metaconfiguration, który konfiguruje klienta do ściągania konfiguracji i zasobów oraz wysyłania danych, raportowania na serwerze ściągania jednego.</span><span class="sxs-lookup"><span data-stu-id="a161f-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="a161f-165">Aby określić serwer raportów, należy użyć **ReportRepositoryWeb** bloku.</span><span class="sxs-lookup"><span data-stu-id="a161f-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="a161f-166">Serwer raportów nie może być serwerem SMB.</span><span class="sxs-lookup"><span data-stu-id="a161f-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="a161f-167">Następujące metaconfiguration konfiguruje klienta ściągania, aby uzyskać jego konfiguracji z **CONTOSO PullSrv** i jej zasobach z **CONTOSO ResourceSrv**i wysyłać raporty o stanie do  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="a161f-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="a161f-168">Udział SMB</span><span class="sxs-lookup"><span data-stu-id="a161f-168">SMB Share</span></span>

<span data-ttu-id="a161f-169">Serwer raportów nie może być udziału SMB.</span><span class="sxs-lookup"><span data-stu-id="a161f-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a161f-170">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a161f-170">Next Steps</span></span>

<span data-ttu-id="a161f-171">Po skonfigurowaniu klienta ściągania następujące przewodniki można użyć, aby wykonać kolejne kroki:</span><span class="sxs-lookup"><span data-stu-id="a161f-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="a161f-172">Publikowanie konfiguracji na serwerze ściągania (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="a161f-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="a161f-173">Pakiet i przekazywanie zasobów do serwera ściągania (v4)</span><span class="sxs-lookup"><span data-stu-id="a161f-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="a161f-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a161f-174">See Also</span></span>

* [<span data-ttu-id="a161f-175">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a161f-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
