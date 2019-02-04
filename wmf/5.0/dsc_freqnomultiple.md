---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688203"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Częstotliwości trybów RefreshMode i ConfigurationMode nie muszą być wielokrotnością liczby siebie

W poprzedniej wersji DSC, czy traktować LCM `RefreshFrequencyMins` i `ConfigurationModeFrequencyMins` jako wielokrotności siebie nawzajem. W programu WMF 5.0 RTM te właściwości są przetwarzane od siebie niezależne.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie programu Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).
