---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="c1281-102">Zasoby oparte na klasie DSC</span><span class="sxs-lookup"><span data-stu-id="c1281-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="c1281-103">Definiowanie konfiguracji DSC zasobów z klasami</span><span class="sxs-lookup"><span data-stu-id="c1281-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="c1281-104">Na podstawie opinii, wprowadziliśmy, Tworzenie klasy zasobów DSC prostsze i łatwiejsze do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="c1281-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="c1281-105">Najważniejsze różnice między zasób DSC klasy i dostawcy zasobów usługi Konfiguracja DSC polecenia cmdlet są:</span><span class="sxs-lookup"><span data-stu-id="c1281-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="c1281-106">Plik MOF do schematu nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="c1281-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="c1281-107">A **DSCResource** podfolderu w folderze modułu nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="c1281-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="c1281-108">Plik modułu programu PowerShell może zawierać wielu klas zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="c1281-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="c1281-109">Aby uzyskać więcej informacji, zobacz [pisania niestandardowego zasobu DSC środowiska PowerShell klasy](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="c1281-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

