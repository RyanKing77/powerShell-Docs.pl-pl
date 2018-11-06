---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998524"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="01d72-102">Słowo kluczowe Import-DscResource obsługuje parametr - ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="01d72-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="01d72-103">Dodano nowy parametr w celu `Import-DscResource` dynamiczne słowo kluczowe, które są dostępne w przypadku tworzenia konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="01d72-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="01d72-104">Autorzy konfiguracji można teraz wprowadzić dokładnie wersji modułu można załadować zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="01d72-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="01d72-105">Składnia nowe słowo kluczowe jest:</span><span class="sxs-lookup"><span data-stu-id="01d72-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="01d72-106">**Nazwa**: nazwy co najmniej jeden zasób do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="01d72-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="01d72-107">**ModuleName**: nazwy modułów lub obiekty ModuleSpecification przynajmniej jeden moduł do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="01d72-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="01d72-108">**ModuleVersion**: wersję modułu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="01d72-108">**ModuleVersion**: Version of module to import.</span></span> <span data-ttu-id="01d72-109">Jeśli używane, ModuleName musi reprezentować tylko jeden moduł według nazwy.</span><span class="sxs-lookup"><span data-stu-id="01d72-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="01d72-110">W środowisku Windows PowerShell ISE zostanie ona wyświetlona za pomocą funkcji IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="01d72-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="01d72-111">**Uwaga**: `–ModuleVersion` parametru należy używać tylko w połączeniu z `–ModuleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="01d72-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="01d72-112">Nie można używać z nazwami zasobów przy użyciu tylko `–Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="01d72-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="01d72-113">Wcześniej jedynym sposobem, aby określić wersję modułu, podczas ładowania zasobów DSC zostało za pomocą obiektu specyfikacji modułu, np.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="01d72-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
