---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Nie trzeba być wielokrotnością liczby wzajemnie częstotliwości RefreshMode i ConfigurationMode

W poprzedniej wersji usługi Konfiguracja DSC, czy traktować LCM `RefreshFrequencyMins` i `ConfigurationModeFrequencyMins` jako wielokrotności od siebie. W WMF 5.0 RTM te właściwości są przetwarzane od siebie niezależne.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie lokalny program Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).