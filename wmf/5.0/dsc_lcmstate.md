---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085800"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="b42c8-102">Szczegółowe informacje na temat stanu LCM</span><span class="sxs-lookup"><span data-stu-id="b42c8-102">Detailed information about LCM state</span></span>

<span data-ttu-id="b42c8-103">Wprowadziliśmy ulepszenia w szczegółowe informacje na temat stanu LCM udostępnianie.</span><span class="sxs-lookup"><span data-stu-id="b42c8-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="b42c8-104">LCMState, który jest zwracany przez Get-DscLocalConfigurationManager może teraz zawierać następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="b42c8-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="b42c8-105">**Bezczynności (%)**</span><span class="sxs-lookup"><span data-stu-id="b42c8-105">**Idle**</span></span>
* <span data-ttu-id="b42c8-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="b42c8-106">**Busy**</span></span>
* <span data-ttu-id="b42c8-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="b42c8-107">**PendingReboot**</span></span>
* <span data-ttu-id="b42c8-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="b42c8-108">**PendingConfiguration**</span></span>

<span data-ttu-id="b42c8-109">Dodaliśmy również właściwość LCMStateDetail, który zawiera więcej informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="b42c8-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
