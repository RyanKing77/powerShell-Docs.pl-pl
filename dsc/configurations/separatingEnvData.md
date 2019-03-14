---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Oddzielanie danych konfiguracji i środowiska
ms.openlocfilehash: 305a766fec81d4ea4afce187756188b067a2048b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794930"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="55d1a-103">Oddzielanie danych konfiguracji i środowiska</span><span class="sxs-lookup"><span data-stu-id="55d1a-103">Separating configuration and environment data</span></span>

><span data-ttu-id="55d1a-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="55d1a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="55d1a-105">Może być przydatne do oddzielania danych używanych w konfiguracji DSC z samej konfiguracji przy użyciu danych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="55d1a-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="55d1a-106">W ten sposób można użyć jednej konfiguracji dla wielu środowisk.</span><span class="sxs-lookup"><span data-stu-id="55d1a-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="55d1a-107">Na przykład jeśli tworzysz aplikację, można użyć jednej konfiguracji dla środowisk środowisk deweloperskich i produkcyjnych i użyj dane konfiguracyjne, aby określić dane dla każdego środowiska.</span><span class="sxs-lookup"><span data-stu-id="55d1a-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="55d1a-108">Co to jest dane konfiguracji?</span><span class="sxs-lookup"><span data-stu-id="55d1a-108">What is configuration data?</span></span>

<span data-ttu-id="55d1a-109">Dane konfiguracji są dane, które jest określone w tablicy skrótów i przekazywane do konfiguracji DSC, podczas kompilowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="55d1a-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="55d1a-110">Aby uzyskać szczegółowy opis **ConfigurationData** hashtable, zobacz [korzystanie z danych konfiguracji](configData.md).</span><span class="sxs-lookup"><span data-stu-id="55d1a-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="55d1a-111">Prosty przykład</span><span class="sxs-lookup"><span data-stu-id="55d1a-111">A simple example</span></span>

<span data-ttu-id="55d1a-112">Przyjrzyjmy się bardzo prosty przykład, aby zobaczyć, jak to działa.</span><span class="sxs-lookup"><span data-stu-id="55d1a-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="55d1a-113">Utworzymy jednej konfiguracji, który zapewnia, że **IIS** znajduje się na niektóre węzły, a **funkcji Hyper-V** znajduje się na innych użytkowników:</span><span class="sxs-lookup"><span data-stu-id="55d1a-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

<span data-ttu-id="55d1a-114">Ostatni wiersz, w tym skrypcie kompiluje konfigurację, przekazując `$MyData` jako wartość **ConfigurationData** parametru.</span><span class="sxs-lookup"><span data-stu-id="55d1a-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="55d1a-115">Wynik jest, że zostaną utworzone dwa pliki MOF:</span><span class="sxs-lookup"><span data-stu-id="55d1a-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="55d1a-116">`$MyData` Określa dwóch różnych węzłach, z których każdy z własną `NodeName` i `Role`.</span><span class="sxs-lookup"><span data-stu-id="55d1a-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="55d1a-117">Konfiguracja dynamicznie tworzy **węzła** bloków, wykonując kolekcję węzłów otrzymuje od `$MyData` (w szczególności `$AllNodes`) i filtruje tej kolekcji przed `Role` właściwości...</span><span class="sxs-lookup"><span data-stu-id="55d1a-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="55d1a-118">Korzystanie z danych konfiguracji do definiowania środowisk deweloperskich i produkcyjnych</span><span class="sxs-lookup"><span data-stu-id="55d1a-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="55d1a-119">Przyjrzyjmy się pełny przykład, który używa jednej konfiguracji do konfigurowania środowisk deweloperskich i produkcyjnych środowisk witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="55d1a-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="55d1a-120">W środowisku deweloperskim usługi IIS i SQL Server są instalowane na pojedyncze węzły.</span><span class="sxs-lookup"><span data-stu-id="55d1a-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="55d1a-121">W środowisku produkcyjnym usług IIS i programu SQL Server są zainstalowane na osobnych węzłach.</span><span class="sxs-lookup"><span data-stu-id="55d1a-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="55d1a-122">Użyjemy pliku psd1 danych konfiguracji do określania danych do dwóch różnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="55d1a-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

