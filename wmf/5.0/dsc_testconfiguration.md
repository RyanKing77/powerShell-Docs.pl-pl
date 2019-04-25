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
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="5f8e1-102">Polecenie cmdlet test-DscConfiguration obsługuje konfiguracje referencyjne</span><span class="sxs-lookup"><span data-stu-id="5f8e1-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="5f8e1-103">Zaktualizowano polecenia cmdlet Test-DscConfiguration umożliwia testowanie konfiguracji żądanego stanu jeden lub więcej węzłów docelowych, określając dokumentu konfiguracji odniesienia, aby porównać.</span><span class="sxs-lookup"><span data-stu-id="5f8e1-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="5f8e1-104">Następujące nowe zestawy parametrów Użyj konfiguracji DSC w określonej ścieżki do tylko testy i nigdy nie stosuj każdej konfiguracji na węzły określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="5f8e1-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="5f8e1-105">Podobnie jak w przypadku rozpoczęcia-DscConfiguration i inne polecenia cmdlet DSC, nazwę każdego pliku MOF umożliwia ustalić, który węzeł docelowy, aby przetestować konfigurację na.</span><span class="sxs-lookup"><span data-stu-id="5f8e1-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="5f8e1-106">Następujące nowe zestawy parametrów użyj jednej konfiguracji DSC, aby tylko przetestować — nigdy nie stosuj konfiguracji na węzły określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="5f8e1-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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
