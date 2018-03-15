---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f1b023291826d5568eb8bdf5a898a00228825276
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="the-isesnippetobject"></a>ISESnippetObject
  **ISESnippet** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISESnippet. Elementy członkowskie **$psISE.CurrentPowerShellTab.Snippets** kolekcji należą do nich **ISESnippet** obiektów. Najprostszym sposobem tworzenia fragment jest użycie [IseSnippet nowy&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) polecenia cmdlet.

## <a name="properties"></a>Właściwości

### <a name="author"></a>Autor
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

 Właściwość tylko do odczytu, który pobiera nazwę autora wstawki kodu.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a>CodeFragment
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

 Właściwość tylko do odczytu, która pobiera fragment kodu, który ma zostać wstawiony do edytora.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a>Skrót
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

 Właściwość tylko do odczytu, która pobiera systemu Windows skrótu klawiaturowego dla elementu menu.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Zobacz też
- [Obiekt ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)
