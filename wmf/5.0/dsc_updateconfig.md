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
# <a name="on-demand-pull-of-dsc-configurations"></a>Ściąganie konfiguracji DSC na żądanie

Nowe polecenie cmdlet Update-DscConfiguration wyzwala ściąganie z serwerów ściągnięcia zdefiniowane w meta konfiguracji. Zachowanie jest często nazywany "Ściągania teraz".


Po wyzwoleniu ściągnięcia zachowuje się dokładnie tak samo jak miałoby, kiedy wyzwalane podczas regularnego częstotliwość:

1. Sumy kontrolnej dla bieżącej konfiguracji jest porównywany sumy kontrolnej dla konfiguracji na serwerze ściągania.
2. Jeśli są one takie same, zostanie pomyślnie zakończona bez stosowania konfiguracji.
3. Jeśli są różne, konfiguracja jest obniżona z serwera ściągania i stosowane.

**Uwaga:** Jeśli RefreshMode konfiguracji Meta = "Push" błąd jest zwracany przez to polecenie cmdlet, dlatego to polecenie cmdlet będzie zawsze nic nie rób gdy węzeł docelowy jest w trybie "Push".

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
