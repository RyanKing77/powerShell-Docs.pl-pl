---
ms.date: 03/04/2019
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Usługa ściągania platformy DSC
ms.openlocfilehash: 865eae5813e0c7b656a4158f0b1350e60f1e3291
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986539"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="b426a-103">Usługa ściągania konfiguracji żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="b426a-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b426a-104">Serwer ściągania (Windows Feature *DSC-Service*) jest obsługiwanym składnikiem systemu Windows Server, ale nie ma żadnych planów do oferowania nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="b426a-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b426a-105">Zalecane jest, aby rozpocząć przechodzenie zarządzanych klientów do [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (obejmuje funkcje wykraczające poza serwer ściągający w systemie Windows Server) lub jedno z rozwiązań społecznościowych wymienionych w [tym miejscu](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="b426a-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b426a-106">Lokalne Configuration Manager mogą być zarządzane centralnie przez rozwiązanie usługi ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-106">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="b426a-107">W przypadku korzystania z tej metody zarządzany węzeł jest rejestrowany w usłudze i przypisuje konfigurację w ustawieniach LCM.</span><span class="sxs-lookup"><span data-stu-id="b426a-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="b426a-108">Konfiguracja i wszystkie zasoby DSC wymaganych jako zależności konfiguracji są pobierane na maszynę i używane przez LCM do zarządzania konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="b426a-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="b426a-109">Informacje o stanie zarządzanej maszyny są przekazywane do usługi na potrzeby raportowania.</span><span class="sxs-lookup"><span data-stu-id="b426a-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="b426a-110">Pojęcie to jest nazywane "usługą ściągania".</span><span class="sxs-lookup"><span data-stu-id="b426a-110">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="b426a-111">Bieżące opcje usługi ściągania obejmują:</span><span class="sxs-lookup"><span data-stu-id="b426a-111">The current options for pull service include:</span></span>

- <span data-ttu-id="b426a-112">Azure Automation usługi konfiguracji żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="b426a-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="b426a-113">Usługa ściągania działająca w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="b426a-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="b426a-114">Społeczność z obsługiwanymi rozwiązaniami "open source"</span><span class="sxs-lookup"><span data-stu-id="b426a-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="b426a-115">Udział SMB</span><span class="sxs-lookup"><span data-stu-id="b426a-115">An SMB share</span></span>

