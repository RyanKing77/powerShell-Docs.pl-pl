---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Konfiguracje częściowe konfiguracji żądanego stanu programu PowerShell"
ms.openlocfilehash: 2c5f29ee2940f4b7955219e97275ffa2695f9dee
ms.sourcegitcommit: aa6890031dad3f2981b24c58893d134bdf4e8655
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2017
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="4f25a-103">Konfiguracje częściowe konfiguracji żądanego stanu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f25a-103">PowerShell Desired State Configuration partial configurations</span></span>

><span data-ttu-id="4f25a-104">Dotyczy: Środowiska Windows PowerShell 5.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="4f25a-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="4f25a-105">W programie PowerShell 5.0 konfiguracji żądanego stanu (DSC) umożliwia konfiguracje, które mają zostać dostarczone w fragmentów i z wielu źródeł.</span><span class="sxs-lookup"><span data-stu-id="4f25a-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="4f25a-106">Lokalne Menedżera konfiguracji (LCM) w docelowym węźle umieszcza fragmentów razem przed ich zastosowaniem jako pojedynczą konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="4f25a-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="4f25a-107">Ta funkcja pozwala na udostępnianie kontroli konfigurację między zespołami lub osoby.</span><span class="sxs-lookup"><span data-stu-id="4f25a-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="4f25a-108">Na przykład jeśli co najmniej dwóch zespołów deweloperów współpracują w usłudze, może każdego chcą tworzyć konfiguracje do zarządzania ich należącej do usługi.</span><span class="sxs-lookup"><span data-stu-id="4f25a-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="4f25a-109">Każdy z tych konfiguracji można ściągnąć z różnych ściągania serwerów i mogą zostać dodane na różnych etapach rozwoju.</span><span class="sxs-lookup"><span data-stu-id="4f25a-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="4f25a-110">Konfiguracje z częściowa również umożliwić różnych konkretnych osób lub zespołów kontrolować różne aspekty konfigurowanie węzłów bez konieczności koordynować edycji konfiguracji pojedynczego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4f25a-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="4f25a-111">Na przykład jeden zespół może być odpowiedzialnych za wdrażanie maszyny Wirtualnej i systemu operacyjnego, podczas gdy inny zespół może wdrożyć inne aplikacje i usługi na danej maszynie Wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="4f25a-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="4f25a-112">Z częściowa konfiguracje każdego zespołu można utworzyć własną konfigurację, bez żadnej z nich jest niepotrzebnie skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="4f25a-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="4f25a-113">Możesz użyć częściowe konfiguracje w trybie wypychania, tryb ściągania lub kombinację obu.</span><span class="sxs-lookup"><span data-stu-id="4f25a-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="4f25a-114">Częściowe konfiguracje w trybie push</span><span class="sxs-lookup"><span data-stu-id="4f25a-114">Partial configurations in push mode</span></span>
<span data-ttu-id="4f25a-115">Aby używać częściowej konfiguracje w trybie wypychania, należy skonfigurować LCM w docelowym węźle do odbierania z częściowa konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="4f25a-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="4f25a-116">Każdej z częściowa konfiguracji musi zostać przeniesiony do docelowego za pomocą polecenia cmdlet Publish-DSCConfiguration.</span><span class="sxs-lookup"><span data-stu-id="4f25a-116">Each partial configuration must be pushed to the target by using the Publish-DSCConfiguration cmdlet.</span></span> <span data-ttu-id="4f25a-117">Węzeł docelowy następnie łączy częściowe konfiguracji w pojedynczą konfiguracją i można zastosować konfiguracji przez wywołanie metody [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f25a-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="4f25a-118">Konfigurowanie LCM częściowe konfiguracji trybu wypychania</span><span class="sxs-lookup"><span data-stu-id="4f25a-118">Configuring the LCM for push-mode partial configurations</span></span>
<span data-ttu-id="4f25a-119">Aby skonfigurować LCM w przypadku konfiguracji z częściowa w trybie wypychania, należy utworzyć **DSCLocalConfigurationManager** konfiguracji z jednego **PartialConfiguration** blok dla każdej z częściowa konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4f25a-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="4f25a-120">Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager systemu Windows](https://technet.microsoft.com/en-us/library/mt421188.aspx).</span><span class="sxs-lookup"><span data-stu-id="4f25a-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](https://technet.microsoft.com/en-us/library/mt421188.aspx).</span></span> <span data-ttu-id="4f25a-121">W poniższym przykładzie przedstawiono konfigurację LCM, która oczekuje dwóch konfiguracji z częściowa — jedną, która wdraża system operacyjny i wdraża i konfiguruje programu SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4f25a-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="4f25a-122">**RefreshMode** dla każdej z częściowa konfiguracji jest ustawiony na "Push".</span><span class="sxs-lookup"><span data-stu-id="4f25a-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="4f25a-123">Nazwy **PartialConfiguration** bloki (w tym przypadku "ServiceAccountConfig" i "SharePointConfig") musi odpowiadać dokładnie nazwy konfiguracji, które są przenoszone do węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="4f25a-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

><span data-ttu-id="4f25a-124">**Uwaga:** nazwanego każdego **PartialConfiguration** bloku musi odpowiadać rzeczywistej nazwy konfiguracji określonym w skryptu konfiguracji, a nie nazwę pliku MOF, powinny być nazwę węzeł docelowy lub `localhost`.</span><span class="sxs-lookup"><span data-stu-id="4f25a-124">**Note:** The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="4f25a-125">Publikowanie i tryb wysyłania częściowej Konfiguracja początkowa</span><span class="sxs-lookup"><span data-stu-id="4f25a-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="4f25a-126">Następnie wywołaj [DSCConfiguration publikowania](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) dla każdej konfiguracji przekazywanie folderów, który zawiera dokumenty konfiguracji jako **ścieżki** parametrów.</span><span class="sxs-lookup"><span data-stu-id="4f25a-126">You then call [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="4f25a-127">`Publish-DSCConfiguration`umieszcza pliki MOF konfiguracji, aby węzły docelowe.</span><span class="sxs-lookup"><span data-stu-id="4f25a-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="4f25a-128">Po opublikowaniu obu konfiguracji, należy wywołać `Start-DSCConfiguration –UseExisting` w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="4f25a-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="4f25a-129">Na przykład, jeśli została wykonana w następujących dokumentach MOF konfiguracji w węźle tworzenia pakietów administracyjnych:</span><span class="sxs-lookup"><span data-stu-id="4f25a-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


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

<span data-ttu-id="4f25a-130">Czy opublikować, a następnie uruchom następujące konfiguracje:</span><span class="sxs-lookup"><span data-stu-id="4f25a-130">You would publish and run the configurations as follows:</span></span>

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command                  
--     ----            -------------   -----         -----------     --------             -------                  
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

><span data-ttu-id="4f25a-131">**Uwaga:** użytkownik uruchamiający [DSCConfiguration publikowania](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) polecenia cmdlet, musisz mieć uprawnienia administratora w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="4f25a-131">**Note:** The user running the [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="4f25a-132">Częściowe konfiguracje w trybie ściągania</span><span class="sxs-lookup"><span data-stu-id="4f25a-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="4f25a-133">Konfiguracje z częściowa można ściągnąć z jednego lub więcej serwerów ściągania (Aby uzyskać więcej informacji na temat ściągania serwerów, zobacz [Windows PowerShell żądanego stanu ściągania serwery konfiguracji](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="4f25a-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="4f25a-134">Aby to zrobić, należy skonfigurować LCM w węźle docelowym w celu ściągania konfiguracje częściowe i nazwy i zlokalizuj dokumenty configuration poprawnie na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="4f25a-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="4f25a-135">Konfigurowanie LCM ściągania konfiguracji węzła</span><span class="sxs-lookup"><span data-stu-id="4f25a-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="4f25a-136">Aby skonfigurować LCM do ściągnięcia z częściowa konfiguracji z serwera ściągania, zdefiniuj z serwerem ściągania albo **ConfigurationRepositoryWeb** (na serwerze ściągania HTTP) lub **ConfigurationRepositoryShare** () dla serwera ściągania SMB) bloku.</span><span class="sxs-lookup"><span data-stu-id="4f25a-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="4f25a-137">Następnie można utworzyć **PartialConfiguration** bloków, które odwołują się do serwera ściągania przy użyciu **ConfigurationSource** właściwości.</span><span class="sxs-lookup"><span data-stu-id="4f25a-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="4f25a-138">Należy także utworzyć **ustawienia** bloku, aby określić, że LCM używa trybu ściągania i określ **ConfigurationNames** lub **ConfigurationID** który serwera ściągania i docelowego węzła w celu zidentyfikowania Użyj konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="4f25a-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="4f25a-139">Meta konfiguracji definiuje ściągania serwera HTTP o nazwie CONTOSO PullSrv i serwerze ściągania dwie konfiguracje częściowe, korzystających z.</span><span class="sxs-lookup"><span data-stu-id="4f25a-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="4f25a-140">Aby uzyskać więcej informacji na temat konfigurowania za pomocą LCM **ConfigurationNames**, zobacz [Konfigurowanie klienta ściągania przy użyciu nazwy konfiguracji](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="4f25a-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="4f25a-141">Informacje o konfigurowaniu przy użyciu LCM **ConfigurationID**, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="4f25a-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="4f25a-142">Konfigurowanie LCM dla konfiguracji trybu ściągania przy użyciu nazwy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4f25a-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="4f25a-143">Konfigurowanie LCM dla konfiguracji trybu ściągania przy użyciu ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="4f25a-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="4f25a-144">Można ściągnąć częściowe konfiguracje z więcej niż jednego serwera ściągania — czy wystarczy zdefiniować każdego serwera ściągania, a następnie zapoznaj się z serwerem ściągania odpowiednie w każdym **PartialConfiguration** bloku.</span><span class="sxs-lookup"><span data-stu-id="4f25a-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="4f25a-145">Po utworzeniu meta konfiguracji, należy uruchomić je do utworzenia konfiguracji dokumentu (pliku MOF), a następnie wywołać [DscLocalConfigurationManager zestaw](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) skonfigurować LCM.</span><span class="sxs-lookup"><span data-stu-id="4f25a-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="4f25a-146">Nazewnictwo i wprowadzania dokumenty konfiguracji na serwerze ściągania (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="4f25a-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="4f25a-147">Dokumenty configuration częściowe muszą znajdować się w folderze określonym jako **ConfigurationPath** w `web.config` pliku na serwerze ściągania (zazwyczaj `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="4f25a-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> 

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="4f25a-148">Nadawanie nazw dokumentów konfiguracji na serwerze ściągania w programie PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4f25a-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="4f25a-149">Jeśli są ściąganie tylko jedną konfigurację częściowe z serwera ściągania poszczególnych, konfiguracji dokumentu może mieć dowolną nazwę.</span><span class="sxs-lookup"><span data-stu-id="4f25a-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="4f25a-150">Jeśli są ściąganie więcej niż jedną konfigurację częściowe z serwera ściągania, konfiguracji dokumentu może mieć nazwę albo `<ConfigurationName>.mof`, gdzie _ConfigurationName_ jest nazwa konfiguracji częściowe, lub `<ConfigurationName>.<NodeName>.mof`, gdzie  _ConfigurationName_ jest nazwa konfiguracji częściowe, i _NodeName_ jest nazwa węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="4f25a-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where _ConfigurationName_ is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  _ConfigurationName_ is the name of the partial configuration, and _NodeName_ is the name of the target node.</span></span> <span data-ttu-id="4f25a-151">Dzięki temu można ściągania konfiguracji z serwera ściągania usługi Konfiguracja DSC automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="4f25a-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="4f25a-152">Nadawanie nazw dokumentów konfiguracji na serwerze ściągania w programie PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4f25a-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="4f25a-153">Dokumenty konfiguracji musi mieć nazwę w następujący sposób: `ConfigurationName.mof`, gdzie _ConfigurationName_ jest nazwa konfiguracji częściowej.</span><span class="sxs-lookup"><span data-stu-id="4f25a-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where _ConfigurationName_ is the name of the partial configuration.</span></span> <span data-ttu-id="4f25a-154">W naszym przykładzie konfiguracji dokumenty powinny mieć nazwę w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4f25a-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="4f25a-155">Nazewnictwo i wprowadzania dokumenty konfiguracji na serwerze ściągania (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="4f25a-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="4f25a-156">Dokumenty configuration częściowe muszą znajdować się w folderze określonym jako **ConfigurationPath** w `web.config` pliku na serwerze ściągania (zazwyczaj `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="4f25a-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="4f25a-157">Dokumenty konfiguracji musi mieć nazwę w następujący sposób: _ConfigurationName_.</span><span class="sxs-lookup"><span data-stu-id="4f25a-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="4f25a-158">_ConfigurationID_`.mof`, gdzie _ConfigurationName_ jest nazwa konfiguracji częściowe i _ConfigurationID_ identyfikator konfiguracji zdefiniowano w LCM na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="4f25a-158">_ConfigurationID_`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="4f25a-159">W naszym przykładzie konfiguracji dokumenty powinny mieć nazwę w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4f25a-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="4f25a-160">Z częściowa konfiguracji z serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="4f25a-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="4f25a-161">Po LCM na węzeł docelowy został skonfigurowany, a konfiguracji dokumentów zostały utworzone i nazwana poprawnie na serwerze ściągania węzeł docelowy będzie pobierać częściowe konfiguracje, łączyć je i zastosować konfigurację wynikową w regularnych odstępach czasu określonych przez **RefreshFrequencyMins** właściwości LCM.</span><span class="sxs-lookup"><span data-stu-id="4f25a-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="4f25a-162">Jeśli chcesz wymusić odświeżenie, należy wywołać [DscConfiguration aktualizacji](https://technet.microsoft.com/en-us/library/mt143541.aspx) polecenia cmdlet ściągania konfiguracje, a następnie `Start-DSCConfiguration –UseExisting` je zastosować.</span><span class="sxs-lookup"><span data-stu-id="4f25a-162">If you want to force a refresh, you can call the [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="4f25a-163">Częściowe konfiguracje w mieszanych trybach wypychania i ściągania</span><span class="sxs-lookup"><span data-stu-id="4f25a-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="4f25a-164">Można także mieszać wypychania i ściągania tryby w przypadku konfiguracji z częściowa.</span><span class="sxs-lookup"><span data-stu-id="4f25a-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="4f25a-165">Oznacza to może mieć jedną z częściowa konfiguracji pobieranych z serwera ściągania, gdy spoczywa innej konfiguracji częściowej.</span><span class="sxs-lookup"><span data-stu-id="4f25a-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="4f25a-166">Określ trybu odświeżania dla każdej z częściowa konfiguracji zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="4f25a-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="4f25a-167">Na przykład meta konfiguracji opisano tym samym przykładzie, z `ServiceAccountConfig` częściowe konfiguracji w trybie ściągania i `SharePointConfig` częściowe konfiguracji w trybie wypychania.</span><span class="sxs-lookup"><span data-stu-id="4f25a-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="4f25a-168">Mieszane trybach wypychania i ściągania za pomocą ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="4f25a-168">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="4f25a-169">Mieszane trybach wypychania i ściągania za pomocą ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="4f25a-169">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="4f25a-170">Należy pamiętać, że **RefreshMode** jest określany w bloku ustawienia "Pull", ale **RefreshMode** dla `SharePointConfig` częściowe konfiguracji to "Push".</span><span class="sxs-lookup"><span data-stu-id="4f25a-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="4f25a-171">Nazwa i Znajdź pliki MOF konfiguracji, jak opisano powyżej dla trybów ich odpowiednich odświeżania.</span><span class="sxs-lookup"><span data-stu-id="4f25a-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="4f25a-172">Wywołanie **DSCConfiguration publikowania** do publikowania `SharePointConfig` częściowe konfiguracji, a następnie poczekaj, aż `ServiceAccountConfig` konfiguracji do pobrania z serwera ściągania lub wymusić odświeżenie przez wywołanie metody [ Aktualizacja DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span><span class="sxs-lookup"><span data-stu-id="4f25a-172">Call **Publish-DSCConfiguration** to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="4f25a-173">Przykładowa konfiguracja ServiceAccountConfig częściowy</span><span class="sxs-lookup"><span data-stu-id="4f25a-173">Example ServiceAccountConfig Partial Configuration</span></span>

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
## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="4f25a-174">Przykładowa konfiguracja SharePointConfig częściowy</span><span class="sxs-lookup"><span data-stu-id="4f25a-174">Example SharePointConfig Partial Configuration</span></span>
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
##<a name="see-also"></a><span data-ttu-id="4f25a-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f25a-175">See Also</span></span> 

<span data-ttu-id="4f25a-176">**Pojęcia dotyczące**
[serwery ściągania stanu konfiguracji żądanego programu Windows PowerShell](pullServer.md)</span><span class="sxs-lookup"><span data-stu-id="4f25a-176">**Concepts**
[Windows PowerShell Desired State Configuration Pull Servers](pullServer.md)</span></span> 

[<span data-ttu-id="4f25a-177">Konfigurowanie lokalny program Configuration Manager systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4f25a-177">Windows Configuring the Local Configuration Manager</span></span>](https://technet.microsoft.com/en-us/library/mt421188.aspx) 

