---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Polecenia cmdlet test-DscConfiguration obsługuje konfiguracje odwołania

Polecenia cmdlet Test-DscConfiguration została zaktualizowana umożliwia testowanie konfiguracji żądanego stanu co najmniej jeden węzeł docelowy, określając dokumentu konfiguracji odwołania do porównania.

Następujące nowe zestawy parametrów w określonej się tylko testy przy użyciu konfiguracji DSC a nigdy nie stosuj każdej konfiguracji na węzłów określonego obiektu docelowego. Podobnie jak w przypadku rozpoczęcia DscConfiguration i innych poleceń cmdlet DSC nazwę każdego MOF służy ustalenie, który węzeł docelowy do testowania konfiguracji na.

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

Następujące zestawy nowy parametr użyj jednej konfiguracji DSC tylko testowe i nigdy nie stosuj konfiguracji na węzłów określonego obiektu docelowego.

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```
