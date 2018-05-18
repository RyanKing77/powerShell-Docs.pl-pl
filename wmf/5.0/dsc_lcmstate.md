---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="db519-102">Szczegółowe informacje na temat stanu LCM</span><span class="sxs-lookup"><span data-stu-id="db519-102">Detailed information about LCM state</span></span>

<span data-ttu-id="db519-103">Wprowadzono ulepszenia udostępnia szczegółowe informacje o stanie LCM.</span><span class="sxs-lookup"><span data-stu-id="db519-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="db519-104">LCMState, zwracane przez Get-DscLocalConfigurationManager teraz może zawierać następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="db519-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="db519-105">**W stanie bezczynności**</span><span class="sxs-lookup"><span data-stu-id="db519-105">**Idle**</span></span>
* <span data-ttu-id="db519-106">**Zajęty**</span><span class="sxs-lookup"><span data-stu-id="db519-106">**Busy**</span></span>
* <span data-ttu-id="db519-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="db519-107">**PendingReboot**</span></span>
* <span data-ttu-id="db519-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="db519-108">**PendingConfiguration**</span></span>

<span data-ttu-id="db519-109">Dodano także właściwością LCMStateDetail, zawierający więcej informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="db519-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
