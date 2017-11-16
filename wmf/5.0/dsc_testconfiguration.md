---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="d7d1c-102">Polecenia cmdlet test-DscConfiguration obsługuje konfiguracje odwołania</span><span class="sxs-lookup"><span data-stu-id="d7d1c-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="d7d1c-103">Polecenia cmdlet Test-DscConfiguration została zaktualizowana umożliwia testowanie konfiguracji żądanego stanu co najmniej jeden węzeł docelowy, określając dokumentu konfiguracji odwołania do porównania.</span><span class="sxs-lookup"><span data-stu-id="d7d1c-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="d7d1c-104">Następujące nowe zestawy parametrów w określonej się tylko testy przy użyciu konfiguracji DSC a nigdy nie stosuj każdej konfiguracji na węzłów określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d7d1c-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="d7d1c-105">Podobnie jak w przypadku rozpoczęcia DscConfiguration i innych poleceń cmdlet DSC nazwę każdego MOF służy ustalenie, który węzeł docelowy do testowania konfiguracji na.</span><span class="sxs-lookup"><span data-stu-id="d7d1c-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span> 

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

<span data-ttu-id="d7d1c-106">Następujące zestawy nowy parametr użyj jednej konfiguracji DSC tylko testowe i nigdy nie stosuj konfiguracji na węzłów określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d7d1c-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span> 

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

