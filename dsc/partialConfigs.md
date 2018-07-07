---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfiguracje częściowe PowerShell Desired State Configuration
ms.openlocfilehash: 1f5ec5bd5055ccc3d83a60712aebe635f2548828
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893005"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="cc67d-103">Konfiguracje częściowe PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="cc67d-103">PowerShell Desired State Configuration partial configurations</span></span>

> <span data-ttu-id="cc67d-104">Dotyczy: Windows PowerShell 5.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="cc67d-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="cc67d-105">W programie PowerShell 5.0 Desired State Configuration (DSC) umożliwia konfiguracje, które mają zostać dostarczone we fragmentach i z wielu źródeł.</span><span class="sxs-lookup"><span data-stu-id="cc67d-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="cc67d-106">Lokalny Menedżer konfiguracji (LCM) w docelowym węźle umieszcza fragmenty ze sobą przed zastosowaniem ich jako jedną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="cc67d-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="cc67d-107">Ta funkcja umożliwia udostępnianie kontrolę nad konfiguracją między zespołami i klientów indywidualnych.</span><span class="sxs-lookup"><span data-stu-id="cc67d-107">This capability allows sharing control of configuration between teams or individuals.</span></span>
<span data-ttu-id="cc67d-108">Na przykład jeśli co najmniej dwóch zespołów deweloperów współpracują w usłudze, może każdego chcą tworzyć konfiguracje do zarządzania ich część usługi.</span><span class="sxs-lookup"><span data-stu-id="cc67d-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="cc67d-109">Każda z tych konfiguracji może zostać pobrane z ściągnięcia różne serwery i może zostać dodany na różnych etapach cyklu rozwoju.</span><span class="sxs-lookup"><span data-stu-id="cc67d-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="cc67d-110">Konfiguracje częściowe umożliwiają także różne konkretnych osób lub zespołów kontrolować różne aspekty konfigurowanie węzłów bez konieczności koordynowania edycji dokumentu jednej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cc67d-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="cc67d-111">Na przykład jeden zespół może być odpowiedzialnego za wdrożenie maszyny Wirtualnej i systemu operacyjnego, podczas gdy inny zespół może wdrożyć inne aplikacje i usługi na tej maszynie Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="cc67d-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="cc67d-112">Za pomocą konfiguracje częściowe każdy zespół może utworzyć własną konfigurację, bez każdej z nich jest niepotrzebnie skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="cc67d-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="cc67d-113">Możesz użyć częściowe konfiguracji w trybie wypychania, tryb ściągania lub kombinacji obu.</span><span class="sxs-lookup"><span data-stu-id="cc67d-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="cc67d-114">Konfiguracje częściowe w trybie wypychania</span><span class="sxs-lookup"><span data-stu-id="cc67d-114">Partial configurations in push mode</span></span>

<span data-ttu-id="cc67d-115">Aby użyć konfiguracje częściowe w trybie wypychania, należy skonfigurować LCM w węźle docelowym, aby otrzymywać konfiguracje częściowe.</span><span class="sxs-lookup"><span data-stu-id="cc67d-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="cc67d-116">Każdy częściowe konfiguracji musi zostać przeniesiony do docelowego przy użyciu `Publish-DSCConfiguration` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc67d-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="cc67d-117">Węzeł docelowy jest następnie łączy częściowe konfiguracji w jednej konfiguracji i konfiguracji mogą być stosowane przez wywołanie metody [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc67d-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="cc67d-118">Konfigurowanie programu LCM w trybie wypychania częściowe konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cc67d-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="cc67d-119">Aby skonfigurować LCM częściowe konfiguracji w trybie wypychania, należy utworzyć **DSCLocalConfigurationManager** konfiguracji o jednym **PartialConfiguration** bloku dla każdej konfiguracji częściowe.</span><span class="sxs-lookup"><span data-stu-id="cc67d-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="cc67d-120">Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Windows Konfigurowanie programu Local Configuration Manager](/powershell/dsc/metaConfig).</span><span class="sxs-lookup"><span data-stu-id="cc67d-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/dsc/metaConfig).</span></span>
<span data-ttu-id="cc67d-121">W poniższym przykładzie pokazano konfigurację LCM, który oczekuje, że dwie konfiguracje częściowe — jedną, która wdraża system operacyjny oraz jedna, która służy do wdrażania i konfiguruje program SharePoint.</span><span class="sxs-lookup"><span data-stu-id="cc67d-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

