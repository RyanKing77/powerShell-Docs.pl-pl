---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Klasa MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09b30edd48384c0e8412e0e6ee926a719249c5b8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726887"
---
# <a name="msftdsclocalconfigurationmanager-class"></a>Klasa MSFT_DSCLocalConfigurationManager

Lokalne konfiguracji Manager (LCM) określa stany pliki konfiguracji, która korzysta z konfiguracji agenta w celu zastosowania konfiguracji.

Następująca składnia jest uproszczony w kodzie Managed Object Format (MOF) i obejmuje wszystkie właściwości dziedziczonych.

## <a name="syntax"></a>Składnia

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Elementy członkowskie

**MSFT_DSCLocalConfigurationManager** klasy ma następujące składowe:

- [Metody] []

### <a name="methods"></a>Metody

**MSFT_DSCLocalConfigurationManager** klasa ma tych metod.

|Metoda |Opis |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Używa agenta konfiguracji, aby zastosować konfigurację, która jest w stanie oczekiwania.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Wyłącza debugowanie zasobów DSC.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Włącza debugowanie zasobów DSC.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Wysyła dokument konfiguracji do zarządzanego węzła i używa **uzyskać** metoda przez agenta konfiguracji, aby zastosować konfigurację.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Pobiera dane wyjściowe agenta konfiguracji odnoszące się do określonego zadania.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Pobieranie historii stanu konfiguracji.|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Pobiera ustawienia LCM, które są używane do kontrolowania konfiguracji agenta.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Uruchamia kontrolę spójności.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Usuwa pliki konfiguracji.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Bezpośrednio wywołuje **uzyskać** metod zasobów DSC.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Bezpośrednio wywołuje **ustaw** metod zasobów DSC.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Bezpośrednio wywołuje **testu** metod zasobów DSC.|
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| Ustala powrót do poprzedniej konfiguracji.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Wysyła dokument konfiguracji w węźle zarządzanym i zapisuje go jako oczekujące zmiany.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Wysyła dokument konfiguracji do zarządzanego węzła i używa agenta konfiguracji, aby zastosować konfigurację.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Wysłany do zarządzanych węzłów konfiguracji i rozpocząć korzystanie przez agenta konfiguracji, aby zastosować konfigurację. Użyj GetConfigurationResultOutput do pobrania danych wyjściowych wyników.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Ustawia ustawienia LCM, które są używane do kontrolowania przez agenta konfiguracji.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Zatrzymuje konfiguracji, który jest w toku.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Wysyła dokument konfiguracji w węźle zarządzanym i sprawdza bieżącą konfigurację dla dokumentu.|

## <a name="requirements"></a>Wymagania

**PLIK MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration
