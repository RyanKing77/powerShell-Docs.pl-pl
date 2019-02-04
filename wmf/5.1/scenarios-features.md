---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Nowych scenariuszy i funkcji w programie WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686999"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="fe371-103">Nowych scenariuszy i funkcji w programie WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="fe371-103">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="fe371-104">Uwaga: Niniejsze informacje mają charakter wstępny i mogą ulec zmianom.</span><span class="sxs-lookup"><span data-stu-id="fe371-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="fe371-105">Wersje programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe371-105">PowerShell Editions</span></span>

<span data-ttu-id="fe371-106">Od wersji 5.1 program PowerShell jest dostępny w różnych wersjach, które charakteryzują się różnymi zestawami funkcji i zgodnością z różnymi platformami.</span><span class="sxs-lookup"><span data-stu-id="fe371-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="fe371-107">**Wersja Desktop:** Oparta na programie .NET Framework i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w pełnych wersjach systemu Windows, takich jak instalacja Server Core i Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="fe371-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="fe371-108">**Wersja Core:** Oparta na module .NET Core i zapewnia zgodność ze skryptami i modułami przeznaczonymi dla wersji programu PowerShell działających w ograniczonych wersjach systemu Windows, takich jak Nano Server i Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="fe371-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="fe371-109">**Dowiedz się więcej o korzystaniu z wersje programu PowerShell**</span><span class="sxs-lookup"><span data-stu-id="fe371-109">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="fe371-110">Określić, działającej wersji programu PowerShell, korzystając z $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="fe371-110">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="fe371-111">Filtrowanie wyników Get-Module przez CompatiblePSEditions przy użyciu parametru PSEdition</span><span class="sxs-lookup"><span data-stu-id="fe371-111">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="fe371-112">Uniemożliwić wykonywanie skryptu, chyba że systemem zgodnej wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe371-112">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="fe371-113">Zadeklaruj zgodność modułu do określonej wersji programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe371-113">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a><span data-ttu-id="fe371-114">Polecenia cmdlet wykazu</span><span class="sxs-lookup"><span data-stu-id="fe371-114">Catalog Cmdlets</span></span>

<span data-ttu-id="fe371-115">Dodano dwa nowe polecenia cmdlet w [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) moduł; to Generowanie i zweryfikować pliki w katalogu Windows.</span><span class="sxs-lookup"><span data-stu-id="fe371-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; these generate and validate Windows catalog files.</span></span>

### <a name="new-filecatalog"></a><span data-ttu-id="fe371-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="fe371-116">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="fe371-117">Nowe FileCatalog tworzy plik katalogu Windows dla zestawu plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="fe371-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="fe371-118">Ten plik w katalogu zawiera skróty dla wszystkich plików w określonych ścieżek.</span><span class="sxs-lookup"><span data-stu-id="fe371-118">This catalog file contains hashes for all files in specified paths.</span></span>
<span data-ttu-id="fe371-119">Użytkownicy mogą dystrybuować zestawu folderów oraz odpowiedni plik wykazu reprezentujący te foldery.</span><span class="sxs-lookup"><span data-stu-id="fe371-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span>
<span data-ttu-id="fe371-120">Te informacje są przydatne sprawdzić, czy zmiany zostały dokonane w folderach od czasu utworzenia katalogu.</span><span class="sxs-lookup"><span data-stu-id="fe371-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="fe371-121">Wykaz w wersji 1 i 2 są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="fe371-121">Catalog versions 1 and 2 are supported.</span></span>
<span data-ttu-id="fe371-122">Wersja 1 używa algorytmu wyznaczania wartości skrótu SHA1 w celu utworzenia skróty plików; w wersji 2 używa SHA256.</span><span class="sxs-lookup"><span data-stu-id="fe371-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span>
<span data-ttu-id="fe371-123">Wykaz w wersji 2 nie jest obsługiwana w *systemu Windows Server 2008 R2* lub *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="fe371-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span>
<span data-ttu-id="fe371-124">Wykaz w wersji 2 powinien być używany w *systemu Windows 8*, *systemu Windows Server 2012*i nowszych systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="fe371-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="fe371-125">Spowoduje to utworzenie pliku wykazu.</span><span class="sxs-lookup"><span data-stu-id="fe371-125">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="fe371-126">Aby sprawdzić integralność pliku wykazu (Pester.cat w powyżej przykładzie), zaloguj się za pomocą [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe371-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span></span>

### <a name="test-filecatalog"></a><span data-ttu-id="fe371-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="fe371-127">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="fe371-128">Test FileCatalog weryfikuje wykazu, reprezentujący zestaw folderów.</span><span class="sxs-lookup"><span data-stu-id="fe371-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="fe371-129">To polecenie cmdlet porównuje wszystkie skróty plików i ich ścieżek względnych znalezionej we *katalogu* z tymi na *dysku*.</span><span class="sxs-lookup"><span data-stu-id="fe371-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span>
<span data-ttu-id="fe371-130">Jeśli wykryje niezgodność skróty plików i ścieżek zwraca stan jako *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="fe371-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span>
<span data-ttu-id="fe371-131">Użytkownicy mogą pobrać te informacje przy użyciu *— szczegółowe* parametru.</span><span class="sxs-lookup"><span data-stu-id="fe371-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span>
<span data-ttu-id="fe371-132">Wyświetla również podpisywania stan katalogu w *podpisu* właściwość, która jest równoważne z wywoływaniem [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) polecenie cmdlet na plik wykazu.</span><span class="sxs-lookup"><span data-stu-id="fe371-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet on the catalog file.</span></span>
<span data-ttu-id="fe371-133">Użytkownicy mogą również pomijać każdego pliku podczas weryfikacji za pomocą *- FilesToSkip* parametru.</span><span class="sxs-lookup"><span data-stu-id="fe371-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

