---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058747"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Polecenie cmdlet test-DscConfiguration obsługuje konfiguracje referencyjne

Zaktualizowano polecenia cmdlet Test-DscConfiguration umożliwia testowanie konfiguracji żądanego stanu jeden lub więcej węzłów docelowych, określając dokumentu konfiguracji odniesienia, aby porównać.

Następujące nowe zestawy parametrów Użyj konfiguracji DSC w określonej ścieżki do tylko testy i nigdy nie stosuj każdej konfiguracji na węzły określonego obiektu docelowego. Podobnie jak w przypadku rozpoczęcia-DscConfiguration i inne polecenia cmdlet DSC, nazwę każdego pliku MOF umożliwia ustalić, który węzeł docelowy, aby przetestować konfigurację na.

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

Następujące nowe zestawy parametrów użyj jednej konfiguracji DSC, aby tylko przetestować — nigdy nie stosuj konfiguracji na węzły określonego obiektu docelowego.

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
