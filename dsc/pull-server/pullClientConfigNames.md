---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji w programie PowerShell 5.0 lub nowszy
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405306"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji w programie PowerShell 5.0 lub nowszy

> Dotyczy: Windows PowerShell 5.0

> [!IMPORTANT]
> Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno. Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).

Przed rozpoczęciem konfigurowania klienta ściągania, należy skonfigurować serwer ściągania. Chociaż ta kolejność nie jest wymagane, pomaga w rozwiązywaniu problemów i pomaga zagwarantować, że rejestracja zakończyła się pomyślnie. Aby skonfigurować serwer ściągania, można użyć następujących przewodników:

- [Konfigurowanie serwera ściągania SMB DSC](pullServerSmb.md)
- [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md)

Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu. Poniższe sekcje pokazują, jak konfigurowanie klienta ściągania przy użyciu udziału SMB lub protokołu HTTP DSC Pull Server. Podczas odświeżania LCM węzła, jej skontaktuje się skonfigurowanej lokalizacji, aby pobrać wszystkie przypisane konfiguracje. Jeśli wszystkie wymagane zasoby, które nie istnieją w węźle, zostaną automatycznie pobrane je ze skonfigurowanej lokalizacji. Jeśli węzeł jest skonfigurowana z [serwera raportów](reportServer.md), następnie zgłasza stan operacji.

> **Uwaga**: Ten temat dotyczy programu PowerShell w wersji 5.0.
Aby uzyskać informacje na temat konfigurowania klienta ściągania w programie PowerShell 4.0, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Konfigurowanie klienta ściągania LCM

Wykonanie wszystkich poniższych przykładach tworzy nowy folder wyjściowy o nazwie **PullClientConfigName** i umieszcza plik MOF metaconfiguration istnieje. W tym przypadku będzie miała nazwę pliku MOF metaconfiguration `localhost.meta.mof`.

Aby zastosować konfigurację, należy wywołać **Set-DscLocalConfigurationManager** polecenia cmdlet, za pomocą **ścieżki** Ustaw lokalizację pliku MOF metaconfiguration. Przykład:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Nazwa konfiguracji

Przykłady poniżej zestawów **ConfigurationName** właściwość LCM nazwę konfiguracji poprzednio skompilowane, utworzone w tym celu. **ConfigurationName** jest LCM używa można odnaleźć odpowiedniej konfiguracji na serwerze ściągania. Musi mieć nazwę pliku MOF konfiguracji na serwerze ściągania `<ConfigurationName>.mof`, w tym przypadku "ClientConfig.mof". Aby uzyskać więcej informacji, zobacz [publikowania konfiguracje serwera ściągania (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Konfigurowanie klienta ściągania można pobrać konfiguracji

Każdy klient musi być skonfigurowany w **ściągnięcia** tryb i adres url serwera ściągania przechowywania jego konfiguracji. Aby to zrobić, należy skonfigurować lokalne Configuration Manager (LCM) niezbędne informacje. Aby skonfigurować LCM, należy utworzyć specjalny rodzaj konfiguracji ozdobione **DSCLocalConfigurationManager** atrybutu. Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md).

Poniższy skrypt konfiguruje LCM ściągania konfiguracje z serwerem o nazwie "CONTOSO-PullSrv".

- W skrypcie **ConfigurationRepositoryWeb** bloku definiuje serwera ściągania. **ServerURL** właściwość określa punkt końcowy serwera ściągania.

- **RegistrationKey** właściwość jest klucz współużytkowany między wszystkie węzły serwera ściągania klienta i że serwera ściągania. Tej samej wartości są przechowywane w pliku na serwerze ściągania.
  > **Uwaga**: Klucze rejestracji działają tylko z **web** pobierania serwerów. Nadal należy użyć **ConfigurationID** z **SMB** serwera ściągania.
  > Aby uzyskać informacje o konfigurowaniu serwera ściągania przy użyciu **ConfigurationID**, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji](pullClientConfigId.md)

- **ConfigurationNames** właściwość jest tablicą, który określa nazwę konfiguracji przeznaczonych dla węzła klienta.
  >**Uwaga:** Jeśli określisz więcej niż jedną wartość w **ConfigurationNames**, należy także określić **PartialConfiguration** bloków w konfiguracji.
  >Aby uzyskać informacje o konfiguracjach częściowe, zobacz [konfiguracje częściowe PowerShell Desired State Configuration](partialConfigs.md).

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

## <a name="set-up-a-pull-client-to-download-resources"></a>Konfigurowanie klienta ściągania można pobrać zasobów

Jeśli określisz tylko **ConfigurationRepositoryWeb** lub **ConfigurationRepositoryShare** blokuje w konfiguracji LCM (jak w poprzednim przykładzie), klienta ściągania będzie pobierać zasoby z takie same Lokalizacja, w którym są przechowywane pliki "MOF". Można również określić różne lokalizacje, w którym klienci mogą pobierać zasoby. Aby określić serwer zasobów, możesz użyć **ResourceRepositoryWeb** (dla internetowego serwera ściągania) lub **ResourceRepositoryShare** bloku (w przypadku serwera ściągania SMB).

Poniższy przykład pokazuje metaconfiguration, który konfiguruje klienta można pobrać konfiguracji z serwera ściągania i zasoby z udziału SMB.

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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Konfigurowanie klienta ściągania raportowanie stanu

Serwer pojedynczego ściągania służy do konfiguracji, zasobów i raportów. Raportowanie nie jest skonfigurowane dla klientów domyślnie. Aby skonfigurować klienta do raportów o stanie, trzeba utworzyć **ReportRepositoryWeb** bloku. Poniższy przykład pokazuje metaconfiguration, który konfiguruje klienta do ściągania konfiguracji i zasobów oraz wysyłania danych, raportowania na serwerze ściągania jednego.

> [!NOTE]
> Serwer raportów nie może być udziału SMB.

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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Zobacz też

* [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji](PullClientConfigNames.md)
* [Konfigurowanie internetowego serwera ściągania DSC](pullServer.md)