## <a name="module-analysis-cache"></a><span data-ttu-id="fe371-134">Moduł analizy w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="fe371-134">Module Analysis Cache</span></span>

<span data-ttu-id="fe371-135">Począwszy od programu WMF 5.1 program PowerShell zapewnia kontrolę nad pliku, który jest używany do pamięci podręcznej dane dotyczące modułu, na przykład polecenia, które eksportuje ona.</span><span class="sxs-lookup"><span data-stu-id="fe371-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="fe371-136">Domyślnie ta pamięć podręczna znajduje się w pliku `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="fe371-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="fe371-137">Pamięć podręczna jest zwykle do odczytu przy uruchamianiu podczas wyszukiwania dla polecenia i jest zapisywany trochę czasu w wątku tła w po zaimportowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="fe371-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="fe371-138">Aby zmienić domyślną lokalizację pamięci podręcznej, należy ustawić `$env:PSModuleAnalysisCachePath` zmiennej środowiskowej przed uruchomieniem programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe371-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span>
<span data-ttu-id="fe371-139">Zmiany w tej zmiennej środowiskowej mają wpływ tylko na procesy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="fe371-139">Changes to this environment variable will only affect children processes.</span></span>
<span data-ttu-id="fe371-140">Pełna ścieżka (takie jak nazwa pliku), programu PowerShell z uprawnieniami do tworzenia i zapisywać pliki należy nadać nazwę wartości.</span><span class="sxs-lookup"><span data-stu-id="fe371-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>
<span data-ttu-id="fe371-141">Aby wyłączyć pamięć podręczną plików, należy ustawić tę wartość w nieprawidłowej lokalizacji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="fe371-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="fe371-142">To ustawia ścieżkę do nieprawidłowe urządzenie.</span><span class="sxs-lookup"><span data-stu-id="fe371-142">This sets the path to an invalid device.</span></span>
<span data-ttu-id="fe371-143">Jeśli programu PowerShell nie można zapisać do ścieżki, zwracany jest błąd braku, ale możesz zobaczyć raportowania za pomocą śledzenia błędów:</span><span class="sxs-lookup"><span data-stu-id="fe371-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="fe371-144">Podczas pisania, limit pamięci podręcznej, programu PowerShell będzie sprawdzać modułów, które już nie istnieją, aby uniknąć niepotrzebnego dużej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="fe371-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="fe371-145">Czasami te testy nie są pożądane, w którym to przypadku należy je wyłączyć, ustawiając:</span><span class="sxs-lookup"><span data-stu-id="fe371-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="fe371-146">Ustawienie tej zmiennej środowiskowej zacznie obowiązywać natychmiast w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="fe371-146">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="fe371-147">Określanie wersji modułu</span><span class="sxs-lookup"><span data-stu-id="fe371-147">Specifying module version</span></span>

<span data-ttu-id="fe371-148">W program WMF 5.1 `using module` działa tak samo jak inne konstrukcje związane z modułu w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe371-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="fe371-149">Miała wcześniej, można określić wersji określonego modułu; Jeśli istnieje wiele wersji, to zakończyło się błędem.</span><span class="sxs-lookup"><span data-stu-id="fe371-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="fe371-150">W programie WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="fe371-150">In WMF 5.1:</span></span>

- <span data-ttu-id="fe371-151">Możesz użyć [ModuleSpecification konstruktora (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="fe371-151">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="fe371-152">Ta tabela skrótów ma tego samego formatu co `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="fe371-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="fe371-153">**Przykład:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="fe371-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="fe371-154">W przypadku wielu wersji modułu programu PowerShell używa **tę samą logikę rozpoznawania** jako `Import-Module` i nie zwraca błąd--takie samo zachowanie jako `Import-Module` i `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="fe371-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="fe371-155">Ulepszenia Pester</span><span class="sxs-lookup"><span data-stu-id="fe371-155">Improvements to Pester</span></span>

<span data-ttu-id="fe371-156">W program WMF 5.1 wersję usług Pester który jest dostarczany za pomocą programu PowerShell została zaktualizowana z 3.3.5 3.4.0 dodając zatwierdzenia https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, która umożliwia lepsze zachowanie dla usług Pester na serwerze Nano Server.</span><span class="sxs-lookup"><span data-stu-id="fe371-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="fe371-157">Możesz przejrzeć zmiany wprowadzone w wersjach 3.3.5 do 3.4.0, sprawdzając plik ChangeLog.md w lokalizacji: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="fe371-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>
