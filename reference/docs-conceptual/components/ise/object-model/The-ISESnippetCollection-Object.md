---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISESnippetCollection
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030497"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="23401-103">Obiekt ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="23401-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="23401-104">**ISESnippetCollection** obiektu jest kolekcją **ISESnippet** obiektów.</span><span class="sxs-lookup"><span data-stu-id="23401-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="23401-105">Kolekcja plików, która jest skojarzona z **PowerShellTab** obiektu jest członkiem tej klasy.</span><span class="sxs-lookup"><span data-stu-id="23401-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="23401-106">Na przykład **$psISE.CurrentPowerShellTab.Files** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="23401-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="23401-107">Metody</span><span class="sxs-lookup"><span data-stu-id="23401-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="23401-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="23401-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="23401-109">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="23401-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="23401-110">Ładunki. plik snippets.ps1xml, który zawiera fragmenty zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="23401-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="23401-111">Najprostszym sposobem utworzenia fragmentów jest należy użyć polecenia cmdlet New-IseSnippet, który automatycznie zapisuje je w folderze profilu, aby były załadowane każdym uruchomieniu programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="23401-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="23401-112">**FilePathName** — ciąg ścieżki i nazwy do pliku. plik snippets.ps1xml, który zawiera definicje fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="23401-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="23401-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23401-113">See Also</span></span>

- [<span data-ttu-id="23401-114">The ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="23401-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="23401-115">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="23401-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="23401-116">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="23401-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
