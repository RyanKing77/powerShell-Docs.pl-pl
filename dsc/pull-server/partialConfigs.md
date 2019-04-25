---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfiguracje częściowe PowerShell Desired State Configuration
ms.openlocfilehash: b2b17e35597707eb97ecdcea9dda4466deeab0cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079527"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Konfiguracje częściowe PowerShell Desired State Configuration

_Dotyczy: Program Windows PowerShell 5.0 lub nowszy._

W programie PowerShell 5.0 Desired State Configuration (DSC) umożliwia konfiguracje, które mają zostać dostarczone we fragmentach i z wielu źródeł. Lokalny Menedżer konfiguracji (LCM) w docelowym węźle umieszcza fragmenty ze sobą przed zastosowaniem ich jako jedną konfigurację. Ta funkcja umożliwia udostępnianie kontrolę nad konfiguracją między zespołami i klientów indywidualnych. Na przykład jeśli co najmniej dwóch zespołów deweloperów współpracują w usłudze, może każdego chcą tworzyć konfiguracje do zarządzania ich część usługi. Każda z tych konfiguracji może zostać pobrane z ściągnięcia różne serwery i może zostać dodany na różnych etapach cyklu rozwoju. Konfiguracje częściowe umożliwiają także różne konkretnych osób lub zespołów kontrolować różne aspekty konfigurowanie węzłów bez konieczności koordynowania edycji dokumentu jednej konfiguracji. Na przykład jeden zespół może być odpowiedzialnego za wdrożenie maszyny Wirtualnej i systemu operacyjnego, podczas gdy inny zespół może wdrożyć inne aplikacje i usługi na tej maszynie Wirtualnej. Za pomocą konfiguracje częściowe każdy zespół może utworzyć własną konfigurację, bez każdej z nich jest niepotrzebnie skomplikowane.

Możesz użyć częściowe konfiguracji w trybie wypychania, tryb ściągania lub kombinacji obu.

## <a name="partial-configurations-in-push-mode"></a>Konfiguracje częściowe w trybie wypychania

Aby użyć konfiguracje częściowe w trybie wypychania, należy skonfigurować LCM w węźle docelowym, aby otrzymywać konfiguracje częściowe. Każdy częściowe konfiguracji musi zostać przeniesiony do docelowego przy użyciu `Publish-DSCConfiguration` polecenia cmdlet. Węzeł docelowy jest następnie łączy częściowe konfiguracji w jednej konfiguracji i konfiguracji mogą być stosowane przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Konfigurowanie programu LCM w trybie wypychania częściowe konfiguracji

Aby skonfigurować LCM częściowe konfiguracji w trybie wypychania, należy utworzyć **DSCLocalConfigurationManager** konfiguracji o jednym **PartialConfiguration** bloku dla każdej konfiguracji częściowe. Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Windows Konfigurowanie programu Local Configuration Manager](/powershell/dsc/metaConfig). W poniższym przykładzie pokazano konfigurację LCM, który oczekuje, że dwie konfiguracje częściowe — jedną, która wdraża system operacyjny oraz jedna, która służy do wdrażania i konfiguruje program SharePoint.

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

**RefreshMode** dla każdej konfiguracji częściowe jest ustawiony na "Wypychania". Nazwy **PartialConfiguration** bloków (w tym przypadku "ServiceAccountConfig" i "SharePointConfig") musi być zgodna dokładnie nazwy konfiguracji, które są przekazywane do węzła docelowego.

