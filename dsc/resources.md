---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasoby usługi Konfiguracja DSC
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a>Zasoby usługi Konfiguracja DSC

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Żądana Konfiguracja stanu (DSC) zasoby dostarczają bloków konstrukcyjnych dla konfiguracji DSC. Zasób udostępnia właściwości, które mogą być skonfigurowane (schemat) i zawiera funkcje skryptu programu PowerShell, które wywołuje lokalnego Menedżera konfiguracji (LCM) umożliwia "tak".

Zasób może modelu coś jako ogólnego jako plik lub jako określone w ustawieniach serwera IIS.  Grupy takich jak zasoby połączone w Module DSC organizuje wszystkie wymagane pliki w strukturze przenośnego i zawierający metadane, aby określić, jak zasoby są przeznaczone do użycia.

DSC zasobów można znaleźć w następujących tematach:

- [Wbudowane zasobów DSC](builtInResource.md)
- [Tworzenie niestandardowych zasobów DSC](authoringResource.md)
- [Wbudowane DSC zasobów dla systemu Linux](lnxBuiltInResources.md)