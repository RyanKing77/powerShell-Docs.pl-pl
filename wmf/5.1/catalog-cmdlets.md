---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Polecenia cmdlet wykazu
ms.openlocfilehash: 7eaca09667af0eb5d719f23e987bb112e8514978
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189071"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="62901-103">Polecenia cmdlet katalogu</span><span class="sxs-lookup"><span data-stu-id="62901-103">Catalog Cmdlets</span></span>

<span data-ttu-id="62901-104">Dodano dwa nowe polecenia cmdlet w [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) modułu, aby wygenerować i zweryfikować pliki w katalogu systemu windows.</span><span class="sxs-lookup"><span data-stu-id="62901-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="62901-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="62901-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="62901-106">`New-FileCatalog` Tworzy plik katalogu systemu windows dla zestawu plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="62901-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="62901-107">Skróty do wszystkich plików określonych ścieżek zawiera plik wykazu.</span><span class="sxs-lookup"><span data-stu-id="62901-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="62901-108">Użytkownicy można rozpowszechniać zestaw folderów oraz odpowiadający plik wykazu, który reprezentuje te foldery.</span><span class="sxs-lookup"><span data-stu-id="62901-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="62901-109">Plik wykazu mogą posłużyć odbiorcom zawartości do sprawdzania, czy wprowadzono zmiany do folderów po utworzeniu katalogu.</span><span class="sxs-lookup"><span data-stu-id="62901-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="62901-110">Firma Microsoft obsługuje tworzenie katalogu w wersji 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="62901-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="62901-111">W wersji 1 używa algorytmu wyznaczania wartości skrótu SHA1 do tworzenia plików, skrótów i w wersji 2 używa SHA256.</span><span class="sxs-lookup"><span data-stu-id="62901-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="62901-112">2. Wersja katalogu nie jest obsługiwana w *systemu Windows Server 2008 R2* i *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="62901-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="62901-113">Zaleca się korzystają z katalogu w wersji 2 przy użyciu platform *systemu Windows 8*, *systemu Windows Server 2012* i powyżej.</span><span class="sxs-lookup"><span data-stu-id="62901-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="62901-114">Aby użyć tego polecenia na istniejący moduł, określ zmienne CatalogFilePath i ścieżka do dopasowania lokalizacja manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="62901-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="62901-115">W poniższym przykładzie manifestu modułu jest C:\Program Files\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="62901-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="62901-116">Spowoduje to utworzenie pliku wykazu.</span><span class="sxs-lookup"><span data-stu-id="62901-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="62901-117">Aby sprawdzić integralność pliku wykazu (Pester.cat w powyżej exmaple) powinien on być podpisany przy użyciu [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="62901-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="62901-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="62901-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="62901-119">`Test-FileCatalog` weryfikuje katalogu, reprezentujący zestaw folderów.</span><span class="sxs-lookup"><span data-stu-id="62901-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="62901-120">To polecenie cmdlet porównuje wartości skrótów wszystkich plików i ich ścieżek względnych znaleziono w pliku wykazu te są zapisywane na dysku.</span><span class="sxs-lookup"><span data-stu-id="62901-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="62901-121">W przypadku wykrycia niezgodność wartości skrótu pliku i ścieżki zwraca stan `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="62901-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="62901-122">Użytkownicy mogą pobrać wszystkie te informacje przy użyciu `Detailed` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="62901-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="62901-123">Stan podpisywania katalogu jest wyświetlany jako `Signature` pola, które jest taka sama jak wywołanie [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) polecenia cmdlet na plik wykazu.</span><span class="sxs-lookup"><span data-stu-id="62901-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="62901-124">Użytkownicy mogą też pominąć każdego pliku, podczas sprawdzania poprawności przy użyciu `FilesToSkip` parametru.</span><span class="sxs-lookup"><span data-stu-id="62901-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
