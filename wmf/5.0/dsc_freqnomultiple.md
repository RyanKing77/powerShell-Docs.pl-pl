---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Nie trzeba być wielokrotnością liczby wzajemnie częstotliwości RefreshMode i ConfigurationMode

W poprzedniej wersji usługi Konfiguracja DSC, czy traktować LCM `RefreshFrequencyMins` i `ConfigurationModeFrequencyMins` jako wielokrotności od siebie. W WMF 5.0 RTM te właściwości są przetwarzane od siebie niezależne.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie lokalny program Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).
