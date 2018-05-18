---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="ff779-102">Nie trzeba być wielokrotnością liczby wzajemnie częstotliwości RefreshMode i ConfigurationMode</span><span class="sxs-lookup"><span data-stu-id="ff779-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="ff779-103">W poprzedniej wersji usługi Konfiguracja DSC, czy traktować LCM `RefreshFrequencyMins` i `ConfigurationModeFrequencyMins` jako wielokrotności od siebie.</span><span class="sxs-lookup"><span data-stu-id="ff779-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="ff779-104">W WMF 5.0 RTM te właściwości są przetwarzane od siebie niezależne.</span><span class="sxs-lookup"><span data-stu-id="ff779-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="ff779-105">Aby uzyskać więcej informacji, zobacz [Konfigurowanie lokalny program Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="ff779-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
