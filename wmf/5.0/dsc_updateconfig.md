---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: f2ddde78f436e6f03f521a9a8246dbda93e7a57a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="a3775-102">Na żądanie pobieranie konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="a3775-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="a3775-103">Nowe polecenie cmdlet Update-DscConfiguration wyzwala ściągnięcia z serwerów ściągania zdefiniowane w meta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a3775-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="a3775-104">Zachowanie jest często określany jako "Pull teraz".</span><span class="sxs-lookup"><span data-stu-id="a3775-104">The behavior is often referred to as 'Pull Now'.</span></span> 


<span data-ttu-id="a3775-105">Po wyzwoleniu ściągania zachowuje się tak samo jak miałoby, kiedy wyzwalane podczas regularnego częstotliwość:</span><span class="sxs-lookup"><span data-stu-id="a3775-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="a3775-106">Sumy kontrolnej dla bieżącej konfiguracji jest porównywany sumy kontrolnej dla konfiguracji na serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="a3775-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span> 
2. <span data-ttu-id="a3775-107">Jeśli są one takie same, pomyślnie zakończy działanie bez stosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a3775-107">If they are the same, it completes successfully without applying the configuration.</span></span> 
3. <span data-ttu-id="a3775-108">Jeśli są różne, konfiguracja jest obniżona z serwera ściągania i stosowane.</span><span class="sxs-lookup"><span data-stu-id="a3775-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="a3775-109">**Uwaga:** Jeśli RefreshMode konfiguracji Meta = "Push" błąd jest zwracany przez to polecenie cmdlet, dlatego to polecenie cmdlet będzie zawsze nic nie rób gdy węzeł docelowy jest w trybie "Push".</span><span class="sxs-lookup"><span data-stu-id="a3775-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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

