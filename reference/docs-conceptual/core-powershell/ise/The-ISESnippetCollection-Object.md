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
# <a name="the-isesnippetcollection-object"></a>Obiekt ISESnippetCollection
  **ISESnippetCollection** obiektu jest kolekcją **ISESnippet** obiektów. Kolekcja plików, z którym skojarzony jest **PowerShellTab** obiektu jest członkiem tej klasy. Na przykład **$psISE.CurrentPowerShellTab.Files** kolekcji.

## <a name="methods"></a>Metody

### <a name="load-filepathname-"></a>Obciążenia\( FilePathName\)
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach. 

 Ładunki. snippets.ps1xml pliku, który zawiera wstawki zdefiniowane przez użytkownika. Najprostszym sposobem utworzenia fragmentów jest użycie polecenia cmdlet New-IseSnippet, który automatycznie zapisuje je w folderze profilu, aby były załadowane każdym uruchomieniu programu Windows PowerShell ISE.

 **FilePathName** — ciąg ścieżkę i nazwę pliku. plik snippets.ps1xml, który zawiera definicje fragment kodu.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a>Zobacz też
- [ISESnippetObject](The-ISESnippetObject.md) 
- [Windows PowerShell ISE skryptów modelu obiektów](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Dotyczące modelu obiektów programu Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Hierarchia modelu obiektów ISE](The-ISE-Object-Model-Hierarchy.md)

  
