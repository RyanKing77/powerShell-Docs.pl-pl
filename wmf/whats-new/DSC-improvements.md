---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Ulepszenia DSC w programie WMF 5.1
ms.openlocfilehash: e7f20bfa865777aeac8f083959782317cfdf6cde
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856231"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="72d55-103">Ulepszenia w Desired State Configuration (DSC) w programie WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="72d55-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="72d55-104">Ulepszenia zasobów klasy DSC</span><span class="sxs-lookup"><span data-stu-id="72d55-104">DSC class resource improvements</span></span>

<span data-ttu-id="72d55-105">W program WMF 5.1 usunęliśmy następujące znane problemy:</span><span class="sxs-lookup"><span data-stu-id="72d55-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="72d55-106">Get-DscConfiguration może zwracać wartości puste (null) lub błędy, jeśli typ tabeli złożone i skrótu jest zwracana przez funkcję Get() zasobu DSC oparte na klasach.</span><span class="sxs-lookup"><span data-stu-id="72d55-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="72d55-107">Get-DscConfiguration zwraca błąd, jeśli poświadczeń Uruchom jako jest używany w konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="72d55-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="72d55-108">Nie można używać zasobów na podstawie klasy złożonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="72d55-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="72d55-109">Start-DscConfiguration zawiesza się, jeśli właściwość swój własny typ oparte na klasach zasobów.</span><span class="sxs-lookup"><span data-stu-id="72d55-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="72d55-110">Oparte na klasach zasobów nie można użyć jako zasób wyłączności.</span><span class="sxs-lookup"><span data-stu-id="72d55-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="72d55-111">Zasób DSC ulepszenia debugowania</span><span class="sxs-lookup"><span data-stu-id="72d55-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="72d55-112">W programie WMF 5.0 debuger programu PowerShell nie zatrzymają w metodzie oparte na klasach zasobów (Get/Set/Test) bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="72d55-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="72d55-113">W program WMF 5.1 debuger zatrzymuje się na metody oparte na klasach zasobów w taki sam sposób jak w przypadku metod zasoby oparte na pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="72d55-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="72d55-114">DSC pull klient obsługuje protokół TLS 1.1 i TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="72d55-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="72d55-115">Wcześniej klienta ściągania DSC obsługiwane tylko SSL3.0 lub TLS1.0 za pośrednictwem połączenia HTTPS.</span><span class="sxs-lookup"><span data-stu-id="72d55-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="72d55-116">Przy wymuszonego, aby użyć bardziej bezpieczne protokoły, klienta ściągania może przestać działać.</span><span class="sxs-lookup"><span data-stu-id="72d55-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="72d55-117">W program WMF 5.1 klienta ściągania DSC nie są już obsługuje protokół SSL 3.0 i dodaje obsługę bardziej bezpieczne protokoły TLS 1.1 i TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="72d55-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="72d55-118">Rejestracja serwera ściągania ulepszone</span><span class="sxs-lookup"><span data-stu-id="72d55-118">Improved pull server registration</span></span>

