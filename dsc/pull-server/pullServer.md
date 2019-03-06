---
ms.date: 03/04/2019
keywords: DSC, powershell, konfiguracja, ustawienia
title: Usługa ściągania platformy DSC
ms.openlocfilehash: 64c22bc021666026ae58a4c4fb4e3d31b25bae5c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429962"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="8be19-103">Usługa ściągania Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="8be19-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8be19-104">Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno.</span><span class="sxs-lookup"><span data-stu-id="8be19-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="8be19-105">Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="8be19-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="8be19-106">Local Configuration Manager mogą centralnie zarządzane przez rozwiązanie usługi ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-106">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="8be19-107">Korzystając z tego podejścia, węzeł, który jest zarządzany jest zarejestrowana przy użyciu usługi i przypisany konfiguracji w ustawieniach LCM.</span><span class="sxs-lookup"><span data-stu-id="8be19-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="8be19-108">Konfiguracji i wszystkie zasoby DSC, wymagane jako zależności w konfiguracji są pobierane do maszyny i używane przez LCM do zarządzania konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="8be19-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="8be19-109">Informacje o stanie maszyny zarządzany jest przekazywany do usługi raportowania.</span><span class="sxs-lookup"><span data-stu-id="8be19-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="8be19-110">Takie podejście jest określany jako "Usługa pull".</span><span class="sxs-lookup"><span data-stu-id="8be19-110">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="8be19-111">Bieżące opcje dla usługi ściągania obejmują:</span><span class="sxs-lookup"><span data-stu-id="8be19-111">The current options for pull service include:</span></span>

- <span data-ttu-id="8be19-112">Usługa Azure Automation Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="8be19-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="8be19-113">Usługa ściągania, w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="8be19-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="8be19-114">Obsługiwane rozwiązań typu open source społeczności</span><span class="sxs-lookup"><span data-stu-id="8be19-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="8be19-115">Udział SMB</span><span class="sxs-lookup"><span data-stu-id="8be19-115">An SMB share</span></span>

