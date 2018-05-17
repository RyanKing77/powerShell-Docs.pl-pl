---
ms.date: 10/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie lokalny program Configuration Manager w poprzednich wersjach programu Windows PowerShell
ms.openlocfilehash: 05e315539e51e31b5a496e8c595ac3695d9a0c97
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Konfigurowanie lokalny program Configuration Manager w poprzednich wersjach programu Windows PowerShell

>Dotyczy: Środowiska Windows PowerShell 4.0

**Aby uzyskać informacje dotyczące programu Windows PowerShell 5.0 i nowszych, zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md).**

Lokalny program Configuration Manager jest aparatu programu Windows PowerShell Desired stan konfiguracji (DSC).
Jest uruchamiany na wszystkie węzły docelowe, a jest odpowiedzialny za wywoływanie zasobów konfiguracji, które znajdują się za pomocą skryptów konfiguracji DSC.
W tym temacie przedstawiono listę właściwości z lokalny program Configuration Manager i w tym artykule opisano, jak można zmodyfikować ustawienia lokalny program Configuration Manager w docelowym węźle.

## <a name="local-configuration-manager-properties"></a>Właściwości lokalny program Configuration Manager

Poniżej przedstawiono listę właściwości lokalny program Configuration Manager, które można ustawić lub pobrać.

