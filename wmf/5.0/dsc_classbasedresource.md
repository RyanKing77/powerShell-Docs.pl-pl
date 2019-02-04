---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685753"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="009d1-102">Zasoby DSC oparte na klasach</span><span class="sxs-lookup"><span data-stu-id="009d1-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="009d1-103">Definiowanie zasobów DSC przy użyciu klasy</span><span class="sxs-lookup"><span data-stu-id="009d1-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="009d1-104">Na podstawie opinii, które wprowadziliśmy tworzenia zasoby DSC oparte na klasie prostsze i łatwiejsze do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="009d1-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="009d1-105">Główne różnice między zasób DSC oparte na klasach i dostawcy zasobów DSC polecenia cmdlet są:</span><span class="sxs-lookup"><span data-stu-id="009d1-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="009d1-106">Plik MOF dla schematu nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="009d1-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="009d1-107">A **DSCResource** podfolderu w folderze modułu nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="009d1-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="009d1-108">Plik modułu programu PowerShell może zawierać wielu klas zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="009d1-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="009d1-109">Aby uzyskać więcej informacji, zobacz [pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="009d1-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
