---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="91f99-103">Logika przygotowania zależności modułu podczas operacji publikowania</span><span class="sxs-lookup"><span data-stu-id="91f99-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="91f99-104">Moduły wymienione na liście jako część RequiredModules są traktowane jako zależności.</span><span class="sxs-lookup"><span data-stu-id="91f99-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="91f99-105">Moduły wymienione na liście jako część NestedModules podstawy modułu, którego nie znajduje się w bazie określony moduł, są traktowane jako zależności.</span><span class="sxs-lookup"><span data-stu-id="91f99-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="91f99-106">Powyżej zależności powinny być dostępne na tym samym repozytorium docelowej, w przeciwnym razie publikowanie operacja spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="91f99-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="91f99-107">Na przykład: Jeśli "SnippetPx" nie jest dostępna w repozytorium, poniżej błąd będą zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="91f99-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="91f99-108">Niektóre modułu zależności, które mogą być zarządzane zewnętrznie, w tym przypadku powinien zostać dodany do wpisu ExternalModuleDependencies w sekcji PSData w manifeście modułu.</span><span class="sxs-lookup"><span data-stu-id="91f99-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="91f99-109">Poniżej część w komunikacie o błędzie powyżej</span><span class="sxs-lookup"><span data-stu-id="91f99-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="91f99-110">*Podczas instalacji modułu powyżej przygotowane zależności listy jest używany do instalowania zależności.*</span><span class="sxs-lookup"><span data-stu-id="91f99-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="91f99-111">*Upewnij się, że zależności z modułu są dostępne w obszarze $env: PSModulePath w systemie podczas operacji publikowania.*</span><span class="sxs-lookup"><span data-stu-id="91f99-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>

