---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Omówienie stanu konfiguracji żądanego programu Windows PowerShell
ms.openlocfilehash: 3f357ea11a388a05b73539a63e52e639ee906f68
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Omówienie stanu konfiguracji żądanego programu Windows PowerShell

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

DSC jest platformy do zarządzania w programie PowerShell, który umożliwia zarządzanie dział IT i Projektowanie infrastruktury z konfiguracją w kodzie.

- Omówienie korzyści biznesowe przy użyciu usługi Konfiguracja DSC, zobacz [żądany przegląd stanu konfiguracji dla inne osoby podejmujące decyzje](decisionMaker.md).
- Omówienie engineering korzyści wynikające ze stosowania DSC, zobacz [żądany przegląd stanu konfiguracji dla inżynierów](DscForEngineers.md).
- Aby rozpocząć korzystanie z usługi Konfiguracja DSC szybkie, zobacz [szybki start DSC](quickStart.md).

## <a name="key-concepts"></a>Podstawowe pojęcia

DSC to platforma deklaratywne używany do konfiguracji, wdrażania i zarządzania systemów. Zawiera trzy główne składniki:

- [Konfiguracje](configurations.md) są deklaratywne skryptów programu PowerShell, które zdefiniować i skonfigurować wystąpień zasobów.
    Podczas uruchamiania konfiguracji (DSC i zasobów, wywoływana przez konfigurację) będzie po prostu "był to", sprawdzanie, czy system istnieje w stanie, którego układ określa się w konfiguracji.
    Konfiguracji DSC są również idempotentności: lokalnego Menedżera konfiguracji (LCM) będą w dalszym ciągu upewnij się, czy maszyny są skonfigurowane w stanie niezależnie od konfiguracji deklaruje.
- [Zasoby](resources.md) są częścią "był to" DSC. Zawierają one kod umieścić i przechowywać element docelowy w konfiguracji w określonym stanie.
    Zasoby znajdują się w modułach programu PowerShell i mogą być zapisywane na model coś jako ogólnego jako pliku lub procesu systemu Windows lub jako określone jako serwer usług IIS lub maszynie Wirtualnej działają na platformie Azure.
- [Lokalnego Configuration Manager (LCM)](metaConfig.md) jest aparatem, przez którą DSC ułatwia interakcji między zasobami i konfiguracji.
    LCM sonduje regularnie systemu przy użyciu przepływu sterowania zaimplementowana przez zasoby do zapewni, że stan zdefiniowane przez konfigurację.
    W przypadku systemu ze stanu, LCM wykonywania wywołań do kodu w zasobach umożliwia "tak" zgodnie z konfiguracją.

## <a name="see-also"></a>Zobacz też

- [Konfiguracji DSC](configurations.md)
- [Zasoby usługi Konfiguracja DSC](resources.md)
- [Konfigurowanie lokalny program Configuration Manager](metaConfig.md)