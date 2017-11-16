---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a>Obiekt ISEFile
  **ISEFile** obiekt reprezentuje plik w Windows PowerShell® Integrated Scripting Environment (ISE). To wystąpienie klasy Microsoft.PowerShell.Host.ISE.ISEFile. W tym temacie wymieniono elementu członkowskiego metod i właściwości elementu członkowskiego. **$PsISE.CurrentFile** i pliki w kolekcji plików na karcie programu PowerShell są wszystkie wystąpienia klasy Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Metody

### <a name="save-saveencoding-"></a>Zapisz\( \[saveEncoding\]\)
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Zapisuje plik na dysku.

 **\[saveEncoding\]**  — opcjonalnie [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalnego parametru kodowanie parametr służący do zapisanego pliku. Wartość domyślna to **UTF8**.

 **Wyjątki**
 -   **System.IO.IOException**: nie można zapisać pliku.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a>Zapisz jako\(nazwę pliku, \[saveEncoding\]\)
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Kodowanie i zapisuje plik z określoną nazwą pliku.

 **Nazwa pliku** -String Nazwa do użycia do zapisania pliku.

 **\[saveEncoding\]**  — opcjonalnie [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalnego parametru kodowanie parametr służący do zapisanego pliku. Wartość domyślna to **UTF8**.

 **Wyjątki**
 -   **System.ArgumentNullException**: **filename** parametr ma wartość null.

- **System.ArgumentException**: **filename** parametr jest pusty.

- **System.IO.IOException**: nie można zapisać pliku.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a>Właściwości

### <a name="displayname"></a>DisplayName
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

 Właściwość tylko do odczytu, która pobiera ciąg, który zawiera nazwę wyświetlaną tego pliku. Nazwa jest wyświetlana na **pliku** kartę w górnej części edytora. Obecność gwiazdkę \( \* \) na końcu nazwy wskazuje, że plik zawiera zmiany, które nie zostały zapisane.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a>Edytor
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwość tylko do odczytu, która pobiera [obiekt](The-ISEEditor-Object.md) używanego do określonego pliku.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a>Kodowanie
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwość tylko do odczytu, która pobiera kodowanie oryginalnego pliku. Jest to **System.Text.Encoding** obiektu.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a>FullPath
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwość tylko do odczytu, która pobiera ciąg, który określa pełną ścieżkę otwarty plik.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a>IsSaved
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwości typu Boolean tylko do odczytu, która zwraca **$true** Jeśli plik został zapisany po ostatniej modyfikacji.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a>IsUntitled
  Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy. 

 Właściwości tylko do odczytu, która zwraca **$true** Jeśli plik nigdy nie został podany tytuł.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a>Zobacz też
- [ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
- [Windows PowerShell ISE skryptów modelu obiektów](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Dotyczące modelu obiektów programu Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [Hierarchia modelu obiektów ISE](The-ISE-Object-Model-Hierarchy.md)
