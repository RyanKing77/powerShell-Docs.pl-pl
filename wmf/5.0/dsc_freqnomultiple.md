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
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="9450f-102">Częstotliwości trybów RefreshMode i ConfigurationMode nie muszą być wielokrotnością liczby siebie</span><span class="sxs-lookup"><span data-stu-id="9450f-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="9450f-103">W poprzedniej wersji DSC, czy traktować LCM `RefreshFrequencyMins` i `ConfigurationModeFrequencyMins` jako wielokrotności siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="9450f-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="9450f-104">W programu WMF 5.0 RTM te właściwości są przetwarzane od siebie niezależne.</span><span class="sxs-lookup"><span data-stu-id="9450f-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="9450f-105">Aby uzyskać więcej informacji, zobacz [Konfigurowanie programu Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="9450f-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
