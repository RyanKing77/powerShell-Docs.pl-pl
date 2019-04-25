---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057931"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="5eac2-102">Obsługa wersji modułu Side-By-Side dla zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="5eac2-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="5eac2-103">Moduły zawierające zasoby DSC może być instalowany side-by-side i konfiguracjach DSC można użyć określonej wersji zasobu, który jest zainstalowany w systemie.</span><span class="sxs-lookup"><span data-stu-id="5eac2-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="5eac2-104">Aby uzyskać więcej informacji, zobacz [korzystanie z zasobów z wieloma wersjami](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="5eac2-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="5eac2-105">Znane problemy</span><span class="sxs-lookup"><span data-stu-id="5eac2-105">Known issues</span></span>

<span data-ttu-id="5eac2-106">W tej wersji następujące znane problemy side-by-side instalacji:</span><span class="sxs-lookup"><span data-stu-id="5eac2-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="5eac2-107">Używających dwóch różnych wersji zasobów DSC w ramach tej samej konfiguracji nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="5eac2-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
