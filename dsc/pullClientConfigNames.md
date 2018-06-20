---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji
ms.openlocfilehash: d71376d84b9d4b0e74fdccab4b9249b2ca4263cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188095"
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a>Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji

> Dotyczy: Środowiska Windows PowerShell 5.0

> [!IMPORTANT]
> Ściągnięcia serwera (funkcja Windows *DSC usługi*) jest obsługiwanych składników systemu Windows Server jednak nie ma żadnych planów oferować nowe funkcje lub możliwości. Zaleca się rozpocząć przechodzenie zarządzanych klientów do [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started) (w tym funkcji poza ściągnięcia serwera w systemie Windows Server) lub jednego z rozwiązań społeczności wymienionych [tutaj](pullserver.md#community-solutions-for-pull-service).

Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL, gdzie może się kontaktować z serwerem ściągania można pobrać konfiguracji.
Aby to zrobić, należy skonfigurować lokalne Menedżera konfiguracji (LCM) niezbędne informacje.
Aby skonfigurować LCM, należy utworzyć specjalny typ konfiguracji ozdobione **DSCLocalConfigurationManager** atrybutu.
Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md).

> **Uwaga**: w tym temacie dotyczą programu PowerShell 5.0.
Aby uzyskać informacje na temat konfigurowania klienta ściągania w programie PowerShell 4.0, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md)

Poniższy skrypt konfiguruje LCM ściągania konfiguracji z serwera o nazwie "CONTOSO-PullSrv":

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

W skrypcie **ConfigurationRepositoryWeb** z serwerem ściągania definiuje bloku.
**ServerURL** właściwość określa punktu końcowego na serwerze ściągania.

**RegistrationKey** właściwość jest kluczem udostępnionego między wszystkie węzły klienta na serwerze ściągania i że serwera ściągania.
Tę samą wartość jest przechowywane w pliku na serwerze ściągania.

**ConfigurationNames** właściwość jest tablicą, który określa nazwę konfiguracji przeznaczonych dla węzła klienta.
Na serwerze ściągania dla tego węzła klienta musi mieć nazwę pliku konfiguracji MOF *ConfigurationNames*MOF, gdzie *ConfigurationNames* odpowiada wartości **ConfigurationNames**  zestawu metakonfigurację tej właściwości.

>**Uwaga:** określenia więcej niż jedną wartość w **ConfigurationNames**, należy także określić **PartialConfiguration** blokuje w konfiguracji.
Informacje o konfiguracjach częściowe, zobacz [konfiguracje częściowe konfiguracji żądanego stanu środowiska PowerShell](partialConfigs.md).

Po uruchomieniu tego skryptu, tworzy nowy folder wyjściowy o nazwie **PullClientConfigNames** i umieszcza metakonfigurację pliku MOF.
W takim przypadku będzie miała nazwę pliku MOF metakonfigurację `localhost.meta.mof`.

Aby zastosować konfigurację, należy wywołać **DscLocalConfigurationManager zestaw** polecenia cmdlet z **ścieżki** Ustaw lokalizację pliku MOF metakonfigurację.

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> **Uwaga**: klucze rejestracji działa tylko z serwerów sieci web ściągania.
Możesz nadal korzystać **ConfigurationID** z serwerem ściągania SMB.
Informacje o konfigurowaniu serwera ściągania przy użyciu **ConfigurationID**, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji](PullClientConfigNames.md)

## <a name="resource-and-report-servers"></a>Serwery zasobów i raportów

Jeśli określisz tylko **ConfigurationRepositoryWeb** lub **ConfigurationRepositoryShare** bloków w konfiguracji LCM (tak jak w poprzednim przykładzie), klient ściągania będzie pobierać zasobów z określony serwer, ale nie będą wysyłały raportów do niego.
Serwer pojedynczego ściągania można używać do konfiguracji, zasobów i raportów, ale należy utworzyć **ReportRepositoryWeb** bloku, aby skonfigurować raportowanie.
W poniższym przykładzie przedstawiono metakonfigurację, który konfiguruje klienta w celu ściągania konfiguracje i zasobów i wysyłania raportowania danych, na serwerze ściągania pojedynczego.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

Można również określić serwery ściągania różnych zasobów i raportowania.
Aby określić serwer zasobów, użyj albo **ResourceRepositoryWeb** (na serwerze ściągania sieci web) lub **ResourceRepositoryShare** bloku (na serwerze ściągania SMB).
Aby określić serwer raportów, należy użyć **ReportRepositoryWeb** bloku.
Serwer raportów nie może być serwerem SMB.
Następujące metakonfigurację konfiguruje klienta ściągania można pobrać jego konfiguracje z **CONTOSO PullSrv** i jej zasobach z **CONTOSO ResourceSrv**i do wysyłania raportów o stanie  **CONTOSO ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Zobacz też

* [Konfigurowanie klienta ściągnięcia z identyfikator konfiguracji](PullClientConfigNames.md)
* [Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md)