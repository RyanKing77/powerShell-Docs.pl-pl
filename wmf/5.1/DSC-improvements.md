---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Ulepszenia DSC w programie WMF 5.1
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085588"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="491db-103">Ulepszenia w Desired State Configuration (DSC) w programie WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="491db-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="491db-104">Ulepszenia zasobów klasy DSC</span><span class="sxs-lookup"><span data-stu-id="491db-104">DSC class resource improvements</span></span>

<span data-ttu-id="491db-105">W program WMF 5.1 usunęliśmy następujące znane problemy:</span><span class="sxs-lookup"><span data-stu-id="491db-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="491db-106">Get-DscConfiguration może zwracać wartości puste (null) lub błędy, jeśli typ tabeli złożone i skrótu jest zwracana przez funkcję Get() zasobu DSC oparte na klasach.</span><span class="sxs-lookup"><span data-stu-id="491db-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="491db-107">Get-DscConfiguration zwraca błąd, jeśli poświadczeń Uruchom jako jest używany w konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="491db-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="491db-108">Nie można używać zasobów na podstawie klasy złożonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="491db-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="491db-109">Start-DscConfiguration zawiesza się, jeśli właściwość swój własny typ oparte na klasach zasobów.</span><span class="sxs-lookup"><span data-stu-id="491db-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="491db-110">Oparte na klasach zasobów nie można użyć jako zasób wyłączności.</span><span class="sxs-lookup"><span data-stu-id="491db-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="491db-111">Zasób DSC ulepszenia debugowania</span><span class="sxs-lookup"><span data-stu-id="491db-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="491db-112">W programie WMF 5.0 debuger programu PowerShell nie zatrzymają w metodzie oparte na klasach zasobów (Get/Set/Test) bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="491db-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="491db-113">W program WMF 5.1 debuger zatrzymuje się na metody oparte na klasach zasobów w taki sam sposób jak w przypadku metod zasoby oparte na pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="491db-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="491db-114">DSC pull klient obsługuje protokół TLS 1.1 i TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="491db-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="491db-115">Wcześniej klienta ściągania DSC obsługiwane tylko SSL3.0 lub TLS1.0 za pośrednictwem połączenia HTTPS.</span><span class="sxs-lookup"><span data-stu-id="491db-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="491db-116">Przy wymuszonego, aby użyć bardziej bezpieczne protokoły, klienta ściągania może przestać działać.</span><span class="sxs-lookup"><span data-stu-id="491db-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="491db-117">W program WMF 5.1 klienta ściągania DSC nie są już obsługuje protokół SSL 3.0 i dodaje obsługę bardziej bezpieczne protokoły TLS 1.1 i TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="491db-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="491db-118">Rejestracja serwera ściągania ulepszone</span><span class="sxs-lookup"><span data-stu-id="491db-118">Improved pull server registration</span></span>

<span data-ttu-id="491db-119">We wcześniejszych wersjach programu WMF równoczesnych rejestracji/zgłoszenie żądania do serwera ściągania DSC podczas korzystania z bazy danych ESENT doprowadziłoby do LCM, których nie można zarejestrować i/lub raportu.</span><span class="sxs-lookup"><span data-stu-id="491db-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="491db-120">W takiej sytuacji dzienniki zdarzeń na serwerze ściągania występuje błąd "Nazwa wystąpienia już w użyciu".</span><span class="sxs-lookup"><span data-stu-id="491db-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="491db-121">Jest to spowodowane nieprawidłowy wzorzec używany do uzyskiwania ESENT bazy danych w scenariuszu wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="491db-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="491db-122">Ten problem został rozwiązany w program WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="491db-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="491db-123">Jednoczesnych rejestracji lub raportowania (obejmujące ESENT bazy danych) działa poprawnie WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="491db-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="491db-124">Ten problem ma zastosowanie tylko do bazy danych ESENT i nie ma zastosowania do bazy danych OLE DB.</span><span class="sxs-lookup"><span data-stu-id="491db-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="491db-125">Włącz dziennik cykliczne w wystąpieniu bazy danych ESENT</span><span class="sxs-lookup"><span data-stu-id="491db-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="491db-126">W wersji eariler DSC PullServer pliki dziennika bazy danych ESENT zostały zapełnia się miejsca na dysku becouse pullserver, utworzenia wystąpienia bazy danych jest bez logowanie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="491db-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="491db-127">W tej wersji masz możliwość sterowania zachowaniem tego wystąpienia przy użyciu pliku web.config pullserver logowanie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="491db-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="491db-128">Domyślnie CircularLogging jest ustawiona na wartość TRUE.</span><span class="sxs-lookup"><span data-stu-id="491db-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="491db-129">Ściągnij konwencji nazewnictwa częściowe konfiguracji</span><span class="sxs-lookup"><span data-stu-id="491db-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="491db-130">W poprzedniej wersji konwencji nazewnictwa częściowe konfiguracji został, czy nazwa pliku MOF usługi ściągania serwer/powinna odpowiadać nazwie częściowe konfiguracji, w określonego w ustawieniach Menedżera konfiguracji lokalnej, które z kolei muszą być zgodne Nazwa konfiguracji jest osadzony w pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="491db-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="491db-131">Zobacz poniższe migawki:</span><span class="sxs-lookup"><span data-stu-id="491db-131">See the snapshots below:</span></span>