<span data-ttu-id="8be19-116">**Zalecanym rozwiązaniem**, a opcja najbardziej funkcje dostępne, jest [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="8be19-116">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="8be19-117">Usługi platformy Azure można zarządzać węzłów lokalnych w centrach danych prywatnych lub w chmurach publicznych, takich jak Azure i AWS.</span><span class="sxs-lookup"><span data-stu-id="8be19-117">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="8be19-118">Prywatne środowiska, w której serwery bezpośrednio nie może połączyć się z Internetem, należy rozważyć ograniczenie ruchu wychodzącego do tylko opublikowane zakres adresów IP platformy Azure (zobacz [zakresów adresów IP centrum danych Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="8be19-118">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="8be19-119">Funkcje usługi online, które nie są obecnie dostępne w usługi ściągania w systemie Windows Server:</span><span class="sxs-lookup"><span data-stu-id="8be19-119">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="8be19-120">Wszystkie dane są szyfrowane podczas przesyłania i magazynowanych</span><span class="sxs-lookup"><span data-stu-id="8be19-120">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="8be19-121">Certyfikaty klienta są tworzone i zarządzane automatycznie</span><span class="sxs-lookup"><span data-stu-id="8be19-121">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="8be19-122">Wpisy tajne przechowywane centralnie zarządzanie [haseł lub poświadczeń](/azure/automation/automation-credentials), lub [zmienne](/azure/automation/automation-variables) takich jak nazwy serwera lub parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="8be19-122">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="8be19-123">Centralnie Zarządzaj węzłem [LCM konfiguracji](../managing-nodes/metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="8be19-123">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="8be19-124">Centralnie Przypisz konfiguracje do węzłów klienta</span><span class="sxs-lookup"><span data-stu-id="8be19-124">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="8be19-125">Konfiguracja wydania zmienia się na "canary groups" do testowania przed dotarciem do produkcji</span><span class="sxs-lookup"><span data-stu-id="8be19-125">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="8be19-126">Graficzny raportowania</span><span class="sxs-lookup"><span data-stu-id="8be19-126">Graphical reporting</span></span>
  - <span data-ttu-id="8be19-127">Szczegóły stanu na poziomie szczegółowości zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="8be19-127">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="8be19-128">Pełne komunikaty z komputerów klienckich w celu rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="8be19-128">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="8be19-129">[Integracja z usługą Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) alertów, automatycznych zadań Android/aplikacji dla systemu iOS raportowania i zgłaszania alertów</span><span class="sxs-lookup"><span data-stu-id="8be19-129">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="8be19-130">Usługa ściągania DSC w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="8be19-130">DSC pull service in Windows Server</span></span>

<span data-ttu-id="8be19-131">Istnieje możliwość konfigurowania usługi ściągania, aby uruchomić w systemie Windows Server.</span><span class="sxs-lookup"><span data-stu-id="8be19-131">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="8be19-132">Należy pamiętać, że rozwiązania usługi ściągania, które są zawarte w systemie Windows Server zawiera tylko możliwości przechowywania konfiguracje/modules do pobrania i przechwytywania danych raportu w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8be19-132">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="8be19-133">Nie obejmuje wiele możliwości oferowanych przez usługę w systemie Azure, a zatem nie jest dobrym narzędziem do oceny, jak usługa będzie używana.</span><span class="sxs-lookup"><span data-stu-id="8be19-133">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="8be19-134">Usługa ściągania oferowanych w systemie Windows Server jest usługi sieci web w usługach IIS, który używa interfejsu OData, aby udostępnić pliki konfiguracji DSC węzły docelowe w przypadku tych węzłów, zadaj je.</span><span class="sxs-lookup"><span data-stu-id="8be19-134">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="8be19-135">Wymagania dotyczące korzystania z serwera ściągania:</span><span class="sxs-lookup"><span data-stu-id="8be19-135">Requirements for using a pull server:</span></span>

- <span data-ttu-id="8be19-136">Serwer z systemem:</span><span class="sxs-lookup"><span data-stu-id="8be19-136">A server running:</span></span>
  - <span data-ttu-id="8be19-137">WMF/PowerShell 4.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="8be19-137">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="8be19-138">Rola serwera IIS</span><span class="sxs-lookup"><span data-stu-id="8be19-138">IIS server role</span></span>
  - <span data-ttu-id="8be19-139">DSC Service</span><span class="sxs-lookup"><span data-stu-id="8be19-139">DSC Service</span></span>
- <span data-ttu-id="8be19-140">W idealnym przypadku niektóre oznacza, że generowania certyfikatu, aby zabezpieczyć poświadczenia przekazywane do lokalnego Configuration Manager (LCM) na węzłach docelowych</span><span class="sxs-lookup"><span data-stu-id="8be19-140">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="8be19-141">Najlepszym sposobem na konfigurowanie systemu Windows Server do usługi ściągania hosta jest korzysta z konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="8be19-141">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="8be19-142">Przykładowy skrypt znajduje się poniżej.</span><span class="sxs-lookup"><span data-stu-id="8be19-142">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="8be19-143">Systemy obsługiwanych baz danych</span><span class="sxs-lookup"><span data-stu-id="8be19-143">Supported database systems</span></span>

|<span data-ttu-id="8be19-144">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="8be19-144">WMF 4.0</span></span>   |<span data-ttu-id="8be19-145">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="8be19-145">WMF 5.0</span></span>  |<span data-ttu-id="8be19-146">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="8be19-146">WMF 5.1</span></span> |<span data-ttu-id="8be19-147">WMF 5.1 (system Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="8be19-147">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="8be19-148">MDB</span><span class="sxs-lookup"><span data-stu-id="8be19-148">MDB</span></span>     |<span data-ttu-id="8be19-149">ESENT (ustawienie domyślne), MDB</span><span class="sxs-lookup"><span data-stu-id="8be19-149">ESENT (Default), MDB</span></span> |<span data-ttu-id="8be19-150">ESENT (ustawienie domyślne), MDB</span><span class="sxs-lookup"><span data-stu-id="8be19-150">ESENT (Default), MDB</span></span>|<span data-ttu-id="8be19-151">ESENT (ustawienie domyślne), programu SQL Server MDB</span><span class="sxs-lookup"><span data-stu-id="8be19-151">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="8be19-152">Począwszy od wersji 17090 z [systemu Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server jest obsługiwaną opcją dla usługi ściągania (funkcja Windows *usługi DSC*).</span><span class="sxs-lookup"><span data-stu-id="8be19-152">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="8be19-153">Zapewnia to nowa opcja skalowania dużych środowiskach DSC, które nie zostały przeniesione do [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="8be19-153">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="8be19-154">**Uwaga**: Obsługa programu SQL Server nie zostanie dodany do poprzednich wersji programu WMF 5.1 (lub starszy) i jest on dostępny w wersjach systemu Windows Server, większa niż lub równa 17090 tylko.</span><span class="sxs-lookup"><span data-stu-id="8be19-154">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="8be19-155">Aby skonfigurować serwer ściągania używać programu SQL Server, należy ustawić **SqlProvider** do `$true` i **SqlConnectionString** na prawidłowe parametry połączenia programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8be19-155">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="8be19-156">Aby uzyskać więcej informacji, zobacz [ciągi połączeń klient SQL](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="8be19-156">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="8be19-157">Przykład konfiguracji programu SQL Server za pomocą **xDscWebService**, najpierw przeczytać artykuł [przy użyciu zasobów xDscWebService](#using-the-xdscwebservice-resource) a następnie przejrzyj [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 w serwisie GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="8be19-157">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="8be19-158">Przy użyciu zasobów xDscWebService</span><span class="sxs-lookup"><span data-stu-id="8be19-158">Using the xDscWebService resource</span></span>

<span data-ttu-id="8be19-159">Najprostszym sposobem skonfigurowania internetowego serwera ściągania jest użycie **xDscWebService** zasobu, objęte **xPSDesiredStateConfiguration** modułu.</span><span class="sxs-lookup"><span data-stu-id="8be19-159">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="8be19-160">Poniższe kroki wyjaśniają jak używać zasobów w konfiguracji, który konfiguruje usługę sieci web.</span><span class="sxs-lookup"><span data-stu-id="8be19-160">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="8be19-161">Wywołaj [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby zainstalować **xPSDesiredStateConfiguration** modułu.</span><span class="sxs-lookup"><span data-stu-id="8be19-161">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>
   > [!NOTE]
   > <span data-ttu-id="8be19-162">**Install-Module** znajduje się w **PowerShellGet** moduł, który znajduje się w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="8be19-162">**Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="8be19-163">Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [Podgląd modułów programu PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="8be19-163">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
2. <span data-ttu-id="8be19-164">Pobieranie certyfikatu SSL dla serwera ściągania DSC od zaufanego urzędu certyfikacji, albo w ramach organizacji lub publicznego urzędu.</span><span class="sxs-lookup"><span data-stu-id="8be19-164">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="8be19-165">Certyfikat odebrany od urzędu zwykle jest w formacie PFX.</span><span class="sxs-lookup"><span data-stu-id="8be19-165">The certificate received from the authority is usually in the PFX format.</span></span>
3. <span data-ttu-id="8be19-166">Zainstaluj certyfikat na węzeł, który będzie serwerem ściągania DSC w lokalizacji domyślnej, która powinna być `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="8be19-166">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="8be19-167">Zanotuj odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8be19-167">Make a note of the certificate thumbprint.</span></span>
4. <span data-ttu-id="8be19-168">Wybierz identyfikator GUID, który ma być używany jako klucz rejestracji.</span><span class="sxs-lookup"><span data-stu-id="8be19-168">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="8be19-169">Aby wygenerować za pomocą programu PowerShell wprowadź następujące polecenie w wierszu PS, a następnie naciśnij klawisz enter: ` [guid]::newGuid()` lub `New-Guid`.</span><span class="sxs-lookup"><span data-stu-id="8be19-169">To generate one using PowerShell enter the following at the PS prompt and press enter: ` [guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="8be19-170">Ten klucz będzie używany przez węzły klienta jako klucza wstępnego, do uwierzytelniania podczas rejestracji.</span><span class="sxs-lookup"><span data-stu-id="8be19-170">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="8be19-171">Aby uzyskać więcej informacji zobacz poniżej sekcję klucza rejestracji.</span><span class="sxs-lookup"><span data-stu-id="8be19-171">For more information, see the Registration Key section below.</span></span>
5. <span data-ttu-id="8be19-172">W środowisku PowerShell ISE Uruchom (F5) poniższy skrypt konfiguracji (zawarte w folderze przykłady **xPSDesiredStateConfiguration** modułu jako `Sample_xDscWebServiceRegistration.ps1`).</span><span class="sxs-lookup"><span data-stu-id="8be19-172">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`).</span></span> <span data-ttu-id="8be19-173">Ten skrypt konfiguruje serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-173">This script sets up the pull server.</span></span>

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

6. <span data-ttu-id="8be19-174">Uruchom konfigurację, przekazując odcisk palca certyfikatu SSL jako **certificateThumbPrint** parametr i rejestracji identyfikator GUID klucza jako **RegistrationKey** parametru:</span><span class="sxs-lookup"><span data-stu-id="8be19-174">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="8be19-175">Klucz rejestracji</span><span class="sxs-lookup"><span data-stu-id="8be19-175">Registration Key</span></span>

<span data-ttu-id="8be19-176">Aby zezwolić na węzły, które można zarejestrować na serwerze, tak aby używały nazwy konfiguracji zamiast Identyfikatora konfiguracji klienta, klucza rejestracji, który został utworzony za pomocą powyższych konfiguracji jest zapisywany w pliku o nazwie `RegistrationKeys.txt` w `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="8be19-176">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="8be19-177">Klucz rejestracji działa jako wspólny klucz tajny, używane podczas wstępnej rejestracji przez klienta z serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-177">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="8be19-178">Klient wygeneruje certyfikat z podpisem własnym, który jest używany do jednoznacznego uwierzytelniania na serwerze ściągania po pomyślnym zakończeniu rejestracji.</span><span class="sxs-lookup"><span data-stu-id="8be19-178">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="8be19-179">Odcisk palca certyfikatu jest przechowywana lokalnie i skojarzone z adresem URL serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-179">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="8be19-180">Klucze rejestracji nie są obsługiwane w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="8be19-180">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="8be19-181">W celu skonfigurowania węzła do uwierzytelniania za pomocą serwera ściągania, klucz rejestracji musi być w metaconfiguration dla dowolnego węzła docelowego, który będzie zarejestrowanie z tym serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-181">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="8be19-182">Należy pamiętać, że **RegistrationKey** w metaconfiguration poniżej zostanie usunięty po pomyślnie zarejestrowała maszynie docelowej, a wartość musi być zgodna wartość przechowywaną w `RegistrationKeys.txt` pliku na serwerze ściągania (" 140a952b-b9d6-406b-b416-e0f759c9c0e4 "w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="8be19-182">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="8be19-183">Jest zawsze traktowany wartość klucza rejestracji bezpieczne, ponieważ wiedząc o tym pozwala na dowolnej maszynie docelowej, można zarejestrować za pomocą serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-183">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="8be19-184">**ReportServerWeb** sekcja umożliwia raportowanie danych, które mają być wysyłane do serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-184">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="8be19-185">Brak **ConfigurationID** właściwości w pliku metaconfiguration niejawnie oznacza, że tego serwera ściągania obsługuje protokół serwera ściągania w wersji V2, więc wstępnej rejestracji jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="8be19-185">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="8be19-186">Z kolei obecność **ConfigurationID** oznacza, że jest używany protokół serwera ściągania w wersji V1 jest nie przetwarzania rejestracji.</span><span class="sxs-lookup"><span data-stu-id="8be19-186">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="8be19-187">W przypadku scenariusza WYPYCHANIA usterkę istnieje w bieżącej wersji, która sprawia, że konieczne jest określenie właściwości ConfigurationID w pliku metaconfiguration dla węzłów, które nigdy nie zostały zarejestrowane przy użyciu serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-187">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="8be19-188">Spowoduje to wymusić protokołu serwera ściągania V1 i uniknąć komunikaty o błędach rejestracji.</span><span class="sxs-lookup"><span data-stu-id="8be19-188">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="8be19-189">Wprowadzenie do konfiguracji i zasobów</span><span class="sxs-lookup"><span data-stu-id="8be19-189">Placing configurations and resources</span></span>

<span data-ttu-id="8be19-190">Po ściągnięcia kończy instalacji serwera, folderów, określone przez **ConfigurationPath** i **ModulePath** właściwości w konfiguracji serwera ściągania są, gdzie zostaną umieszczone modułów i konfiguracji który będzie dostępny dla węzły docelowe ściągnąć.</span><span class="sxs-lookup"><span data-stu-id="8be19-190">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="8be19-191">Te pliki muszą znajdować się w określonym formacie w kolejności dla serwera ściągania poprawnie przetworzyć je.</span><span class="sxs-lookup"><span data-stu-id="8be19-191">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="8be19-192">Format pakietu modułu zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="8be19-192">DSC resource module package format</span></span>

<span data-ttu-id="8be19-193">Każdy moduł zasobów musi być spakowane i nazwanych zgodnie z następującym wzorcem `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="8be19-193">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="8be19-194">Na przykład, czy nazwany moduł o nazwie xWebAdminstration przy użyciu wersji modułu 3.1.2.0 `xWebAdministration_3.2.1.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="8be19-194">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named `xWebAdministration_3.2.1.0.zip`.</span></span>
<span data-ttu-id="8be19-195">Każda wersja modułu musi być zawarty w pliku zip jednego.</span><span class="sxs-lookup"><span data-stu-id="8be19-195">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="8be19-196">Ponieważ istnieje tylko jedną wersję zasobu w każdym pliku zip, format modułu, dodane w programie WMF 5.0 z obsługą wielu wersji modułu w pojedynczym katalogu nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="8be19-196">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="8be19-197">Oznacza to, że przed pakowaniu modułów zasoby DSC do użytku z serwera ściągania należy wprowadź niewielką zmianę do struktury katalogu.</span><span class="sxs-lookup"><span data-stu-id="8be19-197">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="8be19-198">Domyślny format modułów zawierających zasobów DSC w programie WMF 5.0 jest `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="8be19-198">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="8be19-199">Przed pakowania dla serwera ściągania, Usuń **{wersja modułu}** folderu, tak aby stał się ścieżkę `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="8be19-199">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="8be19-200">Dzięki tej zmianie folder zip zgodnie z powyższym opisem i umieścić te pliki zip w **ModulePath** folderu.</span><span class="sxs-lookup"><span data-stu-id="8be19-200">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="8be19-201">Użyj `New-DscChecksum {module zip file}` utworzyć sumy kontrolnej pliku dla nowo dodanym modułem.</span><span class="sxs-lookup"><span data-stu-id="8be19-201">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="8be19-202">Format pliku MOF konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8be19-202">Configuration MOF format</span></span>

<span data-ttu-id="8be19-203">Pliku MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w węźle docelowym można zweryfikować jej konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8be19-203">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="8be19-204">Aby utworzyć sumy kontrolnej, wywołaj [New DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8be19-204">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="8be19-205">Polecenie cmdlet pobiera **ścieżki** parametr, który określa folder, w którym znajduje się plik MOF konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8be19-205">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="8be19-206">Polecenie cmdlet tworzy sumy kontrolnej pliku o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8be19-206">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="8be19-207">Jeśli istnieje więcej niż jedną konfigurację pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.</span><span class="sxs-lookup"><span data-stu-id="8be19-207">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="8be19-208">Umieść pliki MOF i skojarzone sumy kontrolnej plików w **ConfigurationPath** folderu.</span><span class="sxs-lookup"><span data-stu-id="8be19-208">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="8be19-209">Jeśli zmienisz pliku MOF konfiguracji w jakikolwiek sposób, należy odtworzyć pliku sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="8be19-209">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="8be19-210">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="8be19-210">Tooling</span></span>

<span data-ttu-id="8be19-211">Aby uzupełnić ustawienie, sprawdzanie poprawności i zarządzanie nimi było prostsze, serwerze ściągania następujące narzędzia są dołączone jako przykłady w najnowszej wersji modułu xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="8be19-211">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="8be19-212">Moduł, który pomoże pakowanie modułów zasoby DSC oraz pliki konfiguracji do użycia na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-212">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="8be19-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="8be19-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span>
   <span data-ttu-id="8be19-214">Poniższe przykłady:</span><span class="sxs-lookup"><span data-stu-id="8be19-214">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="8be19-215">Skrypt, który sprawdza poprawność serwera ściągania jest poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="8be19-215">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="8be19-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="8be19-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="8be19-217">Rozwiązania społeczności dla usługi ściągania</span><span class="sxs-lookup"><span data-stu-id="8be19-217">Community Solutions for Pull Service</span></span>

<span data-ttu-id="8be19-218">Społeczność DSC ma utworzonych wiele rozwiązań, aby zaimplementować Protokół usługi ściągania.</span><span class="sxs-lookup"><span data-stu-id="8be19-218">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="8be19-219">W środowiskach lokalnych oferują one możliwości usługi ściągania oraz możliwość współtworzenia społeczności ulepszeń przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="8be19-219">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="8be19-220">Holownik</span><span class="sxs-lookup"><span data-stu-id="8be19-220">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="8be19-221">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="8be19-221">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="8be19-222">Ściąganie konfiguracji klienta</span><span class="sxs-lookup"><span data-stu-id="8be19-222">Pull client configuration</span></span>

<span data-ttu-id="8be19-223">Konfigurowanie klientów ściągnięcia szczegółowo można znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="8be19-223">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="8be19-224">Konfigurowanie klienta ściągania DSC przy użyciu Identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8be19-224">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="8be19-225">Konfigurowanie klienta ściągania DSC przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8be19-225">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="8be19-226">Konfiguracje częściowe</span><span class="sxs-lookup"><span data-stu-id="8be19-226">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="8be19-227">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8be19-227">See also</span></span>

- [<span data-ttu-id="8be19-228">Program Windows PowerShell Desired State Configuration — omówienie</span><span class="sxs-lookup"><span data-stu-id="8be19-228">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="8be19-229">Realizacja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8be19-229">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="8be19-230">Używanie serwera raportów platformy DSC</span><span class="sxs-lookup"><span data-stu-id="8be19-230">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="8be19-231">[[MS-DSCPM]: Desired State Configuration protokołu modelu ściągania](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="8be19-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="8be19-232">[[MS-DSCPM]: Desired State Configuration Errata protokołu modelu ściągania](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="8be19-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
