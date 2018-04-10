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
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="7a959-102">Nie trzeba być wielokrotnością liczby wzajemnie częstotliwości RefreshMode i ConfigurationMode</span><span class="sxs-lookup"><span data-stu-id="7a959-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="7a959-103">W poprzedniej wersji usługi Konfiguracja DSC, czy traktować LCM `RefreshFrequencyMins` i `ConfigurationModeFrequencyMins` jako wielokrotności od siebie.</span><span class="sxs-lookup"><span data-stu-id="7a959-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="7a959-104">W WMF 5.0 RTM te właściwości są przetwarzane od siebie niezależne.</span><span class="sxs-lookup"><span data-stu-id="7a959-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="7a959-105">Aby uzyskać więcej informacji, zobacz [Konfigurowanie lokalny program Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="7a959-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>