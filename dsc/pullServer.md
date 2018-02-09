---
ms.date: 2018-02-02
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Usługa ściągania usługi Konfiguracja DSC"
ms.openlocfilehash: d5e24dcc093c73d8ebbaa618517193dacc4f2aaf
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="4860b-103">Usługa replikacji ściąganej konfiguracji żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="4860b-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="4860b-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4860b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4860b-105">Lokalny program Configuration Manager mogą centralnie zarządzane przez rozwiązanie do ściągania usługi.</span><span class="sxs-lookup"><span data-stu-id="4860b-105">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="4860b-106">Podczas korzystania z tej metody, węzeł, który jest zarządzany jest zarejestrowany za pomocą usługi i przypisany konfigurację w ustawieniach LCM.</span><span class="sxs-lookup"><span data-stu-id="4860b-106">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="4860b-107">Konfiguracja i wszystkie zasoby DSC, wymagane jako zależności w konfiguracji są pobierane do maszyny i używane przez LCM do zarządzanie konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="4860b-107">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="4860b-108">Informacje o stanie komputera zarządzanego jest przekazywane do usługi raportowania.</span><span class="sxs-lookup"><span data-stu-id="4860b-108">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="4860b-109">To pojęcie jest określana jako "Usługa ściągania".</span><span class="sxs-lookup"><span data-stu-id="4860b-109">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="4860b-110">Dla aktualnych opcji ściągania usługi obejmują:</span><span class="sxs-lookup"><span data-stu-id="4860b-110">The current options for pull service include:</span></span>

- <span data-ttu-id="4860b-111">Usługa konfiguracji stanu pożądanej usługi Automatyzacja Azure</span><span class="sxs-lookup"><span data-stu-id="4860b-111">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="4860b-112">Usługa replikacji ściąganej w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="4860b-112">A pull service running on Windows Server</span></span>
- <span data-ttu-id="4860b-113">Społeczność utrzymywane rozwiązań typu open source</span><span class="sxs-lookup"><span data-stu-id="4860b-113">Community maintained open source solutions</span></span>
- <span data-ttu-id="4860b-114">Udział SMB</span><span class="sxs-lookup"><span data-stu-id="4860b-114">An SMB share</span></span>

