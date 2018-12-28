---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie programu Local Configuration Manager w poprzednich wersjach programu Windows PowerShell
ms.openlocfilehash: 31ba2ecdaa5a2ff7fcfddb1791c4d00343f4b5d5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404987"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Konfigurowanie programu Local Configuration Manager w poprzednich wersjach programu Windows PowerShell

>Dotyczy: Windows PowerShell 4.0

**Aby uzyskać informacje dotyczące programu Windows PowerShell 5.0 lub nowszego, zobacz [Konfigurowanie programu Local Configuration Manager](metaConfig.md).**

Local Configuration Manager jest aparatu programu Windows PowerShell Desired State Configuration (DSC).
Działa we wszystkich węzłach docelowy i odpowiada za wywołanie zasoby konfiguracji, które są objęte skryptu konfiguracji DSC.
Ten temat zawiera listę właściwości programu Local Configuration Manager i w tym artykule opisano, jak można zmodyfikować ustawienia Local Configuration Manager na węzeł docelowy.

## <a name="local-configuration-manager-properties"></a>Właściwości Local Configuration Manager

Poniższa lista zawiera właściwości Local Configuration Manager, które można ustawić lub pobrać.

- **AllowModuleOverwrite**: Określa, czy nowe konfiguracje pobrane z usługi konfiguracji mogą nadpisać stare w docelowym węźle. Możliwe wartości to True i False.
- **CertificateID**: Odcisk palca certyfikatu używany do zabezpieczania poświadczeń przekazanych w konfiguracji. Aby uzyskać więcej informacji, zobacz [chcesz zabezpieczyć poświadczenia w Desired State Configuration programu Windows PowerShell?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).
- **ConfigurationID**: Określa identyfikator GUID, który jest używany do pobierania pliku szczególną konfigurację przy użyciu usługi ściągania. Identyfikator GUID gwarantuje, że poprawny plik konfiguracji jest dostępny.
- **ConfigurationMode**: Określa, jak programu Local Configuration Manager faktycznie ma zastosowanie do konfiguracji do węzłów docelowych. Może upłynąć następujące wartości:
  - **ApplyOnly**: Po wybraniu tej opcji ma zastosowanie do konfiguracji DSC, a nie robi nic więcej, chyba że nowa konfiguracja zostanie wykryte, albo przez Ciebie wysyłanie nowej konfiguracji bezpośrednio do obiektu docelowego węzła lub jeśli łączysz się usługi ściągania oraz DSC wykryje nową konfigurację po sprawdza przy użyciu usługi ściągania. Jeśli konfiguracja węzła docelowego drifts, nie podjęto żadnej akcji.
  - **ApplyAndMonitor**: Po wybraniu tej opcji (jest to ustawienie domyślne) DSC stosuje wszystkie nowe konfiguracje, czy wysłane bezpośrednio do węzła docelowego lub odnalezione na usługi ściągania. Dzięki temu konfiguracji węzła docelowego drifts z pliku konfiguracji, DSC raporty niezgodności w dziennikach. Aby uzyskać więcej informacji o rejestrowaniu DSC, zobacz [przy użyciu dzienników zdarzeń do diagnozowania błędów w Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: Po wybraniu tej opcji wszelkie nowe konfiguracje dotyczy DSC, czy wysłane bezpośrednio do węzła docelowego lub odnalezione na usługę ściągania. Jeśli konfiguracja węzła docelowego drifts z pliku konfiguracji, DSC raporty niezgodności w dziennikach, a następnie próbuje dopasować konfiguracji węzła docelowego w celu niezgodne z pliku konfiguracji.
- **ConfigurationModeFrequencyMins**: Reprezentuje częstotliwość (w minutach), w którym stosowanie DSC w tle próbuje zaimplementować bieżącą konfigurację w docelowym węźle. Wartość domyślna to 15. Tę wartość można ustawić w połączeniu z trybów RefreshMode. Gdy trybów RefreshMode ŚCIĄGANIA węzeł docelowy kontaktuje się z usługą konfiguracji z interwałem ustawione przez RefreshFrequencyMins i pobiera bieżącą konfigurację. Niezależnie od wartości trybów RefreshMode interwałem ustawione przez ConfigurationModeFrequencyMins, aparat spójności ma zastosowanie najnowszą konfigurację, który został pobrany do węzła docelowego. RefreshFrequencyMins powinien być ustawiony na liczbę całkowitą wielokrotnością ConfigurationModeFrequencyMins.
- **Poświadczenie**: Określa poświadczenia (podobnie jak w przypadku Get-Credential) wymagane do dostępu do zasobów zdalnych, takich jak skontaktować się z usługą konfiguracji.
- **DownloadManagerCustomData**: Reprezentuje tablicę, która zawiera dane niestandardowe, które są specyficzne dla Menedżera pobierania.
- **DownloadManagerName**: Wskazuje nazwę konfiguracji i Menedżer pobierania modułu.
- **RebootNodeIfNeeded**: Pewne zmiany konfiguracji w węźle docelowym może wymagać, aby zastosować zmiany, należy ponownie uruchomić. Wartością **True**, tej właściwości spowoduje ponowne uruchomienie węzła, gdy tylko konfiguracja została całkowicie stosuje bez dalszego ostrzeżenia. Jeśli **False** (wartość domyślna), konfiguracja zostanie ukończona, ale węzła, należy ponownie uruchomić ręcznie zmiany zaczęły obowiązywać.
- **RefreshFrequencyMins**: Używane podczas konfigurowania usługi ściągania. Reprezentuje częstotliwość (w minutach), w którym kontaktuje się usługi ściągania, aby pobrać bieżącą konfigurację programu Local Configuration Manager. Tę wartość można ustawić w połączeniu z ConfigurationModeFrequencyMins. Gdy trybów RefreshMode ŚCIĄGANIA węzeł docelowy kontaktuje się z usługą ściągnięcia z interwałem ustawione przez RefreshFrequencyMins i pobiera bieżącą konfigurację. Ustawione przez ConfigurationModeFrequencyMins interwałem aparatu spójności dotyczy najnowszą konfigurację, który został pobrany do węzła docelowego. Jeśli nie ustawiono RefreshFrequencyMins do liczby całkowitej wielokrotności ConfigurationModeFrequencyMins, system zaokrągli go. Wartość domyślna to 30.
- **RefreshMode**: Możliwe wartości to **wypychania** (ustawienie domyślne) i **ściągnięcia**. W konfiguracji "wypychania" należy umieścić plik konfiguracji na każdym węźle docelowym przy użyciu dowolnego komputera klienckiego. W trybie "pull" należy skonfigurować usługę ściągania dla lokalnego programu Configuration Manager skontaktować się i uzyskać dostęp do plików konfiguracji.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Przykład aktualizowanie ustawień Local Configuration Manager

Możesz zaktualizować ustawienia Local Configuration Manager z węzłem docelowym, w tym **LocalConfigurationManager** block wewnątrz bloku węzła w skrypcie konfiguracji, jak pokazano w poniższym przykładzie.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

Uruchomienie skryptu w poprzednim przykładzie generuje plik MOF, który określa i przechowuje odpowiednie ustawienia.
Aby zastosować ustawienia, można użyć **Set-DscLocalConfigurationManager** polecenia cmdlet, jak pokazano w poniższym przykładzie.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Uwaga**: Dla **ścieżki** parametr należy określić taką samą ścieżkę, który został określony dla **OutputPath** parametru po wywołaniu konfiguracji w poprzednim przykładzie.

Aby wyświetlić bieżące ustawienia Local Configuration Manager, można użyć **Get-DscLocalConfigurationManager** polecenia cmdlet.
Jeśli wywołujesz tego polecenia cmdlet bez parametrów, domyślnie go otrzyma ustawienia Local Configuration Manager dla węzła, na którym zostanie uruchomiona.
Aby określić inny węzeł, użyj **CimSession** parametru za pomocą tego polecenia cmdlet.
