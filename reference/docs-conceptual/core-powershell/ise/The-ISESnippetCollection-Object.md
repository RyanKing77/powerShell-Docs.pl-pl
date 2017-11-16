---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="90701-103">Obiekt ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="90701-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="90701-104">**ISESnippetCollection** obiektu jest kolekcją **ISESnippet** obiektów.</span><span class="sxs-lookup"><span data-stu-id="90701-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="90701-105">Kolekcja plików, z którym skojarzony jest **PowerShellTab** obiektu jest członkiem tej klasy.</span><span class="sxs-lookup"><span data-stu-id="90701-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="90701-106">Na przykład **$psISE.CurrentPowerShellTab.Files** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="90701-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="90701-107">Metody</span><span class="sxs-lookup"><span data-stu-id="90701-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="90701-108">Obciążenia\( FilePathName\)</span><span class="sxs-lookup"><span data-stu-id="90701-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="90701-109">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="90701-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="90701-110">Ładunki. snippets.ps1xml pliku, który zawiera wstawki zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="90701-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="90701-111">Najprostszym sposobem utworzenia fragmentów jest użycie polecenia cmdlet New-IseSnippet, który automatycznie zapisuje je w folderze profilu, aby były załadowane każdym uruchomieniu programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="90701-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="90701-112">**FilePathName** — ciąg ścieżkę i nazwę pliku. plik snippets.ps1xml, który zawiera definicje fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="90701-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="90701-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90701-113">See Also</span></span>
- [<span data-ttu-id="90701-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="90701-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="90701-115">Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="90701-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="90701-116">Dotyczące modelu obiektów programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="90701-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="90701-117">Hierarchia modelu obiektów ISE</span><span class="sxs-lookup"><span data-stu-id="90701-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