<span data-ttu-id="4860b-115">**Zalecane rozwiązanie**, a opcja z najbardziej funkcje dostępne, jest [Konfiguracja DSC automatyzacji Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="4860b-115">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="4860b-116">Usługa Azure mogą zarządzać węzłów lokalnie w centrach danych prywatnych lub chmur publicznych, takich jak Azure i usług AWS.</span><span class="sxs-lookup"><span data-stu-id="4860b-116">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="4860b-117">W środowiskach prywatne, gdzie serwery bezpośrednio nie może połączyć się z Internetem, należy wziąć pod uwagę Ograniczanie ruchu wychodzącego tylko opublikowane zakres IP platformy Azure (zobacz [zakresów IP centrum danych Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="4860b-117">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="4860b-118">Funkcje usługi online, które nie są obecnie dostępne w usłudze replikacji ściąganej w systemie Windows Server:</span><span class="sxs-lookup"><span data-stu-id="4860b-118">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="4860b-119">Wszystkie dane są szyfrowane podczas przesyłania i magazynowane</span><span class="sxs-lookup"><span data-stu-id="4860b-119">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="4860b-120">Certyfikaty klienta są tworzone i zarządzane automatycznie</span><span class="sxs-lookup"><span data-stu-id="4860b-120">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="4860b-121">Przechowywanie kluczy tajnych centralnego zarządzania [haseł lub poświadczeń](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), lub [zmienne](https://docs.microsoft.com/en-us/azure/automation/automation-variables) takich jak nazwy serwera lub parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="4860b-121">Secrets store for centrally managing [passwords/credentials](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), or [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="4860b-122">Centralne zarządzanie węzła [LCM konfiguracji](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="4860b-122">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="4860b-123">Centralnie Przypisz konfiguracje do węzłów klienta</span><span class="sxs-lookup"><span data-stu-id="4860b-123">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="4860b-124">Zmiany konfiguracji wersji do "grup mozgi" do testowania przed dotarciem do produkcji</span><span class="sxs-lookup"><span data-stu-id="4860b-124">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="4860b-125">Raportowania graficznego</span><span class="sxs-lookup"><span data-stu-id="4860b-125">Graphical reporting</span></span>
  - <span data-ttu-id="4860b-126">Szczegóły stanu na poziomie szczegółowości zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="4860b-126">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="4860b-127">Pełne komunikaty z komputerów klienckich do rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="4860b-127">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="4860b-128">[Integracja z usługą Analiza dzienników Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) alertów, automatycznych zadań Android/aplikacji systemu iOS dla raportowania i alerty</span><span class="sxs-lookup"><span data-stu-id="4860b-128">[Integration with Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="4860b-129">Usługa ściągania usługi Konfiguracja DSC w systemie Windows Server</span><span class="sxs-lookup"><span data-stu-id="4860b-129">DSC pull service in Windows Server</span></span>

<span data-ttu-id="4860b-130">Istnieje możliwość konfigurowania usługi ściągnięcia do uruchamiania w systemie Windows Server.</span><span class="sxs-lookup"><span data-stu-id="4860b-130">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="4860b-131">Informujemy, że rozwiązania usługi ściągania zawarte w systemie Windows Server zawiera tylko możliwości przechowywania moduły konfiguracji do pobrania i przechwytywanie danych raportów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="4860b-131">Please be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="4860b-132">Nie obejmuje wiele możliwości oferowane przez usługę w systemie Azure i tak nie jest dobrym narzędzia do oceny, czy użycia usługi.</span><span class="sxs-lookup"><span data-stu-id="4860b-132">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="4860b-133">Usługa replikacji ściąganej oferowanych w systemie Windows Server jest usługi sieci web w usługach IIS, który używa interfejsu OData, aby udostępnić pliki konfiguracji DSC węzły docelowe podczas tych węzłów, poproś o ich.</span><span class="sxs-lookup"><span data-stu-id="4860b-133">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="4860b-134">Wymagania dotyczące korzystania z serwera ściągania:</span><span class="sxs-lookup"><span data-stu-id="4860b-134">Requirements for using a pull server:</span></span>

- <span data-ttu-id="4860b-135">Serwer z systemem:</span><span class="sxs-lookup"><span data-stu-id="4860b-135">A server running:</span></span>
  - <span data-ttu-id="4860b-136">WMF PowerShell 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="4860b-136">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="4860b-137">Rola serwera IIS</span><span class="sxs-lookup"><span data-stu-id="4860b-137">IIS server role</span></span>
  - <span data-ttu-id="4860b-138">Usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="4860b-138">DSC Service</span></span>
- <span data-ttu-id="4860b-139">Najlepiej, jeśli niektóre oznacza generowania certyfikatu, aby zabezpieczyć poświadczenia przekazywane do lokalnego Menedżera konfiguracji (LCM) węzły docelowe</span><span class="sxs-lookup"><span data-stu-id="4860b-139">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="4860b-140">Najlepszym sposobem konfigurowania systemu Windows Server do usługi replikacji ściąganej hosta jest korzysta z konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="4860b-140">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="4860b-141">Poniżej znajduje się przykład skryptu.</span><span class="sxs-lookup"><span data-stu-id="4860b-141">An example script is provided below.</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="4860b-142">Przy użyciu zasobów xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="4860b-142">Using the xDSCWebService resource</span></span>

<span data-ttu-id="4860b-143">Najprostszym sposobem konfigurowania serwera ściągania sieci web jest do użycia zasobu xWebService, zawarte w xPSDesiredStateConfiguration module.</span><span class="sxs-lookup"><span data-stu-id="4860b-143">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="4860b-144">Poniższych krokach opisano sposób użycia zasobu w konfiguracji, który konfiguruje usługę sieci web.</span><span class="sxs-lookup"><span data-stu-id="4860b-144">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="4860b-145">Wywołanie [instalacji modułu](https://technet.microsoft.com/en-us/library/dn807162.aspx) polecenia cmdlet, aby zainstalować **xPSDesiredStateConfiguration** modułu.</span><span class="sxs-lookup"><span data-stu-id="4860b-145">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="4860b-146">**Uwaga**: **instalacji modułu** znajduje się w **PowerShellGet** moduł, który jest dostępny w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="4860b-146">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="4860b-147">Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [PackageManagement moduły programu PowerShell w wersji zapoznawczej](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="4860b-147">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="4860b-148">Uzyskać certyfikat SSL z serwerem ściągania usługi Konfiguracja DSC od zaufanego urzędu certyfikacji, albo w ramach organizacji lub publicznego urzędu.</span><span class="sxs-lookup"><span data-stu-id="4860b-148">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="4860b-149">Certyfikat odebrany od urzędu jest zwykle w formacie PFX.</span><span class="sxs-lookup"><span data-stu-id="4860b-149">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="4860b-150">Zainstaluj certyfikat w węźle, który ma zostać z serwerem ściągania usługi Konfiguracja DSC w domyślnej lokalizacji, która powinna być CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="4860b-150">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="4860b-151">Zanotuj odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="4860b-151">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="4860b-152">Wybierz identyfikator GUID ma być używany jako klucz rejestracji.</span><span class="sxs-lookup"><span data-stu-id="4860b-152">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="4860b-153">Aby wygenerować za pomocą programu PowerShell wpisz następujące polecenie w wierszu PS, a następnie naciśnij klawisz enter: "``` [guid]::newGuid()```"lub"```New-Guid```".</span><span class="sxs-lookup"><span data-stu-id="4860b-153">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="4860b-154">Ten klucz będzie służyć przez węzły klienta jako klucza wspólnego uwierzytelnianie podczas rejestracji.</span><span class="sxs-lookup"><span data-stu-id="4860b-154">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="4860b-155">Aby uzyskać więcej informacji zobacz sekcję poniżej klucz rejestracji.</span><span class="sxs-lookup"><span data-stu-id="4860b-155">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="4860b-156">W programie PowerShell ISE start (F5) następującego skryptu konfiguracji (zawarte w folderze na przykład **xPSDesiredStateConfiguration** modułu jako Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="4860b-156">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="4860b-157">Ten skrypt powoduje ustawienie z serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-157">This script sets up the pull server.</span></span>

```powershell
    configuration Sample_xDscPullServer
    {
        param
        (
                [string[]]$NodeName = 'localhost',

                [ValidateNotNullOrEmpty()]
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey
         )

         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName
         {
             WindowsFeature DSCServiceFeature
             {
                 Ensure = 'Present'
                 Name   = 'DSC-Service'
             }

             xDscWebService PSDSCPullServer
             {
                 Ensure                   = 'Present'
                 EndpointName             = 'PSDSCPullServer'
                 Port                     = 8080
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer"
                 CertificateThumbPrint    = $certificateThumbPrint
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'
                 UseSecurityBestPractices = $false
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

1. <span data-ttu-id="4860b-158">Uruchom konfigurację, przekazywanie odcisk palca certyfikatu SSL jako **certificateThumbPrint** parametru i rejestracji GUID klucz jako **RegistrationKey** parametru:</span><span class="sxs-lookup"><span data-stu-id="4860b-158">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a><span data-ttu-id="4860b-159">Klucz rejestracji</span><span class="sxs-lookup"><span data-stu-id="4860b-159">Registration Key</span></span>

<span data-ttu-id="4860b-160">Aby umożliwić węzłów do rejestrowania na serwerze, tak aby używały nazwy konfiguracji zamiast Identyfikatora konfiguracji klienta, klucz rejestracji, który został utworzony przez powyższej konfiguracji są zapisywane w pliku o nazwie `RegistrationKeys.txt` w `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="4860b-160">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="4860b-161">Klucz rejestracji działa jako wspólny klucz tajny, używane podczas wstępnej przez klienta z serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-161">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="4860b-162">Klient wygeneruje certyfikat z podpisem własnym, który jest używany do jednoznacznego uwierzytelnienie na serwerze ściągania, po pomyślnym zakończeniu rejestracji.</span><span class="sxs-lookup"><span data-stu-id="4860b-162">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="4860b-163">Odcisk palca certyfikatu jest przechowywana lokalnie i skojarzone z adresem URL serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-163">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="4860b-164">**Uwaga**: klucze rejestracji nie są obsługiwane w programie PowerShell w wersji 4.0.</span><span class="sxs-lookup"><span data-stu-id="4860b-164">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="4860b-165">W celu skonfigurowania węzła w celu uwierzytelnienia na serwerze ściągania rejestracji klucza musi być w metakonfigurację dla każdego węzła docelowego będzie rejestrowanie z tym serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-165">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="4860b-166">Należy pamiętać, że **RegistrationKey** w metakonfigurację poniżej zostanie usunięta po pomyślnie zarejestrowała maszyny docelowej, a wartość "140a952b-b9d6-406b-b416-e0f759c9c0e4" musi odpowiadać wartości przechowywanej w Plik RegistrationKeys.txt na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-166">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="4860b-167">Jest zawsze traktowany wartość klucza rejestracji bezpieczne, ponieważ wiedząc o tym umożliwia żadnej maszyny docelowej, można zarejestrować na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-167">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
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
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes


```

> <span data-ttu-id="4860b-168">**Uwaga**: **ReportServerWeb** sekcja umożliwia raportowanie danych, które zostanie wysłane do serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-168">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="4860b-169">Brak **ConfigurationID** właściwość w pliku metakonfigurację niejawnie oznacza, że ten serwer ściągania obsługuje V2 wersji protokołu serwera ściągania, jest wymagana rejestracja początkowej.</span><span class="sxs-lookup"><span data-stu-id="4860b-169">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="4860b-170">Z drugiej strony, obecności **ConfigurationID** oznacza, że używana wersja V1 protokół serwera ściągania i nie istnieje żadne przetwarzania rejestracji.</span><span class="sxs-lookup"><span data-stu-id="4860b-170">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="4860b-171">**Uwaga**: W trybie PUSH scenariuszu usterki istnieje w bieżącej dopuszczeniu, który ułatwia określenie właściwości ConfigurationID w pliku metakonfigurację dla węzłów, które nigdy nie została zarejestrowana na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-171">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="4860b-172">Spowoduje to wymusić protokół serwera ściągania V1 i uniknąć komunikaty o błędach rejestracji.</span><span class="sxs-lookup"><span data-stu-id="4860b-172">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="4860b-173">Wprowadzenie do konfiguracji i zasobów</span><span class="sxs-lookup"><span data-stu-id="4860b-173">Placing configurations and resources</span></span>

<span data-ttu-id="4860b-174">Po ściągania kończy instalacji serwera, folderów, zdefiniowane przez **ConfigurationPath** i **ModulePath** właściwości w konfiguracji serwera ściągania są umieszczane moduły i konfiguracji który będzie dostępna dla węzły docelowe do ściągnięcia.</span><span class="sxs-lookup"><span data-stu-id="4860b-174">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="4860b-175">Te pliki muszą znajdować się w określonym formacie serwer ściągnięcia poprawnie przetworzyć je.</span><span class="sxs-lookup"><span data-stu-id="4860b-175">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="4860b-176">Format pakietu moduł zasobu DSC</span><span class="sxs-lookup"><span data-stu-id="4860b-176">DSC resource module package format</span></span>

<span data-ttu-id="4860b-177">Każdy moduł zasobu musi być spakowane i o nazwie zgodnie z następującego wzorca `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="4860b-177">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="4860b-178">Na przykład moduł o nazwie xWebAdminstration z wersją modułu 3.1.2.0 będą miały postać "xWebAdministration_3.2.1.0.zip".</span><span class="sxs-lookup"><span data-stu-id="4860b-178">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="4860b-179">Każda wersja programu modułu muszą być zawarte w pliku zip pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="4860b-179">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="4860b-180">Ponieważ istnieje tylko jednej wersji zasobów w każdym pliku zip formatu modułu dodane w programie WMF 5.0 z obsługę wielu wersji modułu w jednym katalogu, nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="4860b-180">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="4860b-181">Oznacza to, że przed grupowanie DSC modułów zasobów do użycia z serwera ściągania należy wprowadzić niewielkie zmiany w strukturze katalogu.</span><span class="sxs-lookup"><span data-stu-id="4860b-181">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="4860b-182">Domyślny format modułów zawierających DSC zasobów w programie WMF 5.0 "{modułu Folder}\{wersji modułu} \DscResources\{Folder zasobów DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="4860b-182">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="4860b-183">Przed pakowania dla serwera ściągania po prostu usuń **{wersji modułu}** folderu, tak aby stał się ścieżka "{modułu Folder} \DscResources\{Folder zasobów DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="4860b-183">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="4860b-184">Dzięki tej zmianie skompresować folder zgodnie z powyższym opisem i umieszczenie tych plików zip w **ModulePath** folderu.</span><span class="sxs-lookup"><span data-stu-id="4860b-184">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="4860b-185">Użyj `new-dscchecksum {module zip file}` utworzyć plik sumy kontrolnej dla nowo dodanych modułu.</span><span class="sxs-lookup"><span data-stu-id="4860b-185">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="4860b-186">Format MOF konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4860b-186">Configuration MOF format</span></span>

<span data-ttu-id="4860b-187">Plik MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w docelowym węźle można sprawdzić poprawność konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4860b-187">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="4860b-188">Aby utworzyć sumy kontrolnej, należy wywołać [DSCCheckSum nowy](https://technet.microsoft.com/en-us/library/dn521622.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4860b-188">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span>
<span data-ttu-id="4860b-189">Polecenie cmdlet przyjmuje **ścieżki** parametr, który określa folder, w którym znajduje się konfiguracji MOF.</span><span class="sxs-lookup"><span data-stu-id="4860b-189">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="4860b-190">Polecenie cmdlet tworzy plik sumy kontrolnej o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4860b-190">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="4860b-191">Jeśli istnieje więcej niż jedna konfiguracja pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.</span><span class="sxs-lookup"><span data-stu-id="4860b-191">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="4860b-192">Umieścić pliki MOF i ich skojarzonych sumy kontrolnej plików w **ConfigurationPath** folderu.</span><span class="sxs-lookup"><span data-stu-id="4860b-192">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="4860b-193">**Uwaga**: w przypadku zmiany pliku MOF konfiguracji w dowolny sposób, należy również ponownie utworzyć plik sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="4860b-193">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="4860b-194">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="4860b-194">Tooling</span></span>

<span data-ttu-id="4860b-195">Aby można było uzupełnić ustawienie, sprawdzanie poprawności i zarządzanie nimi z serwerem ściągania łatwiejsze, następujących narzędzi są dołączone jako przykłady w najnowszej wersji modułu xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="4860b-195">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="4860b-196">Moduł, który pomoże pakowania DSC zasobów modułów i pliki konfiguracyjne do użycia na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-196">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="4860b-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="4860b-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="4860b-198">Poniższe przykłady:</span><span class="sxs-lookup"><span data-stu-id="4860b-198">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="4860b-199">Skrypt, który sprawdza poprawność z serwerem ściągania jest poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="4860b-199">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="4860b-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="4860b-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="4860b-201">Społeczności rozwiązań dla usługi replikacji ściąganej</span><span class="sxs-lookup"><span data-stu-id="4860b-201">Community Solutions for Pull Service</span></span>

<span data-ttu-id="4860b-202">Społeczność DSC ma przypisany wielu rozwiązań do implementowania protokołu usługi ściągania.</span><span class="sxs-lookup"><span data-stu-id="4860b-202">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="4860b-203">Dla lokalnych środowiskach, które oferuje możliwości usługi ściągania i możliwość współtworzenia z powrotem do społeczności ulepszeń przyrostowych.</span><span class="sxs-lookup"><span data-stu-id="4860b-203">For on-premises environments these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="4860b-204">Holownik</span><span class="sxs-lookup"><span data-stu-id="4860b-204">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="4860b-205">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="4860b-205">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="4860b-206">Konfiguracja klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="4860b-206">Pull client configuration</span></span>

<span data-ttu-id="4860b-207">Konfigurowanie klientów ściągania szczegóły można znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="4860b-207">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="4860b-208">Konfigurowanie klienta ściągania usługi Konfiguracja DSC przy użyciu Identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4860b-208">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="4860b-209">Konfigurowanie klienta ściągania usługi Konfiguracja DSC przy użyciu nazwy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4860b-209">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="4860b-210">Konfiguracje z częściowa</span><span class="sxs-lookup"><span data-stu-id="4860b-210">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="4860b-211">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4860b-211">See also</span></span>

- [<span data-ttu-id="4860b-212">Omówienie stanu konfiguracji żądanego programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4860b-212">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="4860b-213">Realizacja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4860b-213">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="4860b-214">Używanie serwera raportów platformy DSC</span><span class="sxs-lookup"><span data-stu-id="4860b-214">Using a DSC report server</span></span>](reportServer.md)
