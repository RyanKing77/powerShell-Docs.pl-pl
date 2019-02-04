---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684612"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="287ec-103">Obiekt ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="287ec-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="287ec-104">**ISESnippetCollection** obiektu jest kolekcją **ISESnippet** obiektów.</span><span class="sxs-lookup"><span data-stu-id="287ec-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="287ec-105">Kolekcja plików, która jest skojarzona z **PowerShellTab** obiektu jest członkiem tej klasy.</span><span class="sxs-lookup"><span data-stu-id="287ec-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="287ec-106">Na przykład **$psISE.CurrentPowerShellTab.Files** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="287ec-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="287ec-107">Metody</span><span class="sxs-lookup"><span data-stu-id="287ec-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="287ec-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="287ec-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="287ec-109">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="287ec-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="287ec-110">Ładunki. plik snippets.ps1xml, który zawiera fragmenty zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="287ec-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="287ec-111">Najprostszym sposobem utworzenia fragmentów jest należy użyć polecenia cmdlet New-IseSnippet, który automatycznie zapisuje je w folderze profilu, aby były załadowane każdym uruchomieniu programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="287ec-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="287ec-112">**FilePathName** — ciąg ścieżki i nazwy do pliku. plik snippets.ps1xml, który zawiera definicje fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="287ec-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="287ec-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="287ec-113">See Also</span></span>

- [<span data-ttu-id="287ec-114">The ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="287ec-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="287ec-115">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="287ec-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="287ec-116">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="287ec-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)