<span data-ttu-id="72d55-119">We wcześniejszych wersjach programu WMF równoczesnych rejestracji/zgłoszenie żądania do serwera ściągania DSC podczas korzystania z bazy danych ESENT doprowadziłoby do LCM, których nie można zarejestrować i/lub raportu.</span><span class="sxs-lookup"><span data-stu-id="72d55-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="72d55-120">W takiej sytuacji dzienniki zdarzeń na serwerze ściągania występuje błąd "Nazwa wystąpienia już w użyciu".</span><span class="sxs-lookup"><span data-stu-id="72d55-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="72d55-121">Było to spowodowane przez nieprawidłowy wzorzec używany do uzyskiwania ESENT bazy danych w scenariuszu wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="72d55-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="72d55-122">Ten problem został rozwiązany w program WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="72d55-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="72d55-123">Jednoczesnych rejestracji lub raportowania (obejmujące ESENT bazy danych) działa poprawnie WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="72d55-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="72d55-124">Ten problem ma zastosowanie tylko do bazy danych ESENT i nie ma zastosowania do bazy danych OLE DB.</span><span class="sxs-lookup"><span data-stu-id="72d55-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="72d55-125">Włącz dziennik cykliczne w wystąpieniu bazy danych ESENT</span><span class="sxs-lookup"><span data-stu-id="72d55-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="72d55-126">W wersji eariler DSC PullServer pliki dziennika bazy danych ESENT zostały zapełnia się miejsca na dysku becouse pullserver, utworzenia wystąpienia bazy danych jest bez logowanie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="72d55-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="72d55-127">W tej wersji masz możliwość sterowania zachowaniem tego wystąpienia przy użyciu pliku web.config pullserver logowanie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="72d55-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="72d55-128">Domyślnie CircularLogging jest ustawiona na wartość TRUE.</span><span class="sxs-lookup"><span data-stu-id="72d55-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="72d55-129">Obsługa środowiska WOW64 na potrzeby słowa kluczowego konfiguracji</span><span class="sxs-lookup"><span data-stu-id="72d55-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="72d55-130">`Configuration` — Słowo kluczowe jest teraz obsługiwana w emulatorze WOW64 na komputerze 64-bitowym.</span><span class="sxs-lookup"><span data-stu-id="72d55-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="72d55-131">Oznacza to, że konfiguracji DSC mogą być definiowane i kompilowany w obrębie 32-bitowy proces takich jak Windows PowerShell ISE (x 86) uruchomionego na komputerze 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="72d55-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="72d55-132">Ściągnij konwencji nazewnictwa częściowe konfiguracji</span><span class="sxs-lookup"><span data-stu-id="72d55-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="72d55-133">W poprzedniej wersji konwencji nazewnictwa częściowe konfiguracji został, czy nazwa pliku MOF usługi ściągania serwer/powinna odpowiadać nazwie częściowe konfiguracji, w określonego w ustawieniach Menedżera konfiguracji lokalnej, które z kolei muszą być zgodne Nazwa konfiguracji jest osadzony w pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="72d55-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="72d55-134">Zobacz poniższe migawki:</span><span class="sxs-lookup"><span data-stu-id="72d55-134">See the snapshots below:</span></span>

- <span data-ttu-id="72d55-135">Ustawienia konfiguracji lokalnej, które definiuje częściowe konfiguracji, który węzeł może odbierać.</span><span class="sxs-lookup"><span data-stu-id="72d55-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Przykładowe metaconfiguration](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="72d55-137">Przykładowa definicja częściowe konfiguracji</span><span class="sxs-lookup"><span data-stu-id="72d55-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="72d55-138">"ConfigurationName" osadzona w wygenerowanym pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="72d55-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Przykładowy plik mof wygenerowany](../images/PartialGeneratedMof.png)

