---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji w programie PowerShell 5.0 lub nowszy
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079391"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="830b1-103">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji w programie PowerShell 5.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="830b1-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="830b1-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="830b1-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="830b1-105">Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno.</span><span class="sxs-lookup"><span data-stu-id="830b1-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="830b1-106">Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="830b1-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="830b1-107">Przed rozpoczęciem konfigurowania klienta ściągania, należy skonfigurować serwer ściągania.</span><span class="sxs-lookup"><span data-stu-id="830b1-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="830b1-108">Chociaż ta kolejność nie jest wymagane, pomaga w rozwiązywaniu problemów i pomaga zagwarantować, że rejestracja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="830b1-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="830b1-109">Aby skonfigurować serwer ściągania, można użyć następujących przewodników:</span><span class="sxs-lookup"><span data-stu-id="830b1-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="830b1-110">Konfigurowanie serwera ściągania SMB DSC</span><span class="sxs-lookup"><span data-stu-id="830b1-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="830b1-111">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="830b1-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="830b1-112">Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu.</span><span class="sxs-lookup"><span data-stu-id="830b1-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="830b1-113">Poniższe sekcje pokazują, jak konfigurowanie klienta ściągania przy użyciu udziału SMB lub protokołu HTTP DSC Pull Server.</span><span class="sxs-lookup"><span data-stu-id="830b1-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="830b1-114">Podczas odświeżania LCM węzła, jej skontaktuje się skonfigurowanej lokalizacji, aby pobrać wszystkie przypisane konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="830b1-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="830b1-115">Jeśli wszystkie wymagane zasoby, które nie istnieją w węźle, zostaną automatycznie pobrane je ze skonfigurowanej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="830b1-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="830b1-116">Jeśli węzeł jest skonfigurowana z [serwera raportów](reportServer.md), następnie zgłasza stan operacji.</span><span class="sxs-lookup"><span data-stu-id="830b1-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="830b1-117">Ten temat dotyczy programu PowerShell w wersji 5.0.</span><span class="sxs-lookup"><span data-stu-id="830b1-117">This topic applies to PowerShell 5.0.</span></span>
> <span data-ttu-id="830b1-118">Aby uzyskać informacje na temat konfigurowania klienta ściągania w programie PowerShell 4.0, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="830b1-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="830b1-119">Konfigurowanie klienta ściągania LCM</span><span class="sxs-lookup"><span data-stu-id="830b1-119">Configure the pull client LCM</span></span>

<span data-ttu-id="830b1-120">Wykonanie wszystkich poniższych przykładach tworzy nowy folder wyjściowy o nazwie **PullClientConfigName** i umieszcza plik MOF metaconfiguration istnieje.</span><span class="sxs-lookup"><span data-stu-id="830b1-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="830b1-121">W tym przypadku będzie miała nazwę pliku MOF metaconfiguration `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="830b1-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="830b1-122">Aby zastosować konfigurację, należy wywołać **Set-DscLocalConfigurationManager** polecenia cmdlet, za pomocą **ścieżki** Ustaw lokalizację pliku MOF metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="830b1-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="830b1-123">Przykład:</span><span class="sxs-lookup"><span data-stu-id="830b1-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="830b1-124">Nazwa konfiguracji</span><span class="sxs-lookup"><span data-stu-id="830b1-124">Configuration Name</span></span>

