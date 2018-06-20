---
description: Więcej informacji na temat Historia wersji rozszerzenia konfiguracji żądanego stanu (DSC) na platformie Azure.
ms.date: 05/09/2018
keywords: dsc, powershell, azure, extension
title: Historia wersji Azure rozszerzenia usługi Konfiguracja DSC
ms.openlocfilehash: 81dfcf81bd8f8685a0c8c81cd07bc5447e1abf94
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189945"
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Historia wersji rozszerzenia konfiguracji Azure żądany stan

Konfiguracja żądanego stanu Azure (DSC) rozszerzenia maszyny Wirtualnej jest aktualizowana, wymagane do obsługi nowych możliwości oferowane przez Azure, Windows Server i Windows Management Framework (WMF) zawierający środowiska Windows PowerShell i rozszerzeń.

W tym artykule będzie zawierał informacje o każdej wersji rozszerzenia maszyny Wirtualnej Azure DSC, jakie środowisk obsługuje i komentarze i uwagi na nowe funkcje i zmiany.

## <a name="latest-versions"></a>Najnowsze wersje

### <a name="version-276"></a>Wersja 2.76

- **Data wydania:**
  - 9 maja 2018
- **Obsługiwane systemy operacyjne:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 z dodatkiem SP1
  - Klient systemu Windows 7/8.1/10
  - Serwer Nano Server
- **Obsługa WMF:**
  - WMF 5.1
  - WMF 5.0 RTM
  - Zaktualizuj WMF 4.0
  - WMF 4.0
- **Środowisko:**
  - Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework w wersji 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalowanie WMF wymaga ponownego uruchomienia). Nano Server DSC rola jest zainstalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Ulepszenia w metadanych rozszerzenia podstanu i innych niewielkie poprawki błędów.

### <a name="version-219"></a>Wersja 2.19

- **Data wydania:**
  - 3 czerwca 2016 r.
- **Obsługiwane systemy operacyjne:**
  - Windows Server 2016 Technical Preview
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 z dodatkiem SP1
- **Obsługa WMF:**
  - WMF 5.0 RTM
  - Zaktualizuj WMF 4.0
  - WMF 4.0
- **Środowisko:**
  - Azure
  - Azure China
  - Azure dla instytucji rządowych
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalowanie WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Rozszerzenia DSC teraz jest na dodawanej do Chińskiej wersji platformy Azure. Ta wersja zawiera głównie poprawki dotyczące uruchamiania rozszerzenia w chińskiej wersji platformy Azure.

## <a name="supported-versions"></a>Obsługiwane wersje

> [!WARNING]
> W wersji 2.4 za pośrednictwem 2.13 Użyj WMF 5.0 publicznej wersji zapoznawczej których certyfikaty podpisywania wygasła w sierpniu 2016.  Aby uzyskać więcej informacji na temat tego problemu, zobacz [wpis w blogu](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Wersja 2,75

- **Data wydania:** 5 marca 2018
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Windows klienta 7/8.1/10, Nano Server
- **Obsługa WMF:** WMF 5.1, WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework w wersji 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalowanie WMF wymaga ponownego uruchomienia). Nano Server DSC rola jest zainstalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Po przeniesieniu ostatnie GitHub do protokołu TLS 1.2 nie można dołączyć maszyny Wirtualnej, aby konfiguracja DSC automatyzacji Azure za pomocą szablonów DIY Resource Manager dostępne w witrynie Azure Marketplace, lub użyj rozszerzenia usługi Konfiguracja DSC, aby pobrać wszystkie konfiguracji w usłudze GitHub. Zostanie wyświetlony błąd podobny do następującego podczas wdrażania rozszerzenia:

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

  - W nowej wersji rozszerzenia protokołu TLS 1.2, obecnie jest wymuszany. Podczas wdrażania rozszerzenia, jeśli użytkownik ma już AutoUpgradeMinorVersion = true w szablonie usługi Resource Manager, a następnie rozszerzenie zostanie autoupgraded do 2,75. Ręczne aktualizacje, można określić `TypeHandlerVersion = 2.75` w szablonie usługi Resource Manager.

### <a name="version-270---272"></a>Wersja 2.70 2.72

- **Data wydania:** 13 listopada 2017 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Windows klienta 7/8.1/10, Nano Server
- **Obsługa WMF:** WMF 5.1, WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework w wersji 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalowanie WMF wymaga ponownego uruchomienia). Nano Server DSC rola jest zainstalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Usterek poprawki i ulepszeń, które upraszcza korzystanie z usługi Konfiguracja DSC automatyzacji Azure za pomocą interfejsu użytkownika portalu, a także szablonu usługi Resource Manager.  Aby uzyskać więcej informacji, zobacz [domyślny skrypt konfiguracji](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/extensions-dsc-overview#default-configuration-script) w dokumentacji rozszerzenia usługi Konfiguracja DSC.

### <a name="version-226"></a>Wersja 2.26

- **Data wydania:** 9 czerwca 2017 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Windows klienta 7/8.1/10, Nano Server
- **Obsługa WMF:** WMF 5.1, WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework w wersji 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalowanie WMF wymaga ponownego uruchomienia). Nano Server DSC rola jest zainstalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Ulepszenia telemetrii.