### <a name="configuration-data-file"></a><span data-ttu-id="55d1a-123">Plik danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="55d1a-123">Configuration data file</span></span>

<span data-ttu-id="55d1a-124">Firma Microsoft zdefiniuje dane środowisku deweloperskim i produkcyjnym w pliku o nazwie `DevProdEnvData.psd1` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="55d1a-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a><span data-ttu-id="55d1a-125">Plik skryptu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="55d1a-125">Configuration script file</span></span>

<span data-ttu-id="55d1a-126">Teraz w konfiguracji, który jest zdefiniowany w `.ps1` pliku, możemy filtrować węzłów zdefiniowanych w `DevProdEnvData.psd1` przez ich rolę (`MSSQL`, `Dev`, i / lub) i odpowiednio je skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="55d1a-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="55d1a-127">Środowisko projektowe ma SQL Server i usług IIS na jednym węźle, a w środowisku produkcyjnym ma ich w dwóch różnych węzłach.</span><span class="sxs-lookup"><span data-stu-id="55d1a-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="55d1a-128">Zawartość witryny różni się również, jak określono przez `SiteContents` właściwości.</span><span class="sxs-lookup"><span data-stu-id="55d1a-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="55d1a-129">Na końcu skryptu konfiguracji nazywamy konfiguracji (wkompilować ją w dokument MOF), przekazywanie `DevProdEnvData.psd1` jako `$ConfigurationData` parametru.</span><span class="sxs-lookup"><span data-stu-id="55d1a-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="55d1a-130">**Uwaga:** Ta konfiguracja wymaga moduły `xSqlPs` i `xWebAdministration` do zainstalowania w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="55d1a-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="55d1a-131">Umożliwia definiowanie konfiguracji w pliku o nazwie `MyWebApp.ps1`:</span><span class="sxs-lookup"><span data-stu-id="55d1a-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="55d1a-132">Po uruchomieniu tej konfiguracji, zostaną utworzone trzy pliki MOF (jednej dla każdego o nazwie wejścia w **AllNodes** tablicy):</span><span class="sxs-lookup"><span data-stu-id="55d1a-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="55d1a-133">Korzystanie z danych niż węzła</span><span class="sxs-lookup"><span data-stu-id="55d1a-133">Using non-node data</span></span>

<span data-ttu-id="55d1a-134">Możesz dodać dodatkowe klucze do **ConfigurationData** hashtable dla danych, który nie jest specyficzne dla danego węzła.</span><span class="sxs-lookup"><span data-stu-id="55d1a-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="55d1a-135">Następująca konfiguracja zapewnia obecność dwie witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="55d1a-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="55d1a-136">Dane dla każdej witryny sieci Web są definiowane w **AllNodes** tablicy.</span><span class="sxs-lookup"><span data-stu-id="55d1a-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="55d1a-137">Plik `Config.xml` służy do obu witryn sieci Web, dzięki czemu możemy zdefiniować w dodatkowy klucz o nazwie `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="55d1a-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="55d1a-138">Należy pamiętać, że może mieć dowolną liczbę dodatkowych kluczy ma i nazwać je dowolnych znaków.</span><span class="sxs-lookup"><span data-stu-id="55d1a-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="55d1a-139">`NonNodeData` nie jest słowem zastrzeżonym, jest po prostu co podjęliśmy decyzję o nazwę dodatkowego klucza.</span><span class="sxs-lookup"><span data-stu-id="55d1a-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="55d1a-140">Dostęp do dodatkowych kluczy przy użyciu specjalna zmienna **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="55d1a-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="55d1a-141">W tym przykładzie `ConfigFileContents` odbywa się za pomocą wiersza:</span><span class="sxs-lookup"><span data-stu-id="55d1a-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="55d1a-142">w `File` bloku zasobów.</span><span class="sxs-lookup"><span data-stu-id="55d1a-142">in the `File` resource block.</span></span>


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a><span data-ttu-id="55d1a-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55d1a-143">See Also</span></span>
- [<span data-ttu-id="55d1a-144">Korzystanie z danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="55d1a-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="55d1a-145">Opcje poświadczeń w danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="55d1a-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="55d1a-146">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="55d1a-146">DSC Configurations</span></span>](configurations.md)
