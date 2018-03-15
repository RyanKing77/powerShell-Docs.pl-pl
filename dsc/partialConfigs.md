---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Konfiguracje częściowe konfiguracji żądanego stanu programu PowerShell"
ms.openlocfilehash: 4401ea80cffd09f4b92c9fcca16d5dcad7f6a327
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Konfiguracje częściowe konfiguracji żądanego stanu programu PowerShell

>Dotyczy: Środowiska Windows PowerShell 5.0 i nowszych.

W programie PowerShell 5.0 konfiguracji żądanego stanu (DSC) umożliwia konfiguracje, które mają zostać dostarczone w fragmentów i z wielu źródeł. Lokalne Menedżera konfiguracji (LCM) w docelowym węźle umieszcza fragmentów razem przed ich zastosowaniem jako pojedynczą konfiguracją. Ta funkcja pozwala na udostępnianie kontroli konfigurację między zespołami lub osoby. Na przykład jeśli co najmniej dwóch zespołów deweloperów współpracują w usłudze, może każdego chcą tworzyć konfiguracje do zarządzania ich należącej do usługi. Każdy z tych konfiguracji można ściągnąć z różnych ściągania serwerów i mogą zostać dodane na różnych etapach rozwoju. Konfiguracje z częściowa również umożliwić różnych konkretnych osób lub zespołów kontrolować różne aspekty konfigurowanie węzłów bez konieczności koordynować edycji konfiguracji pojedynczego dokumentu. Na przykład jeden zespół może być odpowiedzialnych za wdrażanie maszyny Wirtualnej i systemu operacyjnego, podczas gdy inny zespół może wdrożyć inne aplikacje i usługi na danej maszynie Wirtualnej. Z częściowa konfiguracje każdego zespołu można utworzyć własną konfigurację, bez żadnej z nich jest niepotrzebnie skomplikowane.

Możesz użyć częściowe konfiguracje w trybie wypychania, tryb ściągania lub kombinację obu.