> [!Note]
> Nazwane każdego **PartialConfiguration** bloku musi odpowiadać rzeczywista nazwa konfiguracji, co zostało określone w skrypcie konfiguracji, a nie nazwę pliku MOF, który powinien być nazwę węzła docelowego lub `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publikowanie i uruchamianie konfiguracje częściowe w trybie wypychania

Następnie wywołaj [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) dla każdej konfiguracji przekazywanie folderów, które zawierają dokumenty konfiguracji jako **ścieżki** parametrów. `Publish-DSCConfiguration`umieszcza pliki MOF konfiguracji do węzłów docelowych. Po opublikowaniu obie konfiguracje, można wywołać `Start-DSCConfiguration –UseExisting` w docelowym węźle.

Na przykład, jeśli została wykonana w następujących dokumentach pliku MOF konfiguracji w węźle tworzenia pakietów administracyjnych:

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

Czy opublikować, a następnie uruchom konfiguracje w następujący sposób:

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
> Użytkownik uruchamiający [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) polecenia cmdlet, musisz mieć uprawnienia administratora w docelowym węźle.

## <a name="partial-configurations-in-pull-mode"></a>Konfiguracje częściowe w tryb ściągania

Konfiguracje częściowe mogą zostać pobrane z co najmniej jeden serwer ściągania (Aby uzyskać więcej informacji na temat serwerów ściągnięcia zobacz [Windows PowerShell Desired State Configuration ściągnięcia serwerów](pullServer.md). Aby to zrobić, należy skonfigurować LCM w węźle docelowym w celu ściągania konfiguracje częściowe i nazwę, a zlokalizuj dokumenty konfiguracji poprawnie na serwerze ściągania.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Konfigurowanie programu LCM do ściągania konfiguracje węzłów

Aby skonfigurować LCM do ściągania konfiguracje częściowe z serwera ściągania, zdefiniuj serwera ściągania albo **ConfigurationRepositoryWeb** (na serwerze ściągania HTTP) lub **ConfigurationRepositoryShare** () dla serwera ściągania SMB) bloku. Następnie utwórz **PartialConfiguration** bloki, które odwołują się do serwera ściągania przy użyciu **ConfigurationSource** właściwości. Musisz także utworzyć **ustawienia** bloku LCM korzysta z trybu ściągania i określ **ConfigurationNames** lub **ConfigurationID** , serwerze ściągania i Użyj węzła docelowego do identyfikowania konfiguracji. Następująca konfiguracja meta definiuje serwera ściągania HTTP o nazwie CONTOSO PullSrv i serwerze ściągania dwie konfiguracje częściowe, które, które używają.

Aby uzyskać więcej informacji o konfigurowaniu przy użyciu LCM **ConfigurationNames**, zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](pullClientConfigNames.md). Informacje o konfigurowaniu przy użyciu LCM **ConfigurationID**, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Konfigurowanie programu LCM w przypadku konfiguracji tryb ściągania przy użyciu nazw konfiguracji

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Konfigurowanie programu LCM w przypadku konfiguracji tryb ściągania przy użyciu ConfigurationID

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

Możesz ściągnąć konfiguracje częściowe z więcej niż jednego serwera ściągania — po prostu musisz zdefiniować każdy serwer ściągania, a następnie zapoznaj się z serwerem ściągania odpowiednie w każdym **PartialConfiguration** bloku.

Po utworzeniu meta konfiguracji, należy uruchomić go do tworzenia dokumentu konfiguracji (plik MOF), a następnie wywołaj [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) skonfigurować LCM.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Nazewnictwo i wprowadzania dokumentów konfiguracji na serwerze ściągania (ConfigurationNames)

Dokumenty częściowe konfiguracji musi być umieszczony w folderze określonym jako **ConfigurationPath** w `web.config` plików na serwerze ściągania (zazwyczaj `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Nadawanie nazw dokumentów konfiguracji na serwerze ściągania w programie PowerShell 5.1