- <span data-ttu-id="491db-132">Ustawienia konfiguracji lokalnej, które definiuje częściowe konfiguracji, który węzeł może odbierać.</span><span class="sxs-lookup"><span data-stu-id="491db-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Przykładowe metaconfiguration](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="491db-134">Przykładowa definicja częściowe konfiguracji</span><span class="sxs-lookup"><span data-stu-id="491db-134">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="491db-135">"ConfigurationName" osadzona w wygenerowanym pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="491db-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![Przykładowy plik mof wygenerowany](../images/PartialGeneratedMof.png)

- <span data-ttu-id="491db-137">Nazwa pliku w repozytorium konfiguracji ściągania</span><span class="sxs-lookup"><span data-stu-id="491db-137">FileName in the pull configuration repository</span></span>

![Nazwa pliku w repozytorium konfiguracji](../images/PartialInConfigRepository.png)

<span data-ttu-id="491db-139">Nazwa usługi w usłudze Azure Automation wygenerowanych plików MOF jako `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="491db-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="491db-140">Dlatego konfiguracji poniżej kompiluje, aby PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="491db-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="491db-141">To uniemożliwił do ściągnięcia jeden częściowe konfiguracji z usługi Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="491db-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

<span data-ttu-id="491db-142">W program WMF 5.1 częściowe konfiguracji w pull server/service może mieć nazwę jako `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="491db-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="491db-143">Ponadto jeśli maszyna jest ściąganie konfiguracji jednego z ściąganie usługa następnie plik konfiguracji do repozytorium konfiguracji serwera ściągania mogą mieć dowolną nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="491db-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="491db-144">Ta elastyczność nazewnictwa pozwala na zarządzanie węzły częściowo przez usługę Azure Automation, gdzie niektóre konfiguracji dla węzła pochodzi z usługi Azure Automation DSC i częściowe konfiguracji, który można zarządzać lokalnie.</span><span class="sxs-lookup"><span data-stu-id="491db-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="491db-145">Metaconfiguration poniżej skonfigurowanie węzła jako zarządzane, zarówno lokalnie, jak również przez usługę Azure Automation do usługi.</span><span class="sxs-lookup"><span data-stu-id="491db-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="491db-146">Za pomocą PsDscRunAsCredential za pomocą DSC zasoby złożone</span><span class="sxs-lookup"><span data-stu-id="491db-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="491db-147">Dodaliśmy obsługę [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) za pomocą DSC [złożonego](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) zasobów.</span><span class="sxs-lookup"><span data-stu-id="491db-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="491db-148">Teraz można określić wartość dla PsDscRunAsCredential, korzystając z zasoby złożone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="491db-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="491db-149">Jeśli zostanie określony, wszystkie zasoby są uruchamiane wewnątrz złożonego zasobów w jako użytkownika Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="491db-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="491db-150">Złożone zasobów wywołuje inny zasób złożonego, wszystkie jej zasoby są również wykonywane jako użytkownika Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="491db-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="491db-151">Poświadczenia programu RunAs są propagowane do dowolnego poziomu hierarchii złożonego zasobów.</span><span class="sxs-lookup"><span data-stu-id="491db-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="491db-152">Jeśli dowolny zasób wewnątrz złożonego zasobu określa jego własnej wartości dla PsDscRunAsCredential, powoduje błąd scalania, podczas kompilacji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="491db-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="491db-153">W tym przykładzie przedstawiono sposób użycia za pomocą [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) złożonego zasobów zawartych w PSDesiredStateConfiguration module.</span><span class="sxs-lookup"><span data-stu-id="491db-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="491db-154">Moduł DSC i podpisywania operacji sprawdzania poprawności konfiguracji</span><span class="sxs-lookup"><span data-stu-id="491db-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="491db-155">W DSC konfiguracji i modułów są dystrybuowane do komputerów zarządzanych z serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="491db-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="491db-156">W przypadku naruszenia zabezpieczeń serwera ściągania osoba atakująca może potencjalnie modyfikowania konfiguracji i modułów na serwerze ściągania i jest dystrybuowane do wszystkich zarządzanych węzłów, wszystkich z nich naruszenie.</span><span class="sxs-lookup"><span data-stu-id="491db-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="491db-157">Program WMF 5.1 DSC obsługuje sprawdzanie podpisów cyfrowych w katalogu i konfiguracji (. Pliki MOF).</span><span class="sxs-lookup"><span data-stu-id="491db-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="491db-158">Ta funkcja zapobiega wykonywania konfiguracji lub plikach modułów, które nie są podpisane przez zaufane osoby podpisującej lub które zostały naruszone po zostały podpisane przez zaufane osoby podpisującej węzłów.</span><span class="sxs-lookup"><span data-stu-id="491db-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="491db-159">Jak zarejestrować konfiguracji i modułów</span><span class="sxs-lookup"><span data-stu-id="491db-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="491db-160">Pliki konfiguracji (. Pliki MOF): Istniejące polecenia cmdlet programu PowerShell [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) jest rozszerzona na potrzeby obsługi podpisywania plików MOF.</span><span class="sxs-lookup"><span data-stu-id="491db-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="491db-161">Moduły: Podpisywanie modułów można to zrobić, rejestrując odpowiedniego katalogu modułu wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="491db-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="491db-162">Utwórz plik w katalogu: Plik wykazu zawiera zbiór skróty kryptograficzne lub odciski palców.</span><span class="sxs-lookup"><span data-stu-id="491db-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="491db-163">Każdy odcisk palca odnosi się do pliku, który znajduje się w module.</span><span class="sxs-lookup"><span data-stu-id="491db-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="491db-164">Nowe polecenie cmdlet [New FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), została dodana do Zezwól użytkownikom na tworzenie plik katalogu dla swojego modułu.</span><span class="sxs-lookup"><span data-stu-id="491db-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="491db-165">Utwórz plik w katalogu: Użyj [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) do podpisania pliku wykazu.</span><span class="sxs-lookup"><span data-stu-id="491db-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="491db-166">Umieść plik wykazu znajdujące się w folderze modułu.</span><span class="sxs-lookup"><span data-stu-id="491db-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="491db-167">Zgodnie z Konwencją plik do katalogu modułu powinna zostać umieszczona w folderze modułu o nazwie identycznej z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="491db-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="491db-168">Ustawienia LocalConfigurationManager, aby umożliwić sprawdzanie poprawności podpisywania</span><span class="sxs-lookup"><span data-stu-id="491db-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="491db-169">Ściągnij</span><span class="sxs-lookup"><span data-stu-id="491db-169">Pull</span></span>

