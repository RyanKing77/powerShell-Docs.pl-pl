---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Konfigurowanie klienta ściągania przy użyciu identyfikator konfiguracji"
ms.openlocfilehash: bb14bff95c626b65e2d0d0072c39e4c571cea4b0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a>Konfigurowanie klienta ściągania przy użyciu identyfikator konfiguracji

> Dotyczy: Środowiska Windows PowerShell 5.0

Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL, gdzie może się kontaktować z serwerem ściągania można pobrać konfiguracji. Aby to zrobić, należy skonfigurować lokalne Menedżera konfiguracji (LCM) niezbędne informacje. Aby skonfigurować LCM, należy utworzyć specjalny typ konfiguracji ozdobione **DSCLocalConfigurationManager** atrybutu. Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md).

> **Uwaga**: w tym temacie dotyczą programu PowerShell 5.0. Aby uzyskać informacje na temat konfigurowania klienta ściągania w programie PowerShell 4.0, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md)

Poniższy skrypt konfiguruje LCM ściągania konfiguracji z serwera o nazwie "CONTOSO-PullSrv".

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }      
    }
}
PullClientConfigID
```

W skrypcie **ConfigurationRepositoryWeb** z serwerem ściągania definiuje bloku. **ServerURL**

Po uruchomieniu tego skryptu, tworzy nowy folder wyjściowy o nazwie **PullClientConfigID** i umieszcza metakonfigurację pliku MOF. W takim przypadku będzie miała nazwę pliku MOF metakonfigurację `localhost.meta.mof`.

Aby zastosować konfigurację, należy wywołać **DscLocalConfigurationManager zestaw** polecenia cmdlet z **ścieżki** Ustaw lokalizację pliku MOF metakonfigurację. Na przykład: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## <a name="configuration-id"></a>Identyfikator konfiguracji

Zestawy skryptu **ConfigurationID** właściwości LCM wcześniej utworzony w tym celu identyfikatorem GUID (identyfikator GUID można tworzyć przy użyciu **identyfikator Guid nowego** polecenia cmdlet). **ConfigurationID** jest LCM używa można znaleźć prawidłowej konfiguracji na serwerze ściągania. Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania _ConfigurationID_MOF, gdzie _ConfigurationID_ jest wartością **ConfigurationID** właściwości elementu docelowego LCM węzła.

## <a name="smb-pull-server"></a>Serwerem ściągania SMB

Aby skonfigurować klienta do ściągania konfiguracje z serwerem SMB, użyj **ConfigurationRepositoryShare** bloku. W **ConfigurationRepositoryShare** bloku, określ ścieżkę do serwera przez ustawienie **Ścieżka_źródłowa** właściwości. Węzeł docelowy do ściąganie danych z serwera ściągania SMB o nazwie konfiguruje następujące metakonfigurację **SMBPullServer**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a>Serwery zasobów i raportów

Jeśli określisz tylko **ConfigurationRepositoryWeb** lub **ConfigurationRepositoryShare** bloków w konfiguracji LCM (tak jak w poprzednim przykładzie), klient ściągania będzie pobierać zasobów z określony serwer, ale nie będą wysyłały raportów do niego. Serwer pojedynczego ściągania można używać do konfiguracji, zasobów i raportów, ale należy utworzyć **ReportRepositoryWeb** bloku, aby skonfigurować raportowanie. 

W poniższym przykładzie przedstawiono metakonfigurację, który konfiguruje klienta w celu ściągania konfiguracje i zasobów i wysyłania raportowania danych, na serwerze ściągania pojedynczego.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Można również określić serwery ściągania różnych zasobów i raportowania. Aby określić serwer zasobów, użyj albo **ResourceRepositoryWeb** (na serwerze ściągania sieci web) lub **ResourceRepositoryShare** bloku (na serwerze ściągania SMB).
Aby określić serwer raportów, należy użyć **ReportRepositoryWeb** bloku. Serwer raportów nie może być serwerem SMB.
Następujące metakonfigurację konfiguruje klienta ściągania można pobrać jego konfiguracje z **CONTOSO PullSrv** i jej zasobach z **CONTOSO ResourceSrv**i do wysyłania raportów o stanie  **CONTOSO ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            
        }
        
        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## <a name="see-also"></a>Zobacz też

* [Konfigurowanie klienta ściągnięcia z nazwy konfiguracji](pullClientConfigNames.md)

