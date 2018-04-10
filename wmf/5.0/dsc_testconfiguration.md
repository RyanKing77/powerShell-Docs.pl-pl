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
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="f2a34-102">Polecenia cmdlet test-DscConfiguration obsługuje konfiguracje odwołania</span><span class="sxs-lookup"><span data-stu-id="f2a34-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="f2a34-103">Polecenia cmdlet Test-DscConfiguration została zaktualizowana umożliwia testowanie konfiguracji żądanego stanu co najmniej jeden węzeł docelowy, określając dokumentu konfiguracji odwołania do porównania.</span><span class="sxs-lookup"><span data-stu-id="f2a34-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="f2a34-104">Następujące nowe zestawy parametrów w określonej się tylko testy przy użyciu konfiguracji DSC a nigdy nie stosuj każdej konfiguracji na węzłów określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f2a34-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="f2a34-105">Podobnie jak w przypadku rozpoczęcia DscConfiguration i innych poleceń cmdlet DSC nazwę każdego MOF służy ustalenie, który węzeł docelowy do testowania konfiguracji na.</span><span class="sxs-lookup"><span data-stu-id="f2a34-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="f2a34-106">Następujące zestawy nowy parametr użyj jednej konfiguracji DSC tylko testowe i nigdy nie stosuj konfiguracji na węzłów określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f2a34-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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