---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Polecenia cmdlet wykazu
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057641"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="a8dc7-103">Polecenia cmdlet wykazu</span><span class="sxs-lookup"><span data-stu-id="a8dc7-103">Catalog Cmdlets</span></span>

<span data-ttu-id="a8dc7-104">Dodaliśmy dwa nowe polecenia cmdlet w [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) modułu, aby wygenerować i zweryfikować pliki w katalogu systemu windows.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="a8dc7-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a8dc7-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="a8dc7-106">`New-FileCatalog` Tworzy plik katalogu systemu windows dla zestawu plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="a8dc7-107">Plik wykazu zawiera skróty dla wszystkich plików w określonych ścieżek.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="a8dc7-108">Użytkownicy mogą dystrybuować zestawu folderów oraz odpowiadający plik wykazu, który reprezentuje te foldery.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="a8dc7-109">Plik wykazu może służyć przez odbiorcę zawartości można sprawdzić, czy zmiany zostały wprowadzone do folderów, po utworzeniu wykazu.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="a8dc7-110">Firma Microsoft obsługuje tworzenie katalogu w wersji 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="a8dc7-111">Wersja 1 używa algorytmu wyznaczania wartości skrótu SHA1 do tworzenia plików, skrótów i w wersji 2 używa SHA256.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="a8dc7-112">Wykaz w wersji 2 nie jest obsługiwana w *systemu Windows Server 2008 R2* i *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="a8dc7-113">Zaleca się używać katalogu w wersji 2, jeśli przy użyciu platform *systemu Windows 8*, *systemu Windows Server 2012* i nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="a8dc7-114">Aby użyć tego polecenia na istniejący moduł, określ CatalogFilePath i Path zmienne jest zgodna z lokalizacją manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="a8dc7-115">W poniższym przykładzie manifest modułu znajduje się w C:\Program Files\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="a8dc7-116">Spowoduje to utworzenie pliku wykazu.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="a8dc7-117">Aby sprawdzić integralność pliku wykazu (Pester.cat w powyżej przykładzie) powinien on być podpisany przy użyciu [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="a8dc7-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a8dc7-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="a8dc7-119">`Test-FileCatalog` sprawdza poprawność wykazu, reprezentujący zestaw folderów.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="a8dc7-120">To polecenie cmdlet porównuje wartości skrótów wszystkich plików i ich ścieżek względnych znajdującą się w pliku wykazu z tymi zapisywany na dysku.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="a8dc7-121">Jeśli wykryje niezgodność skróty plików i ścieżek zwraca stan `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="a8dc7-122">Użytkownicy mogą pobrać wszystkie te informacje przy użyciu `Detailed` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="a8dc7-123">Stan podpisywania katalogu jest wyświetlany jako `Signature` pola, które jest taka sama jak wywołanie [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) polecenie cmdlet na plik wykazu.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="a8dc7-124">Użytkownicy mogą również pomijać każdego pliku podczas weryfikacji za pomocą `FilesToSkip` parametru.</span><span class="sxs-lookup"><span data-stu-id="a8dc7-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
