---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ce5afc2f90f78433b64bf5b41946fc7506c43504
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="dfb15-102">Parametr - ModuleVersion obsługuje importu DscResource — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="dfb15-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="dfb15-103">Dodano nowy parametr `Import-DscResource` dynamiczne słowo kluczowe, które są dostępne podczas tworzenia konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="dfb15-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="dfb15-104">Autorzy konfiguracji można teraz określić dokładnie wersji modułu ładowania zasobów DSC z.</span><span class="sxs-lookup"><span data-stu-id="dfb15-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="dfb15-105">Nowej składni słowa kluczowego jest:</span><span class="sxs-lookup"><span data-stu-id="dfb15-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="dfb15-106">**Nazwa**: nazwy co najmniej jeden zasób do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="dfb15-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="dfb15-107">**Nazwa modułu**: nazwy modułu lub obiektów ModuleSpecification co najmniej jednego modułu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="dfb15-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="dfb15-108">**ModuleVersion**: wersja modułu ot importu.</span><span class="sxs-lookup"><span data-stu-id="dfb15-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="dfb15-109">Jeśli używana, nazwa modułu musi reprezentować tylko jeden moduł według nazwy.</span><span class="sxs-lookup"><span data-stu-id="dfb15-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="dfb15-110">W środowisku Windows PowerShell ISE jest wyświetlane z IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="dfb15-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="dfb15-111">**Uwaga**: `–ModuleVersion` parametru można używać tylko w połączeniu z `–ModuleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="dfb15-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="dfb15-112">Nie można użyć nazwy zasobu tylko przy użyciu `–Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="dfb15-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="dfb15-113">Przed, jedynym sposobem określania wersji modułu podczas ładowania zasobów DSC była za pomocą obiektu specyfikacji modułu, np.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="dfb15-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