Jeśli należy pobrać tylko jeden częściowe konfiguracji z serwera ściągania poszczególnych dokumentu konfiguracji może mieć dowolną nazwę. Jeśli należy pobrać więcej niż jeden częściowe konfiguracji z serwera ściągania dokumentu konfiguracji może mieć nazwę albo `<ConfigurationName>.mof`, gdzie *ConfigurationName* nazywa się częściowe konfiguracji lub `<ConfigurationName>.<NodeName>.mof`, gdzie *ConfigurationName* nazywa się częściowe konfiguracji i *NodeName* jest nazwa węzła docelowego. Dzięki temu można do ściągania konfiguracji z serwera ściągania usługi Azure Automation DSC.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Nadawanie nazw dokumentów konfiguracji na serwerze ściągania w programie PowerShell 5.0

Dokumenty konfiguracji musi mieć nazwę w następujący sposób: `ConfigurationName.mof`, gdzie *ConfigurationName* nazywa się częściowe konfiguracji. W naszym przykładzie dokumentów konfiguracji powinien zostać nazwany w następujący sposób:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Nazewnictwo i wprowadzania dokumentów konfiguracji na serwerze ściągania (ConfigurationID)

Dokumenty częściowe konfiguracji musi być umieszczony w folderze określonym jako **ConfigurationPath** w `web.config` plików na serwerze ściągania (zazwyczaj `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Dokumenty konfiguracji musi mieć nazwę w następujący sposób: `<ConfigurationName>.<ConfigurationID>.mof`, gdzie _ConfigurationName_ nazywa się częściowe konfiguracji i _ConfigurationID_ jest Konfiguracja identyfikator zdefiniowany w LCM w docelowym węźle. W naszym przykładzie dokumentów konfiguracji powinien zostać nazwany w następujący sposób:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Uruchomione konfiguracje częściowe z serwera ściągania

Po LCM na węzeł docelowy został skonfigurowany, a konfiguracja dokumentów zostały utworzone i nazwana poprawnie na serwerze ściągania węzeł docelowy będzie pobierać konfiguracje częściowe, łączyć je i zastosować Wynikowa konfiguracja zwykłych interwały określony przez **RefreshFrequencyMins** właściwość LCM. Jeśli chcesz wymusić odświeżenie, można wywołać [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) polecenia cmdlet, aby ściągnąć konfiguracji, a następnie `Start-DSCConfiguration –UseExisting` ich stosowania.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Konfiguracje częściowe w mieszanych trybach wypychania i ściągania

Możesz mieszać wypychania i ściągania tryby konfiguracje częściowe. Oznacza to może mieć jedną konfigurację częściowe są pobierane z serwera ściągania, gdy zostanie przypisany inny częściowe konfiguracji. Określ tryb odświeżania dla każdej konfiguracji częściowe, zgodnie z opisem w poprzedniej sekcji. Na przykład następująca konfiguracja metadanych w tym artykule opisano tym samym przykładzie, za pomocą `ServiceAccountConfig` częściowe konfiguracji w trybie ściągania i `SharePointConfig` częściowe konfiguracji w trybie wypychania.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Mieszane trybach wypychania i ściągania przy użyciu ConfigurationNames

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Mieszane trybach wypychania i ściągania przy użyciu ConfigurationID

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

Należy pamiętać, że **RefreshMode** określone w bloku ustawień jest "Ściągania", ale **RefreshMode** dla `SharePointConfig` częściowe konfiguracji to "Push".

Nadaj nazwę, a następnie zlokalizuj pliki MOF konfiguracji, zgodnie z powyższym opisem dla trybów ich odpowiednich odświeżania.
Wywołaj `Publish-DSCConfiguration` publikowanie `SharePointConfig` częściowe konfiguracji, a następnie poczekaj, aż `ServiceAccountConfig` konfigurację, aby zostać pobrane z serwera ściągania lub wymusić odświeżenie, wywołując [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Przykładowa konfiguracja ServiceAccountConfig częściowego

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

## <a name="example-sharepointconfig-partial-configuration"></a>Przykładowa konfiguracja SharePointConfig częściowego

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

## <a name="see-also"></a>Zobacz też

[Program Windows PowerShell Desired State Configuration ściągnięcia serwerów](pullServer.md)

[Windows Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md)