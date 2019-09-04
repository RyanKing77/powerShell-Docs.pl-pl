---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria, PowerShell, psgallery
title: Ręczne pobieranie pakietów
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215460"
---
# <a name="manual-package-download"></a><span data-ttu-id="9fa61-103">Ręczne pobieranie pakietów</span><span class="sxs-lookup"><span data-stu-id="9fa61-103">Manual Package Download</span></span>

<span data-ttu-id="9fa61-104">Galeria programu PowerShell obsługuje pobieranie pakietu z witryny sieci Web bezpośrednio, bez korzystania z poleceń cmdlet PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="9fa61-104">The PowerShell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="9fa61-105">Możesz pobrać dowolny pakiet jako plik pakietu NuGet (`.nupkg`), który można następnie skopiować do wewnętrznego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9fa61-105">You can download any package as a NuGet package (`.nupkg`) file, which you can then copy to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="9fa61-106">Ręczne pobieranie pakietu **nie** jest przeznaczone jako zamiennik dla tego `Install-Module` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9fa61-106">Manual package download is **not** intended as a replacement for the `Install-Module` cmdlet.</span></span>
> <span data-ttu-id="9fa61-107">Pobranie pakietu nie powoduje instalacji modułu lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="9fa61-107">Downloading the package doesn't install the module or script.</span></span> <span data-ttu-id="9fa61-108">Zależności nie są uwzględniane w pobranym pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="9fa61-108">Dependencies aren't included in the NuGet package downloaded.</span></span> <span data-ttu-id="9fa61-109">Poniższe instrukcje są dostępne wyłącznie w celach informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="9fa61-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="9fa61-110">Pobieranie pakietu przy użyciu funkcji ręcznego pobierania</span><span class="sxs-lookup"><span data-stu-id="9fa61-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="9fa61-111">Każda Strona zawiera link do pobierania ręcznego, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="9fa61-111">Each page has a link for Manual Download, as shown here:</span></span>

![Pobieranie ręczne](../../Images/packagedisplaypagewithpseditions.png)

<span data-ttu-id="9fa61-113">Aby pobrać ręcznie, kliknij pozycję **Pobierz Nieprzetworzony plik NUPKG**.</span><span class="sxs-lookup"><span data-stu-id="9fa61-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="9fa61-114">Kopia pakietu jest kopiowana do folderu pobierania dla przeglądarki o nazwie `<name>.<version>.nupkg`.</span><span class="sxs-lookup"><span data-stu-id="9fa61-114">A copy of the package is copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="9fa61-115">Pakiet NuGet to archiwum ZIP z dodatkowymi plikami zawierającymi informacje o zawartości pakietu.</span><span class="sxs-lookup"><span data-stu-id="9fa61-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="9fa61-116">Niektóre przeglądarki, takie jak Internet Explorer, automatycznie zamieniają `.nupkg` rozszerzenie pliku na. `.zip`</span><span class="sxs-lookup"><span data-stu-id="9fa61-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="9fa61-117">Aby rozwinąć pakiet, w razie potrzeby `.nupkg` Zmień nazwę `.zip`pliku na, a następnie wyodrębnij zawartość do folderu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="9fa61-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="9fa61-118">Plik pakietu NuGet zawiera następujące **elementy specyficzne dla programu NuGet** , które nie są częścią oryginalnego spakowanego kodu:</span><span class="sxs-lookup"><span data-stu-id="9fa61-118">A NuGet package file includes the following **NuGet-specific elements** that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="9fa61-119">Folder o nazwie `_rels` - `.rels` zawiera plik, w którym znajdują się zależności</span><span class="sxs-lookup"><span data-stu-id="9fa61-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="9fa61-120">Folder o nazwie `package` -zawiera dane specyficzne dla narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="9fa61-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="9fa61-121">Plik o nazwie `[Content_Types].xml` -opisuje, jak rozszerzenia, takie jak PowerShellGet, współpracują z pakietem NuGet</span><span class="sxs-lookup"><span data-stu-id="9fa61-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="9fa61-122">Plik o nazwie `<name>.nuspec` -zawiera zbiorcze metadane</span><span class="sxs-lookup"><span data-stu-id="9fa61-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="9fa61-123">Instalowanie modułów programu PowerShell z pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="9fa61-123">Installing PowerShell modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="9fa61-124">Te instrukcje **nie** dają tego samego wyniku jako uruchomiony `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="9fa61-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="9fa61-125">Te instrukcje spełniają minimalne wymagania.</span><span class="sxs-lookup"><span data-stu-id="9fa61-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="9fa61-126">Nie są one przeznaczone do zamiany na `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="9fa61-126">They aren't intended to be a replacement for `Install-Module`.</span></span>
> <span data-ttu-id="9fa61-127">Niektóre kroki wykonywane przez `Install-Module` nie są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="9fa61-127">Some steps performed by `Install-Module` aren't included.</span></span>

