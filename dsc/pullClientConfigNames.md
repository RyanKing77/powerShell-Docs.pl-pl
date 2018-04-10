---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji
ms.openlocfilehash: dd0526b118b404854b1e9b445ca50bdaafdd01c7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="420ba-103">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="420ba-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="420ba-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="420ba-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="420ba-105">Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL, gdzie może się kontaktować z serwerem ściągania można pobrać konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="420ba-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="420ba-106">Aby to zrobić, należy skonfigurować lokalne Menedżera konfiguracji (LCM) niezbędne informacje.</span><span class="sxs-lookup"><span data-stu-id="420ba-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="420ba-107">Aby skonfigurować LCM, należy utworzyć specjalny typ konfiguracji ozdobione **DSCLocalConfigurationManager** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="420ba-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="420ba-108">Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="420ba-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="420ba-109">**Uwaga**: w tym temacie dotyczą programu PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="420ba-109">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="420ba-110">Aby uzyskać informacje na temat konfigurowania klienta ściągania w programie PowerShell 4.0, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="420ba-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="420ba-111">Poniższy skrypt konfiguruje LCM ściągania konfiguracji z serwera o nazwie "CONTOSO-PullSrv":</span><span class="sxs-lookup"><span data-stu-id="420ba-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

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

<span data-ttu-id="420ba-112">W skrypcie **ConfigurationRepositoryWeb** z serwerem ściągania definiuje bloku.</span><span class="sxs-lookup"><span data-stu-id="420ba-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="420ba-113">**ServerURL** właściwość określa punktu końcowego na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="420ba-113">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="420ba-114">**RegistrationKey** właściwość jest kluczem udostępnionego między wszystkie węzły klienta na serwerze ściągania i że serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="420ba-114">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="420ba-115">Tę samą wartość jest przechowywane w pliku na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="420ba-115">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="420ba-116">**ConfigurationNames** właściwość jest tablicą, który określa nazwę konfiguracji przeznaczonych dla węzła klienta.</span><span class="sxs-lookup"><span data-stu-id="420ba-116">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="420ba-117">Na serwerze ściągania dla tego węzła klienta musi mieć nazwę pliku konfiguracji MOF *ConfigurationNames*MOF, gdzie *ConfigurationNames* odpowiada wartości **ConfigurationNames**  zestawu metakonfigurację tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="420ba-117">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="420ba-118">**Uwaga:** określenia więcej niż jedną wartość w **ConfigurationNames**, należy także określić **PartialConfiguration** blokuje w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="420ba-118">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="420ba-119">Informacje o konfiguracjach częściowe, zobacz [konfiguracje częściowe konfiguracji żądanego stanu środowiska PowerShell](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="420ba-119">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="420ba-120">Po uruchomieniu tego skryptu, tworzy nowy folder wyjściowy o nazwie **PullClientConfigNames** i umieszcza metakonfigurację pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="420ba-120">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="420ba-121">W takim przypadku będzie miała nazwę pliku MOF metakonfigurację `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="420ba-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="420ba-122">Aby zastosować konfigurację, należy wywołać **DscLocalConfigurationManager zestaw** polecenia cmdlet z **ścieżki** Ustaw lokalizację pliku MOF metakonfigurację.</span><span class="sxs-lookup"><span data-stu-id="420ba-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="420ba-123">**Uwaga**: klucze rejestracji działa tylko z serwerów sieci web ściągania.</span><span class="sxs-lookup"><span data-stu-id="420ba-123">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="420ba-124">Możesz nadal korzystać **ConfigurationID** z serwerem ściągania SMB.</span><span class="sxs-lookup"><span data-stu-id="420ba-124">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="420ba-125">Informacje o konfigurowaniu serwera ściągania przy użyciu **ConfigurationID**, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="420ba-125">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="420ba-126">Serwery zasobów i raportów</span><span class="sxs-lookup"><span data-stu-id="420ba-126">Resource and report servers</span></span>

<span data-ttu-id="420ba-127">Jeśli określisz tylko **ConfigurationRepositoryWeb** lub **ConfigurationRepositoryShare** bloków w konfiguracji LCM (tak jak w poprzednim przykładzie), klient ściągania będzie pobierać zasobów z określony serwer, ale nie będą wysyłały raportów do niego.</span><span class="sxs-lookup"><span data-stu-id="420ba-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="420ba-128">Serwer pojedynczego ściągania można używać do konfiguracji, zasobów i raportów, ale należy utworzyć **ReportRepositoryWeb** bloku, aby skonfigurować raportowanie.</span><span class="sxs-lookup"><span data-stu-id="420ba-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="420ba-129">W poniższym przykładzie przedstawiono metakonfigurację, który konfiguruje klienta w celu ściągania konfiguracje i zasobów i wysyłania raportowania danych, na serwerze ściągania pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="420ba-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="420ba-130">Można również określić serwery ściągania różnych zasobów i raportowania.</span><span class="sxs-lookup"><span data-stu-id="420ba-130">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="420ba-131">Aby określić serwer zasobów, użyj albo **ResourceRepositoryWeb** (na serwerze ściągania sieci web) lub **ResourceRepositoryShare** bloku (na serwerze ściągania SMB).</span><span class="sxs-lookup"><span data-stu-id="420ba-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="420ba-132">Aby określić serwer raportów, należy użyć **ReportRepositoryWeb** bloku.</span><span class="sxs-lookup"><span data-stu-id="420ba-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="420ba-133">Serwer raportów nie może być serwerem SMB.</span><span class="sxs-lookup"><span data-stu-id="420ba-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="420ba-134">Następujące metakonfigurację konfiguruje klienta ściągania można pobrać jego konfiguracje z **CONTOSO PullSrv** i jej zasobach z **CONTOSO ResourceSrv**i do wysyłania raportów o stanie  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="420ba-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="420ba-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="420ba-135">See Also</span></span>

* [<span data-ttu-id="420ba-136">Konfigurowanie klienta ściągnięcia z identyfikator konfiguracji</span><span class="sxs-lookup"><span data-stu-id="420ba-136">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="420ba-137">Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web</span><span class="sxs-lookup"><span data-stu-id="420ba-137">Setting up a DSC web pull server</span></span>](pullServer.md)