### <a name="version-225"></a>Wersja 2,25

- **Data wydania:** 2 czerwca 2017 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Windows klienta 7/8.1/10, Nano Server
- **Obsługa WMF:** WMF 5.1, WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework w wersji 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalowanie WMF wymaga ponownego uruchomienia). Nano Server DSC rola jest zainstalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Dodano kilka poprawek i innych drobne ulepszenia.

### <a name="version-224"></a>Wersja 2,24

- **Data wydania:** 13 kwietnia 2017 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Nano Server
- **Obsługa WMF:** WMF 5.1, WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework w wersji 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalowanie WMF wymaga ponownego uruchomienia). Nano Server DSC rola jest zainstalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Przedstawia UUID maszyny Wirtualnej & Identyfikator agentem DSC w postaci metadanych rozszerzenia. Inne ulepszenia pomocnicza została dodana.

### <a name="version-223"></a>Wersja 2.23

- **Data wydania:** 15 marca 2017 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Nano Server
- **Obsługa WMF:** WMF 5.1, WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework w wersji 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalowanie WMF wymaga ponownego uruchomienia). Nano Server DSC rola jest zainstalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Dodano wiele poprawek usterek i inne usprawnienia.

### <a name="version-222"></a>Wersja 2.22

- **Data wydania:** 8 lutego 2017 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Nano Server
- **Obsługa WMF:** WMF 5.1, WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework w wersji 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalowanie WMF wymaga ponownego uruchomienia). Nano Server DSC rola jest zainstalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Rozszerzenia DSC ma teraz obsługę WMF 5.1.
  - Drobne inne ulepszenia zostały dodane.

### <a name="version-221"></a>Wersja 2.21

- **Data wydania:** 2 grudnia 2016 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1, Nano Server
- **Obsługa WMF:** Podgląd 5.1 WMF, WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalowanie WMF wymaga ponownego uruchomienia). Nano Server DSC rola jest zainstalowana na maszynie Wirtualnej.
- **Nowe funkcje:**
  - Rozszerzenia usługi Konfiguracja DSC jest teraz dostępny na serwerze Nano. Ta wersja zawiera głównie zmiany kodu do uruchomienia na serwerze Nano rozszerzenia.
  - Drobne inne ulepszenia zostały dodane.

### <a name="version-220"></a>Wersja 2,20

- **Data wydania:** 2 sierpnia 2016 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1
- **Obsługa WMF:** Podgląd 5.1 WMF, WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalowanie WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Obsługę WMF 5.1 podglądu. Po pierwszym opublikowaniu, ta wersja została uaktualnienia opcjonalne i musiał określić Wmfversion = ' 5.1PP' w szablonach usługi Resource Manager do zainstalowania WMF 5.1 podglądu. Wmfversion = "najnowszej" nadal instaluje [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). Aby uzyskać więcej informacji na podgląd WMF 5.1, zobacz [ten blog]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Inne poprawki niewielkie oraz dodano ulepszenia.

### <a name="version--219"></a>Wersja 2.19

- **Data wydania:** 3 czerwca 2016 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1
- **Obsługa WMF:** WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure, Azure Chin Azure dla instytucji rządowych
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalowanie WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Rozszerzenia usługi Konfiguracja DSC jest teraz dołączać do Chińskiej wersji platformy Azure. Ta wersja zawiera głównie poprawki dotyczące uruchamiania rozszerzenia w chińskiej wersji platformy Azure.

### <a name="version-218"></a>Wersja 2.18

- **Data wydania:** 3 czerwca 2016 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1
- **Obsługa WMF:** WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalowanie WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Upewnij się, dane telemetryczne nieblokujące po wystąpieniu błędu podczas pobierania poprawki telemetrii (znany problem usługi Azure DNS) lub w trakcie instalacji.
  - Napraw dla tymczasowy problem, gdzie rozszerzenia zatrzymuje przetwarzanie konfiguracji po ponownym rozruchu. To powodowało rozszerzenia usługi Konfiguracja DSC w przejście stanu.
  - Inne poprawki niewielkie oraz dodano ulepszenia.

### <a name="version-217"></a>Wersja 2.17

