---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a>Ściąganie konfiguracji DSC na żądanie

Nowe polecenie cmdlet Update-DscConfiguration wyzwala ściągnięcia z serwerów ściągania zdefiniowane w meta konfiguracji. Zachowanie jest często określany jako "Pull teraz".


Po wyzwoleniu ściągania zachowuje się tak samo jak miałoby, kiedy wyzwalane podczas regularnego częstotliwość:

1. Sumy kontrolnej dla bieżącej konfiguracji jest porównywany sumy kontrolnej dla konfiguracji na serwerze ściągania.
2. Jeśli są one takie same, pomyślnie zakończy działanie bez stosowania konfiguracji.
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
