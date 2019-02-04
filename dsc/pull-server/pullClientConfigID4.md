---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji w programie PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685480"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="00024-103">Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji w programie PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="00024-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="00024-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="00024-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00024-105">Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno.</span><span class="sxs-lookup"><span data-stu-id="00024-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="00024-106">Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="00024-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="00024-107">Przed rozpoczęciem konfigurowania klienta ściągania, należy skonfigurować serwer ściągania.</span><span class="sxs-lookup"><span data-stu-id="00024-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="00024-108">Chociaż ta kolejność nie jest wymagane, pomaga w rozwiązywaniu problemów i pomaga zagwarantować, że rejestracja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="00024-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="00024-109">Aby skonfigurować serwer ściągania, można użyć następujących przewodników:</span><span class="sxs-lookup"><span data-stu-id="00024-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="00024-110">Konfigurowanie serwera ściągania SMB DSC</span><span class="sxs-lookup"><span data-stu-id="00024-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="00024-111">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="00024-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="00024-112">Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu.</span><span class="sxs-lookup"><span data-stu-id="00024-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="00024-113">Poniższe sekcje pokazują, jak konfigurowanie klienta ściągania przy użyciu udziału SMB lub protokołu HTTP DSC Pull Server.</span><span class="sxs-lookup"><span data-stu-id="00024-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="00024-114">Podczas odświeżania LCM węzła, jej skontaktuje się skonfigurowanej lokalizacji, aby pobrać wszystkie przypisane konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="00024-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="00024-115">Jeśli wszystkie wymagane zasoby, które nie istnieją w węźle, zostaną automatycznie pobrane je ze skonfigurowanej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="00024-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="00024-116">Jeśli węzeł jest skonfigurowana z [serwera raportów](reportServer.md), następnie zgłasza stan operacji.</span><span class="sxs-lookup"><span data-stu-id="00024-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="00024-117">Konfigurowanie klienta ściągania LCM</span><span class="sxs-lookup"><span data-stu-id="00024-117">Configure the pull client LCM</span></span>

<span data-ttu-id="00024-118">Wykonanie wszystkich poniższych przykładach tworzy nowy folder wyjściowy o nazwie **PullClientConfigID** i umieszcza plik MOF metaconfiguration istnieje.</span><span class="sxs-lookup"><span data-stu-id="00024-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="00024-119">W tym przypadku będzie miała nazwę pliku MOF metaconfiguration `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="00024-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="00024-120">Aby zastosować konfigurację, należy wywołać **Set-DscLocalConfigurationManager** polecenia cmdlet, za pomocą **ścieżki** Ustaw lokalizację pliku MOF metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="00024-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="00024-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="00024-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="00024-122">Identyfikator konfiguracji</span><span class="sxs-lookup"><span data-stu-id="00024-122">Configuration ID</span></span>

<span data-ttu-id="00024-123">Przykłady poniżej zestaw **ConfigurationID** właściwość LCM do **Guid** które było wcześniej utworzone w tym celu.</span><span class="sxs-lookup"><span data-stu-id="00024-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="00024-124">**ConfigurationID** jest LCM używa można odnaleźć odpowiedniej konfiguracji na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="00024-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="00024-125">Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania `ConfigurationID.mof`, gdzie *ConfigurationID* jest wartością **ConfigurationID** właściwość LCM węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="00024-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="00024-126">Aby uzyskać więcej informacji, zobacz [publikowania konfiguracje serwera ściągania (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="00024-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="00024-127">Można utworzyć losowej **Guid** przy użyciu w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="00024-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="00024-128">Konfigurowanie klienta ściągania można pobrać konfiguracji</span><span class="sxs-lookup"><span data-stu-id="00024-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="00024-129">Każdy klient musi być skonfigurowany w **ściągnięcia** tryb i adres url serwera ściągania przechowywania jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="00024-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="00024-130">Aby to zrobić, należy skonfigurować lokalne Configuration Manager (LCM) niezbędne informacje.</span><span class="sxs-lookup"><span data-stu-id="00024-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="00024-131">Aby skonfigurować LCM, utworzyć specjalny rodzaj konfiguracji, za pomocą **LocalConfigurationManager** bloku.</span><span class="sxs-lookup"><span data-stu-id="00024-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="00024-132">Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="00024-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="00024-133">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="00024-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="00024-134">Jeśli serwer ściągania jest skonfigurowany jako usługę sieci web, należy ustawić **DownloadManagerName** do **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="00024-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="00024-135">**WebDownloadManager** wymaga określenia **ServerUrl** do **DownloadManagerCustomData** klucza.</span><span class="sxs-lookup"><span data-stu-id="00024-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="00024-136">Można także określić wartość dla **AllowUnsecureConnection**, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="00024-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="00024-137">Poniższy skrypt konfiguruje LCM ściągania konfiguracje z serwerem o nazwie "PullServer".</span><span class="sxs-lookup"><span data-stu-id="00024-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="00024-138">Udział SMB</span><span class="sxs-lookup"><span data-stu-id="00024-138">SMB Share</span></span>

<span data-ttu-id="00024-139">Jeśli serwer ściągania jest skonfigurowany jako udział plików SMB, a nie usługi sieci web, należy ustawić **DownloadManagerName** do **DscFileDownloadManager** zamiast **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="00024-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="00024-140">**DscFileDownloadManager** wymaga określenia **Ścieżka_źródłowa** właściwość **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="00024-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="00024-141">Poniższy skrypt konfiguruje LCM do ściągania konfiguracji z udziału SMB na serwerze o nazwie "CONTOSO-SERVER" o nazwie "SmbDscShare".</span><span class="sxs-lookup"><span data-stu-id="00024-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a><span data-ttu-id="00024-142">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="00024-142">Next Steps</span></span>

<span data-ttu-id="00024-143">Po skonfigurowaniu klienta ściągania następujące przewodniki można użyć, aby wykonać kolejne kroki:</span><span class="sxs-lookup"><span data-stu-id="00024-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="00024-144">Publikowanie konfiguracji na serwerze ściągania (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="00024-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="00024-145">Pakiet i przekazywanie zasobów do serwera ściągania (v4)</span><span class="sxs-lookup"><span data-stu-id="00024-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="00024-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00024-146">See Also</span></span>

- [<span data-ttu-id="00024-147">Konfigurowanie internetowego serwera ściągania DSC</span><span class="sxs-lookup"><span data-stu-id="00024-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="00024-148">Konfigurowanie serwera ściągania DSC SMB</span><span class="sxs-lookup"><span data-stu-id="00024-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
