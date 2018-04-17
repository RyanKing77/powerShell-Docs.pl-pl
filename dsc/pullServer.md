---
ms.date: 04/11/2018
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Usługa ściągania platformy DSC
ms.openlocfilehash: 61b4c0e9cfe1d1d7539cd32da35d2fe50da4b0e3
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="dcd7b-103">Usługa replikacji ściąganej konfiguracji żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="dcd7b-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="dcd7b-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dcd7b-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dcd7b-105">Ściągnięcia serwera (funkcja Windows *DSC usługi*) jest obsługiwanych składników systemu Windows Server jednak nie ma żadnych planów oferować nowe funkcje lub możliwości.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="dcd7b-106">Zaleca się rozpocząć przechodzenie zarządzanych klientów do [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started) (w tym funkcji poza ściągnięcia serwera w systemie Windows Server) lub jednego z rozwiązań społeczności wymienionych [tutaj](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="dcd7b-107">Lokalny program Configuration Manager mogą centralnie zarządzane przez rozwiązanie do ściągania usługi.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-107">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="dcd7b-108">Podczas korzystania z tej metody, węzeł, który jest zarządzany jest zarejestrowany za pomocą usługi i przypisany konfigurację w ustawieniach LCM.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-108">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="dcd7b-109">Konfiguracja i wszystkie zasoby DSC, wymagane jako zależności w konfiguracji są pobierane do maszyny i używane przez LCM do zarządzanie konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-109">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="dcd7b-110">Informacje o stanie komputera zarządzanego jest przekazywane do usługi raportowania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-110">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="dcd7b-111">To pojęcie jest określany jako "Usługa ściągania".</span><span class="sxs-lookup"><span data-stu-id="dcd7b-111">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="dcd7b-112">Dla aktualnych opcji ściągania usługi obejmują:</span><span class="sxs-lookup"><span data-stu-id="dcd7b-112">The current options for pull service include:</span></span>

- <span data-ttu-id="dcd7b-113">Usługa konfiguracji stanu pożądanej usługi Automatyzacja Azure</span><span class="sxs-lookup"><span data-stu-id="dcd7b-113">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="dcd7b-114">Usługa replikacji ściąganej w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="dcd7b-114">A pull service running on Windows Server</span></span>
- <span data-ttu-id="dcd7b-115">Społeczność utrzymywane rozwiązania open source</span><span class="sxs-lookup"><span data-stu-id="dcd7b-115">Community maintained open-source solutions</span></span>
- <span data-ttu-id="dcd7b-116">Udział SMB</span><span class="sxs-lookup"><span data-stu-id="dcd7b-116">An SMB share</span></span>

