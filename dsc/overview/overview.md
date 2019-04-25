---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Program Windows PowerShell Desired State Configuration — omówienie
ms.openlocfilehash: 3e4f0afa17ab60bfa98f1b86b9830462a7c8e1cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079975"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Program Windows PowerShell Desired State Configuration — omówienie

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC to platforma zarządzania w programie PowerShell, który pozwala na zarządzanie IT i rozwój infrastruktury za pomocą konfiguracji jako kodu.

- Aby uzyskać ogólne korzyści dla firm za pomocą DSC, zobacz [Przegląd Desired State Configuration dla osób podejmujących](decisionMaker.md).
- Omówienie zalet engineering za pomocą DSC, zobacz [Przegląd Desired State Configuration dla inżynierów](DscForEngineers.md).
- Aby rozpocząć korzystanie z DSC szybko, zobacz [DSC — szybki start](../quickstarts/website-quickstart.md).

## <a name="key-concepts"></a>Kluczowe pojęcia

DSC to platforma deklaracyjne używane do konfiguracji, wdrażania i zarządzania systemami. Składa się z trzech podstawowych składników:

- [Konfiguracje](../configurations/configurations.md) to deklaratywne skrypty programu PowerShell, które zdefiniować i skonfigurować wystąpień zasobów.
    Podczas uruchamiania konfiguracji DSC (i zasoby wywoływane przez tę konfigurację) będą po prostu "Przechowuj je tak", sprawdzanie, czy system istnieje w stanie rozmieszczony w konfiguracji.
    Konfiguracje DSC są również idempotentne: lokalne Configuration Manager (LCM) będzie w dalszym ciągu upewnij się, czy maszyny są skonfigurowane w stanie niezależnie od konfiguracji deklaruje.
- [Zasoby](../resources/resources.md) są częścią "Przechowuj je więc" DSC. Zawierają one kod, który umieścić i utrzymania docelowej konfiguracji w określonym stanie.
    Zasoby znajdują się w modułach programu PowerShell i mogą być zapisywane do modelowania wystąpił ogólny jako plik lub proces Windows lub tak dokładnie, jak serwer usług IIS lub maszyny Wirtualnej działającej na platformie Azure.
- [Lokalnego Configuration Manager (LCM)](../managing-nodes/metaConfig.md) to aparat za pomocą którego ułatwia tworzenie interakcji między zasobami i konfiguracje DSC.
    LCM sonduje regularnie systemu, zapewni, że stan zdefiniowane przez konfigurację przy użyciu przepływu sterowania implementowany przez zasoby.
    W przypadku systemu ze stanu LCM wykonywania wywołań do kodu w zasobach być "tak" zgodnie z konfiguracją.

## <a name="see-also"></a>Zobacz też

- [Konfiguracje DSC](../configurations/configurations.md)
- [Zasoby DSC](../resources/resources.md)
- [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md)
