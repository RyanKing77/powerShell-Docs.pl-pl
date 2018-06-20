---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Ulepszenia usługi Konfiguracja DSC w WMF 5.1
ms.openlocfilehash: 32bdde6d43d17cc76c454fe10b00097753a9eebe
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309546"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="629a7-103">Ulepszenia w konfiguracji żądanego stanu (DSC) w wersji 5.1 WMF</span><span class="sxs-lookup"><span data-stu-id="629a7-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="629a7-104">Ulepszenia zasobów klasy DSC</span><span class="sxs-lookup"><span data-stu-id="629a7-104">DSC class resource improvements</span></span>

<span data-ttu-id="629a7-105">W wersji 5.1 WMF Naprawiono następujące znane problemy:</span><span class="sxs-lookup"><span data-stu-id="629a7-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="629a7-106">Get-DscConfiguration może zwrócić wartości puste (null) lub błędy, jeśli typem tabeli złożone i skrótu jest zwracane przez funkcję Get() zasobu DSC klasy.</span><span class="sxs-lookup"><span data-stu-id="629a7-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="629a7-107">Get-DscConfiguration zwraca błąd, jeśli poświadczeń Uruchom jako jest używane w konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="629a7-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="629a7-108">Nie można używać zasobów na podstawie klasy w złożonych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="629a7-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="629a7-109">Start-DscConfiguration zawiesza się, jeśli na podstawie klasy zasób ma właściwość jego własnego typu.</span><span class="sxs-lookup"><span data-stu-id="629a7-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="629a7-110">Na podstawie klasy zasobu nie można użyć jako zasób wyłącznego.</span><span class="sxs-lookup"><span data-stu-id="629a7-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="629a7-111">Ulepszenia debugowania zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="629a7-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="629a7-112">W programie WMF 5.0 debuger programu PowerShell nie zatrzymał się w metodzie zasobów na podstawie klasy (Test-Get/Set) bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="629a7-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="629a7-113">W wersji 5.1 WMF debuger zatrzymuje się na metodę klasy zasobów w taki sam sposób jak w przypadku zasobów opartych na plikach MOF metody.</span><span class="sxs-lookup"><span data-stu-id="629a7-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="629a7-114">Klient ściągania usługi Konfiguracja DSC obsługuje protokołu TLS 1.1 i TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="629a7-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="629a7-115">Wcześniej klient ściągania usługi Konfiguracja DSC obsługiwane tylko SSL3.0 i TLS1.0 za pośrednictwem połączenia HTTPS.</span><span class="sxs-lookup"><span data-stu-id="629a7-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="629a7-116">Gdy wymuszono są używane protokoły bardziej bezpieczne, klienta ściągania będzie przestaną działać.</span><span class="sxs-lookup"><span data-stu-id="629a7-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="629a7-117">W wersji 5.1 WMF nie jest już klienta ściągania usługi Konfiguracja DSC protokół SSL 3.0 i dodaje obsługę bezpieczniejsze protokoły TLS 1.1 i TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="629a7-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="629a7-118">Rejestracja serwera ściągania ulepszone</span><span class="sxs-lookup"><span data-stu-id="629a7-118">Improved pull server registration</span></span>

<span data-ttu-id="629a7-119">We wcześniejszych wersjach WMF równoczesnych rejestracji/reporting żądania do serwera ściągania usługi Konfiguracja DSC podczas korzystania z bazy danych ESENT doprowadziłoby do LCM nie powiodło się zarejestrować i/lub raportu.</span><span class="sxs-lookup"><span data-stu-id="629a7-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="629a7-120">W takiej sytuacji dzienniki zdarzeń na serwerze ściągania ma błędu "Nazwa wystąpienia już w użyciu".</span><span class="sxs-lookup"><span data-stu-id="629a7-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="629a7-121">Jest to spowodowane nieprawidłowy wzorzec używane do dostępu do bazy danych ESENT w scenariuszu wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="629a7-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="629a7-122">W wersji 5.1 WMF ten problem został rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="629a7-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="629a7-123">Równoczesnych rejestracji lub wykonywania raportu (związanej z bazą danych ESENT) działa prawidłowo w wersji 5.1 WMF.</span><span class="sxs-lookup"><span data-stu-id="629a7-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="629a7-124">Ten problem dotyczy tylko ESENT bazy danych i nie ma zastosowania do bazy danych OLEDB.</span><span class="sxs-lookup"><span data-stu-id="629a7-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="629a7-125">Włącz cyklicznego pliku dziennika ESENT wystąpienia bazy danych</span><span class="sxs-lookup"><span data-stu-id="629a7-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="629a7-126">W wersji eariler DSC PullServer pliki dziennika bazy danych ESENT zostały zapełnia się miejsca na dysku becouse pullserver, utworzenia wystąpienia bazy danych trwa bez logowanie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="629a7-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="629a7-127">W tej wersji istnieje możliwość kontrolowania zachowania logowanie cykliczne wystąpienia przy użyciu pliku web.config pullserver.</span><span class="sxs-lookup"><span data-stu-id="629a7-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="629a7-128">Domyślnie CircularLogging ma wartość TRUE.</span><span class="sxs-lookup"><span data-stu-id="629a7-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="629a7-129">Ściąganie konwencji nazewnictwa częściowe konfiguracji</span><span class="sxs-lookup"><span data-stu-id="629a7-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="629a7-130">W poprzednich wersjach konwencji nazewnictwa w przypadku konfiguracji z częściowa został czy nazwa pliku MOF w usłudze ściągania serwer/powinna odpowiadać nazwie częściowe konfiguracji określone w ustawieniach menedżera lokalnej konfiguracji, które z kolei muszą być zgodne Nazwa konfiguracji jest osadzony w pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="629a7-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="629a7-131">Zobacz migawki poniżej:</span><span class="sxs-lookup"><span data-stu-id="629a7-131">See the snapshots below:</span></span>