<span data-ttu-id="cc67d-122">**RefreshMode** dla każdej konfiguracji częściowe jest ustawiony na "Wypychania".</span><span class="sxs-lookup"><span data-stu-id="cc67d-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="cc67d-123">Nazwy **PartialConfiguration** bloków (w tym przypadku "ServiceAccountConfig" i "SharePointConfig") musi być zgodna dokładnie nazwy konfiguracji, które są przekazywane do węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="cc67d-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="cc67d-124">Nazwane każdego **PartialConfiguration** bloku musi odpowiadać rzeczywista nazwa konfiguracji, co zostało określone w skrypcie konfiguracji, a nie nazwę pliku MOF, który powinien być nazwę węzła docelowego lub `localhost`.</span><span class="sxs-lookup"><span data-stu-id="cc67d-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="cc67d-125">Publikowanie i uruchamianie konfiguracje częściowe w trybie wypychania</span><span class="sxs-lookup"><span data-stu-id="cc67d-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="cc67d-126">Następnie wywołaj [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) dla każdej konfiguracji przekazywanie folderów, które zawierają dokumenty konfiguracji jako **ścieżki** parametrów.</span><span class="sxs-lookup"><span data-stu-id="cc67d-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="cc67d-127">`Publish-DSCConfiguration`umieszcza pliki MOF konfiguracji do węzłów docelowych.</span><span class="sxs-lookup"><span data-stu-id="cc67d-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="cc67d-128">Po opublikowaniu obie konfiguracje, można wywołać `Start-DSCConfiguration –UseExisting` w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="cc67d-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="cc67d-129">Na przykład, jeśli została wykonana w następujących dokumentach pliku MOF konfiguracji w węźle tworzenia pakietów administracyjnych:</span><span class="sxs-lookup"><span data-stu-id="cc67d-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="cc67d-130">Czy opublikować, a następnie uruchom konfiguracje w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cc67d-130">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="cc67d-131">Użytkownik uruchamiający [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) polecenia cmdlet, musisz mieć uprawnienia administratora w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="cc67d-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="cc67d-132">Konfiguracje częściowe w tryb ściągania</span><span class="sxs-lookup"><span data-stu-id="cc67d-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="cc67d-133">Konfiguracje częściowe mogą zostać pobrane z co najmniej jeden serwer ściągania (Aby uzyskać więcej informacji na temat serwerów ściągnięcia zobacz [Windows PowerShell Desired State Configuration ściągnięcia serwerów](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="cc67d-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="cc67d-134">Aby to zrobić, należy skonfigurować LCM w węźle docelowym w celu ściągania konfiguracje częściowe i nazwę, a zlokalizuj dokumenty konfiguracji poprawnie na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="cc67d-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="cc67d-135">Konfigurowanie programu LCM do ściągania konfiguracje węzłów</span><span class="sxs-lookup"><span data-stu-id="cc67d-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="cc67d-136">Aby skonfigurować LCM do ściągania konfiguracje częściowe z serwera ściągania, zdefiniuj serwera ściągania albo **ConfigurationRepositoryWeb** (na serwerze ściągania HTTP) lub **ConfigurationRepositoryShare** () dla serwera ściągania SMB) bloku.</span><span class="sxs-lookup"><span data-stu-id="cc67d-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="cc67d-137">Następnie utwórz **PartialConfiguration** bloki, które odwołują się do serwera ściągania przy użyciu **ConfigurationSource** właściwości.</span><span class="sxs-lookup"><span data-stu-id="cc67d-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="cc67d-138">Musisz także utworzyć **ustawienia** bloku LCM korzysta z trybu ściągania i określ **ConfigurationNames** lub **ConfigurationID** , serwerze ściągania i Użyj węzła docelowego do identyfikowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cc67d-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="cc67d-139">Następująca konfiguracja meta definiuje serwera ściągania HTTP o nazwie CONTOSO PullSrv i serwerze ściągania dwie konfiguracje częściowe, które, które używają.</span><span class="sxs-lookup"><span data-stu-id="cc67d-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="cc67d-140">Aby uzyskać więcej informacji o konfigurowaniu przy użyciu LCM **ConfigurationNames**, zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="cc67d-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span>
<span data-ttu-id="cc67d-141">Informacje o konfigurowaniu przy użyciu LCM **ConfigurationID**, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="cc67d-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="cc67d-142">Konfigurowanie programu LCM w przypadku konfiguracji tryb ściągania przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cc67d-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="cc67d-143">Konfigurowanie programu LCM w przypadku konfiguracji tryb ściągania przy użyciu ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="cc67d-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="cc67d-144">Możesz ściągnąć konfiguracje częściowe z więcej niż jednego serwera ściągania — po prostu musisz zdefiniować każdy serwer ściągania, a następnie zapoznaj się z serwerem ściągania odpowiednie w każdym **PartialConfiguration** bloku.</span><span class="sxs-lookup"><span data-stu-id="cc67d-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="cc67d-145">Po utworzeniu meta konfiguracji, należy uruchomić go do tworzenia dokumentu konfiguracji (plik MOF), a następnie wywołaj [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) skonfigurować LCM.</span><span class="sxs-lookup"><span data-stu-id="cc67d-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="cc67d-146">Nazewnictwo i wprowadzania dokumentów konfiguracji na serwerze ściągania (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="cc67d-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="cc67d-147">Dokumenty częściowe konfiguracji musi być umieszczony w folderze określonym jako **ConfigurationPath** w `web.config` plików na serwerze ściągania (zazwyczaj `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="cc67d-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="cc67d-148">Nadawanie nazw dokumentów konfiguracji na serwerze ściągania w programie PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="cc67d-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="cc67d-149">Jeśli należy pobrać tylko jeden częściowe konfiguracji z serwera ściągania poszczególnych dokumentu konfiguracji może mieć dowolną nazwę.</span><span class="sxs-lookup"><span data-stu-id="cc67d-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span>
<span data-ttu-id="cc67d-150">Jeśli należy pobrać więcej niż jeden częściowe konfiguracji z serwera ściągania dokumentu konfiguracji może mieć nazwę albo `<ConfigurationName>.mof`, gdzie *ConfigurationName* nazywa się częściowe konfiguracji lub `<ConfigurationName>.<NodeName>.mof`, gdzie  *ConfigurationName* nazywa się częściowe konfiguracji i *NodeName* jest nazwa węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="cc67d-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span>
<span data-ttu-id="cc67d-151">Dzięki temu można do ściągania konfiguracji z serwera ściągania usługi Azure Automation DSC.</span><span class="sxs-lookup"><span data-stu-id="cc67d-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="cc67d-152">Nadawanie nazw dokumentów konfiguracji na serwerze ściągania w programie PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cc67d-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="cc67d-153">Dokumenty konfiguracji musi mieć nazwę w następujący sposób: `ConfigurationName.mof`, gdzie *ConfigurationName* nazywa się częściowe konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cc67d-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="cc67d-154">W naszym przykładzie dokumentów konfiguracji powinien zostać nazwany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cc67d-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="cc67d-155">Nazewnictwo i wprowadzania dokumentów konfiguracji na serwerze ściągania (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="cc67d-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="cc67d-156">Dokumenty częściowe konfiguracji musi być umieszczony w folderze określonym jako **ConfigurationPath** w `web.config` plików na serwerze ściągania (zazwyczaj `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="cc67d-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="cc67d-157">Dokumenty konfiguracji musi mieć nazwę w następujący sposób: *ConfigurationName*.</span><span class="sxs-lookup"><span data-stu-id="cc67d-157">The configuration documents must be named as follows: *ConfigurationName*.</span></span> <span data-ttu-id="cc67d-158">\* ConfigurationID8`.mof`, gdzie *ConfigurationName* nazywa się częściowe konfiguracji i *ConfigurationID* identyfikator konfiguracji zdefiniowano LCM w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="cc67d-158">\*ConfigurationID8`.mof`, where *ConfigurationName* is the name of the partial configuration and *ConfigurationID* is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="cc67d-159">W naszym przykładzie dokumentów konfiguracji powinien zostać nazwany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cc67d-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="cc67d-160">Uruchomione konfiguracje częściowe z serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="cc67d-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="cc67d-161">Po LCM na węzeł docelowy został skonfigurowany, a konfiguracja dokumentów zostały utworzone i nazwana poprawnie na serwerze ściągania węzeł docelowy będzie pobierać konfiguracje częściowe, łączyć je i zastosować Wynikowa konfiguracja zwykłych interwały określony przez **RefreshFrequencyMins** właściwość LCM.</span><span class="sxs-lookup"><span data-stu-id="cc67d-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="cc67d-162">Jeśli chcesz wymusić odświeżenie, można wywołać [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) polecenia cmdlet, aby ściągnąć konfiguracji, a następnie `Start-DSCConfiguration –UseExisting` ich stosowania.</span><span class="sxs-lookup"><span data-stu-id="cc67d-162">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="cc67d-163">Konfiguracje częściowe w mieszanych trybach wypychania i ściągania</span><span class="sxs-lookup"><span data-stu-id="cc67d-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="cc67d-164">Możesz mieszać wypychania i ściągania tryby konfiguracje częściowe.</span><span class="sxs-lookup"><span data-stu-id="cc67d-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="cc67d-165">Oznacza to może mieć jedną konfigurację częściowe są pobierane z serwera ściągania, gdy zostanie przypisany inny częściowe konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cc67d-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="cc67d-166">Określ tryb odświeżania dla każdej konfiguracji częściowe, zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="cc67d-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span>
<span data-ttu-id="cc67d-167">Na przykład następująca konfiguracja metadanych w tym artykule opisano tym samym przykładzie, za pomocą `ServiceAccountConfig` częściowe konfiguracji w trybie ściągania i `SharePointConfig` częściowe konfiguracji w trybie wypychania.</span><span class="sxs-lookup"><span data-stu-id="cc67d-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="cc67d-168">Mieszane trybach wypychania i ściągania przy użyciu ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="cc67d-168">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="cc67d-169">Mieszane trybach wypychania i ściągania przy użyciu ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="cc67d-169">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="cc67d-170">Należy pamiętać, że **RefreshMode** określone w bloku ustawień jest "Ściągania", ale **RefreshMode** dla `SharePointConfig` częściowe konfiguracji to "Push".</span><span class="sxs-lookup"><span data-stu-id="cc67d-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="cc67d-171">Nadaj nazwę, a następnie zlokalizuj pliki MOF konfiguracji, zgodnie z powyższym opisem dla trybów ich odpowiednich odświeżania.</span><span class="sxs-lookup"><span data-stu-id="cc67d-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="cc67d-172">Wywołaj `Publish-DSCConfiguration` publikowanie `SharePointConfig` częściowe konfiguracji, a następnie poczekaj, aż `ServiceAccountConfig` konfigurację, aby zostać pobrane z serwera ściągania lub wymusić odświeżenie, wywołując [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="cc67d-172">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="cc67d-173">Przykładowa konfiguracja ServiceAccountConfig częściowego</span><span class="sxs-lookup"><span data-stu-id="cc67d-173">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration


    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential

        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig

```

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="cc67d-174">Przykładowa konfiguracja SharePointConfig częściowego</span><span class="sxs-lookup"><span data-stu-id="cc67d-174">Example SharePointConfig Partial Configuration</span></span>

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a><span data-ttu-id="cc67d-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc67d-175">See Also</span></span>

[<span data-ttu-id="cc67d-176">Program Windows PowerShell Desired State Configuration ściągnięcia serwerów</span><span class="sxs-lookup"><span data-stu-id="cc67d-176">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="cc67d-177">Windows Konfigurowanie programu Local Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="cc67d-177">Windows Configuring the Local Configuration Manager</span></span>](/powershell/dsc/metaConfig)