---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086678"
---
# <a name="the-isesnippetcollection-object"></a>Obiekt ISESnippetCollection

**ISESnippetCollection** obiektu jest kolekcją **ISESnippet** obiektów. Kolekcja plików, która jest skojarzona z **PowerShellTab** obiektu jest członkiem tej klasy. Na przykład **$psISE.CurrentPowerShellTab.Files** kolekcji.

## <a name="methods"></a>Metody

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Ładunki. plik snippets.ps1xml, który zawiera fragmenty zdefiniowanych przez użytkownika. Najprostszym sposobem utworzenia fragmentów jest należy użyć polecenia cmdlet New-IseSnippet, który automatycznie zapisuje je w folderze profilu, aby były załadowane każdym uruchomieniu programu Windows PowerShell ISE.

**FilePathName** — ciąg ścieżki i nazwy do pliku. plik snippets.ps1xml, który zawiera definicje fragmentu kodu.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Zobacz też

- [The ISESnippetObject](The-ISESnippetObject.md)
- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)