- <span data-ttu-id="629a7-132">Ustawienia konfiguracji lokalnej, które definiuje konfigurację częściowy, który może odbierać węzła.</span><span class="sxs-lookup"><span data-stu-id="629a7-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Metakonfigurację próbki](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="629a7-134">Przykład definicji częściowej konfiguracji</span><span class="sxs-lookup"><span data-stu-id="629a7-134">Sample partial configuration definition</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

- <span data-ttu-id="629a7-135">"ConfigurationName" osadzonego w wygenerowanym pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="629a7-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![Przykładowy plik mof wygenerowany](../images/PartialGeneratedMof.png)

- <span data-ttu-id="629a7-137">Nazwa pliku w repozytorium konfiguracji replikacji ściąganej</span><span class="sxs-lookup"><span data-stu-id="629a7-137">FileName in the pull configuration repository</span></span>

![Nazwa pliku w repozytorium konfiguracji](../images/PartialInConfigRepository.png)

<span data-ttu-id="629a7-139">Nazwa usługi Automatyzacja Azure wygenerowanych plików MOF jako `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="629a7-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="629a7-140">Dlatego konfiguracja poniżej kompiluje do PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="629a7-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="629a7-141">To uniemożliwił do ściągania jedną z częściowa konfiguracji od usługi Automatyzacja Azure.</span><span class="sxs-lookup"><span data-stu-id="629a7-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="629a7-142">W wersji 5.1 WMF, częściowe konfiguracji w usłudze ściągania serwer/może mieć nazwę jako `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="629a7-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="629a7-143">Ponadto jeśli maszyna jest ściąganie pojedynczą konfiguracją z ściąganie usługa następnie pliku konfiguracji w repozytorium konfiguracji serwera ściągania może mieć dowolną nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="629a7-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="629a7-144">Taka elastyczność nazewnictwa pozwala na zarządzanie węzły częściowo przez usługi Automatyzacja Azure, gdzie konfiguracyjnych dla węzeł pochodzi z usługi Konfiguracja DSC automatyzacji Azure i z częściowa konfiguracji, którą zarządzasz lokalnie.</span><span class="sxs-lookup"><span data-stu-id="629a7-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="629a7-145">Metakonfigurację poniżej konfiguruje węzeł, aby być zarządzane zarówno lokalnie, a także przez usługi Automatyzacja Azure usługi.</span><span class="sxs-lookup"><span data-stu-id="629a7-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration RegistrationMetaConfig
{
    Settings
    {
        RefreshFrequencyMins = 30
        RefreshMode = "PULL"
    }

    ConfigurationRepositoryWeb web
    {
        ServerURL =  $endPoint
        RegistrationKey = $registrationKey
        ConfigurationNames = $configurationName
    }

    # Partial configuration managed by Azure Automation service.
    PartialConfiguration PartialConfigurationManagedByAzureAutomation
    {
        ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
    }

    # This partial configuration is managed locally.
    PartialConfiguration OnPremisesConfig
    {
        RefreshMode = "PUSH"
        ExclusiveResources = @("Script")
    }

}

