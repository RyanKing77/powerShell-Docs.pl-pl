---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 27f8fab6a72e7f3a3f510f5a9e503bbfb8a8f618
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="5d923-102">Ściąganie konfiguracji DSC na żądanie</span><span class="sxs-lookup"><span data-stu-id="5d923-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="5d923-103">Nowe polecenie cmdlet Update-DscConfiguration wyzwala ściągnięcia z serwerów ściągania zdefiniowane w meta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5d923-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="5d923-104">Zachowanie jest często określany jako "Pull teraz".</span><span class="sxs-lookup"><span data-stu-id="5d923-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="5d923-105">Po wyzwoleniu ściągania zachowuje się tak samo jak miałoby, kiedy wyzwalane podczas regularnego częstotliwość:</span><span class="sxs-lookup"><span data-stu-id="5d923-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="5d923-106">Sumy kontrolnej dla bieżącej konfiguracji jest porównywany sumy kontrolnej dla konfiguracji na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="5d923-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="5d923-107">Jeśli są one takie same, pomyślnie zakończy działanie bez stosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5d923-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="5d923-108">Jeśli są różne, konfiguracja jest obniżona z serwera ściągania i stosowane.</span><span class="sxs-lookup"><span data-stu-id="5d923-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="5d923-109">**Uwaga:** Jeśli RefreshMode konfiguracji Meta = "Push" błąd jest zwracany przez to polecenie cmdlet, dlatego to polecenie cmdlet będzie zawsze nic nie rób gdy węzeł docelowy jest w trybie "Push".</span><span class="sxs-lookup"><span data-stu-id="5d923-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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