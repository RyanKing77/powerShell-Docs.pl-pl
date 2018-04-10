---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="e8930-102">Zasoby DSC oparte na klasach</span><span class="sxs-lookup"><span data-stu-id="e8930-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="e8930-103">Definiowanie konfiguracji DSC zasobów z klasami</span><span class="sxs-lookup"><span data-stu-id="e8930-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="e8930-104">Na podstawie opinii, wprowadziliśmy, Tworzenie klasy zasobów DSC prostsze i łatwiejsze do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="e8930-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="e8930-105">Najważniejsze różnice między zasób DSC klasy i dostawcy zasobów usługi Konfiguracja DSC polecenia cmdlet są:</span><span class="sxs-lookup"><span data-stu-id="e8930-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="e8930-106">Plik MOF do schematu nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="e8930-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="e8930-107">A **DSCResource** podfolderu w folderze modułu nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="e8930-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="e8930-108">Plik modułu programu PowerShell może zawierać wielu klas zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="e8930-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="e8930-109">Aby uzyskać więcej informacji, zobacz [pisania niestandardowego zasobu DSC środowiska PowerShell klasy](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="e8930-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>