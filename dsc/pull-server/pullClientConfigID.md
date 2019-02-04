---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji w programie PowerShell 5.0 lub nowszy
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685872"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji w programie PowerShell 5.0 lub nowszy

> Dotyczy: Windows PowerShell 5.0

> [!IMPORTANT]
> Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno. Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).

Przed rozpoczęciem konfigurowania klienta ściągania, należy skonfigurować serwer ściągania. Chociaż ta kolejność nie jest wymagane, pomaga w rozwiązywaniu problemów i pomaga zagwarantować, że rejestracja zakończyła się pomyślnie. Aby skonfigurować serwer ściągania, można użyć następujących przewodników:

- [Konfigurowanie serwera ściągania SMB DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)

Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu. Poniższe sekcje pokazują, jak konfigurowanie klienta ściągania przy użyciu udziału SMB lub protokołu HTTP DSC Pull Server. Podczas odświeżania LCM węzła, jej skontaktuje się skonfigurowanej lokalizacji, aby pobrać wszystkie przypisane konfiguracje. Jeśli wszystkie wymagane zasoby, które nie istnieją w węźle, zostaną automatycznie pobrane je ze skonfigurowanej lokalizacji. Jeśli węzeł jest skonfigurowana z [serwera raportów](reportServer.md), następnie zgłasza stan operacji.

> **Uwaga**: Ten temat dotyczy programu PowerShell w wersji 5.0. Aby uzyskać informacje na temat konfigurowania klienta ściągania w programie PowerShell 4.0, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Konfigurowanie klienta ściągania LCM

Wykonanie wszystkich poniższych przykładach tworzy nowy folder wyjściowy o nazwie **PullClientConfigID** i umieszcza plik MOF metaconfiguration istnieje. W tym przypadku będzie miała nazwę pliku MOF metaconfiguration `localhost.meta.mof`.

Aby zastosować konfigurację, należy wywołać **Set-DscLocalConfigurationManager** polecenia cmdlet, za pomocą **ścieżki** Ustaw lokalizację pliku MOF metaconfiguration. Przykład:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Identyfikator konfiguracji

Przykłady poniżej zestawów **ConfigurationID** właściwość LCM do **Guid** które było wcześniej utworzone w tym celu. **ConfigurationID** jest LCM używa można odnaleźć odpowiedniej konfiguracji na serwerze ściągania. Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania `ConfigurationID.mof`, gdzie *ConfigurationID* jest wartością **ConfigurationID** właściwość LCM węzeł docelowy. Aby uzyskać więcej informacji, zobacz [publikowania konfiguracje serwera ściągania (v4/v5)](publishConfigs.md).