<span data-ttu-id="9fa61-128">Najprostszym rozwiązaniem jest usunięcie elementów specyficznych dla programu NuGet z folderu.</span><span class="sxs-lookup"><span data-stu-id="9fa61-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="9fa61-129">Usunięcie elementów pozostawia kod programu PowerShell utworzony przez autora pakietu.</span><span class="sxs-lookup"><span data-stu-id="9fa61-129">Removing the elements leaves the PowerShell code created by the package author.</span></span>
<span data-ttu-id="9fa61-130">Aby uzyskać listę elementów specyficznych dla narzędzia NuGet, zobacz [Pobieranie pakietu przy użyciu funkcji ręcznego pobierania](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="9fa61-130">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

<span data-ttu-id="9fa61-131">Dostępne są następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9fa61-131">The steps are as follows:</span></span>

1. <span data-ttu-id="9fa61-132">Wyodrębnij zawartość pakietu NuGet do folderu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="9fa61-132">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="9fa61-133">Usuń elementy specyficzne dla narzędzia NuGet z folderu.</span><span class="sxs-lookup"><span data-stu-id="9fa61-133">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="9fa61-134">Zmień nazwę folderu.</span><span class="sxs-lookup"><span data-stu-id="9fa61-134">Rename the folder.</span></span> <span data-ttu-id="9fa61-135">Domyślna nazwa folderu jest zwykle `<name>.<version>`.</span><span class="sxs-lookup"><span data-stu-id="9fa61-135">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="9fa61-136">Wersja może obejmować `-prerelease` , czy moduł jest oznaczony jako wersja wstępna.</span><span class="sxs-lookup"><span data-stu-id="9fa61-136">The version can include `-prerelease` if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="9fa61-137">Zmień nazwę folderu na tylko nazwę modułu.</span><span class="sxs-lookup"><span data-stu-id="9fa61-137">Rename the folder to just the module name.</span></span> <span data-ttu-id="9fa61-138">Na przykład `azurerm.storage.5.0.4-preview` zostanie `azurerm.storage`.</span><span class="sxs-lookup"><span data-stu-id="9fa61-138">For example, `azurerm.storage.5.0.4-preview` becomes `azurerm.storage`.</span></span>
4. <span data-ttu-id="9fa61-139">Skopiuj folder do jednego z folderów w `$env:PSModulePath value`.</span><span class="sxs-lookup"><span data-stu-id="9fa61-139">Copy the folder to one of the folders in the `$env:PSModulePath value`.</span></span> <span data-ttu-id="9fa61-140">`$env:PSModulePath`to rozdzielany średnikami zestaw ścieżek, w których program PowerShell powinien szukać modułów.</span><span class="sxs-lookup"><span data-stu-id="9fa61-140">`$env:PSModulePath` is a semicolon-delimited set of paths in which PowerShell should look for modules.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9fa61-141">Pobieranie ręczne nie obejmuje żadnych zależności wymaganych przez moduł.</span><span class="sxs-lookup"><span data-stu-id="9fa61-141">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="9fa61-142">Jeśli pakiet ma zależności, muszą one być zainstalowane w systemie, aby ten moduł działał poprawnie.</span><span class="sxs-lookup"><span data-stu-id="9fa61-142">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="9fa61-143">W Galeria programu PowerShell są wyświetlane wszystkie zależności wymagane przez pakiet.</span><span class="sxs-lookup"><span data-stu-id="9fa61-143">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="9fa61-144">Instalowanie skryptów programu PowerShell z pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="9fa61-144">Installing PowerShell scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="9fa61-145">Te instrukcje **nie** dają tego samego wyniku jako uruchomiony `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="9fa61-145">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="9fa61-146">Te instrukcje spełniają minimalne wymagania.</span><span class="sxs-lookup"><span data-stu-id="9fa61-146">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="9fa61-147">Nie są one przeznaczone do zamiany na `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="9fa61-147">They aren't intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="9fa61-148">Najprostszym podejściem jest wyodrębnienie pakietu NuGet, a następnie użycie skryptu bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="9fa61-148">The easiest approach is to extract the NuGet package, then use the script directly.</span></span>

<span data-ttu-id="9fa61-149">Dostępne są następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9fa61-149">The steps are as follows:</span></span>

1. <span data-ttu-id="9fa61-150">Wyodrębnij zawartość pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="9fa61-150">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="9fa61-151">`.PS1` Plik w folderze może być używany bezpośrednio z tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9fa61-151">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="9fa61-152">Elementy specyficzne dla programu NuGet można usunąć w folderze.</span><span class="sxs-lookup"><span data-stu-id="9fa61-152">You may delete the NuGet-specific elements in the folder.</span></span>

<span data-ttu-id="9fa61-153">Aby uzyskać listę elementów specyficznych dla narzędzia NuGet, zobacz [Pobieranie pakietu przy użyciu funkcji ręcznego pobierania](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="9fa61-153">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9fa61-154">Pobieranie ręczne nie obejmuje żadnych zależności wymaganych przez moduł.</span><span class="sxs-lookup"><span data-stu-id="9fa61-154">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="9fa61-155">Jeśli pakiet ma zależności, muszą one być zainstalowane w systemie, aby ten moduł działał poprawnie.</span><span class="sxs-lookup"><span data-stu-id="9fa61-155">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="9fa61-156">W Galeria programu PowerShell są wyświetlane wszystkie zależności wymagane przez pakiet.</span><span class="sxs-lookup"><span data-stu-id="9fa61-156">The PowerShell Gallery shows all dependencies required by the package.</span></span>