<span data-ttu-id="b426a-116">**Zalecanym rozwiązaniem**i opcją z największą liczbą dostępnych funkcji jest [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="b426a-116">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="b426a-117">Usługa platformy Azure umożliwia zarządzanie węzłami lokalnie w prywatnych centrach danych lub w chmurach publicznych, takich jak Azure i AWS.</span><span class="sxs-lookup"><span data-stu-id="b426a-117">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="b426a-118">W przypadku środowisk prywatnych, w których serwery nie mogą łączyć się bezpośrednio z Internetem, należy rozważyć ograniczenie ruchu wychodzącego tylko do opublikowanego zakresu adresów IP platformy Azure (zobacz [zakres adresów IP centrum danych platformy Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="b426a-118">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="b426a-119">Funkcje usługi online, które nie są obecnie dostępne w usłudze ściągania w systemie Windows Server, obejmują:</span><span class="sxs-lookup"><span data-stu-id="b426a-119">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="b426a-120">Wszystkie dane są szyfrowane podczas przesyłania i przechowywania</span><span class="sxs-lookup"><span data-stu-id="b426a-120">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="b426a-121">Certyfikaty klienta są tworzone i zarządzane automatycznie</span><span class="sxs-lookup"><span data-stu-id="b426a-121">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="b426a-122">Wpisy tajne do centralnego zarządzania [hasłami/poświadczeniami](/azure/automation/automation-credentials)lub [zmiennymi](/azure/automation/automation-variables) , takimi jak nazwy serwerów lub parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="b426a-122">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="b426a-123">Centralne zarządzanie konfiguracją [LCM](../managing-nodes/metaConfig.md#basic-settings) Node</span><span class="sxs-lookup"><span data-stu-id="b426a-123">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="b426a-124">Centralne przypisywanie konfiguracji do węzłów klienta</span><span class="sxs-lookup"><span data-stu-id="b426a-124">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="b426a-125">Wprowadzenie zmian w konfiguracji "grup Kanaryjskich" w celu przetestowania przed osiągnięciem produkcji</span><span class="sxs-lookup"><span data-stu-id="b426a-125">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="b426a-126">Raportowanie graficzne</span><span class="sxs-lookup"><span data-stu-id="b426a-126">Graphical reporting</span></span>
  - <span data-ttu-id="b426a-127">Szczegóły stanu na poziomie szczegółowości zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="b426a-127">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="b426a-128">Pełne komunikaty o błędach z komputerów klienckich w celu rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="b426a-128">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="b426a-129">[Integracja z usługą Azure log Analytics](/azure/automation/automation-dsc-diagnostics) na potrzeby alertów, zautomatyzowanych zadań, aplikacji systemu Android/iOS na potrzeby raportowania i alertów</span><span class="sxs-lookup"><span data-stu-id="b426a-129">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="b426a-130">Usługa ściągania DSC w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="b426a-130">DSC pull service in Windows Server</span></span>

<span data-ttu-id="b426a-131">Istnieje możliwość skonfigurowania usługi ściągania do uruchamiania w systemie Windows Server.</span><span class="sxs-lookup"><span data-stu-id="b426a-131">It is possible to configure a pull service to run on Windows Server.</span></span>
<span data-ttu-id="b426a-132">Zaleca się, aby rozwiązanie usługi ściągania dołączone do systemu Windows Server zawierało tylko możliwości przechowywania konfiguracji/modułów do pobierania i przechwytywania danych raportu w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="b426a-132">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="b426a-133">Nie obejmuje to wielu możliwości oferowanych przez usługę na platformie Azure i dlatego nie jest dobrym narzędziem do oceny sposobu korzystania z usługi.</span><span class="sxs-lookup"><span data-stu-id="b426a-133">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="b426a-134">Usługa ściągania oferowana w systemie Windows Server jest usługą sieci Web w usługach IIS, która korzysta z interfejsu OData do udostępniania plików konfiguracji DSC węzłom docelowym, gdy te węzły poproszą z nimi.</span><span class="sxs-lookup"><span data-stu-id="b426a-134">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="b426a-135">Wymagania dotyczące korzystania z serwera ściągania:</span><span class="sxs-lookup"><span data-stu-id="b426a-135">Requirements for using a pull server:</span></span>

- <span data-ttu-id="b426a-136">Serwer z systemem:</span><span class="sxs-lookup"><span data-stu-id="b426a-136">A server running:</span></span>
  - <span data-ttu-id="b426a-137">WMF/PowerShell 4,0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="b426a-137">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="b426a-138">Rola serwera IIS</span><span class="sxs-lookup"><span data-stu-id="b426a-138">IIS server role</span></span>
  - <span data-ttu-id="b426a-139">Usługa DSC</span><span class="sxs-lookup"><span data-stu-id="b426a-139">DSC Service</span></span>
- <span data-ttu-id="b426a-140">W idealnym przypadku niektóre sposoby generowania certyfikatu w celu zabezpieczenia poświadczeń przekazaną do lokalnego Configuration Manager (LCM) na węzłach docelowych</span><span class="sxs-lookup"><span data-stu-id="b426a-140">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="b426a-141">Najlepszym sposobem skonfigurowania usługi ściągania systemu Windows Server jest użycie konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="b426a-141">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="b426a-142">Poniżej przedstawiono przykładowy skrypt.</span><span class="sxs-lookup"><span data-stu-id="b426a-142">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="b426a-143">Obsługiwane systemy baz danych</span><span class="sxs-lookup"><span data-stu-id="b426a-143">Supported database systems</span></span>

|<span data-ttu-id="b426a-144">WMF 4,0</span><span class="sxs-lookup"><span data-stu-id="b426a-144">WMF 4.0</span></span>   |<span data-ttu-id="b426a-145">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="b426a-145">WMF 5.0</span></span>  |<span data-ttu-id="b426a-146">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b426a-146">WMF 5.1</span></span> |<span data-ttu-id="b426a-147">WMF 5,1 (wersja zapoznawcza programu Windows Server w wersji zapoznawczej 17090)</span><span class="sxs-lookup"><span data-stu-id="b426a-147">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="b426a-148">MDB</span><span class="sxs-lookup"><span data-stu-id="b426a-148">MDB</span></span>     |<span data-ttu-id="b426a-149">ESENT (domyślnie), MDB</span><span class="sxs-lookup"><span data-stu-id="b426a-149">ESENT (Default), MDB</span></span> |<span data-ttu-id="b426a-150">ESENT (domyślnie), MDB</span><span class="sxs-lookup"><span data-stu-id="b426a-150">ESENT (Default), MDB</span></span>|<span data-ttu-id="b426a-151">ESENT (domyślnie), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="b426a-151">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="b426a-152">Począwszy od wersji 17090 wersji zapoznawczej programu [Windows Server](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server jest obsługiwaną opcją dla usługi ściągania (Windows Feature *DSC-Service*).</span><span class="sxs-lookup"><span data-stu-id="b426a-152">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="b426a-153">Zapewnia to nową opcję skalowania dużych środowisk DSC, które nie zostały zmigrowane do [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="b426a-153">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="b426a-154">Obsługa SQL Server nie zostanie dodana do poprzednich wersji programu WMF 5,1 (lub starszych) i będzie dostępna tylko w systemie Windows Server w wersji większej niż lub równej 17090.</span><span class="sxs-lookup"><span data-stu-id="b426a-154">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="b426a-155">Aby skonfigurować serwer ściągania tak, aby używał SQL Server , należy ustawić element `$true` na i SqlConnectionString na prawidłowe parametry połączenia SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b426a-155">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="b426a-156">Aby uzyskać więcej informacji, zobacz [Parametry połączenia SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="b426a-156">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="b426a-157">Aby zapoznać się z przykładem konfiguracji SQL Server z **xDscWebService**, najpierw Przeczytaj [przy użyciu zasobu xDscWebService](#using-the-xdscwebservice-resource) , a następnie przejrzyj [Sample_xDscWebServiceRegistration_UseSQLProvider. ps1 w serwisie GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="b426a-157">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="b426a-158">Korzystanie z zasobu xDscWebService</span><span class="sxs-lookup"><span data-stu-id="b426a-158">Using the xDscWebService resource</span></span>

<span data-ttu-id="b426a-159">Najprostszym sposobem skonfigurowania serwera ściągania sieci Web jest użycie zasobu **xDscWebService** znajdującego się w module **xPSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="b426a-159">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="b426a-160">Poniższe kroki wyjaśniają, jak używać zasobu w konfiguracji, która konfiguruje usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b426a-160">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="b426a-161">Wywołaj polecenie cmdlet [Install-module](/powershell/module/PowershellGet/Install-Module) , aby zainstalować moduł **xPSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="b426a-161">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>
   > [!NOTE]
   > <span data-ttu-id="b426a-162">Polecenie **Install-module** jest dołączone do modułu **PowerShellGet** , który jest zawarty w programie PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="b426a-162">**Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b426a-163">Moduł **PowerShellGet** dla programu PowerShell 3,0 i 4,0 można pobrać na stronie [PackageManagement programu PowerShell w wersji](https://www.microsoft.com/en-us/download/details.aspx?id=49186)zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="b426a-163">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
2. <span data-ttu-id="b426a-164">Pobierz certyfikat protokołu SSL dla serwera ściągania DSC z zaufanego urzędu certyfikacji w ramach organizacji lub urzędu publicznego.</span><span class="sxs-lookup"><span data-stu-id="b426a-164">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="b426a-165">Certyfikat otrzymany od urzędu jest zwykle w formacie PFX.</span><span class="sxs-lookup"><span data-stu-id="b426a-165">The certificate received from the authority is usually in the PFX format.</span></span>
3. <span data-ttu-id="b426a-166">Zainstaluj certyfikat w węźle, który będzie serwerem ściągania DSC w domyślnej lokalizacji, która powinna być `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="b426a-166">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="b426a-167">Zanotuj odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="b426a-167">Make a note of the certificate thumbprint.</span></span>
4. <span data-ttu-id="b426a-168">Wybierz identyfikator GUID, który ma być używany jako klucz rejestracji.</span><span class="sxs-lookup"><span data-stu-id="b426a-168">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="b426a-169">Aby wygenerować go przy użyciu programu PowerShell, wprowadź następujące w wierszu polecenia PS i naciśnij `[guid]::newGuid()` klawisz `New-Guid`ENTER: lub.</span><span class="sxs-lookup"><span data-stu-id="b426a-169">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="b426a-170">Ten klucz będzie używany przez węzły klienta jako klucz współużytkowany do uwierzytelniania podczas rejestracji.</span><span class="sxs-lookup"><span data-stu-id="b426a-170">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="b426a-171">Aby uzyskać więcej informacji, zobacz sekcję klucz rejestracji poniżej.</span><span class="sxs-lookup"><span data-stu-id="b426a-171">For more information, see the Registration Key section below.</span></span>
5. <span data-ttu-id="b426a-172">W programie PowerShell ISE Uruchom (F5) następujący skrypt konfiguracyjny (zawarty w folderze przykłady modułu **xPSDesiredStateConfiguration** jako `Sample_xDscWebServiceRegistration.ps1`).</span><span class="sxs-lookup"><span data-stu-id="b426a-172">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`).</span></span> <span data-ttu-id="b426a-173">Ten skrypt konfiguruje serwer ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-173">This script sets up the pull server.</span></span>

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

6. <span data-ttu-id="b426a-174">Uruchom konfigurację, przekazując odcisk palca certyfikatu SSL jako parametr **certificateThumbPrint** i klucz rejestracji identyfikatora GUID jako parametr **RegistrationKey** :</span><span class="sxs-lookup"><span data-stu-id="b426a-174">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="b426a-175">Klucz rejestracji</span><span class="sxs-lookup"><span data-stu-id="b426a-175">Registration Key</span></span>

<span data-ttu-id="b426a-176">Aby umożliwić węzłom klienckim zarejestrowanie się na serwerze, tak aby mogły używać nazw konfiguracji zamiast identyfikatora konfiguracji, klucz rejestracji utworzony przez powyższą konfigurację jest zapisywany w pliku o nazwie `RegistrationKeys.txt` w. `C:\Program Files\WindowsPowerShell\DscService`</span><span class="sxs-lookup"><span data-stu-id="b426a-176">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="b426a-177">Klucz rejestracji działa jako wspólny klucz tajny używany podczas wstępnej rejestracji przez klienta z serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-177">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="b426a-178">Klient wygeneruje certyfikat z podpisem własnym, który jest używany do jednoznacznego uwierzytelniania na serwerze ściągania po pomyślnym zakończeniu rejestracji.</span><span class="sxs-lookup"><span data-stu-id="b426a-178">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="b426a-179">Odcisk palca tego certyfikatu jest przechowywany lokalnie i skojarzony z adresem URL serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-179">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="b426a-180">Klucze rejestracji nie są obsługiwane w programie PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="b426a-180">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="b426a-181">W celu skonfigurowania węzła do uwierzytelniania przy użyciu serwera ściągania klucz rejestracji musi znajdować się w konfiguracji z dowolnego węzła docelowego, który zostanie zarejestrowany na tym serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-181">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="b426a-182">Należy pamiętać, że **RegistrationKey** w konfiguracji poniżej jest usuwany po pomyślnym zarejestrowaniu maszyny docelowej i że wartość musi być zgodna z wartością przechowywaną `RegistrationKeys.txt` w pliku na serwerze ściągania (" 140a952b-b9d6-406B-b416-e0f759c9c0e4 "w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="b426a-182">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="b426a-183">Należy zawsze traktować bezpieczną wartość klucza rejestracji, ponieważ wiedzą, że każdy komputer docelowy może zarejestrować się na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-183">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> <span data-ttu-id="b426a-184">Sekcja **ReportServerWeb** umożliwia wysyłanie danych raportowania do serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-184">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="b426a-185">Brak właściwości **ConfigurationID** w pliku konfiguracji niejawnie oznacza, że serwer ściągania obsługuje wersję v2 protokołu serwera ściągania, więc wymagana jest rejestracja wstępna.</span><span class="sxs-lookup"><span data-stu-id="b426a-185">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="b426a-186">Z drugiej strony, obecność **ConfigurationID** oznacza, że używana jest wersja v1 protokołu serwera ściągania i nie ma żadnego przetwarzania rejestracji.</span><span class="sxs-lookup"><span data-stu-id="b426a-186">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="b426a-187">W scenariuszu WYPYCHANia usterka istnieje w bieżącej wersji, która wymaga zdefiniowania w pliku konfiguracji właściwości ConfigurationID dla węzłów, które nigdy nie zostały zarejestrowane na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-187">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="b426a-188">Spowoduje to wymuszenie protokołu serwera ściągania V1 i uniknięcie komunikatów o niepowodzeniu rejestracji.</span><span class="sxs-lookup"><span data-stu-id="b426a-188">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="b426a-189">Umieszczanie konfiguracji i zasobów</span><span class="sxs-lookup"><span data-stu-id="b426a-189">Placing configurations and resources</span></span>

<span data-ttu-id="b426a-190">Po zakończeniu instalacji serwera ściągania foldery zdefiniowane przez właściwości **ConfigurationPath** i **ModulePath** w konfiguracji serwera ściągania są miejscem, w którym zostaną umieszczone moduły i konfiguracje, które będą dostępne dla węzłów docelowych do ściągnięcia.</span><span class="sxs-lookup"><span data-stu-id="b426a-190">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="b426a-191">Te pliki muszą być w określonym formacie, aby serwer ściągania mógł prawidłowo je przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="b426a-191">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="b426a-192">Format pakietu modułu zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="b426a-192">DSC resource module package format</span></span>

<span data-ttu-id="b426a-193">Każdy moduł zasobów musi być spakowany i nazwany zgodnie z poniższym wzorcem `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="b426a-193">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="b426a-194">Na przykład moduł o nazwie xWebAdminstration z wersją modułu 3.1.2.0 powinien mieć nazwę `xWebAdministration_3.1.2.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="b426a-194">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span>
<span data-ttu-id="b426a-195">Każda wersja modułu musi być zawarta w pojedynczym pliku zip.</span><span class="sxs-lookup"><span data-stu-id="b426a-195">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="b426a-196">Ponieważ w każdym pliku zip istnieje tylko jedna wersja zasobu, format modułu dodany w programie WMF 5,0 z obsługą wielu wersji modułów w jednym katalogu nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="b426a-196">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="b426a-197">Oznacza to, że przed spakowaniem modułów zasobów DSC do użycia z serwerem ściągania należy wprowadzić małą zmianę w strukturze katalogów.</span><span class="sxs-lookup"><span data-stu-id="b426a-197">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="b426a-198">Domyślny format modułów zawierających zasób DSC w programie WMF 5,0 to `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="b426a-198">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="b426a-199">Przed spakowaniem na serwer ściągania Usuń folder **{module Version}** , aby ścieżka się popełniła `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="b426a-199">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="b426a-200">W przypadku tej zmiany należy umieścić folder zip zgodnie z powyższym opisem i umieocić te pliki zip w folderze **ModulePath** .</span><span class="sxs-lookup"><span data-stu-id="b426a-200">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="b426a-201">Użyj `New-DscChecksum {module zip file}` polecenia, aby utworzyć plik sumy kontrolnej dla nowo dodanego modułu.</span><span class="sxs-lookup"><span data-stu-id="b426a-201">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="b426a-202">Format MOF konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b426a-202">Configuration MOF format</span></span>

<span data-ttu-id="b426a-203">Plik MOF konfiguracji musi być sparowany z plikiem sum kontrolnych tak, aby LCM w węźle docelowym mógł sprawdzić poprawność konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b426a-203">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="b426a-204">Aby utworzyć sumę kontrolną, wywołaj polecenie cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) .</span><span class="sxs-lookup"><span data-stu-id="b426a-204">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="b426a-205">Polecenie cmdlet przyjmuje parametr **Path** , który określa folder, w którym znajduje się plik MOF konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b426a-205">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="b426a-206">Polecenie cmdlet tworzy plik sumy kontrolnej `ConfigurationMOFName.mof.checksum`o nazwie `ConfigurationMOFName` , gdzie jest nazwą pliku MOF konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b426a-206">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="b426a-207">Jeśli w określonym folderze znajduje się więcej niż jeden plik MOF konfiguracji, zostanie utworzona suma kontrolna dla każdej konfiguracji w folderze.</span><span class="sxs-lookup"><span data-stu-id="b426a-207">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="b426a-208">Umieść pliki MOF i skojarzone z nimi pliki sum kontrolnych w folderze **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="b426a-208">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="b426a-209">Jeśli plik MOF konfiguracji zostanie zmieniony w dowolny sposób, należy również ponownie utworzyć plik sum kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="b426a-209">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="b426a-210">Narzędzi</span><span class="sxs-lookup"><span data-stu-id="b426a-210">Tooling</span></span>

<span data-ttu-id="b426a-211">W celu ułatwienia konfigurowania, weryfikowania i zarządzania serwerem ściągania są dostępne następujące narzędzia jako przykłady w najnowszej wersji modułu xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="b426a-211">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="b426a-212">Moduł, który będzie pomocny przy pakowaniu modułów zasobów DSC i plików konfiguracji do użycia na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-212">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="b426a-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="b426a-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span>
   <span data-ttu-id="b426a-214">Poniższe przykłady:</span><span class="sxs-lookup"><span data-stu-id="b426a-214">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="b426a-215">Skrypt, który sprawdza poprawność serwera ściągania, jest poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="b426a-215">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="b426a-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="b426a-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="b426a-217">Rozwiązania społeczności dla usługi ściągania</span><span class="sxs-lookup"><span data-stu-id="b426a-217">Community Solutions for Pull Service</span></span>

<span data-ttu-id="b426a-218">Społeczność DSC utworzyła wiele rozwiązań do wdrożenia protokołu usługi ściągania.</span><span class="sxs-lookup"><span data-stu-id="b426a-218">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="b426a-219">W przypadku środowisk lokalnych te oferty oferują możliwości usługi ściągania i możliwość współtworzenia do społeczności użytkowników przy użyciu ulepszeń przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="b426a-219">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="b426a-220">Tug</span><span class="sxs-lookup"><span data-stu-id="b426a-220">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="b426a-221">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="b426a-221">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="b426a-222">Konfiguracja klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="b426a-222">Pull client configuration</span></span>

<span data-ttu-id="b426a-223">W poniższych tematach opisano szczegółowo konfigurację klientów ściągania:</span><span class="sxs-lookup"><span data-stu-id="b426a-223">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="b426a-224">Konfigurowanie klienta ściągania DSC przy użyciu identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b426a-224">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="b426a-225">Konfigurowanie klienta ściągania DSC przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b426a-225">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="b426a-226">Konfiguracje częściowe</span><span class="sxs-lookup"><span data-stu-id="b426a-226">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="b426a-227">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b426a-227">See also</span></span>

- [<span data-ttu-id="b426a-228">Przegląd konfiguracji żądanego stanu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b426a-228">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="b426a-229">Realizacja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b426a-229">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="b426a-230">Używanie serwera raportów platformy DSC</span><span class="sxs-lookup"><span data-stu-id="b426a-230">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="b426a-231">[[MS-DSCPM]: Protokół ściągania konfiguracji żądanego stanu](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="b426a-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="b426a-232">[[MS-DSCPM]: Konfiguracja żądanego stanu Errata modelu ściągania](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="b426a-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