<span data-ttu-id="491db-170">LocalConfigurationManager węzła przeprowadza weryfikację podpisywania modułów i konfiguracji, w oparciu o bieżące ustawienia.</span><span class="sxs-lookup"><span data-stu-id="491db-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="491db-171">Domyślnie Weryfikacja podpisu jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="491db-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="491db-172">Weryfikacja podpisu można włączyć poprzez dodanie bloku "SignatureValidation" do definicji metadanych konfiguracji węzła jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="491db-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="491db-173">Ustawienie metaconfiguration powyżej w węźle umożliwia weryfikację podpisu na konfiguracje pobrane i modułów.</span><span class="sxs-lookup"><span data-stu-id="491db-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="491db-174">Local Configuration Manager wykonuje następujące kroki, aby sprawdzanie podpisów cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="491db-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="491db-175">Weryfikuje podpis w pliku konfiguracji (. MOF) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="491db-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="491db-176">Używa polecenia cmdlet programu PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), który jest rozszerzony w 5.1 do obsługi sprawdzania poprawności podpisu pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="491db-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="491db-177">Sprawdź, czy urząd certyfikacji, który autoryzowane osoby podpisującej jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="491db-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="491db-178">Pobierz moduł lub zasobu zależności w konfiguracji w tymczasowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="491db-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="491db-179">Zweryfikować podpisu wykazu zawarte wewnątrz modułu.</span><span class="sxs-lookup"><span data-stu-id="491db-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="491db-180">Znajdź `<moduleName>.cat` i sprawdzić jego podpisu, używając polecenia cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="491db-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="491db-181">Sprawdź, czy urząd certyfikacji, który uwierzytelnił podpisującego jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="491db-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="491db-182">Sprawdź, nie został zmodyfikowany zawartość modułów za pomocą nowego polecenia cmdlet [FileCatalog testu](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="491db-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="491db-183">Install-Module do $env: ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="491db-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="491db-184">Konfiguracja procesu</span><span class="sxs-lookup"><span data-stu-id="491db-184">Process configuration</span></span>

> <span data-ttu-id="491db-185">Uwaga: Weryfikacja podpisu na katalog modułu i konfiguracji jest realizowane wyłącznie, gdy po raz pierwszy lub w przypadku, gdy moduł jest pobierany i instalowany, konfiguracja jest stosowana do systemu.</span><span class="sxs-lookup"><span data-stu-id="491db-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="491db-186">Przebiegi spójności nie weryfikują podpisu Current.mof lub jego zależności modułu.</span><span class="sxs-lookup"><span data-stu-id="491db-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="491db-187">Jeśli weryfikacja nie powiodła się na każdym etapie, na przykład jeśli konfiguracji są pobierane z serwera ściągania jest podpisany, a następnie przetwarzania konfiguracji kończy się błędem pokazany poniżej i zostaną usunięte wszystkie pliki tymczasowe.</span><span class="sxs-lookup"><span data-stu-id="491db-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Przykładowa konfiguracja danych wyjściowych błędu](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="491db-189">Podobnie ściąganie modułu, którego katalog nie jest podpisany wyniki w następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="491db-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Przykładowe błąd danych wyjściowych modułu](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="491db-191">wypychania</span><span class="sxs-lookup"><span data-stu-id="491db-191">Push</span></span>

<span data-ttu-id="491db-192">Konfiguracja dostarczane za pomocą instalacji wypychanej może dało się w ich źródle przed dostarczeniem jej do węzła.</span><span class="sxs-lookup"><span data-stu-id="491db-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="491db-193">Local Configuration Manager wykonuje podobne kroki weryfikacji podpisu konfiguracje nastąpiło wypychanie oraz opublikowane.</span><span class="sxs-lookup"><span data-stu-id="491db-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="491db-194">Poniżej znajduje się pełny przykład Weryfikacja podpisu do wypychania.</span><span class="sxs-lookup"><span data-stu-id="491db-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="491db-195">Włącz weryfikację podpisu na węźle.</span><span class="sxs-lookup"><span data-stu-id="491db-195">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="491db-196">Utwórz przykładowy plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="491db-196">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="491db-197">Spróbuj wypychaniu można znaleźć pliku konfiguracji bez znaku w do węzła.</span><span class="sxs-lookup"><span data-stu-id="491db-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="491db-199">Zaloguj się przy użyciu certyfikatu podpisywania kodu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="491db-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="491db-201">Spróbuj wypychanie podpisany plik MOF.</span><span class="sxs-lookup"><span data-stu-id="491db-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