- **AllowModuleOverwrite**: Określa, czy nowe konfiguracje pobrane z usługi konfiguracji mogą nadpisać stare w docelowym węźle. Możliwe wartości to True i False.
- **CertificateID**: Odcisk palca certyfikatu używany do zabezpieczania poświadczenia przekazywane w konfiguracji. Aby uzyskać więcej informacji, zobacz [chcesz zabezpieczyć poświadczenia w konfiguracji żądanego stanu programu Windows PowerShell?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).
- **ConfigurationID**: Określa identyfikator GUID, który jest używany do pobierania plików określoną konfigurację z usługi replikacji ściąganej. Identyfikator GUID gwarantuje, że poprawny plik konfiguracji jest dostępny.
- **ConfigurationMode**: Określa, jak lokalny program Configuration Manager faktycznie dotyczy konfiguracji węzły docelowe. Przyjmuje następujące wartości:
  - **ApplyOnly**: po wybraniu tej opcji DSC ma zastosowanie do konfiguracji i nie działają dalsze, chyba że zostanie wykryty nową konfigurację, albo przez Ciebie wysyłanie nową konfigurację bezpośrednio do węzła docelowego lub jeśli łączysz się ściągania usługi i konfiguracji DSC podczas sprawdzania z usługą replikacji ściąganej umożliwia odnalezienie nowej konfiguracji. Jeśli konfiguracja węzła docelowego drifts, nie podjęto żadnej akcji.
  - **ApplyAndMonitor**: po wybraniu tej opcji (która jest wartością domyślną) DSC stosuje wszelkie nowe konfiguracje czy wysłane bezpośrednio do węzła docelowego lub zostały odnalezione w usłudze ściągania. Po tej dacie konfiguracji węzła docelowego drifts z pliku konfiguracji, DSC raporty niezgodności w dziennikach. Aby uzyskać więcej informacji na temat rejestrowania DSC, zobacz [przy użyciu dzienników zdarzeń, aby diagnozowanie błędów w konfiguracji żądanego stanu](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: po wybraniu tej opcji DSC stosuje wszelkie nowe konfiguracje czy wysłane bezpośrednio do węzła docelowego lub zostały odnalezione w usłudze ściągania. Później Jeśli konfiguracji węzła docelowego drifts z pliku konfiguracji, DSC raporty niezgodności w dziennikach, a następnie próbuje dopasować konfiguracji węzła docelowego, aby przywrócić zgodność z pliku konfiguracji.
- **ConfigurationModeFrequencyMins**: reprezentuje częstotliwość (w minutach), jaką aplikacja usługi Konfiguracja DSC w tle próbuje zaimplementować bieżącą konfigurację w docelowym węźle. Wartość domyślna to 15. Tę wartość można ustawić w połączeniu z RefreshMode. Gdy RefreshMode ŚCIĄGANIA węzeł docelowy kontaktuje się z usługą konfiguracji z interwałem ustawione przez RefreshFrequencyMins i pobiera bieżącej konfiguracji. Niezależnie od wartości RefreshMode interwałem ustawione przez ConfigurationModeFrequencyMins, aparat spójności stosuje najnowszej konfiguracji, który został pobrany do węzła docelowego. RefreshFrequencyMins powinien być ustawiony na liczbę całkowitą wielokrotnością ConfigurationModeFrequencyMins.
- **Poświadczenie**: wskazuje poświadczeń (podobnie jak w przypadku Get-Credential) wymagane do uzyskania dostępu zdalnego zasobów, takich jak skontaktować się z usługą konfiguracji.
- **DownloadManagerCustomData**: reprezentuje tablicę, która zawiera niestandardowe dane specyficzne dla Menedżera pobierania.
- **DownloadManagerName**: wskazuje nazwę konfiguracji i Menedżer pobierania modułu.
- **RebootNodeIfNeeded**: niektóre zmiany konfiguracji w docelowym węźle może wymagać, aby zmiany zostały zastosowane, należy ponownie uruchomić. Z wartością **True**, ta właściwość zostanie uruchomiony ponownie węzła, gdy tylko konfiguracja została całkowicie stosuje bez dalszego ostrzeżenia. Jeśli **False** (wartość domyślna), konfiguracja zostanie ukończona, ale węzeł musi zostać uruchomione ponownie ręcznie aby zmiany zaczęły obowiązywać.
- **RefreshFrequencyMins**: używany podczas konfigurowania usługi ściągania. Reprezentuje częstotliwość (w minutach), jaką lokalny program Configuration Manager kontaktuje się z usługą ściągania można pobrać bieżącą konfigurację. Tę wartość można ustawić w połączeniu z ConfigurationModeFrequencyMins. Gdy RefreshMode ŚCIĄGANIA węzeł docelowy kontaktuje się z usługą replikacji ściąganej interwałem ustawione przez RefreshFrequencyMins i pobiera bieżącej konfiguracji. Ustawione przez ConfigurationModeFrequencyMins interwałem aparat spójności stosuje najnowszej konfiguracji, który został pobrany do węzła docelowego. Jeśli RefreshFrequencyMins nie jest ustawiona na liczbę całkowitą wielokrotnością ConfigurationModeFrequencyMins, system zaokrągli go. Wartość domyślna to 30.
- **RefreshMode**: możliwe wartości to **Push** (ustawienie domyślne) i **ściągnięcia**. W konfiguracji "push" należy umieścić plik konfiguracji w każdym węźle docelowym za pomocą dowolnego komputera klienckiego. W trybie "ściągania" należy skonfigurować usługę ściągania dla lokalnego programu Configuration Manager skontaktuj się i uzyskać dostęp do plików konfiguracji.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Przykład aktualizowania ustawień lokalny program Configuration Manager

Można zaktualizować ustawień lokalny program Configuration Manager z węzła docelowego przez dołączenie **LocalConfigurationManager** zablokować wewnątrz bloku węzła w skrypcie konfiguracji, jak pokazano w poniższym przykładzie.

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

Uruchamianie skryptu w poprzednim przykładzie generuje plik MOF, który określa i przechowuje odpowiednie ustawienia.
Aby zastosować ustawienia, można użyć **DscLocalConfigurationManager zestaw** polecenia cmdlet, jak pokazano w poniższym przykładzie.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Uwaga**: dla **ścieżki** parametr, należy określić określony dla tej samej ścieżki **OutputPath** parametru, gdy została wywołana z konfiguracją w poprzednim przykładzie.

Aby zobaczyć bieżące ustawienia lokalny program Configuration Manager, można użyć **Get-DscLocalConfigurationManager** polecenia cmdlet.
Jeśli wywołanie tego polecenia cmdlet bez parametrów, domyślnie pobierze ustawienia lokalny program Configuration Manager dla węzła, na którym zostanie uruchomiony.
Aby określić inny węzeł, użyj **CimSession** parametru za pomocą tego polecenia cmdlet.