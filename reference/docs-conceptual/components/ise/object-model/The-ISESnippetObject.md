---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405547"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="109b8-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="109b8-103">The ISESnippetObject</span></span>

<span data-ttu-id="109b8-104">**ISESnippet** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="109b8-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="109b8-105">Elementy członkowskie **$psISE.CurrentPowerShellTab.Snippets** kolekcji należą do nich **ISESnippet** obiektów.</span><span class="sxs-lookup"><span data-stu-id="109b8-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="109b8-106">Najprostszym sposobem utworzenia fragment jest użycie [New IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="109b8-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="109b8-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="109b8-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="109b8-108">Autor</span><span class="sxs-lookup"><span data-stu-id="109b8-108">Author</span></span>

<span data-ttu-id="109b8-109">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="109b8-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="109b8-110">Właściwość tylko do odczytu, który pobiera nazwę autora fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="109b8-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="109b8-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="109b8-111">CodeFragment</span></span>

<span data-ttu-id="109b8-112">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="109b8-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="109b8-113">Właściwość tylko do odczytu, która fragmentu kodu, który ma zostać wstawiony do edytora.</span><span class="sxs-lookup"><span data-stu-id="109b8-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="109b8-114">Skrót</span><span class="sxs-lookup"><span data-stu-id="109b8-114">Shortcut</span></span>

<span data-ttu-id="109b8-115">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="109b8-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="109b8-116">Właściwość tylko do odczytu, która pobiera Windows skrótu klawiaturowego dla elementu menu.</span><span class="sxs-lookup"><span data-stu-id="109b8-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="109b8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="109b8-117">See Also</span></span>

- [<span data-ttu-id="109b8-118">Obiekt ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="109b8-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="109b8-119">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="109b8-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="109b8-120">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="109b8-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)