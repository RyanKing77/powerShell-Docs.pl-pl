---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="627db-102">Szczegółowe informacje na temat stanu LCM</span><span class="sxs-lookup"><span data-stu-id="627db-102">Detailed information about LCM state</span></span>

<span data-ttu-id="627db-103">Wprowadzono ulepszenia udostępnia szczegółowe informacje o stanie LCM.</span><span class="sxs-lookup"><span data-stu-id="627db-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="627db-104">LCMState, zwracane przez Get-DscLocalConfigurationManager teraz może zawierać następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="627db-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="627db-105">**W stanie bezczynności**</span><span class="sxs-lookup"><span data-stu-id="627db-105">**Idle**</span></span>
* <span data-ttu-id="627db-106">**Zajęty**</span><span class="sxs-lookup"><span data-stu-id="627db-106">**Busy**</span></span>
* <span data-ttu-id="627db-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="627db-107">**PendingReboot**</span></span>
* <span data-ttu-id="627db-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="627db-108">**PendingConfiguration**</span></span>

<span data-ttu-id="627db-109">Dodano także właściwością LCMStateDetail, zawierający więcej informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="627db-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

