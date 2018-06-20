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
ms.locfileid: "30950954"
---
# <a name="the-isesnippetcollection-object"></a>Obiekt ISESnippetCollection

**ISESnippetCollection** obiektu jest kolekcją **ISESnippet** obiektów. Kolekcja plików, z którym skojarzony jest **PowerShellTab** obiektu jest członkiem tej klasy. Na przykład **$psISE.CurrentPowerShellTab.Files** kolekcji.

## <a name="methods"></a>Metody

### <a name="load-filepathname-"></a>Obciążenia\( FilePathName \)

Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

Ładunki. snippets.ps1xml pliku, który zawiera wstawki zdefiniowane przez użytkownika. Najprostszym sposobem utworzenia fragmentów jest użycie polecenia cmdlet New-IseSnippet, który automatycznie zapisuje je w folderze profilu, aby były załadowane każdym uruchomieniu programu Windows PowerShell ISE.

**FilePathName** — ciąg ścieżkę i nazwę pliku. plik snippets.ps1xml, który zawiera definicje fragment kodu.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Zobacz też

- [ISESnippetObject](The-ISESnippetObject.md)
- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)