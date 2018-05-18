---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="218fe-102">Zasoby DSC oparte na klasach</span><span class="sxs-lookup"><span data-stu-id="218fe-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="218fe-103">Definiowanie konfiguracji DSC zasobów z klasami</span><span class="sxs-lookup"><span data-stu-id="218fe-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="218fe-104">Na podstawie opinii, wprowadziliśmy, Tworzenie klasy zasobów DSC prostsze i łatwiejsze do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="218fe-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="218fe-105">Najważniejsze różnice między zasób DSC klasy i dostawcy zasobów usługi Konfiguracja DSC polecenia cmdlet są:</span><span class="sxs-lookup"><span data-stu-id="218fe-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="218fe-106">Plik MOF do schematu nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="218fe-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="218fe-107">A **DSCResource** podfolderu w folderze modułu nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="218fe-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="218fe-108">Plik modułu programu PowerShell może zawierać wielu klas zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="218fe-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="218fe-109">Aby uzyskać więcej informacji, zobacz [pisania niestandardowego zasobu DSC środowiska PowerShell klasy](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="218fe-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
