---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684598"
---
# <a name="the-isefilecollection-object"></a>Obiekt ISEFileCollection

**ISEFileCollection** obiektu jest kolekcją **ISEFile** obiektów. Przykładem jest kolekcją $psISE.CurrentPowerShellTab.Files.

## <a name="methods"></a>Metody

### <a name="add-fullpath-"></a>Dodaj\( \[fullPath\] \)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Tworzy i zwraca nowy plik bez tytułu i dodaje go do kolekcji. **IsUntitled** właściwość nowo tworzonych plików jest **$true**.

**\[fullPath\]**  — opcjonalny ciąg w pełni określona ścieżka pliku. Wyjątek jest generowany, Jeśli dołączysz **fullPath** parametru i ścieżki względnej, czy przy użyciu nazwy pliku zamiast pełnej ścieżki.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Remove\( File, \[Force\] \)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Usuwa określony plik z bieżącej karty programu PowerShell.

**Plik** — plik ISEFile ciąg, który ma zostać usunięty z kolekcji. Jeśli nie został zapisany plik, ta metoda zgłasza wyjątek. Użyj **wymusić** Przełącz parametru, aby wymusić usunięcie niezapisanym pliku.

**\[Wymuś\]**  -opcjonalna wartość logiczna Jeśli równa **$true**, przyznaje uprawnienia do usunięcia pliku, nawet jeśli nie zostały zapisane po ostatnim zastosowaniu. Wartość domyślna to **$false**.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Wybiera pliku, który jest określony przez **selectedFile** parametru.

**selectedFile** — plik ISEFile Microsoft.PowerShell.Host.ISE.ISEFile, który ma zostać wybrana.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Zobacz też

- [Obiekt ISEFile](The-ISEFile-Object.md)
- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)