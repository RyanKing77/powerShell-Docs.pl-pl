---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Konfigurowanie klienta ściągania przy użyciu identyfikator konfiguracji w programie PowerShell 4.0"
ms.openlocfilehash: 2449a4ddfea5c0ee7096ad7478e80166eb095bbe
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="7f363-103">Konfigurowanie klienta ściągania przy użyciu identyfikator konfiguracji w programie PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="7f363-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="7f363-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7f363-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7f363-105">Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL, gdzie może się kontaktować z serwerem ściągania można pobrać konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7f363-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="7f363-106">Aby to zrobić, należy skonfigurować lokalne Menedżera konfiguracji (LCM) niezbędne informacje.</span><span class="sxs-lookup"><span data-stu-id="7f363-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="7f363-107">Aby skonfigurować LCM, należy utworzyć specjalny typ Konfiguracja znana jako "metakonfigurację".</span><span class="sxs-lookup"><span data-stu-id="7f363-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="7f363-108">Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [Windows PowerShell 4.0 żądanego stanu konfiguracji lokalny program Configuration Manager](metaConfig4.md)</span><span class="sxs-lookup"><span data-stu-id="7f363-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="7f363-109">Poniższy skrypt konfiguruje LCM ściągania konfiguracji z serwera o nazwie "PullServer":</span><span class="sxs-lookup"><span data-stu-id="7f363-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull 
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
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="7f363-110">W skrypcie **DownloadManagerCustomData** przekazuje niezabezpieczone połączenie umożliwia adres URL serwera ściągania i (w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="7f363-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span> 

<span data-ttu-id="7f363-111">Po uruchomieniu tego skryptu, tworzy nowy folder wyjściowy o nazwie **SimpleMetaConfigurationForPull** i umieszcza metakonfigurację pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="7f363-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="7f363-112">Aby zastosować konfigurację, użyj **DscLocalConfigurationManager zestaw** wraz z parametrami **ComputerName** (Użyj "localhost") i **ścieżki** (ścieżka do lokalizacji cel pliku localhost.meta.mof węzła).</span><span class="sxs-lookup"><span data-stu-id="7f363-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="7f363-113">Przykład:</span><span class="sxs-lookup"><span data-stu-id="7f363-113">For example:</span></span> 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="7f363-114">Identyfikator konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7f363-114">Configuration ID</span></span>
<span data-ttu-id="7f363-115">Zestawy skryptu **ConfigurationID** właściwości LCM wcześniej utworzony w tym celu identyfikatorem GUID (identyfikator GUID można tworzyć przy użyciu **identyfikator Guid nowego** polecenia cmdlet).</span><span class="sxs-lookup"><span data-stu-id="7f363-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="7f363-116">**ConfigurationID** jest LCM używa można znaleźć prawidłowej konfiguracji na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="7f363-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="7f363-117">Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania `ConfigurationID.mof`, gdzie *ConfigurationID* jest wartością **ConfigurationID** właściwości LCM węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="7f363-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="7f363-118">Ściąganie z serwerem SMB</span><span class="sxs-lookup"><span data-stu-id="7f363-118">Pulling from an SMB server</span></span>

<span data-ttu-id="7f363-119">Jeśli serwer ściągania jest skonfigurowany jako udziału plików SMB, a nie usługi sieci web, określ **DscFileDownloadManager** zamiast **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="7f363-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="7f363-120">**DscFileDownloadManager** przyjmuje **Ścieżka_źródłowa** właściwości zamiast **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="7f363-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="7f363-121">Poniższy skrypt konfiguruje LCM ściągania konfiguracje z udziału SMB na serwerze o nazwie "CONTOSO-SERVER" o nazwie "SmbDscShare":</span><span class="sxs-lookup"><span data-stu-id="7f363-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull 
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="7f363-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f363-122">See Also</span></span>

- [<span data-ttu-id="7f363-123">Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web</span><span class="sxs-lookup"><span data-stu-id="7f363-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="7f363-124">Konfigurowanie serwera ściągania SMB platformy DSC</span><span class="sxs-lookup"><span data-stu-id="7f363-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)

