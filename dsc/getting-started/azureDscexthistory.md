---
description: Poznaj historię wersji rozszerzenia Desired State Configuration (DSC) na platformie Azure.
ms.date: 06/21/2018
keywords: dsc, powershell, azure, extension
title: Historia wersji rozszerzenie DSC usługi Azure
ms.openlocfilehash: 2c076e3beccc15e99af2327820916d7a4d28da68
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688126"
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Historia wersji rozszerzenia Azure Desired State Configuration

Rozszerzenie maszyny Wirtualnej platformy Azure Desired State Configuration (DSC) jest aktualizowana, wymagane do obsługi ulepszeń i nowych możliwości realizowane przez Azure, Windows Server i Windows Management Framework (WMF) zawierający programu Windows PowerShell.

W tym artykule zawierają informacje o każdej wersji rozszerzenia maszyny Wirtualnej platformy Azure DSC, jakich środowiskach ją obsługuje, komentarze i uwagi nad nowymi funkcjami lub zmiany.

## <a name="latest-version"></a>Najnowsza wersja

### <a name="version-276"></a>Wersja 2.76

- **Data wydania:**
  - 9 maja 2018 r. (Azure) | Czerwiec 21 2018 r. (chińska wersja platformy Azure, platforma Azure Government)
- **Obsługa systemu operacyjnego:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 z dodatkiem SP1
  - Windows Client 7/8.1/10
  - Serwer Nano Server
- **Pomoc techniczna platformy WMF:**
  - WMF 5.1
  - WMF 5.0 RTM
  - Aktualizacja programu WMF 4.0
  - WMF 4.0
- **Środowisko:**
  - Azure
  - Azure China
  - Platforma Azure Government
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (Instalowanie programu WMF wymaga ponownego uruchomienia). Dla serwera Nano Server DSC rola jest instalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Poprawa metadane rozszerzenia podstanu i inne poprawki drobnych błędów.

## <a name="supported-versions"></a>Obsługiwane wersje

