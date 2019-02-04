---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685452"
---
# <a name="the-isesnippetobject"></a>ISESnippetObject

**ISESnippet** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISESnippet. Elementy członkowskie **$psISE.CurrentPowerShellTab.Snippets** kolekcji należą do nich **ISESnippet** obiektów. Najprostszym sposobem utworzenia fragment jest użycie [New IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) polecenia cmdlet.

## <a name="properties"></a>Właściwości

### <a name="author"></a>Autor

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Właściwość tylko do odczytu, który pobiera nazwę autora fragmentu kodu.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Właściwość tylko do odczytu, która fragmentu kodu, który ma zostać wstawiony do edytora.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Skrót

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Właściwość tylko do odczytu, która pobiera Windows skrótu klawiaturowego dla elementu menu.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Zobacz też

- [Obiekt ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)