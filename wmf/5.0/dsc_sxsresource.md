---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: a565f2befddc32f5088fa3e158f58d2dd78d41b4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="d0ae8-102">Obsługa wersji modułu Side-By-Side dla zasobów usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="d0ae8-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="d0ae8-103">Moduły zawierającego zasoby DSC mogą być zainstalowane side-by-side i konfiguracji DSC można użyć określonej wersji zasobu, który jest zainstalowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="d0ae8-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="d0ae8-104">Aby uzyskać więcej informacji, zobacz [przy użyciu zasobów z wieloma wersjami](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="d0ae8-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="d0ae8-105">Znane problemy</span><span class="sxs-lookup"><span data-stu-id="d0ae8-105">Known issues</span></span>

<span data-ttu-id="d0ae8-106">W tej wersji poniżej przedstawiono znane problemy side-by-side instalacji:</span><span class="sxs-lookup"><span data-stu-id="d0ae8-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="d0ae8-107">Używanie dwie różne wersje zasobu usługi Konfiguracja DSC w tej samej konfiguracji nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d0ae8-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>