<span data-ttu-id="830b1-125">Przykłady poniżej zestawów **ConfigurationName** właściwość LCM nazwę konfiguracji poprzednio skompilowane, utworzone w tym celu.</span><span class="sxs-lookup"><span data-stu-id="830b1-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="830b1-126">**ConfigurationName** jest LCM używa można odnaleźć odpowiedniej konfiguracji na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="830b1-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="830b1-127">Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania `<ConfigurationName>.mof`, w tym przypadku "ClientConfig.mof".</span><span class="sxs-lookup"><span data-stu-id="830b1-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="830b1-128">Aby uzyskać więcej informacji, zobacz [publikowania konfiguracje serwera ściągania (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="830b1-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="830b1-129">Konfigurowanie klienta ściągania można pobrać konfiguracji</span><span class="sxs-lookup"><span data-stu-id="830b1-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="830b1-130">Każdy klient musi być skonfigurowany w **ściągnięcia** tryb i adres url serwera ściągania przechowywania jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="830b1-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="830b1-131">Aby to zrobić, należy skonfigurować lokalne Configuration Manager (LCM) niezbędne informacje.</span><span class="sxs-lookup"><span data-stu-id="830b1-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="830b1-132">Aby skonfigurować LCM, należy utworzyć specjalny rodzaj konfiguracji ozdobione **DSCLocalConfigurationManager** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="830b1-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="830b1-133">Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="830b1-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="830b1-134">Poniższy skrypt konfiguruje LCM ściągania konfiguracje z serwerem o nazwie "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="830b1-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="830b1-135">W skrypcie **ConfigurationRepositoryWeb** bloku definiuje serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="830b1-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="830b1-136">**ServerURL** właściwość określa punkt końcowy serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="830b1-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="830b1-137">**RegistrationKey** właściwość jest klucz współużytkowany między wszystkie węzły serwera ściągania klienta i że serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="830b1-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="830b1-138">Tej samej wartości są przechowywane w pliku na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="830b1-138">The same value is stored in a file on the pull server.</span></span>
  > [!NOTE]
  > <span data-ttu-id="830b1-139">Klucze rejestracji działają tylko z **web** pobierania serwerów.</span><span class="sxs-lookup"><span data-stu-id="830b1-139">Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="830b1-140">Nadal należy użyć **ConfigurationID** z **SMB** serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="830b1-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="830b1-141">Aby uzyskać informacje o konfigurowaniu serwera ściągania przy użyciu **ConfigurationID**, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="830b1-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="830b1-142">**ConfigurationNames** właściwość jest tablicą, który określa nazwę konfiguracji przeznaczonych dla węzła klienta.</span><span class="sxs-lookup"><span data-stu-id="830b1-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="830b1-143">**Uwaga:** Jeśli określisz więcej niż jedną wartość w **ConfigurationNames**, należy także określić **PartialConfiguration** bloków w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="830b1-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="830b1-144">Aby uzyskać informacje o konfiguracjach częściowe, zobacz [konfiguracje częściowe PowerShell Desired State Configuration](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="830b1-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="830b1-145">Konfigurowanie klienta ściągania można pobrać zasobów</span><span class="sxs-lookup"><span data-stu-id="830b1-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="830b1-146">Jeśli określisz tylko **ConfigurationRepositoryWeb** lub **ConfigurationRepositoryShare** blokuje w konfiguracji LCM (jak w poprzednim przykładzie), klienta ściągania będzie pobierać zasoby z takie same Lokalizacja, w którym są przechowywane pliki "MOF".</span><span class="sxs-lookup"><span data-stu-id="830b1-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="830b1-147">Można również określić różne lokalizacje, w którym klienci mogą pobierać zasoby.</span><span class="sxs-lookup"><span data-stu-id="830b1-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="830b1-148">Aby określić serwer zasobów, możesz użyć **ResourceRepositoryWeb** (dla internetowego serwera ściągania) lub **ResourceRepositoryShare** bloku (w przypadku serwera ściągania SMB).</span><span class="sxs-lookup"><span data-stu-id="830b1-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="830b1-149">Poniższy przykład pokazuje metaconfiguration, który konfiguruje klienta można pobrać konfiguracji z serwera ściągania i zasoby z udziału SMB.</span><span class="sxs-lookup"><span data-stu-id="830b1-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="830b1-150">Konfigurowanie klienta ściągania raportowanie stanu</span><span class="sxs-lookup"><span data-stu-id="830b1-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="830b1-151">Serwer pojedynczego ściągania służy do konfiguracji, zasobów i raportów.</span><span class="sxs-lookup"><span data-stu-id="830b1-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="830b1-152">Raportowanie nie jest skonfigurowane dla klientów domyślnie.</span><span class="sxs-lookup"><span data-stu-id="830b1-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="830b1-153">Aby skonfigurować klienta do raportów o stanie, trzeba utworzyć **ReportRepositoryWeb** bloku.</span><span class="sxs-lookup"><span data-stu-id="830b1-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="830b1-154">Poniższy przykład pokazuje metaconfiguration, który konfiguruje klienta do ściągania konfiguracji i zasobów oraz wysyłania danych, raportowania na serwerze ściągania jednego.</span><span class="sxs-lookup"><span data-stu-id="830b1-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="830b1-155">Serwer raportów nie może być udziału SMB.</span><span class="sxs-lookup"><span data-stu-id="830b1-155">A report server cannot be an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="830b1-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="830b1-156">See Also</span></span>

* [<span data-ttu-id="830b1-157">Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="830b1-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="830b1-158">Konfigurowanie internetowego serwera ściągania DSC</span><span class="sxs-lookup"><span data-stu-id="830b1-158">Setting up a DSC web pull server</span></span>](pullServer.md)
