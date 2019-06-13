---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEFile
ms.openlocfilehash: ebb5a35f6ea9d93eab633b9f4e6c84e4fddd6ae8
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028963"
---
# <a name="the-isefile-object"></a>Obiekt ISEFile

**ISEFile** obiekt reprezentuje plików w Windows PowerShell® zintegrowane Scripting Environment (ISE). Jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEFile. Ten temat zawiera element członkowski metod i właściwości elementu członkowskiego. **$PsISE.CurrentFile** i pliki w kolekcji plików w kartę programu PowerShell są wszystkie wystąpienia klasy Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Metody

### <a name="save-saveencoding-"></a>Zapisz\( \[saveEncoding\] \)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Zapisuje plik na dysku.

**\[saveEncoding\]**  — wartość opcjonalna [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalny znak kodowanie parametr służący do zapisanego pliku. Wartość domyślna to **UTF8**.

### <a name="exceptions"></a>Wyjątki

- **System.IO.IOException**: Nie można zapisać pliku.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>Zapisz jako\(nazwy pliku, \[saveEncoding\]\)

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Zapisuje plik przy użyciu określonej nazwy pliku i kodowanie.

**Nazwa pliku** -String nazwa ma być używany do zapisania pliku.

**\[saveEncoding\]**  — wartość opcjonalna [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalny znak kodowanie parametr służący do zapisanego pliku. Wartość domyślna to **UTF8**.

### <a name="exceptions"></a>Wyjątki

- **System.ArgumentNullException**: **Filename** parametr ma wartość null.
- **System.ArgumentException**: **Filename** parametr jest pusty.
- **System.IO.IOException**: Nie można zapisać pliku.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Właściwości

### <a name="displayname"></a>DisplayName

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która pobiera ciąg, który zawiera nazwę wyświetlaną tego pliku. Nazwa jest wyświetlana na **pliku** kartę w górnej części edytora. Obecność gwiazdki \( \* \) na końcu nazwy wskazuje, że plik ma zmiany, które nie zostały zapisane.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Edytor

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która pobiera [obiekt edytora](The-ISEEditor-Object.md) używany dla określonego pliku.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Kodowanie

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, oryginalnym kodowanie pliku. Jest to **System.Text.Encoding** obiektu.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która pobiera ciąg, który określa pełną ścieżkę otwarty plik.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość logiczna przeznaczony tylko do odczytu, która zwraca **$true** Jeśli plik został zapisany po ostatniej modyfikacji.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która zwraca **$true** Jeśli plik nigdy nie został podany tytuł.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Zobacz też

- [The ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)
