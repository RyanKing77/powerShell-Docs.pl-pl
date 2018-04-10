---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="bbb9f-103">Obiekt ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="bbb9f-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="bbb9f-104">**ISESnippetCollection** obiektu jest kolekcją **ISESnippet** obiektów.</span><span class="sxs-lookup"><span data-stu-id="bbb9f-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="bbb9f-105">Kolekcja plików, z którym skojarzony jest **PowerShellTab** obiektu jest członkiem tej klasy.</span><span class="sxs-lookup"><span data-stu-id="bbb9f-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="bbb9f-106">Na przykład **$psISE.CurrentPowerShellTab.Files** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bbb9f-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="bbb9f-107">Metody</span><span class="sxs-lookup"><span data-stu-id="bbb9f-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="bbb9f-108">Obciążenia\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="bbb9f-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="bbb9f-109">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="bbb9f-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="bbb9f-110">Ładunki. snippets.ps1xml pliku, który zawiera wstawki zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bbb9f-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="bbb9f-111">Najprostszym sposobem utworzenia fragmentów jest użycie polecenia cmdlet New-IseSnippet, który automatycznie zapisuje je w folderze profilu, aby były załadowane każdym uruchomieniu programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bbb9f-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="bbb9f-112">**FilePathName** — ciąg ścieżkę i nazwę pliku. plik snippets.ps1xml, który zawiera definicje fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="bbb9f-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="bbb9f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbb9f-113">See Also</span></span>

- [<span data-ttu-id="bbb9f-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="bbb9f-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="bbb9f-115">Cel programu Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="bbb9f-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="bbb9f-116">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="bbb9f-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)