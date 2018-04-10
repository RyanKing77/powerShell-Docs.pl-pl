---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 18c1dab7412b8e9d31960507b612dd6cc56d31d5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
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