<span data-ttu-id="dcd7b-117">**Zalecane rozwiązanie**, a opcja z najbardziej funkcje dostępne, jest [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-117">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="dcd7b-118">Usługa Azure mogą zarządzać węzłów lokalnie w centrach danych prywatnych lub chmur publicznych, takich jak Azure i usług AWS.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-118">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="dcd7b-119">W środowiskach prywatne, gdzie serwery bezpośrednio nie może połączyć się z Internetem, należy wziąć pod uwagę Ograniczanie ruchu wychodzącego tylko opublikowane zakres IP platformy Azure (zobacz [zakresów IP centrum danych Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-119">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="dcd7b-120">Funkcje usługi online, które nie są obecnie dostępne w usłudze replikacji ściąganej w systemie Windows Server:</span><span class="sxs-lookup"><span data-stu-id="dcd7b-120">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="dcd7b-121">Wszystkie dane są szyfrowane podczas przesyłania i magazynowane</span><span class="sxs-lookup"><span data-stu-id="dcd7b-121">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="dcd7b-122">Certyfikaty klienta są tworzone i zarządzane automatycznie</span><span class="sxs-lookup"><span data-stu-id="dcd7b-122">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="dcd7b-123">Przechowywanie kluczy tajnych centralnego zarządzania [haseł lub poświadczeń](/azure/automation/automation-credentials), lub [zmienne](/azure/automation/automation-variables) takich jak nazwy serwera lub parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="dcd7b-123">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="dcd7b-124">Centralne zarządzanie węzła [LCM konfiguracji](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="dcd7b-124">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="dcd7b-125">Centralnie Przypisz konfiguracje do węzłów klienta</span><span class="sxs-lookup"><span data-stu-id="dcd7b-125">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="dcd7b-126">Zmiany konfiguracji wersji do "grup mozgi" do testowania przed dotarciem do produkcji</span><span class="sxs-lookup"><span data-stu-id="dcd7b-126">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="dcd7b-127">Raportowania graficznego</span><span class="sxs-lookup"><span data-stu-id="dcd7b-127">Graphical reporting</span></span>
  - <span data-ttu-id="dcd7b-128">Szczegóły stanu na poziomie szczegółowości zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="dcd7b-128">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="dcd7b-129">Pełne komunikaty z komputerów klienckich do rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="dcd7b-129">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="dcd7b-130">[Integracja z usługą Analiza dzienników Azure](/azure/automation/automation-dsc-diagnostics) alertów, automatycznych zadań Android/aplikacji systemu iOS dla raportowania i alerty</span><span class="sxs-lookup"><span data-stu-id="dcd7b-130">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="dcd7b-131">Usługa ściągania usługi Konfiguracja DSC w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="dcd7b-131">DSC pull service in Windows Server</span></span>

<span data-ttu-id="dcd7b-132">Istnieje możliwość konfigurowania usługi ściągnięcia do uruchamiania w systemie Windows Server.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-132">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="dcd7b-133">Można wskazać, że rozwiązania usługi ściągania zawarte w systemie Windows Server zawiera tylko możliwości przechowywania moduły konfiguracji do pobrania i przechwytywanie danych raportów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-133">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="dcd7b-134">Nie obejmuje wiele możliwości oferowane przez usługę w systemie Azure i tak nie jest dobrym narzędzia do oceny, czy użycia usługi.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-134">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="dcd7b-135">Usługa replikacji ściąganej oferowanych w systemie Windows Server jest usługi sieci web w usługach IIS, który używa interfejsu OData, aby udostępnić pliki konfiguracji DSC węzły docelowe podczas tych węzłów, poproś o ich.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-135">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="dcd7b-136">Wymagania dotyczące korzystania z serwera ściągania:</span><span class="sxs-lookup"><span data-stu-id="dcd7b-136">Requirements for using a pull server:</span></span>

- <span data-ttu-id="dcd7b-137">Serwer z systemem:</span><span class="sxs-lookup"><span data-stu-id="dcd7b-137">A server running:</span></span>
  - <span data-ttu-id="dcd7b-138">WMF PowerShell 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="dcd7b-138">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="dcd7b-139">Rola serwera IIS</span><span class="sxs-lookup"><span data-stu-id="dcd7b-139">IIS server role</span></span>
  - <span data-ttu-id="dcd7b-140">Usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="dcd7b-140">DSC Service</span></span>
- <span data-ttu-id="dcd7b-141">Najlepiej, jeśli niektóre oznacza generowania certyfikatu, aby zabezpieczyć poświadczenia przekazywane do lokalnego Menedżera konfiguracji (LCM) węzły docelowe</span><span class="sxs-lookup"><span data-stu-id="dcd7b-141">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="dcd7b-142">Najlepszym sposobem konfigurowania systemu Windows Server do usługi replikacji ściąganej hosta jest korzysta z konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-142">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="dcd7b-143">Poniżej znajduje się przykład skryptu.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-143">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="dcd7b-144">Systemy obsługiwanych baz danych</span><span class="sxs-lookup"><span data-stu-id="dcd7b-144">Supported database systems</span></span>

|<span data-ttu-id="dcd7b-145">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="dcd7b-145">WMF 4.0</span></span>   |<span data-ttu-id="dcd7b-146">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="dcd7b-146">WMF 5.0</span></span>  |<span data-ttu-id="dcd7b-147">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="dcd7b-147">WMF 5.1</span></span> |<span data-ttu-id="dcd7b-148">WMF 5.1 (z systemem Windows Server niejawnego Podgląd 17090)</span><span class="sxs-lookup"><span data-stu-id="dcd7b-148">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="dcd7b-149">MDB</span><span class="sxs-lookup"><span data-stu-id="dcd7b-149">MDB</span></span>     |<span data-ttu-id="dcd7b-150">ESENT (ustawienie domyślne), MDB</span><span class="sxs-lookup"><span data-stu-id="dcd7b-150">ESENT (Default), MDB</span></span> |<span data-ttu-id="dcd7b-151">ESENT (ustawienie domyślne), MDB</span><span class="sxs-lookup"><span data-stu-id="dcd7b-151">ESENT (Default), MDB</span></span>|<span data-ttu-id="dcd7b-152">ESENT (ustawienie domyślne), programu SQL Server MDB</span><span class="sxs-lookup"><span data-stu-id="dcd7b-152">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="dcd7b-153">Począwszy od wersji 17090 z [systemu Windows Server niejawnego Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), programu SQL Server jest obsługiwane opcji ściągania usługi (funkcji systemu Windows *usługi Konfiguracja DSC*).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-153">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span>  <span data-ttu-id="dcd7b-154">Zapewnia to nowa opcja skalowania dużych środowiskach DSC, które nie zostały zmigrowane do [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-154">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="dcd7b-155">**Uwaga**: Obsługa programu SQL Server nie zostanie dodany do poprzednich wersji WMF 5.1 (lub starszym), a tylko będą dostępne w wersjach systemu Windows Server większa niż lub równa 17090.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-155">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="dcd7b-156">Aby skonfigurować serwer ściągnięcia do korzystania z programu SQL Server, należy ustawić **SqlProvider** do `$true` i **SqlConnectionString** do prawidłowego ciągu połączenia serwera SQL.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-156">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span>  <span data-ttu-id="dcd7b-157">Aby uzyskać więcej informacji, zobacz [parametry połączenia SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-157">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="dcd7b-158">Na przykład konfigurację programu SQL Server z **xDscWebService**, najpierw przeczytać artykuł [przy użyciu zasobów xDscWebService](#using-the-xdscwebservice-resource) , a następnie przejrzyj [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 w serwisie GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-158">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="dcd7b-159">Przy użyciu zasobów xDscWebService</span><span class="sxs-lookup"><span data-stu-id="dcd7b-159">Using the xDscWebService resource</span></span>

<span data-ttu-id="dcd7b-160">Najprostszym sposobem konfigurowania serwera ściągania sieci web jest użycie **xDscWebService** zasobów objętych **xPSDesiredStateConfiguration** modułu.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-160">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="dcd7b-161">Poniższych krokach opisano sposób użycia zasobu w konfiguracji, który konfiguruje usługę sieci web.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-161">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="dcd7b-162">Wywołanie [instalacji modułu](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby zainstalować **xPSDesiredStateConfiguration** modułu.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-162">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="dcd7b-163">**Uwaga**: **instalacji modułu** znajduje się w **PowerShellGet** moduł, który jest dostępny w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-163">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="dcd7b-164">Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [PackageManagement moduły programu PowerShell w wersji zapoznawczej](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-164">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="dcd7b-165">Uzyskać certyfikat SSL z serwerem ściągania usługi Konfiguracja DSC od zaufanego urzędu certyfikacji, albo w ramach organizacji lub publicznego urzędu.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-165">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="dcd7b-166">Certyfikat odebrany od urzędu jest zwykle w formacie PFX.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-166">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="dcd7b-167">Zainstaluj certyfikat w węźle, który ma zostać z serwerem ściągania usługi Konfiguracja DSC w domyślnej lokalizacji, która powinna być CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-167">Install the certificate on the node that will become the DSC Pull server in the default location, which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="dcd7b-168">Zanotuj odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-168">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="dcd7b-169">Wybierz identyfikator GUID ma być używany jako klucz rejestracji.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-169">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="dcd7b-170">Aby wygenerować za pomocą programu PowerShell wpisz następujące polecenie w wierszu PS, a następnie naciśnij klawisz enter: "``` [guid]::newGuid()```"lub"```New-Guid```".</span><span class="sxs-lookup"><span data-stu-id="dcd7b-170">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="dcd7b-171">Ten klucz będzie służyć przez węzły klienta jako klucza wspólnego uwierzytelnianie podczas rejestracji.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-171">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="dcd7b-172">Aby uzyskać więcej informacji zobacz sekcję poniżej klucz rejestracji.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-172">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="dcd7b-173">W programie PowerShell ISE start (F5) następującego skryptu konfiguracji (zawarte w folderze przykłady **xPSDesiredStateConfiguration** modułu jako Sample_xDscWebServiceRegistration.ps1).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-173">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebServiceRegistration.ps1).</span></span> <span data-ttu-id="dcd7b-174">Ten skrypt powoduje ustawienie z serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-174">This script sets up the pull server.</span></span>

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

1. <span data-ttu-id="dcd7b-175">Uruchom konfigurację, przekazywanie odcisk palca certyfikatu SSL jako **certificateThumbPrint** parametru i rejestracji GUID klucz jako **RegistrationKey** parametru:</span><span class="sxs-lookup"><span data-stu-id="dcd7b-175">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a><span data-ttu-id="dcd7b-176">Klucz rejestracji</span><span class="sxs-lookup"><span data-stu-id="dcd7b-176">Registration Key</span></span>

<span data-ttu-id="dcd7b-177">Aby umożliwić węzłów do rejestrowania na serwerze, tak aby używały nazwy konfiguracji zamiast Identyfikatora konfiguracji klienta, klucz rejestracyjny, który został utworzony przez powyższej konfiguracji są zapisywane w pliku o nazwie `RegistrationKeys.txt` w `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-177">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="dcd7b-178">Klucz rejestracji działa jako wspólny klucz tajny, używane podczas wstępnej przez klienta z serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-178">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="dcd7b-179">Klient wygeneruje certyfikat z podpisem własnym używany do jednoznacznego uwierzytelnienie na serwerze ściągania, po pomyślnym zakończeniu rejestracji.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-179">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="dcd7b-180">Odcisk palca certyfikatu jest przechowywana lokalnie i skojarzone z adresem URL serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-180">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="dcd7b-181">**Uwaga**: klucze rejestracji nie są obsługiwane w programie PowerShell w wersji 4.0.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-181">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="dcd7b-182">W celu skonfigurowania węzła w celu uwierzytelnienia na serwerze ściągania, klucz rejestracji musi być w metakonfigurację dla każdego węzła docelowego będzie rejestrowanie z tym serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-182">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="dcd7b-183">Należy pamiętać, że **RegistrationKey** w metakonfigurację poniżej zostanie usunięta po pomyślnie zarejestrowała maszyny docelowej, a wartość "140a952b-b9d6-406b-b416-e0f759c9c0e4" musi odpowiadać wartości przechowywanej w Plik RegistrationKeys.txt na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-183">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="dcd7b-184">Jest zawsze traktowany wartość klucza rejestracji bezpieczne, ponieważ wiedząc o tym umożliwia żadnej maszyny docelowej, można zarejestrować na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-184">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

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

> <span data-ttu-id="dcd7b-185">**Uwaga**: **ReportServerWeb** sekcja umożliwia raportowanie danych, które zostanie wysłane do serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-185">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="dcd7b-186">Brak **ConfigurationID** właściwość w pliku metakonfigurację niejawnie oznacza, że ten serwer ściągania obsługuje V2 wersji protokołu serwera ściągania, jest wymagana rejestracja początkowej.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-186">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="dcd7b-187">Z drugiej strony, obecności **ConfigurationID** oznacza, że używana wersja V1 protokół serwera ściągania i nie istnieje żadne przetwarzania rejestracji.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-187">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="dcd7b-188">**Uwaga**: W trybie PUSH scenariuszu usterki istnieje w bieżącej wersji, który ułatwia określenie właściwości ConfigurationID w pliku metakonfigurację dla węzłów, które nigdy nie została zarejestrowana na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-188">**Note**: In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="dcd7b-189">Spowoduje to wymusić protokół serwera ściągania V1 i uniknąć komunikaty o błędach rejestracji.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-189">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="dcd7b-190">Wprowadzenie do konfiguracji i zasobów</span><span class="sxs-lookup"><span data-stu-id="dcd7b-190">Placing configurations and resources</span></span>

<span data-ttu-id="dcd7b-191">Po ściągania kończy instalacji serwera, folderów, zdefiniowane przez **ConfigurationPath** i **ModulePath** właściwości w konfiguracji serwera ściągania są umieszczane moduły i konfiguracji który będzie dostępna dla węzły docelowe do ściągnięcia.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-191">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="dcd7b-192">Te pliki muszą znajdować się w określonym formacie serwer ściągnięcia poprawnie przetworzyć je.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-192">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="dcd7b-193">Format pakietu moduł zasobu DSC</span><span class="sxs-lookup"><span data-stu-id="dcd7b-193">DSC resource module package format</span></span>

<span data-ttu-id="dcd7b-194">Każdy moduł zasobu musi być spakowane i o nazwie zgodnie z następującego wzorca `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-194">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="dcd7b-195">Na przykład moduł o nazwie xWebAdminstration z wersją modułu 3.1.2.0 będą miały postać "xWebAdministration_3.2.1.0.zip".</span><span class="sxs-lookup"><span data-stu-id="dcd7b-195">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="dcd7b-196">Każda wersja programu modułu muszą być zawarte w pliku zip pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-196">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="dcd7b-197">Ponieważ tylko jedną wersję zasobu w każdym pliku zip, format modułu, dodane w programie WMF 5.0 z obsługą wielu wersji modułu w jednym katalogu, nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-197">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="dcd7b-198">Oznacza to, że przed grupowanie DSC modułów zasobów do użycia z serwera ściągania należy wprowadzić niewielkie zmiany w strukturze katalogu.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-198">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="dcd7b-199">Domyślny format modułów zawierających DSC zasobów w programie WMF 5.0 "{modułu Folder}\{wersji modułu} \DscResources\{Folder zasobów DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-199">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="dcd7b-200">Przed pakowania dla serwera ściągania, Usuń **{wersji modułu}** folderu, tak aby stał się ścieżka "{modułu Folder} \DscResources\{Folder zasobów DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-200">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="dcd7b-201">Dzięki tej zmianie skompresować folder zgodnie z powyższym opisem i umieszczenie tych plików zip w **ModulePath** folderu.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-201">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="dcd7b-202">Użyj `New-DscChecksum {module zip file}` do utworzenia pliku sumy kontrolnej dla nowo dodanym module.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-202">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="dcd7b-203">Format MOF konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dcd7b-203">Configuration MOF format</span></span>

<span data-ttu-id="dcd7b-204">Plik MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w docelowym węźle można sprawdzić poprawność konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-204">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="dcd7b-205">Aby utworzyć sumy kontrolnej, należy wywołać [DscChecksum nowy](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-205">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="dcd7b-206">Polecenie cmdlet przyjmuje **ścieżki** parametr, który określa folder, w którym znajduje się konfiguracji MOF.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-206">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="dcd7b-207">Polecenie cmdlet tworzy plik sumy kontrolnej o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-207">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="dcd7b-208">Jeśli istnieje więcej niż jedna konfiguracja pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-208">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="dcd7b-209">Umieścić pliki MOF i ich skojarzonych sumy kontrolnej plików w **ConfigurationPath** folderu.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-209">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="dcd7b-210">**Uwaga**: w przypadku zmiany pliku MOF konfiguracji w dowolny sposób, należy również ponownie utworzyć plik sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-210">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="dcd7b-211">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="dcd7b-211">Tooling</span></span>

<span data-ttu-id="dcd7b-212">Aby można było uzupełnić ustawienie, sprawdzanie poprawności i zarządzanie nimi z serwerem ściągania łatwiejsze, następujących narzędzi są dołączone jako przykłady w najnowszej wersji modułu xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="dcd7b-212">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="dcd7b-213">Moduł, który pomoże pakowania DSC zasobów modułów i pliki konfiguracyjne do użycia na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-213">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="dcd7b-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="dcd7b-215">Poniższe przykłady:</span><span class="sxs-lookup"><span data-stu-id="dcd7b-215">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="dcd7b-216">Skrypt, który sprawdza poprawność z serwerem ściągania jest poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-216">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="dcd7b-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="dcd7b-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="dcd7b-218">Społeczności rozwiązań dla usługi replikacji ściąganej</span><span class="sxs-lookup"><span data-stu-id="dcd7b-218">Community Solutions for Pull Service</span></span>

<span data-ttu-id="dcd7b-219">Społeczność DSC ma przypisany wielu rozwiązań do implementowania protokołu usługi ściągania.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-219">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="dcd7b-220">W środowiskach lokalnych oferuje możliwości usługi ściągania i możliwość współtworzenia społeczności ulepszeń przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="dcd7b-220">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="dcd7b-221">Holownik</span><span class="sxs-lookup"><span data-stu-id="dcd7b-221">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="dcd7b-222">DSC TRÆK</span><span class="sxs-lookup"><span data-stu-id="dcd7b-222">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="dcd7b-223">Konfiguracja klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="dcd7b-223">Pull client configuration</span></span>

<span data-ttu-id="dcd7b-224">Konfigurowanie klientów ściągania szczegóły można znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="dcd7b-224">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="dcd7b-225">Konfigurowanie klienta ściągania usługi Konfiguracja DSC przy użyciu Identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dcd7b-225">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="dcd7b-226">Konfigurowanie klienta ściągania usługi Konfiguracja DSC przy użyciu nazwy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dcd7b-226">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="dcd7b-227">Konfiguracje z częściowa</span><span class="sxs-lookup"><span data-stu-id="dcd7b-227">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="dcd7b-228">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dcd7b-228">See also</span></span>

- [<span data-ttu-id="dcd7b-229">Omówienie stanu konfiguracji żądanego programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dcd7b-229">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="dcd7b-230">Realizacja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dcd7b-230">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="dcd7b-231">Używanie serwera raportów platformy DSC</span><span class="sxs-lookup"><span data-stu-id="dcd7b-231">Using a DSC report server</span></span>](reportServer.md)