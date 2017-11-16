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
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a>Logika przygotowania zależności modułu podczas operacji publikowania
1.  Moduły wymienione na liście jako część RequiredModules są traktowane jako zależności.
2.  Moduły wymienione na liście jako część NestedModules podstawy modułu, którego nie znajduje się w bazie określony moduł, są traktowane jako zależności.

3.  Powyżej zależności powinny być dostępne na tym samym repozytorium docelowej, w przeciwnym razie publikowanie operacja spowoduje błąd.
    Na przykład: Jeśli "SnippetPx" nie jest dostępna w repozytorium, poniżej błąd będą zgłaszane.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Niektóre modułu zależności, które mogą być zarządzane zewnętrznie, w tym przypadku powinien zostać dodany do wpisu ExternalModuleDependencies w sekcji PSData w manifeście modułu.
    Poniżej część w komunikacie o błędzie powyżej
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Podczas instalacji modułu powyżej przygotowane zależności listy jest używany do instalowania zależności.*

*Upewnij się, że zależności z modułu są dostępne w obszarze $env: PSModulePath w systemie podczas operacji publikowania.*

