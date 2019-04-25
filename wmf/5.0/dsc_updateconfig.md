---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057574"
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="906cf-102">Ściąganie konfiguracji DSC na żądanie</span><span class="sxs-lookup"><span data-stu-id="906cf-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="906cf-103">Nowe polecenie cmdlet Update-DscConfiguration wyzwala ściąganie z serwerów ściągnięcia zdefiniowane w meta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="906cf-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="906cf-104">Zachowanie jest często nazywany "Ściągania teraz".</span><span class="sxs-lookup"><span data-stu-id="906cf-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="906cf-105">Po wyzwoleniu ściągnięcia zachowuje się dokładnie tak samo jak miałoby, kiedy wyzwalane podczas regularnego częstotliwość:</span><span class="sxs-lookup"><span data-stu-id="906cf-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="906cf-106">Sumy kontrolnej dla bieżącej konfiguracji jest porównywany sumy kontrolnej dla konfiguracji na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="906cf-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="906cf-107">Jeśli są one takie same, zostanie pomyślnie zakończona bez stosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="906cf-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="906cf-108">Jeśli są różne, konfiguracja jest obniżona z serwera ściągania i stosowane.</span><span class="sxs-lookup"><span data-stu-id="906cf-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="906cf-109">**Uwaga:** Jeśli RefreshMode konfiguracji Meta = "Push" błąd jest zwracany przez to polecenie cmdlet, dlatego to polecenie cmdlet będzie zawsze nic nie rób gdy węzeł docelowy jest w trybie "Push".</span><span class="sxs-lookup"><span data-stu-id="906cf-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
