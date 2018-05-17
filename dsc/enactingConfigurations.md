---
ms.date: 10/16/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Realizacja konfiguracji
ms.openlocfilehash: 3d938d14a4da645bbea7ba30ab41e0af72c4b94e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="enacting-configurations"></a>Realizacja konfiguracji

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Istnieją dwa sposoby wprowadza konfiguracje konfiguracji żądanego stanu środowiska PowerShell (DSC): push trybu ani ściągania.

## <a name="push-mode"></a>Tryb wypychania

![Tryb wypychania](images/pushModel.png "push jak działa tryb")

Tryb wypychania odwołuje się do użytkownika aktywnie stosowania konfiguracji do węzła docelowego przez wywołanie metody [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) polecenia cmdlet.

Po utworzeniu i kompilowania konfiguracji, można go wprowadza w trybie wypychania — w tym wywołując [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) polecenia cmdlet, ustawienie parametru - Path, polecenia cmdlet do ścieżki, w którym znajduje się konfiguracji MOF.
Na przykład, jeśli konfiguracja MOF znajduje się pod adresem `C:\DSC\Configurations\localhost.mof`, czy zastosować je na komputerze lokalnym przy użyciu następującego polecenia: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Uwaga__: domyślnie DSC uruchamia konfigurację jako zadanie w tle. Aby pracować w trybie interakcyjnym konfiguracji, należy wywołać [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) z __— oczekiwania__ parametru.

## <a name="pull-mode"></a>Tryb ściągania

![Ściąganie tryb](images/pullModel.png "ściągnięcia jak działa tryb")

W trybie ściągania ściągania klienci są skonfigurowani do pobrania ich konfiguracji żądanego stanu z usługi zdalnego ściągania.
Podobnie usługa ściągania nie został skonfigurowany do usługi hosta DSC i zainicjowano z konfiguracjami i zasobów, które są wymagane przez klientów ściągania.
Każda klientów ściągania ma zaplanowane zdarzenie, który sprawdza zgodność okresowe konfiguracji węzła.
Gdy zdarzenie jest wywoływane po raz pierwszy, lokalnego Menedżera konfiguracji (LCM) na komputerze klienckim ściągania zgłasza żądanie do usługi ściągania można pobrać konfiguracji określone w LCM.
Jeśli istnieje tej konfiguracji w usłudze ściągania i przekazaniem sprawdzanie poprawności początkowej, konfiguracji są pobierane klienta ściągania, gdzie następnie jest wykonywany przez LCM.

LCM sprawdza, czy klient jest zgodność z konfiguracji w regularnych odstępach czasu określonego przez **ConfigurationModeFrequencyMins** właściwości LCM.
LCM wyszukuje zaktualizowanej konfiguracji w usłudze replikacji ściąganej w regularnych odstępach czasu określonego przez **RefreshModeFrequency** właściwości LCM.
Aby uzyskać informacje o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md).

Zalecane rozwiązanie w celu hostowania usługi ściągnięcia jest DSC usługi w chmurze, [usługi Automatyzacja Azure](https://azure.microsoft.com/services/automation/).
Znajduje to rozwiązanie zapewnia zarządzania w trybie graficznym, raportowanie i scentralizowane administrowanie.

Aby uzyskać więcej informacji na temat konfigurowania usługi ściągnięcia w systemie Windows Server, zobacz [ustawienie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md).
Zrozumieć jednak, że ta implementacja ma ograniczone funkcje i wymagają do działania integracji niektórych "to zrobić samodzielnie".

W poniższych tematach opisano ściągania usług i klientów:

- [Przegląd usługi Konfiguracja DSC automatyzacji Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Konfigurowanie serwera ściągania SMB](pullServerSMB.md)
- [Konfigurowanie klienta ściągania](pullClientConfigID.md)