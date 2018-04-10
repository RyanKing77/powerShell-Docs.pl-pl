---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: psget_moduledependencypopulation
ms.openlocfilehash: c4c9f203e9c526ff532c2388acb6334515d66934
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="dc889-103">Logika przygotowania zależności modułu podczas operacji publikowania</span><span class="sxs-lookup"><span data-stu-id="dc889-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="dc889-104">Moduły wymienione na liście jako część RequiredModules są traktowane jako zależności.</span><span class="sxs-lookup"><span data-stu-id="dc889-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="dc889-105">Moduły wymienione na liście jako część NestedModules podstawy modułu, którego nie znajduje się w bazie określony moduł, są traktowane jako zależności.</span><span class="sxs-lookup"><span data-stu-id="dc889-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="dc889-106">Powyżej zależności powinny być dostępne na tym samym repozytorium docelowej, w przeciwnym razie publikowanie operacja spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="dc889-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="dc889-107">Na przykład: Jeśli "SnippetPx" nie jest dostępna w repozytorium, poniżej błąd będą zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="dc889-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="dc889-108">Niektóre modułu zależności, które mogą być zarządzane zewnętrznie, w tym przypadku powinien zostać dodany do wpisu ExternalModuleDependencies w sekcji PSData w manifeście modułu.</span><span class="sxs-lookup"><span data-stu-id="dc889-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="dc889-109">Poniżej część w komunikacie o błędzie powyżej</span><span class="sxs-lookup"><span data-stu-id="dc889-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="dc889-110">*Podczas instalacji modułu powyżej przygotowane zależności listy jest używany do instalowania zależności.*</span><span class="sxs-lookup"><span data-stu-id="dc889-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="dc889-111">*Upewnij się, że zależności z modułu są dostępne w obszarze $env: PSModulePath w systemie podczas operacji publikowania.*</span><span class="sxs-lookup"><span data-stu-id="dc889-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>