---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Oddzielanie danych konfiguracji i środowiska"
ms.openlocfilehash: 861a4cecc28b2d93b2cfa2743d47ee0e5025e1f4
ms.sourcegitcommit: 60c6f9d8cf316e6d5b285854e6e5641ac7648f3f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="separating-configuration-and-environment-data"></a>Oddzielanie danych konfiguracji i środowiska

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Może być przydatne do oddzielania danych używane w konfiguracji DSC z samej konfiguracji przy użyciu danych konfiguracji.
W ten sposób można użyć jednej konfiguracji w wielu środowiskach.

Na przykład jeśli tworzysz aplikację, można korzystać z jednej konfiguracji dla środowisk zarówno projektowania i produkcji i korzystać z danych konfiguracji do określania danych dla każdego środowiska.

## <a name="what-is-configuration-data"></a>Co to jest konfiguracja danych?

Dane konfiguracyjne są dane, które jest określone w tablicy skrótów i przekazane do konfiguracji DSC podczas kompilowania tej konfiguracji.

Aby uzyskać szczegółowy opis **ConfigurationData** hashtable, zobacz [przy użyciu danych konfiguracji](configData.md).

## <a name="a-simple-example"></a>Prosty przykład

Przyjrzyjmy się jest bardzo prosty przykład, aby zobaczyć, jak to działa. Utworzymy jednej konfiguracji, który zapewnia, że **IIS** na niektóre węzły, a ma **funkcji Hyper-V** znajduje się na inne: 

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

Ostatni wiersz w tym skrypcie kompiluje konfigurację przekazywanie `$MyData` jako wartość **ConfigurationData** parametru.

Wynik jest, że są tworzone dwa pliki MOF:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:09 PM           1968 VM-1.mof                                                                                                                
-a----        3/31/2017   5:09 PM           1970 VM-2.mof  
```
 
`$MyData`Określa dwóch różnych węzłach, każdego z jego własnej `NodeName` i `Role`. Konfiguracja dynamicznie tworzy **węzła** bloków, wykonując kolekcja węzłów otrzymuje od `$MyData` (w szczególności `$AllNodes`) i filtry kolekcji przed `Role` właściwości...

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Przy użyciu danych konfiguracji do definiowania środowisk projektowania i produkcji

Przyjrzyjmy się pełny przykład, który używa jednej konfiguracji, aby skonfigurować zarówno programowanie i środowiska produkcyjne witryny sieci Web. W środowisku programistycznym zarówno usług IIS, jak i SQL Server są zainstalowane na pojedynczych węzłów. W środowisku produkcyjnym usług IIS i programu SQL Server są zainstalowane na osobne węzły. Użyjemy plik psd1 danych konfiguracji do określania danych dla dwóch różnych środowiskach.

 ### <a name="configuration-data-file"></a>Plik danych konfiguracji

Zdefiniujemy danych środowiska projektowania i produkcji w namd pliku `DevProdEnvData.psd1` w następujący sposób:

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

Teraz, w konfiguracji, który jest zdefiniowany w `.ps1` pliku, możemy filtrować węzłów zdefiniowanego w `DevProdEnvData.psd1` przez ich rolę (`MSSQL`, `Dev`, lub obie) i odpowiednio je skonfigurować. Środowisko projektowe ma serwer SQL i IIS na jednym węźle, podczas gdy środowiska produkcyjnego ma ich w dwóch różnych węzłach. Zawartość witryny różni się również, określony przez `SiteContents` właściwości.

Na końcu skryptu konfiguracji nazywamy konfiguracji (Skompiluj go do dokumentu MOF), przekazywanie `DevProdEnvData.psd1` jako `$ConfigurationData` parametru.

>**Uwaga:** ta konfiguracja wymaga modułów `xSqlPs` i `xWebAdministration` do zainstalowania w docelowym węźle.

Umożliwia definiowanie konfiguracji w pliku o nazwie `MyWebApp.ps1`:

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
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

Po uruchomieniu tej konfiguracji są tworzone trzy pliki MOF (po jednej dla każdego o nazwie wejścia w **AllNodes** tablicy):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof                                                                                                            
-a----        3/31/2017   5:47 PM           6994 Dev.mof                                                                                                                 
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Przy użyciu danych z systemem innym niż węzeł

Można dodać dodatkowe klucze do **ConfigurationData** hashtable danych, która nie jest specyficzne dla danego węzła.
Następująca konfiguracja zapewnia obecności dwie witryny sieci Web.
Dane dla każdej witryny sieci Web są zdefiniowane w **AllNodes** tablicy.
Plik `Config.xml` jest używane w obu witryn sieci Web, więc definiujemy w dodatkowych klucz o nazwie `NonNodeData`.
Należy pamiętać, że może mieć dowolną liczbę dodatkowych kluczy mają i można określić nazwę je dowolnych znaków.
`NonNodeData`nie jest ona słowem zastrzeżonym, jest tylko co zdecydowaliśmy się nazwę dodatkowe klucza.

Dostęp do dodatkowych kluczy przy użyciu specjalna zmienna **$ConfigurationData**.
W tym przykładzie `ConfigFileContents` jest dostępny z poziomu wiersza:
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
            NodeName           = “*”
            LogPath            = “C:\Logs”
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
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
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
- [Przy użyciu danych konfiguracji](configData.md)
- [Opcje poświadczeń w danych konfiguracji](configDataCredentials.md)
- [Konfiguracji DSC](configurations.md)

