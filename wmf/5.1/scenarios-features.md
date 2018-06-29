---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Nowe scenariusze i funkcje w wersji 5.1 WMF
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: 50b66cada6943784b8d3c103cebc3c1e3e286a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37090367"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="ac506-103">Nowe scenariusze i funkcje w wersji 5.1 WMF</span><span class="sxs-lookup"><span data-stu-id="ac506-103">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="ac506-104">Uwaga: Te informacje są wstępne i mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="ac506-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="ac506-105">Wersje programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac506-105">PowerShell Editions</span></span>

<span data-ttu-id="ac506-106">Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.</span><span class="sxs-lookup"><span data-stu-id="ac506-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="ac506-107">**Wersja Desktop:** jest oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Podstawowe funkcje serwera i system Windows dla komputerów stacjonarnych.</span><span class="sxs-lookup"><span data-stu-id="ac506-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="ac506-108">**Wersja Core:** jest oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak system Nano Server i Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="ac506-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="ac506-109">**Dowiedz się więcej o korzystaniu z wersji programu PowerShell**</span><span class="sxs-lookup"><span data-stu-id="ac506-109">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="ac506-110">Określić uruchomiona wersja programu PowerShell przy użyciu $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="ac506-110">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="ac506-111">Filtrowanie wyników Get-Module przez CompatiblePSEditions za pomocą parametru PSEdition</span><span class="sxs-lookup"><span data-stu-id="ac506-111">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="ac506-112">Uniemożliwić wykonywanie skryptu, chyba że Uruchom na zgodna wersja środowiska PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac506-112">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="ac506-113">Deklarowanie zgodności modułu do określonej wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac506-113">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a><span data-ttu-id="ac506-114">Polecenia cmdlet katalogu</span><span class="sxs-lookup"><span data-stu-id="ac506-114">Catalog Cmdlets</span></span>

<span data-ttu-id="ac506-115">Dodano dwa nowe polecenia cmdlet w [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) modułu; te Generowanie i zweryfikować pliki w katalogu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ac506-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; these generate and validate Windows catalog files.</span></span>

### <a name="new-filecatalog"></a><span data-ttu-id="ac506-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="ac506-116">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="ac506-117">Nowe FileCatalog tworzy plik katalogu systemu Windows dla zestawu plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="ac506-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="ac506-118">Ten plik katalogu zawiera wartości skrótu dla wszystkich plików w określonych ścieżek.</span><span class="sxs-lookup"><span data-stu-id="ac506-118">This catalog file contains hashes for all files in specified paths.</span></span>
<span data-ttu-id="ac506-119">Użytkownicy można rozpowszechniać zestaw folderów wraz z odpowiedniego pliku wykazu reprezentujący te foldery.</span><span class="sxs-lookup"><span data-stu-id="ac506-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span>
<span data-ttu-id="ac506-120">Informacje te są przydatne w celu zweryfikowania, czy zmiany zostały wprowadzone do folderów od czasu utworzenia katalogu.</span><span class="sxs-lookup"><span data-stu-id="ac506-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="ac506-121">Katalog w wersji 1 i 2 są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ac506-121">Catalog versions 1 and 2 are supported.</span></span>
<span data-ttu-id="ac506-122">W wersji 1 używa algorytmu wyznaczania wartości skrótu SHA1 do utworzenia skróty plików; w wersji 2 używa SHA256.</span><span class="sxs-lookup"><span data-stu-id="ac506-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span>
<span data-ttu-id="ac506-123">2. Wersja katalogu nie jest obsługiwana w *systemu Windows Server 2008 R2* lub *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="ac506-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span>
<span data-ttu-id="ac506-124">Należy użyć w katalogu w wersji 2 *systemu Windows 8*, *systemu Windows Server 2012*i nowszych systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="ac506-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="ac506-125">Spowoduje to utworzenie pliku wykazu.</span><span class="sxs-lookup"><span data-stu-id="ac506-125">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="ac506-126">Aby sprawdzić integralność pliku katalogu (Pester.cat w powyżej przykładzie), podpisz go za pomocą [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ac506-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span></span>

### <a name="test-filecatalog"></a><span data-ttu-id="ac506-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="ac506-127">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="ac506-128">Test FileCatalog weryfikuje katalogu, reprezentujący zestaw folderów.</span><span class="sxs-lookup"><span data-stu-id="ac506-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="ac506-129">To polecenie cmdlet porównuje wszystkie wartości skrótów plików i ich ścieżek względnych znalezione w *katalogu* z tych na *dysku*.</span><span class="sxs-lookup"><span data-stu-id="ac506-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span>
<span data-ttu-id="ac506-130">W przypadku wykrycia niezgodność wartości skrótu pliku i ścieżki zwraca stan jako *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="ac506-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span>
<span data-ttu-id="ac506-131">Użytkownicy mogą pobierać te informacje przy użyciu *— szczegółowe* parametru.</span><span class="sxs-lookup"><span data-stu-id="ac506-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span>
<span data-ttu-id="ac506-132">Wyświetla również podpisywania stan katalogu w *podpisu* właściwości, który jest odpowiednikiem wywołania [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) polecenia cmdlet na plik wykazu.</span><span class="sxs-lookup"><span data-stu-id="ac506-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet on the catalog file.</span></span>
<span data-ttu-id="ac506-133">Użytkownicy mogą też pominąć każdego pliku, podczas sprawdzania poprawności przy użyciu *- FilesToSkip* parametru.</span><span class="sxs-lookup"><span data-stu-id="ac506-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

