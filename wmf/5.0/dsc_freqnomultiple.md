---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058407"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="efff3-102">Częstotliwości trybów RefreshMode i ConfigurationMode nie muszą być wielokrotnością liczby siebie</span><span class="sxs-lookup"><span data-stu-id="efff3-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="efff3-103">W poprzedniej wersji DSC, czy traktować LCM `RefreshFrequencyMins` i `ConfigurationModeFrequencyMins` jako wielokrotności siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="efff3-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="efff3-104">W programu WMF 5.0 RTM te właściwości są przetwarzane od siebie niezależne.</span><span class="sxs-lookup"><span data-stu-id="efff3-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="efff3-105">Aby uzyskać więcej informacji, zobacz [Konfigurowanie programu Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="efff3-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
