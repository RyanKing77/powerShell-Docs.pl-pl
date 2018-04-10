---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="0ccc6-103">Obiekt ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="0ccc6-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="0ccc6-104">**ISEFileCollection** obiektu jest kolekcją **ISEFile** obiektów.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="0ccc6-105">Przykładem jest $psISE.CurrentPowerShellTab.Files kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="0ccc6-106">Metody</span><span class="sxs-lookup"><span data-stu-id="0ccc6-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="0ccc6-107">Add\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="0ccc6-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="0ccc6-108">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0ccc6-109">Tworzy i zwraca nowy plik bez tytułu i dodaje go do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="0ccc6-110">**IsUntitled** właściwość nowo utworzonego pliku jest **$true**.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="0ccc6-111">**\[fullPath\]**  — opcjonalny ciąg pełni określona ścieżka pliku.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="0ccc6-112">Wyjątek jest generowany, Jeśli dołączysz **fullPath** parametr i ścieżką względną lub jeśli używasz nazwę pliku zamiast pełnej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="0ccc6-113">Usuń\( pliku \[życie\] \)</span><span class="sxs-lookup"><span data-stu-id="0ccc6-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="0ccc6-114">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0ccc6-115">Usuwa określony plik z bieżącej karty środowiska PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="0ccc6-116">**Plik** -plik ISEFile ciąg, który ma zostać usunięty z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="0ccc6-117">Jeśli plik nie został zapisany, ta metoda zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="0ccc6-118">Użyj **wymusić** przełącznika parametr, aby wymusić usunięcie niezapisanym pliku.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="0ccc6-119">**\[Wymuś\]**  -opcjonalna wartość logiczna Jeśli równa **$true**, udziela uprawnień, aby usunąć plik, nawet jeśli nie zostały zapisane po ostatnim zastosowaniu.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="0ccc6-120">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="0ccc6-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="0ccc6-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="0ccc6-122">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0ccc6-123">Wybiera pliku, określonej przez **selectedFile** parametru.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="0ccc6-124">**selectedFile** -ISEFile Microsoft.PowerShell.Host.ISE.ISEFile pliku, który chcesz wybrać.</span><span class="sxs-lookup"><span data-stu-id="0ccc6-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="0ccc6-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ccc6-125">See Also</span></span>

- [<span data-ttu-id="0ccc6-126">Obiekt ISEFile</span><span class="sxs-lookup"><span data-stu-id="0ccc6-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="0ccc6-127">Cel programu Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="0ccc6-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="0ccc6-128">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="0ccc6-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)