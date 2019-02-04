---
ms.date: 10/16/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Realizacja konfiguracji
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684178"
---
# <a name="enacting-configurations"></a>Realizacja konfiguracji

>Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

Istnieją dwa sposoby wprowadzenie konfiguracje programu PowerShell Desired State Configuration (DSC): wypychanie trybu ani ściągnięcia.

## <a name="push-mode"></a>Trybie wypychania

![Tryb wypychania](../images/pushModel.png "wypychania jak działa tryb")

Trybie wypychania, który odwołuje się do użytkownika aktywnie zastosowanie konfiguracji do węzła docelowego przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.

Po utworzeniu i kompilacji konfiguracji, może ona wprowadza w trybie wypychania — w tym przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet, ustawienie parametru - Path, polecenia cmdlet do ścieżki, w którym znajduje się plik MOF konfiguracji.
Na przykład, jeśli konfiguracja MOF znajduje się w `C:\DSC\Configurations\localhost.mof`, czy dotyczą komputera lokalnego za pomocą następującego polecenia: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Uwaga__: Domyślnie DSC uruchamia konfigurację jako zadanie w tle. Interaktywnie Uruchom konfigurację, należy wywołać [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) z __— oczekiwania__ parametru.

## <a name="pull-mode"></a>Tryb ściągania

![Tryb ściągania](../images/pullModel.png "jak ściągać działa tryb")

W trybie ściągnięcia ściągnięcia klienci są skonfigurowani do pobrania ich konfiguracji żądanego stanu z usługi ściągania zdalnego.
Podobnie usługa ściągania zostało skonfigurowane do hosta DSC usługi i został aprowizowany przy użyciu konfiguracji i zasobów, które są wymagane przez klientów ściągnięcia.
Każdy z klientów ściągania ma zaplanowane zdarzenie, która sprawdza zgodność okresowe konfiguracji węzła.
Gdy zdarzenie zostanie wyzwolone po raz pierwszy, lokalnego Menedżera konfiguracji (LCM) na komputerze klienckim ściągnięcia kieruje żądanie do usługi ściągania można pobrać konfiguracji określone w LCM.
W przypadku tej konfiguracji istnieje na usługi ściągania i przekazuje sprawdzania wstępnego sprawdzania poprawności, konfiguracja jest pobierany do klienta ściągania, gdzie następnie jest wykonywany przez LCM.

LCM sprawdza, czy klient jest zgodne z konfiguracji w regularnych odstępach czasu określonego przez **ConfigurationModeFrequencyMins** właściwość LCM.
LCM sprawdza, czy zaktualizowane konfiguracje usługi ściągania w regularnych odstępach czasu określonego przez **RefreshModeFrequency** właściwość LCM.
Aby dowiedzieć się, jak konfigurowanie programu LCM, zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md).

Zalecane rozwiązanie do hostowania usługi ściągania, to usługa w chmurze DSC, [usługi Azure Automation](https://azure.microsoft.com/services/automation/).
Znajduje się to rozwiązanie zapewnia zarządzania w trybie graficznym, raportowanie i scentralizowanej administracji.

Aby uzyskać więcej informacji na temat konfigurowania usługi ściągania w systemie Windows Server, zobacz [Konfigurowanie internetowego serwera ściągania DSC](pullServer.md).
Dowiedz się, że ta implementacja ma ograniczone funkcje i wymagają do działania integracji niektórych "zrobić to samodzielnie".

W poniższych tematach opisano usługi ściągania i klientami:

- [Omówienie DSC usługi Azure Automation](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Konfigurowanie serwera ściągania SMB](pullServerSMB.md)
- [Konfigurowanie klienta ściągania](pullClientConfigID.md)