> [!WARNING]
> W wersji 2.4 za pośrednictwem 2.13 Użyj WMF 5.0 publicznej wersji zapoznawczej których certyfikaty podpisywania wygasła w sierpniu 2016.  Aby uzyskać więcej informacji na temat tego problemu, zobacz [wpis w blogu](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Wersja 2,75

- **Data wydania:** 5 marca 2018 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Windows klienta 7/8.1/10 systemu Nano Server
- **Pomoc techniczna platformy WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (Instalowanie programu WMF wymaga ponownego uruchomienia). Dla serwera Nano Server DSC rola jest instalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Po przeniesieniu ostatnie usługi GitHub do protokołu TLS 1.2 nie można dodać maszyny Wirtualnej do usługi Azure Automation DSC, za pomocą szablonów możesz Menedżera zasobów dostępnych w witrynie Azure Marketplace lub użyć rozszerzenia DSC można pobrać żadnych konfiguracji w serwisie GitHub. Zostanie wyświetlony błąd podobny do następującego podczas wdrażania rozszerzenia:

    ```json
    {
        "code": "DeploymentFailed",
        "message": "At least one resource deployment operation failed. Please list deployment operations for details. Please see https://aka.ms/arm-debug for usage details.",
        "details": [{
            "code": "Conflict",
            "message": "{
                \"status\": \"Failed\",
                \"error\": {
                    \"code\": \"ResourceDeploymentFailure\",
                    \"message\": \"The resource operation completed with terminal provisioning state 'Failed'.\",
                    \"details\": [ {
                        \"code\": \"VMExtensionProvisioningError\",
                        \"message\": \"VM has reported a failure when processing extension 'Microsoft.Powershell.DSC'.
                        Error message: \\\"The DSC Extension failed to execute: Error downloading
                        https://github.com/Azure/azure-quickstart-templates/raw/master/dsc-extension-azure-automation-pullserver/UpdateLCMforAAPull.zip
                        after 29 attempts: The request was aborted: Could not create SSL/TLS secure channel..\\nMore information about the failure can
                        be found in the logs located under 'C:\\\\WindowsAzure\\\\Logs\\\\Plugins\\\\Microsoft.Powershell.DSC\\\\2.74.0.0' on the VM.\\\".\"
                    } ]
                }
            }"
        }]
    }
    ```

  - W nowej wersji rozszerzenia protokołu TLS 1.2, obecnie jest wymuszany. Podczas wdrażania rozszerzenia, jeśli masz już AutoUpgradeMinorVersion = true w szablonie usługi Resource Manager, a następnie rozszerzenia będą autoupgraded do 2,75. Ręczne aktualizacje, można określić `TypeHandlerVersion = 2.75` w szablonie usługi Resource Manager.

### <a name="version-270---272"></a>Wersja 2.70 2.72

- **Data wydania:** 13 listopada 2017 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Windows klienta 7/8.1/10 systemu Nano Server
- **Pomoc techniczna platformy WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (Instalowanie programu WMF wymaga ponownego uruchomienia). Dla serwera Nano Server DSC rola jest instalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Usterki, poprawki i udoskonalenia, które upraszcza przy użyciu usługi Azure Automation DSC za pośrednictwem portalu, interfejsu użytkownika, a także szablonu usługi Resource Manager.  Aby uzyskać więcej informacji, zobacz [domyślne skryptu konfiguracji](/azure/virtual-machines/extensions/dsc-overview) w dokumentacji rozszerzenia DSC.

### <a name="version-226"></a>Wersja 2.26

- **Data wydania:** 9 czerwca 2017 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Windows klienta 7/8.1/10 systemu Nano Server
- **Pomoc techniczna platformy WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (Instalowanie programu WMF wymaga ponownego uruchomienia). Dla serwera Nano Server DSC rola jest instalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Ulepszenia telemetrii.

### <a name="version-225"></a>Wersja 2,25

- **Data wydania:** 2 czerwca 2017 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Windows klienta 7/8.1/10 systemu Nano Server
- **Pomoc techniczna platformy WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (Instalowanie programu WMF wymaga ponownego uruchomienia). Dla serwera Nano Server DSC rola jest instalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Kilka poprawek usterek i inne drobne ulepszenia zostały dodane.

### <a name="version-224"></a>Wersja 2.24

- **Data wydania:** 13 kwietnia 2017 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Nano Server
- **Pomoc techniczna platformy WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (Instalowanie programu WMF wymaga ponownego uruchomienia). Dla serwera Nano Server DSC rola jest instalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Przedstawia identyfikator UUID maszyny Wirtualnej i Identyfikatora agenta DSC w postaci metadanych rozszerzenia. Drobne ulepszenia zostały dodane.

### <a name="version-223"></a>Wersja 2.23

- **Data wydania:** 15 marca 2017 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Nano Server
- **Pomoc techniczna platformy WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (Instalowanie programu WMF wymaga ponownego uruchomienia). Dla serwera Nano Server DSC rola jest instalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Wiele poprawek usterek i inne ulepszenia zostały dodane.

### <a name="version-222"></a>Wersja 2.22

- **Data wydania:** 8 lutego 2017 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Nano Server
- **Pomoc techniczna platformy WMF:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (Instalowanie programu WMF wymaga ponownego uruchomienia). Dla serwera Nano Server DSC rola jest instalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Rozszerzenie DSC ma teraz obsługę programu WMF 5.1.
  - Drobne inne ulepszenia zostały dodane.

### <a name="version-221"></a>Wersja 2.21

- **Data wydania:** 2 grudnia 2016 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Nano Server
- **Pomoc techniczna platformy WMF:** WMF 5.1 (wersja zapoznawcza), program WMF 5.0 RTM, WMF 4.0 Update, programu WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (Instalowanie programu WMF wymaga ponownego uruchomienia). Dla serwera Nano Server DSC rola jest instalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Rozszerzenie DSC jest teraz dostępna w systemie Nano Server. Ta wersja zawiera przede wszystkim zmian w kodzie dla rozszerzenia w systemie Nano Server.
  - Drobne inne ulepszenia zostały dodane.

### <a name="version-220"></a>Wersja 2,20

- **Data wydania:** 2 sierpnia 2016 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Pomoc techniczna platformy WMF:** WMF 5.1 (wersja zapoznawcza), program WMF 5.0 RTM, WMF 4.0 Update, programu WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (Instalowanie programu WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Obsługa programu WMF 5.1 (wersja zapoznawcza). Podczas pierwszej publikacji, ta wersja została uaktualnienia opcjonalne i musiał określić Wmfversion = "5.1PP' w szablonach usługi Resource Manager, aby zainstalować program WMF 5.1 (wersja zapoznawcza). Wmfversion = "latest" nadal instaluje [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). Aby uzyskać więcej informacji na temat programu WMF 5.1 (wersja zapoznawcza), zobacz [ten blog]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Pomocnicza inne poprawki i ulepszenia zostały dodane.

### <a name="version--219"></a>Wersja 2.19

- **Data wydania:** 3 czerwca 2016 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Pomoc techniczna platformy WMF:** WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure, chińska wersja platformy Azure, platforma Azure Government
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (Instalowanie programu WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Rozszerzenie DSC jest teraz dołączone do Azure (Chiny). Ta wersja zawiera przede wszystkim poprawki dotyczące korzystania z rozszerzenia w chińskiej wersji platformy Azure.

### <a name="version-218"></a>Wersja 2.18

- **Data wydania:** 3 czerwca 2016 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Pomoc techniczna platformy WMF:** WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (Instalowanie programu WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Upewnij się, dane telemetryczne nieblokującej na poziomie po wystąpieniu błędu podczas pobierania poprawki danych telemetrycznych (znany problem usługi Azure DNS) lub podczas instalacji.
  - Poprawka tymczasowy problem gdzie rozszerzenie zatrzymuje przetwarzanie konfiguracji po ponownym uruchomieniu. To powodowało rozszerzenia DSC w przejście stanu.
  - Pomocnicza inne poprawki i ulepszenia zostały dodane.

### <a name="version-217"></a>Wersja 2.17

- **Data wydania:** 26 kwietnia 2016 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Pomoc techniczna platformy WMF:** WMF 5.0 RTM, WMF 4.0 Update, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (Instalowanie programu WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Obsługa programu WMF 4.0 Update. Aby uzyskać więcej informacji na temat aktualizacji programu WMF 4.0, zobacz [ten blog](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Zainstaluj logikę ponawiania próby na błędy, które występują podczas instalacji rozszerzenia DSC lub podczas stosowania konfiguracji DSC wpis rozszerzenia. W ramach tej zmiany rozszerzenia ponów próbę instalacji, jeśli poprzednia instalacja nie powiodła się lub ponownie wprowadź w życie konfiguracji DSC, która wcześniej zakończonej niepowodzeniem, maksymalnie trzy razy dopóki nie osiągnie stan ukończenia (powodzenie lub błąd), czy nowe żądanie pochodzi. Jeśli rozszerzenie nie powiedzie się z powodu nieprawidłowego użytkownika ustawienia/użytkownika w danych wejściowych, nie ponowień. W takim przypadku rozszerzenie musi ponownie wywołany z nowego żądania i popraw ustawienia użytkownika. Uwaga: Rozszerzenie DSC jest zależna od agenta maszyny Wirtualnej platformy Azure w zakresie ponawiania prób. Agent maszyny Wirtualnej platformy Azure wywołuje rozszerzenia z ostatniego żądania zakończone niepowodzeniem, dopóki nie osiągnie stan powodzenia lub błędu.

### <a name="version-216"></a>Wersja 2,16

- **Data wydania:** 21 kwietnia 2016 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Pomoc techniczna platformy WMF:** WMF 5.0 RTM, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (Instalowanie programu WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Poprawa obsługi błędów i inne poprawki drobnych błędów.
  - Nowe właściwości w ustawieniach rozszerzenia DSC. "ForcePullAndApply" w AdvancedOptions jest dodawany do włączyć rozszerzenie DSC wprowadza konfiguracje DSC, gdy tryb odświeżania jest ściągnięcia (w przeciwieństwie do domyślny tryb Push). Aby uzyskać więcej informacji można znaleźć [ten blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) Aby uzyskać więcej informacji na temat ustawień rozszerzenia DSC.

### <a name="version-215"></a>Wersja 2.15

- **Data wydania:** 14 marca 2016 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Pomoc techniczna platformy WMF:** WMF 5.0 RTM, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (Instalowanie programu WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - W wersji rozszerzenia 2.14 zmiany w instalacji programu WMF RTM zostaną uwzględnione. Podczas uaktualniania z wersji rozszerzenia 2.13.2.0 do 2.14.0.0, możesz zauważyć, że niektóre polecenia cmdlet DSC się nie powieść lub konfigurację zakończy się niepowodzeniem z powodu błędu — "Wystąpienie nie znaleziono z danej wartości właściwości". Aby uzyskać więcej informacji, zobacz [DSC — informacje o wersji](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). W wersji 2.15 zostały dodane obejścia tych problemów.
  - Niestety Jeśli masz już zainstalowaną wersję 2.14 i działają w jednej z dwóch powyższych problemów, należy wykonać te kroki ręcznie.  W sesji programu PowerShell z podwyższonym poziomem uprawnień:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Wersja 2.14

- **Data wydania:** 25 lutego 2016 r.
- **Obsługa systemu operacyjnego:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Pomoc techniczna platformy WMF:** WMF 5.0 RTM, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** Ta wersja wykorzystuje DSC zawartych w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (Instalowanie programu WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Korzysta z wersji RTM programu WMF.
  - Umożliwia zbieranie danych w celu poprawy jakości rozszerzenia DSC. Aby uzyskać więcej informacji, zobacz [blogu](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Miejsce na format zaktualizowanych ustawień rozszerzenia w szablonie usługi Resource Manager. Aby uzyskać więcej informacji, zobacz [blogu](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Poprawki błędów i inne rozszerzenia.

## <a name="next-steps"></a>Następne kroki

- Aby uzyskać więcej informacji na temat programu PowerShell DSC, przejdź do [Centrum dokumentacji programu PowerShell](../overview/overview.md).
- Sprawdź [szablonu usługi Resource Manager dla rozszerzenia DSC](/azure/virtual-machines/extensions/dsc-template).
- Przeglądaj więcej funkcji, w którym można zarządzać za pomocą programu PowerShell DSC, a inne zasoby DSC, [galerii programu PowerShell](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Aby uzyskać szczegółowe informacje o przekazywaniu parametrów poufnych w konfiguracji, zobacz [Zarządzanie poświadczeniami w bezpieczny sposób za pomocą procedury obsługi rozszerzenia DSC](/azure/virtual-machines/extensions/dsc-credentials).