## <a name="partial-configurations-in-push-mode"></a>Częściowe konfiguracje w trybie push
Aby używać częściowej konfiguracje w trybie wypychania, należy skonfigurować LCM w docelowym węźle do odbierania z częściowa konfiguracje. Każdej z częściowa konfiguracji musi zostać przeniesiony do docelowego za pomocą polecenia cmdlet Publish-DSCConfiguration. Węzeł docelowy następnie łączy częściowe konfiguracji w pojedynczą konfiguracją i można zastosować konfiguracji przez wywołanie metody [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) polecenia cmdlet.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Konfigurowanie LCM częściowe konfiguracji trybu wypychania
Aby skonfigurować LCM w przypadku konfiguracji z częściowa w trybie wypychania, należy utworzyć **DSCLocalConfigurationManager** konfiguracji z jednego **PartialConfiguration** blok dla każdej z częściowa konfiguracji. Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager systemu Windows](https://technet.microsoft.com/library/mt421188.aspx). W poniższym przykładzie przedstawiono konfigurację LCM, która oczekuje dwóch konfiguracji z częściowa — jedną, która wdraża system operacyjny i wdraża i konfiguruje programu SharePoint.

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

**RefreshMode** dla każdej z częściowa konfiguracji jest ustawiony na "Push". Nazwy **PartialConfiguration** bloki (w tym przypadku "ServiceAccountConfig" i "SharePointConfig") musi odpowiadać dokładnie nazwy konfiguracji, które są przenoszone do węzła docelowego.

>**Uwaga:** nazwanego każdego **PartialConfiguration** bloku musi odpowiadać rzeczywistej nazwy konfiguracji określonym w skryptu konfiguracji, a nie nazwę pliku MOF, powinny być nazwę węzeł docelowy lub `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publikowanie i tryb wysyłania częściowej Konfiguracja początkowa

Następnie wywołaj [DSCConfiguration publikowania](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) dla każdej konfiguracji przekazywanie folderów, który zawiera dokumenty konfiguracji jako **ścieżki** parametrów. `Publish-DSCConfiguration`umieszcza pliki MOF konfiguracji, aby węzły docelowe. Po opublikowaniu obu konfiguracji, należy wywołać `Start-DSCConfiguration –UseExisting` w docelowym węźle.

Na przykład, jeśli została wykonana w następujących dokumentach MOF konfiguracji w węźle tworzenia pakietów administracyjnych:

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

Czy opublikować, a następnie uruchom następujące konfiguracje:

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command                  
--     ----            -------------   -----         -----------     --------             -------                  
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

>**Uwaga:** użytkownik uruchamiający [DSCConfiguration publikowania](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) polecenia cmdlet, musisz mieć uprawnienia administratora w docelowym węźle.

## <a name="partial-configurations-in-pull-mode"></a>Częściowe konfiguracje w trybie ściągania

Konfiguracje z częściowa można ściągnąć z jednego lub więcej serwerów ściągania (Aby uzyskać więcej informacji na temat ściągania serwerów, zobacz [Windows PowerShell żądanego stanu ściągania serwery konfiguracji](pullServer.md). Aby to zrobić, należy skonfigurować LCM w węźle docelowym w celu ściągania konfiguracje częściowe i nazwy i zlokalizuj dokumenty configuration poprawnie na serwerze ściągania.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Konfigurowanie LCM ściągania konfiguracji węzła

Aby skonfigurować LCM do ściągnięcia z częściowa konfiguracji z serwera ściągania, zdefiniuj z serwerem ściągania albo **ConfigurationRepositoryWeb** (na serwerze ściągania HTTP) lub **ConfigurationRepositoryShare** () dla serwera ściągania SMB) bloku. Następnie można utworzyć **PartialConfiguration** bloków, które odwołują się do serwera ściągania przy użyciu **ConfigurationSource** właściwości. Należy także utworzyć **ustawienia** bloku, aby określić, że LCM używa trybu ściągania i określ **ConfigurationNames** lub **ConfigurationID** który serwera ściągania i docelowego węzła w celu zidentyfikowania Użyj konfiguracje. Meta konfiguracji definiuje ściągania serwera HTTP o nazwie CONTOSO PullSrv i serwerze ściągania dwie konfiguracje częściowe, korzystających z.

Aby uzyskać więcej informacji na temat konfigurowania za pomocą LCM **ConfigurationNames**, zobacz [Konfigurowanie klienta ściągania przy użyciu nazwy konfiguracji](pullClientConfigNames.md). Informacje o konfigurowaniu przy użyciu LCM **ConfigurationID**, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Konfigurowanie LCM dla konfiguracji trybu ściągania przy użyciu nazwy konfiguracji

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Konfigurowanie LCM dla konfiguracji trybu ściągania przy użyciu ConfigurationID

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

Można ściągnąć częściowe konfiguracje z więcej niż jednego serwera ściągania — czy wystarczy zdefiniować każdego serwera ściągania, a następnie zapoznaj się z serwerem ściągania odpowiednie w każdym **PartialConfiguration** bloku.

Po utworzeniu meta konfiguracji, należy uruchomić je do utworzenia konfiguracji dokumentu (pliku MOF), a następnie wywołać [DscLocalConfigurationManager zestaw](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) skonfigurować LCM.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Nazewnictwo i wprowadzania dokumenty konfiguracji na serwerze ściągania (ConfigurationNames)

Dokumenty configuration częściowe muszą znajdować się w folderze określonym jako **ConfigurationPath** w `web.config` pliku na serwerze ściągania (zazwyczaj `C:\Program Files\WindowsPowerShell\DscService\Configuration`). 

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Nadawanie nazw dokumentów konfiguracji na serwerze ściągania w programie PowerShell 5.1

Jeśli są ściąganie tylko jedną konfigurację częściowe z serwera ściągania poszczególnych, konfiguracji dokumentu może mieć dowolną nazwę. Jeśli są ściąganie więcej niż jedną konfigurację częściowe z serwera ściągania, konfiguracji dokumentu może mieć nazwę albo `<ConfigurationName>.mof`, gdzie _ConfigurationName_ jest nazwa konfiguracji częściowe, lub `<ConfigurationName>.<NodeName>.mof`, gdzie  _ConfigurationName_ jest nazwa konfiguracji częściowe, i _NodeName_ jest nazwa węzła docelowego. Dzięki temu można ściągania konfiguracji z serwera ściągania usługi Konfiguracja DSC automatyzacji Azure.


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Nadawanie nazw dokumentów konfiguracji na serwerze ściągania w programie PowerShell 5.0

Dokumenty konfiguracji musi mieć nazwę w następujący sposób: `ConfigurationName.mof`, gdzie _ConfigurationName_ jest nazwa konfiguracji częściowej. W naszym przykładzie konfiguracji dokumenty powinny mieć nazwę w następujący sposób:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Nazewnictwo i wprowadzania dokumenty konfiguracji na serwerze ściągania (ConfigurationID)

Dokumenty configuration częściowe muszą znajdować się w folderze określonym jako **ConfigurationPath** w `web.config` pliku na serwerze ściągania (zazwyczaj `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Dokumenty konfiguracji musi mieć nazwę w następujący sposób: _ConfigurationName_. _ConfigurationID_`.mof`, gdzie _ConfigurationName_ jest nazwa konfiguracji częściowe i _ConfigurationID_ zdefiniowano identyfikator konfiguracji w LCM w systemie docelowym węzeł. W naszym przykładzie konfiguracji dokumenty powinny mieć nazwę w następujący sposób:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a>Z częściowa konfiguracji z serwera ściągania

Po LCM na węzeł docelowy został skonfigurowany, a konfiguracji dokumentów zostały utworzone i nazwana poprawnie na serwerze ściągania węzeł docelowy będzie pobierać częściowe konfiguracje, łączyć je i zastosować konfigurację wynikową w regularnych odstępach czasu określonych przez **RefreshFrequencyMins** właściwości LCM. Jeśli chcesz wymusić odświeżenie, należy wywołać [DscConfiguration aktualizacji](https://technet.microsoft.com/en-us/library/mt143541.aspx) polecenia cmdlet ściągania konfiguracje, a następnie `Start-DSCConfiguration –UseExisting` je zastosować.


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Częściowe konfiguracje w mieszanych trybach wypychania i ściągania

Można także mieszać wypychania i ściągania tryby w przypadku konfiguracji z częściowa. Oznacza to może mieć jedną z częściowa konfiguracji pobieranych z serwera ściągania, gdy spoczywa innej konfiguracji częściowej. Określ trybu odświeżania dla każdej z częściowa konfiguracji zgodnie z opisem w poprzedniej sekcji. Na przykład meta konfiguracji opisano tym samym przykładzie, z `ServiceAccountConfig` częściowe konfiguracji w trybie ściągania i `SharePointConfig` częściowe konfiguracji w trybie wypychania.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Mieszane trybach wypychania i ściągania za pomocą ConfigurationNames

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Mieszane trybach wypychania i ściągania za pomocą ConfigurationID

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

Należy pamiętać, że **RefreshMode** jest określany w bloku ustawienia "Pull", ale **RefreshMode** dla `SharePointConfig` częściowe konfiguracji to "Push".

Nazwa i Znajdź pliki MOF konfiguracji, jak opisano powyżej dla trybów ich odpowiednich odświeżania. Wywołanie **DSCConfiguration publikowania** do publikowania `SharePointConfig` częściowe konfiguracji, a następnie poczekaj, aż `ServiceAccountConfig` konfiguracji do pobrania z serwera ściągania lub wymusić odświeżenie przez wywołanie metody [ Aktualizacja DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Przykładowa konfiguracja ServiceAccountConfig częściowy

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
## <a name="example-sharepointconfig-partial-configuration"></a>Przykładowa konfiguracja SharePointConfig częściowy
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
##<a name="see-also"></a>Zobacz też 

**Pojęcia dotyczące**
[serwery ściągania stanu konfiguracji żądanego programu Windows PowerShell](pullServer.md) 

[Konfigurowanie lokalny program Configuration Manager systemu Windows](https://technet.microsoft.com/library/mt421188.aspx) 

