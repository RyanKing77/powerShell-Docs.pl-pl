---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="the-isefilecollection-object"></a>Obiekt ISEFileCollection

**ISEFileCollection** obiektu jest kolekcją **ISEFile** obiektów. Przykładem jest $psISE.CurrentPowerShellTab.Files kolekcji.

## <a name="methods"></a>Metody

### <a name="add-fullpath-"></a>Add\( \[fullPath\] \)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Tworzy i zwraca nowy plik bez tytułu i dodaje go do kolekcji. **IsUntitled** właściwość nowo utworzonego pliku jest **$true**.

**\[fullPath\]**  — opcjonalny ciąg pełni określona ścieżka pliku. Wyjątek jest generowany, Jeśli dołączysz **fullPath** parametr i ścieżką względną lub jeśli używasz nazwę pliku zamiast pełnej ścieżki.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Usuń\( pliku \[życie\] \)

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Usuwa określony plik z bieżącej karty środowiska PowerShell.

**Plik** -plik ISEFile ciąg, który ma zostać usunięty z kolekcji. Jeśli plik nie został zapisany, ta metoda zgłasza wyjątek. Użyj **wymusić** przełącznika parametr, aby wymusić usunięcie niezapisanym pliku.

**\[Wymuś\]**  -opcjonalna wartość logiczna Jeśli równa **$true**, udziela uprawnień, aby usunąć plik, nawet jeśli nie zostały zapisane po ostatnim zastosowaniu. Wartość domyślna to **$false**.

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

Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Wybiera pliku, określonej przez **selectedFile** parametru.

**selectedFile** -ISEFile Microsoft.PowerShell.Host.ISE.ISEFile pliku, który chcesz wybrać.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Zobacz też

- [Obiekt ISEFile](The-ISEFile-Object.md)
- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)