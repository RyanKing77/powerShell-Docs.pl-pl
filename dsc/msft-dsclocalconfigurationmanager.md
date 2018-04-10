---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Klasa MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 598bd7490043975d9d965c12a7337fb3475b3ded
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="msftdsclocalconfigurationmanager-class"></a>Klasa MSFT_DSCLocalConfigurationManager

Lokalnego Configuration Manager (LCM) określa stany pliki konfiguracji, który korzysta z konfiguracji agenta w celu zastosowania konfiguracji.

Następująca składnia jest uproszczone z kodu Managed Object Format (MOF) i zawiera wszystkie właściwości dziedziczone.

## <a name="syntax"></a>Składnia
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Elementy członkowskie
-------

**MSFT_DSCLocalConfigurationManager** klasa ma następujące elementy:

-   [Metody] []

### <a name="methods"></a>Metody

**MSFT_DSCLocalConfigurationManager** klasa ma tych metod.

|Metoda |Opis |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Używa agenta konfiguracji umożliwiają zastosowanie konfiguracji, który jest w stanie oczekiwania.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Wyłącza debugowanie zasobów usługi Konfiguracja DSC.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Włącza debugowanie zasobów usługi Konfiguracja DSC.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Wysyła dokument konfiguracji do węzła zarządzanego i używa **uzyskać** metody Agent konfiguracji, aby zastosować konfigurację.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Pobiera dane wyjściowe Agent konfiguracji odnoszące się do określonego zadania.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Podgląd historii stanu konfiguracji.|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Pobiera ustawienia LCM, które są używane do kontrolowania konfiguracji agenta.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Uruchamia kontrolę spójności.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Usuwa pliki konfiguracji.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Bezpośrednio wywołuje **uzyskać** metody zasobu usługi Konfiguracja DSC.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Bezpośrednio wywołuje **ustawić** metody zasobu usługi Konfiguracja DSC.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Bezpośrednio wywołuje **testu** metody zasobu usługi Konfiguracja DSC.|
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| Przedstawia powrót do poprzedniej konfiguracji.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Wysyła dokument konfiguracji do węzła zarządzanego i zapisuje go jako oczekujące zmiany.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Wysłany do węzła zarządzanego konfiguracji i uruchomić przy użyciu agenta konfiguracji, aby zastosować konfigurację. Użyj GetConfigurationResultOutput, aby pobrać dane wyjściowe wynik.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Konfiguruje ustawienia LCM, które są używane do sterowania agenta konfiguracji.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Zatrzymuje konfigurację, która jest w toku.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Wysyła dokument konfiguracji do węzła zarządzanego i sprawdza bieżącą konfigurację względem dokumentu.|





## <a name="requirements"></a>Wymagania
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration