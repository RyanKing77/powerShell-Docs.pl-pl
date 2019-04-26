---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085746"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="a8b96-102">Słowo kluczowe Import-DscResource obsługuje parametr - ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="a8b96-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="a8b96-103">Dodano nowy parametr w celu `Import-DscResource` dynamiczne słowo kluczowe, które są dostępne w przypadku tworzenia konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="a8b96-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="a8b96-104">Autorzy konfiguracji można teraz wprowadzić dokładnie wersji modułu można załadować zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="a8b96-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="a8b96-105">Składnia nowe słowo kluczowe jest:</span><span class="sxs-lookup"><span data-stu-id="a8b96-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="a8b96-106">**Nazwa**: Nazwy co najmniej jeden zasób do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="a8b96-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="a8b96-107">**ModuleName**: Nazwy modułów lub obiektów ModuleSpecification przynajmniej jeden moduł do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="a8b96-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="a8b96-108">**ModuleVersion**: Wersja modułu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="a8b96-108">**ModuleVersion**: Version of module to import.</span></span> <span data-ttu-id="a8b96-109">Jeśli używane, ModuleName musi reprezentować tylko jeden moduł według nazwy.</span><span class="sxs-lookup"><span data-stu-id="a8b96-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="a8b96-110">W środowisku Windows PowerShell ISE zostanie ona wyświetlona za pomocą funkcji IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="a8b96-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="a8b96-111">**Uwaga**: `–ModuleVersion` parametru należy używać tylko w połączeniu z `–ModuleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="a8b96-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="a8b96-112">Nie można używać z nazwami zasobów przy użyciu tylko `–Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="a8b96-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="a8b96-113">Wcześniej jedynym sposobem, aby określić wersję modułu, podczas ładowania zasobów DSC zostało za pomocą obiektu specyfikacji modułu, np.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="a8b96-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
