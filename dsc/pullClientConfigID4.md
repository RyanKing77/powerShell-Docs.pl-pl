---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu identyfikator konfiguracji w programie PowerShell 4.0
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a>Konfigurowanie klienta ściągania przy użyciu identyfikator konfiguracji w programie PowerShell 4.0

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL, gdzie może się kontaktować z serwerem ściągania można pobrać konfiguracji. Aby to zrobić, należy skonfigurować lokalne Menedżera konfiguracji (LCM) niezbędne informacje. Aby skonfigurować LCM, należy utworzyć specjalny typ Konfiguracja znana jako "metakonfigurację". Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [Windows PowerShell 4.0 żądanego stanu konfiguracji lokalny program Configuration Manager](metaConfig4.md)

Poniższy skrypt konfiguruje LCM ściągania konfiguracji z serwera o nazwie "PullServer":

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

W skrypcie **DownloadManagerCustomData** przekazuje niezabezpieczone połączenie umożliwia adres URL serwera ściągania i (w tym przykładzie).

Po uruchomieniu tego skryptu, tworzy nowy folder wyjściowy o nazwie **SimpleMetaConfigurationForPull** i umieszcza metakonfigurację pliku MOF.

Aby zastosować konfigurację, użyj **DscLocalConfigurationManager zestaw** wraz z parametrami **ComputerName** (Użyj "localhost") i **ścieżki** (ścieżka do lokalizacji cel pliku localhost.meta.mof węzła). Przykład:
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a>Identyfikator konfiguracji
Zestawy skryptu **ConfigurationID** właściwości LCM wcześniej utworzony w tym celu identyfikatorem GUID (identyfikator GUID można tworzyć przy użyciu **identyfikator Guid nowego** polecenia cmdlet). **ConfigurationID** jest LCM używa można znaleźć prawidłowej konfiguracji na serwerze ściągania. Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania `ConfigurationID.mof`, gdzie *ConfigurationID* jest wartością **ConfigurationID** właściwości LCM węzeł docelowy.

## <a name="pulling-from-an-smb-server"></a>Ściąganie z serwerem SMB

Jeśli serwer ściągania jest skonfigurowany jako udziału plików SMB, a nie usługi sieci web, określ **DscFileDownloadManager** zamiast **WebDownLoadManager**.
**DscFileDownloadManager** przyjmuje **Ścieżka_źródłowa** właściwości zamiast **ServerUrl**. Poniższy skrypt konfiguruje LCM ściągania konfiguracje z udziału SMB na serwerze o nazwie "CONTOSO-SERVER" o nazwie "SmbDscShare":

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md)
- [Konfigurowanie serwera ściągania SMB platformy DSC](pullServerSMB.md)