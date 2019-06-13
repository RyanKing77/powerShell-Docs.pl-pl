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