## <a name="module-analysis-cache"></a><span data-ttu-id="ac506-134">Moduł analizy w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="ac506-134">Module Analysis Cache</span></span>

<span data-ttu-id="ac506-135">Począwszy od wersji 5.1 WMF, programu PowerShell zapewnia kontrolę nad pliku, który jest używany do pamięci podręcznej dane dotyczące modułu, na przykład poleceń, które eksportuje go.</span><span class="sxs-lookup"><span data-stu-id="ac506-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="ac506-136">Domyślnie ta pamięć podręczna jest przechowywane w pliku `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="ac506-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="ac506-137">Pamięć podręczna jest zazwyczaj odczytu przy uruchamianiu podczas wyszukiwania dla polecenia i jest zapisywany jakimś wątku w tle w po zaimportowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="ac506-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="ac506-138">Aby zmienić domyślną lokalizację pamięci podręcznej, ustaw `$env:PSModuleAnalysisCachePath` zmiennej środowiskowej przed uruchomieniem programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac506-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span>
<span data-ttu-id="ac506-139">Zmiany tej zmiennej środowiskowej wpływają tylko procesów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ac506-139">Changes to this environment variable will only affect children processes.</span></span>
<span data-ttu-id="ac506-140">Wartość powinna nazw pełną ścieżkę (takie jak nazwa pliku), programu PowerShell z uprawnieniami do tworzenia i zapisać pliki.</span><span class="sxs-lookup"><span data-stu-id="ac506-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>
<span data-ttu-id="ac506-141">Aby wyłączyć pamięć podręczną plików, ustaw tę wartość nieprawidłową lokalizację, na przykład:</span><span class="sxs-lookup"><span data-stu-id="ac506-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="ac506-142">To ustawia ścieżkę do urządzenia z systemem nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ac506-142">This sets the path to an invalid device.</span></span>
<span data-ttu-id="ac506-143">Jeśli programu PowerShell nie można zapisać do ścieżki, zwracany jest błąd, ale mogą przeglądać raportowania za pomocą śledzenia błędów:</span><span class="sxs-lookup"><span data-stu-id="ac506-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="ac506-144">Podczas zapisywania w pamięci podręcznej, programu PowerShell będzie sprawdzać dla modułów, które już nie istnieje w celu uniknięcia niepotrzebnie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ac506-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="ac506-145">Czasami te testy nie są pożądane, w którym to przypadku należy je wyłączyć, ustawiając:</span><span class="sxs-lookup"><span data-stu-id="ac506-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="ac506-146">Ustawienie tej zmiennej środowiskowej zacznie obowiązywać natychmiast w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="ac506-146">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="ac506-147">Określanie wersji modułu</span><span class="sxs-lookup"><span data-stu-id="ac506-147">Specifying module version</span></span>

<span data-ttu-id="ac506-148">W wersji 5.1 WMF `using module` działa tak samo jak inne konstrukcje związanych z modułu w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac506-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="ac506-149">Wcześniej trzeba było ma sposobu na określenie wersji danego modułu; Jeśli istnieje wiele wersji, to spowodowało wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="ac506-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="ac506-150">W WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="ac506-150">In WMF 5.1:</span></span>

- <span data-ttu-id="ac506-151">Można użyć [ModuleSpecification — Konstruktor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="ac506-151">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="ac506-152">Ta tabela skrótów ma tego samego formatu co `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="ac506-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="ac506-153">**Przykład:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="ac506-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="ac506-154">W przypadku wielu wersji modułu PowerShell korzysta z **samej logiki rozpoznawania** jako `Import-Module` i nie zwraca błąd — jak `Import-Module` i `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="ac506-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="ac506-155">Ulepszenia Pester</span><span class="sxs-lookup"><span data-stu-id="ac506-155">Improvements to Pester</span></span>

<span data-ttu-id="ac506-156">W wersji 5.1 WMF, wersja Pester jest dostarczany z programem PowerShell zaktualizowano z 3.3.5 3.4.0, z uwzględnieniem zatwierdzania https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, która umożliwia lepsze zachowanie dla Pester na serwerze Nano.</span><span class="sxs-lookup"><span data-stu-id="ac506-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="ac506-157">Możesz przejrzeć zmiany w wersji 3.3.5 i 3.4.0 przez sprawdzanie pliku ChangeLog.md na: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="ac506-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>
