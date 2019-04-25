---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji w programie PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079476"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji w programie PowerShell 4.0

>Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno. Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).

Przed rozpoczęciem konfigurowania klienta ściągania, należy skonfigurować serwer ściągania. Chociaż ta kolejność nie jest wymagane, pomaga w rozwiązywaniu problemów i pomaga zagwarantować, że rejestracja zakończyła się pomyślnie. Aby skonfigurować serwer ściągania, można użyć następujących przewodników:

- [Konfigurowanie serwera ściągania SMB DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)

Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu. Poniższe sekcje pokazują, jak konfigurowanie klienta ściągania przy użyciu udziału SMB lub protokołu HTTP DSC Pull Server. Podczas odświeżania LCM węzła, jej skontaktuje się skonfigurowanej lokalizacji, aby pobrać wszystkie przypisane konfiguracje. Jeśli wszystkie wymagane zasoby, które nie istnieją w węźle, zostaną automatycznie pobrane je ze skonfigurowanej lokalizacji. Jeśli węzeł jest skonfigurowana z [serwera raportów](reportServer.md), następnie zgłasza stan operacji.

## <a name="configure-the-pull-client-lcm"></a>Konfigurowanie klienta ściągania LCM

Wykonanie wszystkich poniższych przykładach tworzy nowy folder wyjściowy o nazwie **PullClientConfigID** i umieszcza plik MOF metaconfiguration istnieje. W tym przypadku będzie miała nazwę pliku MOF metaconfiguration `localhost.meta.mof`.

Aby zastosować konfigurację, należy wywołać **Set-DscLocalConfigurationManager** polecenia cmdlet, za pomocą **ścieżki** Ustaw lokalizację pliku MOF metaconfiguration. Przykład:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Identyfikator konfiguracji

Przykłady poniżej zestaw **ConfigurationID** właściwość LCM do **Guid** które było wcześniej utworzone w tym celu. **ConfigurationID** jest LCM używa można odnaleźć odpowiedniej konfiguracji na serwerze ściągania. Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania `ConfigurationID.mof`, gdzie *ConfigurationID* jest wartością **ConfigurationID** właściwość LCM węzeł docelowy. Aby uzyskać więcej informacji, zobacz [publikowania konfiguracje serwera ściągania (v4/v5)](publishConfigs.md).

Można utworzyć losowej **Guid** przy użyciu w poniższym przykładzie.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Konfigurowanie klienta ściągania można pobrać konfiguracji

Każdy klient musi być skonfigurowany w **ściągnięcia** tryb i adres url serwera ściągania przechowywania jego konfiguracji. Aby to zrobić, należy skonfigurować lokalne Configuration Manager (LCM) niezbędne informacje. Aby skonfigurować LCM, utworzyć specjalny rodzaj konfiguracji, za pomocą **LocalConfigurationManager** bloku. Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>HTTP DSC Pull Server

Jeśli serwer ściągania jest skonfigurowany jako usługę sieci web, należy ustawić **DownloadManagerName** do **WebDownloadManager**. **WebDownloadManager** wymaga określenia **ServerUrl** do **DownloadManagerCustomData** klucza. Można także określić wartość dla **AllowUnsecureConnection**, jak w poniższym przykładzie. Poniższy skrypt konfiguruje LCM ściągania konfiguracje z serwerem o nazwie "PullServer".

```powershell
Configuration PullClientConfigId
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
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>Udział SMB

Jeśli serwer ściągania jest skonfigurowany jako udział plików SMB, a nie usługi sieci web, należy ustawić **DownloadManagerName** do **DscFileDownloadManager** zamiast **WebDownLoadManager**. **DscFileDownloadManager** wymaga określenia **Ścieżka_źródłowa** właściwość **DownloadManagerCustomData**. Poniższy skrypt konfiguruje LCM do ściągania konfiguracji z udziału SMB na serwerze o nazwie "CONTOSO-SERVER" o nazwie "SmbDscShare".

```powershell
Configuration PullClientConfigId
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
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Następne kroki

Po skonfigurowaniu klienta ściągania następujące przewodniki można użyć, aby wykonać kolejne kroki:

- [Publikowanie konfiguracji na serwerze ściągania (v4/v5)](publishConfigs.md)
- [Pakiet i przekazywanie zasobów do serwera ściągania (v4)](package-upload-resources.md)

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie internetowego serwera ściągania DSC](pullServer.md)
- [Konfigurowanie serwera ściągania DSC SMB](pullServerSMB.md)