- **Data wydania:** 26 kwietnia 2016 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1
- **Obsługa WMF:** WMF 5.0 RTM, aktualizacji programu WMF 4.0, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalowanie WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Obsługę WMF 4.0 aktualizacji. Aby uzyskać więcej informacji o aktualizacji programu WMF 4.0, zobacz [ten blog](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Logika ponawiania o błędach podczas instalacji rozszerzenia DSC lub podczas stosowania konfiguracji DSC post rozszerzenia instalacji. W ramach tej zmiany rozszerzenie ponów próbę instalacji, jeśli poprzednia instalacja nie powiodła się lub ponownie wprowadza konfiguracji DSC, która wcześniej nie powiodło się, maksymalnie trzy razy aż osiągnie stan wykonania (powodzenie lub błąd) lub gdy nadejdzie nowe żądanie. Jeśli rozszerzenie zakończy się niepowodzeniem z powodu nieprawidłowego użytkownika ustawienia/użytkownikiem, nie Ponów. W takim przypadku rozszerzenie musi ponownie wywołany z nowego żądania i popraw ustawienia użytkownika. Uwaga: Rozszerzenia DSC jest zależna od agenta maszyny Wirtualnej platformy Azure dla liczby ponownych prób. Agent maszyny Wirtualnej platformy Azure wywołuje rozszerzenie z ostatniego żądania nie powiodło się, dopóki nie osiągnie stan powodzenia lub błędu.

### <a name="version-216"></a>Wersja 2,16

- **Data wydania:** 21 kwietnia 2016 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1
- **Obsługa WMF:** WMF 5.0 RTM, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalowanie WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Poprawy obsługi błędów i innych niewielkie poprawki błędów.
  - Nowe właściwości w ustawieniach rozszerzenia usługi Konfiguracja DSC. "ForcePullAndApply" w AdvancedOptions dodaniu można włączyć rozszerzenia DSC wprowadza konfiguracji DSC, gdy tryb odświeżania jest ściągania (w przeciwieństwie do wypychania tryb domyślny). Aby uzyskać więcej informacji, zapoznaj się [ten blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) Aby uzyskać więcej informacji na temat ustawień rozszerzenia usługi Konfiguracja DSC.

### <a name="version-215"></a>Wersja 2.15

- **Data wydania:** 14 marca 2016 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1
- **Obsługa WMF:** WMF 5.0 RTM, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalowanie WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - W wersji rozszerzenia 2.14 zmiany do zainstalowania WMF RTM zostały uwzględnione. Podczas uaktualniania z wersji rozszerzenia 2.13.2.0 do 2.14.0.0, możesz zauważyć, że niektóre polecenia cmdlet DSC się nie powieść lub konfigurację zakończy się niepowodzeniem z powodu błędu — "Wystąpienia nie znaleziono podanego wartości właściwości". Aby uzyskać więcej informacji, zobacz [DSC wersji](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). W wersji 2.15 zostały dodane rozwiązania tych problemów.
  - Niestety Jeśli została już zainstalowana wersja 2.14 i działają w jednym z powyższych dwóch problemów, należy ręcznie wykonać następujące kroki.  W sesji programu PowerShell z podwyższonym poziomem uprawnień:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Wersja 2.14

- **Data wydania:** 25 lutego 2016 r.
- **Obsługiwane systemy operacyjne:** systemu Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 z dodatkiem SP1
- **Obsługa WMF:** WMF 5.0 RTM, WMF 4.0
- **Środowisko:** Azure
- **Uwagi:** DSC korzysta z tej wersji w systemie Windows Server 2016 Technical Preview; dla innych systemów operacyjnych Windows, instaluje [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalowanie WMF wymaga ponownego uruchomienia).
- **Nowe funkcje:**
  - Używa WMF RTM.
  - Umożliwia zbieranie danych w celu poprawy jakości rozszerzenia usługi Konfiguracja DSC. Aby uzyskać więcej informacji, zobacz [blogu](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Zapewnia to format zaktualizowanych ustawień rozszerzenia w szablonie usługi Resource Manager. Aby uzyskać więcej informacji, zobacz [blogu](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Poprawki błędów i inne rozszerzenia.

## <a name="next-steps"></a>Następne kroki

- Aby uzyskać więcej informacji o konfiguracji DSC środowiska PowerShell, przejdź do [Centrum dokumentacji programu PowerShell](overview.md).
- Sprawdź [szablonu usługi Resource Manager dla rozszerzenia DSC](/azure/virtual-machines/windows/extensions-dsc-template).
- Więcej funkcji, którą można zarządzać za pomocą usługi Konfiguracja DSC środowiska PowerShell, a więcej zasobów DSC, Przeglądaj [galerii programu PowerShell](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Szczegółowe informacje na temat przekazywania poufnych parametrów w konfiguracji, zobacz [Zarządzanie poświadczenia bezpiecznie z obsługą rozszerzenia DSC](/azure/virtual-machines/windows/extensions-dsc-credentials).