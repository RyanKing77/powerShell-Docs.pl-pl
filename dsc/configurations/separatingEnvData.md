---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Oddzielanie danych konfiguracji i środowiska
ms.openlocfilehash: 305a766fec81d4ea4afce187756188b067a2048b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080037"
---
# <a name="separating-configuration-and-environment-data"></a>Oddzielanie danych konfiguracji i środowiska

>Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

Może być przydatne do oddzielania danych używanych w konfiguracji DSC z samej konfiguracji przy użyciu danych konfiguracji.
W ten sposób można użyć jednej konfiguracji dla wielu środowisk.

Na przykład jeśli tworzysz aplikację, można użyć jednej konfiguracji dla środowisk środowisk deweloperskich i produkcyjnych i użyj dane konfiguracyjne, aby określić dane dla każdego środowiska.

## <a name="what-is-configuration-data"></a>Co to jest dane konfiguracji?

Dane konfiguracji są dane, które jest określone w tablicy skrótów i przekazywane do konfiguracji DSC, podczas kompilowania konfiguracji.

Aby uzyskać szczegółowy opis **ConfigurationData** hashtable, zobacz [korzystanie z danych konfiguracji](configData.md).

## <a name="a-simple-example"></a>Prosty przykład

Przyjrzyjmy się bardzo prosty przykład, aby zobaczyć, jak to działa.
Utworzymy jednej konfiguracji, który zapewnia, że **IIS** znajduje się na niektóre węzły, a **funkcji Hyper-V** znajduje się na innych użytkowników:

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

Ostatni wiersz, w tym skrypcie kompiluje konfigurację, przekazując `$MyData` jako wartość **ConfigurationData** parametru.

Wynik jest, że zostaną utworzone dwa pliki MOF:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` Określa dwóch różnych węzłach, z których każdy z własną `NodeName` i `Role`. Konfiguracja dynamicznie tworzy **węzła** bloków, wykonując kolekcję węzłów otrzymuje od `$MyData` (w szczególności `$AllNodes`) i filtruje tej kolekcji przed `Role` właściwości...

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Korzystanie z danych konfiguracji do definiowania środowisk deweloperskich i produkcyjnych

Przyjrzyjmy się pełny przykład, który używa jednej konfiguracji do konfigurowania środowisk deweloperskich i produkcyjnych środowisk witryny sieci Web. W środowisku deweloperskim usługi IIS i SQL Server są instalowane na pojedyncze węzły. W środowisku produkcyjnym usług IIS i programu SQL Server są zainstalowane na osobnych węzłach. Użyjemy pliku psd1 danych konfiguracji do określania danych do dwóch różnych środowisk.

### <a name="configuration-data-file"></a>Plik danych konfiguracji

Firma Microsoft zdefiniuje dane środowisku deweloperskim i produkcyjnym w pliku o nazwie `DevProdEnvData.psd1` w następujący sposób:

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

### <a name="configuration-script-file"></a>Plik skryptu konfiguracji

Teraz w konfiguracji, który jest zdefiniowany w `.ps1` pliku, możemy filtrować węzłów zdefiniowanych w `DevProdEnvData.psd1` przez ich rolę (`MSSQL`, `Dev`, i / lub) i odpowiednio je skonfigurować.
Środowisko projektowe ma SQL Server i usług IIS na jednym węźle, a w środowisku produkcyjnym ma ich w dwóch różnych węzłach.
Zawartość witryny różni się również, jak określono przez `SiteContents` właściwości.

Na końcu skryptu konfiguracji nazywamy konfiguracji (wkompilować ją w dokument MOF), przekazywanie `DevProdEnvData.psd1` jako `$ConfigurationData` parametru.

>**Uwaga:** Ta konfiguracja wymaga moduły `xSqlPs` i `xWebAdministration` do zainstalowania w docelowym węźle.

Umożliwia definiowanie konfiguracji w pliku o nazwie `MyWebApp.ps1`:

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

Po uruchomieniu tej konfiguracji, zostaną utworzone trzy pliki MOF (jednej dla każdego o nazwie wejścia w **AllNodes** tablicy):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Korzystanie z danych niż węzła

Możesz dodać dodatkowe klucze do **ConfigurationData** hashtable dla danych, który nie jest specyficzne dla danego węzła.
Następująca konfiguracja zapewnia obecność dwie witryny sieci Web.
Dane dla każdej witryny sieci Web są definiowane w **AllNodes** tablicy.
Plik `Config.xml` służy do obu witryn sieci Web, dzięki czemu możemy zdefiniować w dodatkowy klucz o nazwie `NonNodeData`.
Należy pamiętać, że może mieć dowolną liczbę dodatkowych kluczy ma i nazwać je dowolnych znaków.
`NonNodeData` nie jest słowem zastrzeżonym, jest po prostu co podjęliśmy decyzję o nazwę dodatkowego klucza.

Dostęp do dodatkowych kluczy przy użyciu specjalna zmienna **$ConfigurationData**.
W tym przykładzie `ConfigFileContents` odbywa się za pomocą wiersza:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 w `File` bloku zasobów.


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


## <a name="see-also"></a>Zobacz też
- [Korzystanie z danych konfiguracji](configData.md)
- [Opcje poświadczeń w danych konfiguracji](configDataCredentials.md)
- [Konfiguracje DSC](configurations.md)
