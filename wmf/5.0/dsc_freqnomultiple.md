---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="e23fe-102">Nie trzeba być wielokrotnością liczby wzajemnie częstotliwości RefreshMode i ConfigurationMode</span><span class="sxs-lookup"><span data-stu-id="e23fe-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="e23fe-103">W poprzedniej wersji usługi Konfiguracja DSC, czy traktować LCM `RefreshFrequencyMins` i `ConfigurationModeFrequencyMins` jako wielokrotności od siebie.</span><span class="sxs-lookup"><span data-stu-id="e23fe-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="e23fe-104">W WMF 5.0 RTM te właściwości są przetwarzane od siebie niezależne.</span><span class="sxs-lookup"><span data-stu-id="e23fe-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span> 

<span data-ttu-id="e23fe-105">Aby uzyskać więcej informacji, zobacz [Konfigurowanie lokalny program Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="e23fe-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>