- <span data-ttu-id="72d55-140">Nazwa pliku w repozytorium konfiguracji ściągania</span><span class="sxs-lookup"><span data-stu-id="72d55-140">FileName in the pull configuration repository</span></span>

  ![Nazwa pliku w repozytorium konfiguracji](../images/PartialInConfigRepository.png)

  <span data-ttu-id="72d55-142">Nazwa usługi w usłudze Azure Automation wygenerowanych plików MOF jako `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="72d55-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="72d55-143">Dlatego konfiguracji poniżej kompiluje, aby PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="72d55-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="72d55-144">To uniemożliwił do ściągnięcia jeden częściowe konfiguracji z usługi Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="72d55-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="72d55-145">W program WMF 5.1 częściowe konfiguracji w pull server/service może mieć nazwę jako `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="72d55-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="72d55-146">Ponadto jeśli maszyna jest ściąganie konfiguracji jednego z ściąganie usługa następnie plik konfiguracji do repozytorium konfiguracji serwera ściągania mogą mieć dowolną nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="72d55-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="72d55-147">Ta elastyczność nazewnictwa pozwala na zarządzanie węzły częściowo przez usługę Azure Automation, gdzie niektóre konfiguracji dla węzła pochodzi z usługi Azure Automation DSC i częściowe konfiguracji, który można zarządzać lokalnie.</span><span class="sxs-lookup"><span data-stu-id="72d55-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="72d55-148">Metaconfiguration poniżej skonfigurowanie węzła jako zarządzane, zarówno lokalnie, jak również przez usługę Azure Automation do usługi.</span><span class="sxs-lookup"><span data-stu-id="72d55-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="72d55-149">Za pomocą PsDscRunAsCredential za pomocą DSC zasoby złożone</span><span class="sxs-lookup"><span data-stu-id="72d55-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="72d55-150">Dodaliśmy obsługę [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) za pomocą DSC [złożonego](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) zasobów.</span><span class="sxs-lookup"><span data-stu-id="72d55-150">We have added support for using [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="72d55-151">Teraz można określić wartość dla **PsDscRunAsCredential** korzystając zasoby złożone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="72d55-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="72d55-152">Jeśli zostanie określony, wszystkie zasoby są uruchamiane wewnątrz złożonego zasobów w jako użytkownika Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="72d55-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="72d55-153">Jeśli złożonego zasobów wywołuje inny zasób złożonego, te zasoby również są wykonywane jako użytkownika Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="72d55-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="72d55-154">Poświadczenia programu RunAs są propagowane do dowolnego poziomu hierarchii złożonego zasobów.</span><span class="sxs-lookup"><span data-stu-id="72d55-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="72d55-155">Określa wartość dla dowolnego zasobu wewnątrz złożonego zasobów **PsDscRunAsCredential**, błąd scalania wyniki podczas kompilacji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="72d55-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="72d55-156">W tym przykładzie przedstawiono sposób użycia za pomocą [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) złożonego zasobów zawartych w PSDesiredStateConfiguration module.</span><span class="sxs-lookup"><span data-stu-id="72d55-156">This example shows usage with the [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="72d55-157">Zezwalanie na identycznych powielonych zasobów w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="72d55-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="72d55-158">DSC Zezwalaj lub nie obsługiwać sprzeczne definicje zasobów w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="72d55-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="72d55-159">Zamiast próbować rozwiązać konflikt, ją po prostu nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="72d55-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="72d55-160">Jak ponowne użycie konfiguracji staje się bardziej wykorzystywany przez zasoby złożone, konflikty itp. nastąpi częściej.</span><span class="sxs-lookup"><span data-stu-id="72d55-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="72d55-161">W przypadku identyczne sprzecznych definicji zasobu DSC należy inteligentne i zezwolić na to.</span><span class="sxs-lookup"><span data-stu-id="72d55-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="72d55-162">W tej wersji obsługiwane jest posiadanie wielu wystąpień zasobów, które mają identyczne definicje:</span><span class="sxs-lookup"><span data-stu-id="72d55-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="72d55-163">W poprzednich wersjach wynik będzie, że zainstalowano kompilacji nie powiodło się z powodu konfliktu między WindowsFeature FE_IIS i wystąpień WindowsFeature Worker_IIS próby zapewnienia rolę "Serwer sieci Web".</span><span class="sxs-lookup"><span data-stu-id="72d55-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="72d55-164">Należy zauważyć, że *wszystkich* właściwości, które są konfigurowane są identyczne w dwóch konfiguracjach.</span><span class="sxs-lookup"><span data-stu-id="72d55-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="72d55-165">Ponieważ *wszystkich* właściwości w te dwa zasoby są identyczne, wynikiem będzie teraz pomyślnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="72d55-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="72d55-166">Jeśli dowolne z właściwości różnią się między dwa zasoby, one nie zostanie uwzględniony identyczne i kompilacja zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="72d55-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="72d55-167">Moduł DSC i podpisywania operacji sprawdzania poprawności konfiguracji</span><span class="sxs-lookup"><span data-stu-id="72d55-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="72d55-168">W DSC konfiguracji i modułów są dystrybuowane do komputerów zarządzanych z serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="72d55-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="72d55-169">W przypadku naruszenia zabezpieczeń serwera ściągania osoba atakująca może potencjalnie modyfikować konfiguracje i modułów na serwerze ściągania i jest dystrybuowane do wszystkich zarządzanych węzłów.</span><span class="sxs-lookup"><span data-stu-id="72d55-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="72d55-170">Program WMF 5.1 DSC obsługuje sprawdzanie podpisów cyfrowych w katalogu i konfiguracji (. Pliki MOF).</span><span class="sxs-lookup"><span data-stu-id="72d55-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="72d55-171">Ta funkcja zapobiega wykonywania konfiguracji lub plikach modułów, które nie są podpisane przez zaufane osoby podpisującej lub które zostały naruszone po zostały podpisane przez zaufane osoby podpisującej węzłów.</span><span class="sxs-lookup"><span data-stu-id="72d55-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="72d55-172">Jak zarejestrować konfiguracji i modułów</span><span class="sxs-lookup"><span data-stu-id="72d55-172">How to sign configuration and module</span></span>

- <span data-ttu-id="72d55-173">Pliki konfiguracji (. Pliki MOF): Istniejące polecenia cmdlet programu PowerShell [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) jest rozszerzona na potrzeby obsługi podpisywania plików MOF.</span><span class="sxs-lookup"><span data-stu-id="72d55-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="72d55-174">Moduły: Podpisywanie modułów można to zrobić, rejestrując odpowiedniego katalogu modułu wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="72d55-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="72d55-175">Utwórz plik w katalogu: Plik wykazu zawiera zbiór skróty kryptograficzne lub odciski palców.</span><span class="sxs-lookup"><span data-stu-id="72d55-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="72d55-176">Każdy odcisk palca odnosi się do pliku, który znajduje się w module.</span><span class="sxs-lookup"><span data-stu-id="72d55-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="72d55-177">Nowe polecenie cmdlet [New FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), została dodana do Zezwól użytkownikom na tworzenie plik katalogu dla swojego modułu.</span><span class="sxs-lookup"><span data-stu-id="72d55-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="72d55-178">Utwórz plik w katalogu: Użyj [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) do podpisania pliku wykazu.</span><span class="sxs-lookup"><span data-stu-id="72d55-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="72d55-179">Umieść plik wykazu znajdujące się w folderze modułu.</span><span class="sxs-lookup"><span data-stu-id="72d55-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="72d55-180">Zgodnie z Konwencją plik do katalogu modułu powinna zostać umieszczona w folderze modułu o nazwie identycznej z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="72d55-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="72d55-181">Ustawienia LocalConfigurationManager, aby umożliwić sprawdzanie poprawności podpisywania</span><span class="sxs-lookup"><span data-stu-id="72d55-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="72d55-182">Ściągnij</span><span class="sxs-lookup"><span data-stu-id="72d55-182">Pull</span></span>

<span data-ttu-id="72d55-183">LocalConfigurationManager węzła przeprowadza weryfikację podpisywania modułów i konfiguracji, w oparciu o bieżące ustawienia.</span><span class="sxs-lookup"><span data-stu-id="72d55-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="72d55-184">Domyślnie Weryfikacja podpisu jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="72d55-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="72d55-185">Weryfikacja podpisu można włączyć poprzez dodanie bloku "SignatureValidation" do definicji metadanych konfiguracji węzła jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="72d55-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="72d55-186">Ustawienie metaconfiguration powyżej w węźle umożliwia weryfikację podpisu na konfiguracje pobrane i modułów.</span><span class="sxs-lookup"><span data-stu-id="72d55-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="72d55-187">Local Configuration Manager wykonuje następujące kroki, aby sprawdzanie podpisów cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="72d55-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="72d55-188">Weryfikuje podpis w pliku konfiguracji (. Nadaje MOF) przy użyciu `Get-AuthenticodeSignature` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72d55-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="72d55-189">Sprawdź, czy urząd certyfikacji, który autoryzowane osoby podpisującej jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="72d55-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="72d55-190">Pobierz moduł lub zasobu zależności w konfiguracji w tymczasowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="72d55-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="72d55-191">Zweryfikować podpisu wykazu zawarte wewnątrz modułu.</span><span class="sxs-lookup"><span data-stu-id="72d55-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="72d55-192">Znajdź `<moduleName>.cat` i sprawdzić jego za pomocą podpisu `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="72d55-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="72d55-193">Sprawdź, czy urząd certyfikacji, który uwierzytelnił podpisującego jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="72d55-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="72d55-194">Sprawdź, nie został zmodyfikowany zawartość modułów za pomocą nowego polecenia cmdlet `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="72d55-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="72d55-195">`Install-Module` Aby `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="72d55-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="72d55-196">Konfiguracja procesu</span><span class="sxs-lookup"><span data-stu-id="72d55-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="72d55-197">Weryfikacja podpisu na katalog modułu i konfiguracji jest realizowane wyłącznie, gdy po raz pierwszy lub w przypadku, gdy moduł jest pobierany i instalowany, konfiguracja jest stosowana do systemu.</span><span class="sxs-lookup"><span data-stu-id="72d55-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="72d55-198">Przebiegi spójności nie weryfikują podpisu Current.mof lub jego zależności modułu.</span><span class="sxs-lookup"><span data-stu-id="72d55-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="72d55-199">Jeśli weryfikacja nie powiodła się na każdym etapie, na przykład jeśli konfiguracji są pobierane z serwera ściągania jest podpisany, a następnie przetwarzania konfiguracji kończy się błędem pokazany poniżej i zostaną usunięte wszystkie pliki tymczasowe.</span><span class="sxs-lookup"><span data-stu-id="72d55-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Przykładowa konfiguracja danych wyjściowych błędu](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="72d55-201">Podobnie ściąganie modułu, którego katalog nie jest podpisany wyniki w następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="72d55-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Przykładowe błąd danych wyjściowych modułu](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="72d55-203">wypychania</span><span class="sxs-lookup"><span data-stu-id="72d55-203">Push</span></span>

<span data-ttu-id="72d55-204">Konfiguracja dostarczane za pomocą instalacji wypychanej może dało się w ich źródle przed dostarczeniem jej do węzła.</span><span class="sxs-lookup"><span data-stu-id="72d55-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="72d55-205">Local Configuration Manager wykonuje podobne kroki weryfikacji podpisu konfiguracje nastąpiło wypychanie oraz opublikowane.</span><span class="sxs-lookup"><span data-stu-id="72d55-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="72d55-206">Poniżej znajduje się pełny przykład Weryfikacja podpisu do wypychania.</span><span class="sxs-lookup"><span data-stu-id="72d55-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="72d55-207">Włącz weryfikację podpisu na węźle.</span><span class="sxs-lookup"><span data-stu-id="72d55-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="72d55-208">Utwórz przykładowy plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="72d55-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="72d55-209">Spróbuj wypychaniu można znaleźć pliku konfiguracji bez znaku w do węzła.</span><span class="sxs-lookup"><span data-stu-id="72d55-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="72d55-211">Zaloguj się przy użyciu certyfikatu podpisywania kodu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="72d55-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="72d55-213">Spróbuj wypychanie podpisany plik MOF.</span><span class="sxs-lookup"><span data-stu-id="72d55-213">Try pushing the signed MOF file.</span></span>

  ![SignMofFile](../images/PushSignedMof.png)