RegistrationMetaConfig
Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="629a7-146">Przy użyciu PsDscRunAsCredential z zasobami złożonego DSC</span><span class="sxs-lookup"><span data-stu-id="629a7-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="629a7-147">Dodano obsługę protokołu [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) usłudze Konfiguracja DSC [złożonego](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) zasobów.</span><span class="sxs-lookup"><span data-stu-id="629a7-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="629a7-148">Teraz można określić wartość dla PsDscRunAsCredential, korzystając z zasobów złożonego w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="629a7-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="629a7-149">W przypadku uruchamiania wszystkich zasobów wewnątrz złożonego zasobów użytkownika Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="629a7-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="629a7-150">Złożone zasobów wywołuje inny zasób złożonego, wszystkie jej zasoby są również wykonywane jako użytkownika Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="629a7-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="629a7-151">Poświadczenia programu RunAs są propagowane do dowolnego poziomu hierarchii złożonego zasobów.</span><span class="sxs-lookup"><span data-stu-id="629a7-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="629a7-152">Jeśli dowolnego zasobu wewnątrz złożonego zasobu określa własnej wartości PsDscRunAsCredential, błąd scalania wyniki podczas kompilacji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="629a7-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="629a7-153">W tym przykładzie pokazano sposób użycia z [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) złożonego zasobu zawarte w PSDesiredStateConfiguration module.</span><span class="sxs-lookup"><span data-stu-id="629a7-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="629a7-154">Moduł DSC i podpisywania operacji sprawdzania poprawności konfiguracji</span><span class="sxs-lookup"><span data-stu-id="629a7-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="629a7-155">W konfiguracji DSC konfiguracji i moduły są dystrybuowane do zarządzanych komputerów z serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="629a7-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="629a7-156">W przypadku naruszenia zabezpieczeń serwera ściągania osoba atakująca może potencjalnie zmodyfikować konfiguracje i modułów na serwerze ściągania a go rozłożone na wszystkie węzły zarządzane, naruszania ich wszystkich.</span><span class="sxs-lookup"><span data-stu-id="629a7-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="629a7-157">W wersji 5.1 WMF, obsługuje weryfikowania podpisów cyfrowych w katalogu i konfiguracji DSC (. Pliki MOF).</span><span class="sxs-lookup"><span data-stu-id="629a7-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="629a7-158">Ta funkcja zapobiega wykonywania konfiguracji lub moduł pliki, które nie są podpisane przez zaufane osoby podpisującej lub które zostały zmodyfikowane po zostały podpisane przez zaufane osoby podpisującej węzłów.</span><span class="sxs-lookup"><span data-stu-id="629a7-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="629a7-159">Jak zarejestrować konfiguracji i modułu</span><span class="sxs-lookup"><span data-stu-id="629a7-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="629a7-160">Pliki konfiguracji (. Za): istniejącego polecenia cmdlet programu PowerShell [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) jest rozszerzony do obsługi podpisywania plików MOF.</span><span class="sxs-lookup"><span data-stu-id="629a7-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="629a7-161">Moduły: Podpisywanie modułów można to zrobić po zarejestrowaniu odpowiedniego katalogu modułu, wykonując poniższe kroki:</span><span class="sxs-lookup"><span data-stu-id="629a7-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="629a7-162">Utworzenie pliku wykazu: plik katalogu zawiera kolekcję skróty kryptograficzne lub odciski palców.</span><span class="sxs-lookup"><span data-stu-id="629a7-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="629a7-163">Każdy odcisk palca odnosi się do pliku, który znajduje się w module.</span><span class="sxs-lookup"><span data-stu-id="629a7-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="629a7-164">Nowe polecenia cmdlet [FileCatalog nowy](https://technet.microsoft.com/library/cc732148.aspx), dodano umożliwiające użytkownikom tworzenie plik katalogu dla ich modułu.</span><span class="sxs-lookup"><span data-stu-id="629a7-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="629a7-165">Podpisać plik wykazu: Użyj [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) do podpisywania pliku wykazu.</span><span class="sxs-lookup"><span data-stu-id="629a7-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="629a7-166">Umieść plik wykazu znajdujące się w folderze modułu.</span><span class="sxs-lookup"><span data-stu-id="629a7-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="629a7-167">Według Konwencji modułu katalogu plik należy umieścić w folderze modułu o nazwie identycznej z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="629a7-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="629a7-168">LocalConfigurationManager ustawienia, aby włączyć sprawdzanie poprawności podpisywania</span><span class="sxs-lookup"><span data-stu-id="629a7-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="629a7-169">Ściągania</span><span class="sxs-lookup"><span data-stu-id="629a7-169">Pull</span></span>

<span data-ttu-id="629a7-170">LocalConfigurationManager węzła sprawdza poprawność podpisywania modułów i konfiguracji w oparciu o bieżące ustawienia.</span><span class="sxs-lookup"><span data-stu-id="629a7-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="629a7-171">Domyślnie jest wyłączona Walidacja podpisu.</span><span class="sxs-lookup"><span data-stu-id="629a7-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="629a7-172">Walidacja podpisu można włączyć przez dodanie bloku "SignatureValidation" do definicji meta konfiguracji węzła jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="629a7-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

<span data-ttu-id="629a7-173">Ustawienie metakonfigurację powyżej w węźle umożliwia weryfikację podpisu na konfiguracje pobrane i modułów.</span><span class="sxs-lookup"><span data-stu-id="629a7-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="629a7-174">Lokalny program Configuration Manager wykonuje następujące czynności w celu zweryfikowania podpisów cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="629a7-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="629a7-175">Weryfikacja podpisu w pliku konfiguracji (. MOF) jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="629a7-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="629a7-176">Używa polecenia cmdlet programu PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), który został rozszerzony w wersji 5.1 do obsługi sprawdzania poprawności podpisu MOF.</span><span class="sxs-lookup"><span data-stu-id="629a7-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="629a7-177">Sprawdź, czy urząd certyfikacji, który autoryzowane osoby podpisującej jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="629a7-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="629a7-178">Pobierz moduł zasobów zależności konfiguracji do tymczasowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="629a7-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="629a7-179">Weryfikacja podpisu katalogu uwzględniony w module.</span><span class="sxs-lookup"><span data-stu-id="629a7-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="629a7-180">Znajdź `<moduleName>.cat` i sprawdzić jego podpisu za pomocą polecenia cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="629a7-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="629a7-181">Sprawdź, czy urząd certyfikacji, który uwierzytelnieni osoby podpisującej jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="629a7-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="629a7-182">Sprawdź nie został naruszony zawartość modułów za pomocą polecenia cmdlet nowe [FileCatalog testu](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="629a7-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="629a7-183">Install-moduł $env: ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="629a7-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="629a7-184">Konfiguracja procesu</span><span class="sxs-lookup"><span data-stu-id="629a7-184">Process configuration</span></span>

> <span data-ttu-id="629a7-185">Uwaga: Walidacja podpisu na katalog modułu oraz konfiguracji jest realizowane wyłącznie podczas stosowania konfiguracji systemu, po raz pierwszy lub gdy moduł jest pobierane i instalowane.</span><span class="sxs-lookup"><span data-stu-id="629a7-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="629a7-186">Uruchamia spójności nie weryfikują podpisu Current.mof lub jego zależności modułu.</span><span class="sxs-lookup"><span data-stu-id="629a7-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="629a7-187">Jeśli weryfikacja nie powiodła się na każdym etapie, na przykład, jeśli konfiguracji są pobierane z z serwerem ściągania nie jest podpisany, następnie kończy przetwarzanie konfiguracji z powodu błędu, pokazano poniżej i wszystkie pliki tymczasowe są usuwane.</span><span class="sxs-lookup"><span data-stu-id="629a7-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Przykładowa konfiguracja danych wyjściowych błędu](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="629a7-189">Podobnie ściąganie modułu, którego katalogu nie jest podpisany powoduje następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="629a7-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Moduł wyjściowej błąd próbki](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="629a7-191">Push</span><span class="sxs-lookup"><span data-stu-id="629a7-191">Push</span></span>

<span data-ttu-id="629a7-192">Konfiguracji wydana za pomocą wypychania może niepowołane w jego źródle przed on dostarczony do tego węzła.</span><span class="sxs-lookup"><span data-stu-id="629a7-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="629a7-193">Lokalny program Configuration Manager wykonuje podobne kroki weryfikacji podpisu dla konfiguracje wciśnięcia lub opublikowany.</span><span class="sxs-lookup"><span data-stu-id="629a7-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="629a7-194">Poniżej znajduje się pełny przykład Walidacja podpisu do wypychania.</span><span class="sxs-lookup"><span data-stu-id="629a7-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="629a7-195">Włącz weryfikację podpisu na węźle.</span><span class="sxs-lookup"><span data-stu-id="629a7-195">Enable signature validation on the node.</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

- <span data-ttu-id="629a7-196">Utwórz przykładowy plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="629a7-196">Create a sample configuration file.</span></span>

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

- <span data-ttu-id="629a7-197">Spróbuj wypychanie pliku konfiguracji bez znaku do węzła.</span><span class="sxs-lookup"><span data-stu-id="629a7-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="629a7-199">Zaloguj się przy użyciu certyfikatu podpisywania kodu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="629a7-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="629a7-201">Spróbuj wypychanie podpisany plik MOF.</span><span class="sxs-lookup"><span data-stu-id="629a7-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
