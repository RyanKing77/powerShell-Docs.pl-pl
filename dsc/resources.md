---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasoby usługi Konfiguracja DSC
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-resources"></a>Zasoby usługi Konfiguracja DSC

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Żądana Konfiguracja stanu (DSC) zasoby dostarczają bloków konstrukcyjnych dla konfiguracji DSC. Zasób udostępnia właściwości, które mogą być skonfigurowane (schemat) i zawiera funkcje skryptu programu PowerShell, które wywołuje lokalnego Menedżera konfiguracji (LCM) umożliwia "tak".

Zasób może modelu coś jako ogólnego jako plik lub jako określone w ustawieniach serwera IIS.  Grupy takich jak zasoby połączone w Module DSC organizuje wszystkie wymagane pliki w strukturze przenośnego i zawierający metadane, aby określić, jak zasoby są przeznaczone do użycia.

DSC zasobów można znaleźć w następujących tematach:

- [Wbudowane zasobów DSC](builtInResource.md)
- [Tworzenie niestandardowych zasobów DSC](authoringResource.md)
- [Wbudowane DSC zasobów dla systemu Linux](lnxBuiltInResources.md)