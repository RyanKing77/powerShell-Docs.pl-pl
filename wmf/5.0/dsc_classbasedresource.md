---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058118"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="85318-102">Zasoby DSC oparte na klasach</span><span class="sxs-lookup"><span data-stu-id="85318-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="85318-103">Definiowanie zasobów DSC przy użyciu klasy</span><span class="sxs-lookup"><span data-stu-id="85318-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="85318-104">Na podstawie opinii, które wprowadziliśmy tworzenia zasoby DSC oparte na klasie prostsze i łatwiejsze do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="85318-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="85318-105">Główne różnice między zasób DSC oparte na klasach i dostawcy zasobów DSC polecenia cmdlet są:</span><span class="sxs-lookup"><span data-stu-id="85318-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="85318-106">Plik MOF dla schematu nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="85318-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="85318-107">A **DSCResource** podfolderu w folderze modułu nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="85318-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="85318-108">Plik modułu programu PowerShell może zawierać wielu klas zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="85318-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="85318-109">Aby uzyskać więcej informacji, zobacz [pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="85318-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
