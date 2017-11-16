---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: b839b476bb4ef7f8d73b158d61f0e8cbc1265e60
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="ce086-102">Parametr - ModuleVersion obsługuje importu DscResource — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="ce086-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="ce086-103">Dodano nowy parametr `Import-DscResource` dynamiczne słowo kluczowe, które są dostępne podczas tworzenia konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="ce086-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="ce086-104">Autorzy konfiguracji można teraz określić dokładnie wersji modułu ładowania zasobów DSC z.</span><span class="sxs-lookup"><span data-stu-id="ce086-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="ce086-105">Nowej składni słowa kluczowego jest:</span><span class="sxs-lookup"><span data-stu-id="ce086-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="ce086-106">**Nazwa**: nazwy co najmniej jeden zasób do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="ce086-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="ce086-107">**Nazwa modułu**: nazwy modułu lub obiektów ModuleSpecification co najmniej jednego modułu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="ce086-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="ce086-108">**ModuleVersion**: wersja modułu ot importu.</span><span class="sxs-lookup"><span data-stu-id="ce086-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="ce086-109">Jeśli używana, nazwa modułu musi reprezentować tylko jeden moduł według nazwy.</span><span class="sxs-lookup"><span data-stu-id="ce086-109">If used, ModuleName must represent only one module by name.</span></span> 

<span data-ttu-id="ce086-110">W środowisku Windows PowerShell ISE jest wyświetlane z IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="ce086-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="ce086-111">**Uwaga**: `–ModuleVersion` parametru można używać tylko w połączeniu z `–ModuleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="ce086-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="ce086-112">Nie można użyć nazwy zasobu tylko przy użyciu `–Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="ce086-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="ce086-113">Przed, jedynym sposobem określania wersji modułu podczas ładowania zasobów DSC była za pomocą obiektu specyfikacji modułu, np.:`–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="ce086-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>

