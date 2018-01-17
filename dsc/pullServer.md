---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web"
ms.openlocfilehash: 9a09804ef0efe3e4c92923910884710187d44ac5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="c43fe-103">Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web</span><span class="sxs-lookup"><span data-stu-id="c43fe-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="c43fe-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c43fe-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="c43fe-105">Serwera ściągania usługi Konfiguracja DSC jest usługą sieci web w usługach IIS, który używa interfejsu OData, aby udostępnić pliki konfiguracji DSC węzły docelowe podczas tych węzłów, poproś o ich.</span><span class="sxs-lookup"><span data-stu-id="c43fe-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="c43fe-106">Wymagania dotyczące korzystania z serwera ściągania:</span><span class="sxs-lookup"><span data-stu-id="c43fe-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="c43fe-107">Serwer z systemem:</span><span class="sxs-lookup"><span data-stu-id="c43fe-107">A server running:</span></span>
  - <span data-ttu-id="c43fe-108">WMF PowerShell 5.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="c43fe-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="c43fe-109">Rola serwera IIS</span><span class="sxs-lookup"><span data-stu-id="c43fe-109">IIS server role</span></span>
  - <span data-ttu-id="c43fe-110">Usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="c43fe-110">DSC Service</span></span>
* <span data-ttu-id="c43fe-111">Najlepiej, jeśli niektóre oznacza generowania certyfikatu, aby zabezpieczyć poświadczenia przekazywane do lokalnego Menedżera konfiguracji (LCM) węzły docelowe</span><span class="sxs-lookup"><span data-stu-id="c43fe-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="c43fe-112">Przy użyciu Kreatora dodawania ról i funkcji w Menedżerze serwera lub za pomocą programu PowerShell, można dodać rolę serwera usług IIS oraz usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="c43fe-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="c43fe-113">Przykładowe skrypty zawarte w tym temacie będzie obsługiwać oba te kroki można również.</span><span class="sxs-lookup"><span data-stu-id="c43fe-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="c43fe-114">Przy użyciu zasobów xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="c43fe-114">Using the xDSCWebService resource</span></span>
<span data-ttu-id="c43fe-115">Najprostszym sposobem konfigurowania serwera ściągania sieci web jest do użycia zasobu xWebService, zawarte w xPSDesiredStateConfiguration module.</span><span class="sxs-lookup"><span data-stu-id="c43fe-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="c43fe-116">Poniższych krokach opisano sposób użycia zasobu w konfiguracji, który konfiguruje usługę sieci web.</span><span class="sxs-lookup"><span data-stu-id="c43fe-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="c43fe-117">Wywołanie [instalacji modułu](https://technet.microsoft.com/en-us/library/dn807162.aspx) polecenia cmdlet, aby zainstalować **xPSDesiredStateConfiguration** modułu.</span><span class="sxs-lookup"><span data-stu-id="c43fe-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="c43fe-118">**Uwaga**: **instalacji modułu** znajduje się w **PowerShellGet** moduł, który jest dostępny w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="c43fe-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="c43fe-119">Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [PackageManagement moduły programu PowerShell w wersji zapoznawczej](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="c43fe-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="c43fe-120">Uzyskać certyfikat SSL z serwerem ściągania usługi Konfiguracja DSC od zaufanego urzędu certyfikacji, albo w ramach organizacji lub publicznego urzędu.</span><span class="sxs-lookup"><span data-stu-id="c43fe-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="c43fe-121">Certyfikat odebrany od urzędu jest zwykle w formacie PFX.</span><span class="sxs-lookup"><span data-stu-id="c43fe-121">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="c43fe-122">Zainstaluj certyfikat w węźle, który ma zostać z serwerem ściągania usługi Konfiguracja DSC w domyślnej lokalizacji, która powinna być CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="c43fe-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="c43fe-123">Zanotuj odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c43fe-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="c43fe-124">Wybierz identyfikator GUID ma być używany jako klucz rejestracji.</span><span class="sxs-lookup"><span data-stu-id="c43fe-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="c43fe-125">Aby wygenerować za pomocą programu PowerShell wpisz następujące polecenie w wierszu PS, a następnie naciśnij klawisz enter: "``` [guid]::newGuid()```"lub"```New-Guid```".</span><span class="sxs-lookup"><span data-stu-id="c43fe-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="c43fe-126">Ten klucz będzie służyć przez węzły klienta jako klucza wspólnego uwierzytelnianie podczas rejestracji.</span><span class="sxs-lookup"><span data-stu-id="c43fe-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="c43fe-127">Aby uzyskać więcej informacji zobacz sekcję poniżej klucz rejestracji.</span><span class="sxs-lookup"><span data-stu-id="c43fe-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="c43fe-128">W programie PowerShell ISE start (F5) następującego skryptu konfiguracji (zawarte w folderze na przykład **xPSDesiredStateConfiguration** modułu jako Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="c43fe-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="c43fe-129">Ten skrypt powoduje ustawienie z serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="c43fe-129">This script sets up the pull server.</span></span>
  
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

1. <span data-ttu-id="c43fe-130">Uruchom konfigurację, przekazywanie odcisk palca certyfikatu SSL jako **certificateThumbPrint** parametru i rejestracji GUID klucz jako **RegistrationKey** parametru:</span><span class="sxs-lookup"><span data-stu-id="c43fe-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a><span data-ttu-id="c43fe-131">Klucz rejestracji</span><span class="sxs-lookup"><span data-stu-id="c43fe-131">Registration Key</span></span>
<span data-ttu-id="c43fe-132">Aby umożliwić węzłów do rejestrowania na serwerze, tak aby używały nazwy konfiguracji zamiast Identyfikatora konfiguracji klienta, klucz rejestracji, który został utworzony przez powyższej konfiguracji są zapisywane w pliku o nazwie `RegistrationKeys.txt` w `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="c43fe-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="c43fe-133">Klucz rejestracji działa jako wspólny klucz tajny, używane podczas wstępnej przez klienta z serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="c43fe-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="c43fe-134">Klient wygeneruje certyfikat z podpisem własnym, który jest używany do jednoznacznego uwierzytelnienie na serwerze ściągania, po pomyślnym zakończeniu rejestracji.</span><span class="sxs-lookup"><span data-stu-id="c43fe-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="c43fe-135">Odcisk palca certyfikatu jest przechowywana lokalnie i skojarzone z adresem URL serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="c43fe-135">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="c43fe-136">**Uwaga**: klucze rejestracji nie są obsługiwane w programie PowerShell w wersji 4.0.</span><span class="sxs-lookup"><span data-stu-id="c43fe-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="c43fe-137">W celu skonfigurowania węzła w celu uwierzytelnienia na serwerze ściągania rejestracji klucza musi być w metakonfigurację dla każdego węzła docelowego będzie rejestrowanie z tym serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="c43fe-137">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="c43fe-138">Należy pamiętać, że **RegistrationKey** w metakonfigurację poniżej zostanie usunięta po pomyślnie zarejestrowała maszyny docelowej, a wartość "140a952b-b9d6-406b-b416-e0f759c9c0e4" musi odpowiadać wartości przechowywanej w Plik RegistrationKeys.txt na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="c43fe-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="c43fe-139">Jest zawsze traktowany wartość klucza rejestracji bezpieczne, ponieważ wiedząc o tym umożliwia żadnej maszyny docelowej, można zarejestrować na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="c43fe-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="c43fe-140">**Uwaga**: **ReportServerWeb** sekcja umożliwia raportowanie danych, które zostanie wysłane do serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="c43fe-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="c43fe-141">Brak **ConfigurationID** właściwość w pliku metakonfigurację niejawnie oznacza, że ten serwer ściągania obsługuje V2 wersji protokołu serwera ściągania, jest wymagana rejestracja początkowej.</span><span class="sxs-lookup"><span data-stu-id="c43fe-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="c43fe-142">Z drugiej strony, obecności **ConfigurationID** oznacza, że używana wersja V1 protokół serwera ściągania i nie istnieje żadne przetwarzania rejestracji.</span><span class="sxs-lookup"><span data-stu-id="c43fe-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="c43fe-143">**Uwaga**: W trybie PUSH scenariuszu usterki istnieje w bieżącej dopuszczeniu, który ułatwia określenie właściwości ConfigurationID w pliku metakonfigurację dla węzłów, które nigdy nie została zarejestrowana na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="c43fe-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="c43fe-144">Spowoduje to wymusić protokół serwera ściągania V1 i uniknąć komunikaty o błędach rejestracji.</span><span class="sxs-lookup"><span data-stu-id="c43fe-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="c43fe-145">Wprowadzenie do konfiguracji i zasobów</span><span class="sxs-lookup"><span data-stu-id="c43fe-145">Placing configurations and resources</span></span>

<span data-ttu-id="c43fe-146">Po ściągania kończy instalacji serwera, folderów, zdefiniowane przez **ConfigurationPath** i **ModulePath** właściwości w konfiguracji serwera ściągania są umieszczane moduły i konfiguracji który będzie dostępna dla węzły docelowe do ściągnięcia.</span><span class="sxs-lookup"><span data-stu-id="c43fe-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="c43fe-147">Te pliki muszą znajdować się w określonym formacie serwer ściągnięcia poprawnie przetworzyć je.</span><span class="sxs-lookup"><span data-stu-id="c43fe-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="c43fe-148">Format pakietu moduł zasobu DSC</span><span class="sxs-lookup"><span data-stu-id="c43fe-148">DSC resource module package format</span></span>

<span data-ttu-id="c43fe-149">Każdy moduł zasobu musi być spakowane i o nazwie zgodnie z następującego wzorca `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="c43fe-149">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="c43fe-150">Na przykład moduł o nazwie xWebAdminstration z wersją modułu 3.1.2.0 będą miały postać "xWebAdministration_3.2.1.0.zip".</span><span class="sxs-lookup"><span data-stu-id="c43fe-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="c43fe-151">Każda wersja programu modułu muszą być zawarte w pliku zip pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="c43fe-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="c43fe-152">Ponieważ istnieje tylko jednej wersji zasobów w każdym pliku zip formatu modułu dodane w programie WMF 5.0 z obsługę wielu wersji modułu w jednym katalogu, nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="c43fe-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="c43fe-153">Oznacza to, że przed grupowanie DSC modułów zasobów do użycia z serwera ściągania należy wprowadzić niewielkie zmiany w strukturze katalogu.</span><span class="sxs-lookup"><span data-stu-id="c43fe-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="c43fe-154">Domyślny format modułów zawierających DSC zasobów w programie WMF 5.0 "{modułu Folder}\{wersji modułu} \DscResources\{Folder zasobów DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="c43fe-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="c43fe-155">Przed pakowania dla serwera ściągania po prostu usuń **{wersji modułu}** folderu, tak aby stał się ścieżka "{modułu Folder} \DscResources\{Folder zasobów DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="c43fe-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="c43fe-156">Dzięki tej zmianie skompresować folder zgodnie z powyższym opisem i umieszczenie tych plików zip w **ModulePath** folderu.</span><span class="sxs-lookup"><span data-stu-id="c43fe-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="c43fe-157">Użyj `new-dscchecksum {module zip file}` utworzyć plik sumy kontrolnej dla nowo dodanych modułu.</span><span class="sxs-lookup"><span data-stu-id="c43fe-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="c43fe-158">Format MOF konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c43fe-158">Configuration MOF format</span></span> 
<span data-ttu-id="c43fe-159">Plik MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w docelowym węźle można sprawdzić poprawność konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c43fe-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="c43fe-160">Aby utworzyć sumy kontrolnej, należy wywołać [DSCCheckSum nowy](https://technet.microsoft.com/en-us/library/dn521622.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c43fe-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="c43fe-161">Polecenie cmdlet przyjmuje **ścieżki** parametr, który określa folder, w którym znajduje się konfiguracji MOF.</span><span class="sxs-lookup"><span data-stu-id="c43fe-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="c43fe-162">Polecenie cmdlet tworzy plik sumy kontrolnej o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c43fe-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="c43fe-163">Jeśli istnieje więcej niż jedna konfiguracja pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.</span><span class="sxs-lookup"><span data-stu-id="c43fe-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="c43fe-164">Umieścić pliki MOF i ich skojarzonych sumy kontrolnej plików w **ConfigurationPath** folderu.</span><span class="sxs-lookup"><span data-stu-id="c43fe-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="c43fe-165">**Uwaga**: w przypadku zmiany pliku MOF konfiguracji w dowolny sposób, należy również ponownie utworzyć plik sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="c43fe-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="c43fe-166">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="c43fe-166">Tooling</span></span>
<span data-ttu-id="c43fe-167">Aby można było uzupełnić ustawienie, sprawdzanie poprawności i zarządzanie nimi z serwerem ściągania łatwiejsze, następujących narzędzi są dołączone jako przykłady w najnowszej wersji modułu xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="c43fe-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="c43fe-168">Moduł, który pomoże pakowania DSC zasobów modułów i pliki konfiguracyjne do użycia na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="c43fe-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="c43fe-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="c43fe-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="c43fe-170">Poniższe przykłady:</span><span class="sxs-lookup"><span data-stu-id="c43fe-170">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="c43fe-171">Skrypt, który sprawdza poprawność z serwerem ściągania jest poprawnie skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="c43fe-171">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="c43fe-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="c43fe-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="c43fe-173">Konfiguracja klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="c43fe-173">Pull client configuration</span></span> 
<span data-ttu-id="c43fe-174">Konfigurowanie klientów ściągania szczegóły można znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="c43fe-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="c43fe-175">Konfigurowanie klienta ściągania usługi Konfiguracja DSC przy użyciu Identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c43fe-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="c43fe-176">Konfigurowanie klienta ściągania usługi Konfiguracja DSC przy użyciu nazwy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c43fe-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="c43fe-177">Konfiguracje z częściowa</span><span class="sxs-lookup"><span data-stu-id="c43fe-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="c43fe-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c43fe-178">See also</span></span>
* [<span data-ttu-id="c43fe-179">Omówienie stanu konfiguracji żądanego programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c43fe-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="c43fe-180">Realizacja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c43fe-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="c43fe-181">Używanie serwera raportów platformy DSC</span><span class="sxs-lookup"><span data-stu-id="c43fe-181">Using a DSC report server</span></span>](reportServer.md)

