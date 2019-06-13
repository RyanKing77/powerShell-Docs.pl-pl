---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEFileCollection
ms.openlocfilehash: 96db51ee921cc0fa34803091d563bc6e118643b6
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030521"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="d62d4-103">Obiekt ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="d62d4-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="d62d4-104">**ISEFileCollection** obiektu jest kolekcją **ISEFile** obiektów.</span><span class="sxs-lookup"><span data-stu-id="d62d4-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="d62d4-105">Przykładem jest kolekcją $psISE.CurrentPowerShellTab.Files.</span><span class="sxs-lookup"><span data-stu-id="d62d4-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="d62d4-106">Metody</span><span class="sxs-lookup"><span data-stu-id="d62d4-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="d62d4-107">Dodaj\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="d62d4-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="d62d4-108">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="d62d4-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d62d4-109">Tworzy i zwraca nowy plik bez tytułu i dodaje go do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d62d4-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="d62d4-110">**IsUntitled** właściwość nowo tworzonych plików jest **$true**.</span><span class="sxs-lookup"><span data-stu-id="d62d4-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="d62d4-111">**\[fullPath\]**  — opcjonalny ciąg w pełni określona ścieżka pliku.</span><span class="sxs-lookup"><span data-stu-id="d62d4-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="d62d4-112">Wyjątek jest generowany, Jeśli dołączysz **fullPath** parametru i ścieżki względnej, czy przy użyciu nazwy pliku zamiast pełnej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="d62d4-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="d62d4-113">Remove\( File, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="d62d4-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="d62d4-114">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="d62d4-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d62d4-115">Usuwa określony plik z bieżącej karty programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d62d4-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="d62d4-116">**Plik** — plik ISEFile ciąg, który ma zostać usunięty z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d62d4-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="d62d4-117">Jeśli nie został zapisany plik, ta metoda zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d62d4-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="d62d4-118">Użyj **wymusić** Przełącz parametru, aby wymusić usunięcie niezapisanym pliku.</span><span class="sxs-lookup"><span data-stu-id="d62d4-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="d62d4-119">**\[Wymuś\]**  -opcjonalna wartość logiczna Jeśli równa **$true**, przyznaje uprawnienia do usunięcia pliku, nawet jeśli nie zostały zapisane po ostatnim zastosowaniu.</span><span class="sxs-lookup"><span data-stu-id="d62d4-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="d62d4-120">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="d62d4-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="d62d4-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="d62d4-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="d62d4-122">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="d62d4-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d62d4-123">Wybiera pliku, który jest określony przez **selectedFile** parametru.</span><span class="sxs-lookup"><span data-stu-id="d62d4-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="d62d4-124">**selectedFile** — plik ISEFile Microsoft.PowerShell.Host.ISE.ISEFile, który ma zostać wybrana.</span><span class="sxs-lookup"><span data-stu-id="d62d4-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="d62d4-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d62d4-125">See Also</span></span>

- [<span data-ttu-id="d62d4-126">Obiekt ISEFile</span><span class="sxs-lookup"><span data-stu-id="d62d4-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="d62d4-127">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d62d4-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d62d4-128">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="d62d4-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