Można utworzyć losowej **Guid** w przykładzie poniżej lub za pomocą [nowy Guid](/powershell/module/microsoft.powershell.utility/new-guid) polecenia cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Aby uzyskać więcej informacji o korzystaniu z **identyfikatorów GUID** w danym środowisku, zobacz [planowanie identyfikatorów GUID](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Konfigurowanie klienta ściągania można pobrać konfiguracji

Każdy klient musi być skonfigurowany w **ściągnięcia** tryb i adres url serwera ściągania przechowywania jego konfiguracji. Aby to zrobić, należy skonfigurować lokalne Configuration Manager (LCM) niezbędne informacje. Aby skonfigurować LCM, należy utworzyć specjalny rodzaj konfiguracji ozdobione **DSCLocalConfigurationManager** atrybutu. Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>HTTP DSC Pull Server

Poniższy skrypt konfiguruje LCM ściągania konfiguracje z serwerem o nazwie "CONTOSO-PullSrv".

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

W skrypcie **ConfigurationRepositoryWeb** bloku definiuje serwera ściągania. **ServerUrl** Określa adres url ściągnięcia DSC

### <a name="smb-share"></a>Udział SMB

Poniższy skrypt konfiguruje LCM ściągania konfiguracje z udziału SMB `\\SMBPullServer\Pull`.

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
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

W skrypcie **ConfigurationRepositoryShare** bloku definiuje serwera ściągania, w tym przypadku jest po prostu udziału SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Konfigurowanie klienta ściągania można pobrać zasobów

Jeśli określisz tylko **ConfigurationRepositoryWeb** lub **ConfigurationRepositoryShare** blokuje w konfiguracji LCM (tak jak w poprzednich przykładach), klienta ściągania będzie pobierać zasoby z tej samej Lokalizacja pobierania jego konfiguracji. Można również określić oddzielne lokalizacje dla zasobów. Aby określić lokalizację zasobu jako oddzielny serwer, użyj **ResourceRepositoryWeb** bloku. Aby określić lokalizację zasobu jako udziału SMB, użyj **ResourceRepositoryShare** bloku.

> [!NOTE]
> Można połączyć **ConfigurationRepositoryWeb** z **ResourceRepositoryShare** lub **ConfigurationRepositoryShare** z **ResourceRepositoryWeb** . Przykłady tego nie zostały wymienione poniżej.

### <a name="http-dsc-pull-server"></a>HTTP DSC Pull Server

Następujące metaconfiguration konfiguruje klienta ściągania, aby uzyskać jego konfiguracji z **CONTOSO PullSrv** i jej zasobach z **CONTOSO ResourceSrv**.

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
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>Udział SMB

W poniższym przykładzie pokazano metaconfiguration, który konfiguruje klienta do ściągania konfiguracji z udziału SMB `\\SMBPullServer\Configurations`i zasoby z udziału SMB `\\SMBPullServer\Resources`.

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
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Automatycznie pobieraj zasobami w trybie Push

Począwszy od programu PowerShell w wersji 5.0 klientów ściągnięcia można pobrać modułów z udziału SMB nawet wtedy, gdy są one konfigurowane na potrzeby **wypychania** trybu. Jest to szczególnie przydatne w scenariuszach, w których nie chcesz skonfigurować serwer ściągania. **ResourceRepositoryShare** bloku mogą być używane bez określania **ConfigurationRepositoryShare**. W poniższym przykładzie pokazano metaconfiguration, który konfiguruje klienta do ściągnięcia zasobów z udziału SMB `\\SMBPullServer\Resources`. Gdy węzeł zostaje **PUSHED** konfiguracji automatycznie pobierze wszystkie wymagane zasoby z udziału określonego.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Konfigurowanie klienta ściągania raportowanie stanu

Domyślnie węzły nie będą wysyłały raporty do skonfigurowanego serwera ściągania. Serwer pojedynczego ściągania można użyć do konfiguracji, zasobów i raportów, ale należy utworzyć **ReportRepositoryWeb** bloku, aby skonfigurować raportowanie.

### <a name="http-dsc-pull-server"></a>HTTP DSC Pull Server

Poniższy przykład pokazuje metaconfiguration, który konfiguruje klienta do ściągania konfiguracji i zasobów oraz wysyłania danych, raportowania na serwerze ściągania jednego.

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

Aby określić serwer raportów, należy użyć **ReportRepositoryWeb** bloku. Serwer raportów nie może być serwerem SMB.
Następujące metaconfiguration konfiguruje klienta ściągania, aby uzyskać jego konfiguracji z **CONTOSO PullSrv** i jej zasobach z **CONTOSO ResourceSrv**i wysyłać raporty o stanie do  **CONTOSO ReportSrv**:

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

### <a name="smb-share"></a>Udział SMB

Serwer raportów nie może być udziału SMB.

## <a name="next-steps"></a>Następne kroki

Po skonfigurowaniu klienta ściągania następujące przewodniki można użyć, aby wykonać kolejne kroki:

- [Publikowanie konfiguracji na serwerze ściągania (v4/v5)](publishConfigs.md)
- [Pakiet i przekazywanie zasobów do serwera ściągania (v4)](package-upload-resources.md)

## <a name="see-also"></a>Zobacz też

* [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](pullClientConfigNames.md)
