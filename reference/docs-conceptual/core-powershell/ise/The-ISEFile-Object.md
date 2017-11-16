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
# <a name="the-isefile-object"></a><span data-ttu-id="ff101-103">Obiekt ISEFile</span><span class="sxs-lookup"><span data-stu-id="ff101-103">The ISEFile Object</span></span>
  <span data-ttu-id="ff101-104">**ISEFile** obiekt reprezentuje plik w Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="ff101-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="ff101-105">To wystąpienie klasy Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="ff101-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="ff101-106">W tym temacie wymieniono elementu członkowskiego metod i właściwości elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ff101-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="ff101-107">**$PsISE.CurrentFile** i pliki w kolekcji plików na karcie programu PowerShell są wszystkie wystąpienia klasy Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="ff101-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="ff101-108">Metody</span><span class="sxs-lookup"><span data-stu-id="ff101-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="ff101-109">Zapisz\( \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="ff101-109">Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="ff101-110">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ff101-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff101-111">Zapisuje plik na dysku.</span><span class="sxs-lookup"><span data-stu-id="ff101-111">Saves the file to disk.</span></span>

 <span data-ttu-id="ff101-112">**\[saveEncoding\]**  — opcjonalnie [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalnego parametru kodowanie parametr służący do zapisanego pliku.</span><span class="sxs-lookup"><span data-stu-id="ff101-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="ff101-113">Wartość domyślna to **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="ff101-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="ff101-114">**Wyjątki**</span><span class="sxs-lookup"><span data-stu-id="ff101-114">**Exceptions**</span></span>
 -   <span data-ttu-id="ff101-115">**System.IO.IOException**: nie można zapisać pliku.</span><span class="sxs-lookup"><span data-stu-id="ff101-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="ff101-116">Zapisz jako\(nazwę pliku, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="ff101-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="ff101-117">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ff101-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff101-118">Kodowanie i zapisuje plik z określoną nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="ff101-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="ff101-119">**Nazwa pliku** -String Nazwa do użycia do zapisania pliku.</span><span class="sxs-lookup"><span data-stu-id="ff101-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="ff101-120">**\[saveEncoding\]**  — opcjonalnie [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalnego parametru kodowanie parametr służący do zapisanego pliku.</span><span class="sxs-lookup"><span data-stu-id="ff101-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="ff101-121">Wartość domyślna to **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="ff101-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="ff101-122">**Wyjątki**</span><span class="sxs-lookup"><span data-stu-id="ff101-122">**Exceptions**</span></span>
 -   <span data-ttu-id="ff101-123">**System.ArgumentNullException**: **filename** parametr ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="ff101-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

- <span data-ttu-id="ff101-124">**System.ArgumentException**: **filename** parametr jest pusty.</span><span class="sxs-lookup"><span data-stu-id="ff101-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

- <span data-ttu-id="ff101-125">**System.IO.IOException**: nie można zapisać pliku.</span><span class="sxs-lookup"><span data-stu-id="ff101-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="ff101-126">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ff101-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="ff101-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ff101-127">DisplayName</span></span>
  <span data-ttu-id="ff101-128">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ff101-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="ff101-129">Właściwość tylko do odczytu, która pobiera ciąg, który zawiera nazwę wyświetlaną tego pliku.</span><span class="sxs-lookup"><span data-stu-id="ff101-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="ff101-130">Nazwa jest wyświetlana na **pliku** kartę w górnej części edytora.</span><span class="sxs-lookup"><span data-stu-id="ff101-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="ff101-131">Obecność gwiazdkę \( \* \) na końcu nazwy wskazuje, że plik zawiera zmiany, które nie zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="ff101-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a><span data-ttu-id="ff101-132">Edytor</span><span class="sxs-lookup"><span data-stu-id="ff101-132">Editor</span></span>
  <span data-ttu-id="ff101-133">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ff101-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff101-134">Właściwość tylko do odczytu, która pobiera [obiekt](The-ISEEditor-Object.md) używanego do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="ff101-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a><span data-ttu-id="ff101-135">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="ff101-135">Encoding</span></span>
  <span data-ttu-id="ff101-136">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ff101-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff101-137">Właściwość tylko do odczytu, która pobiera kodowanie oryginalnego pliku.</span><span class="sxs-lookup"><span data-stu-id="ff101-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="ff101-138">Jest to **System.Text.Encoding** obiektu.</span><span class="sxs-lookup"><span data-stu-id="ff101-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a><span data-ttu-id="ff101-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="ff101-139">FullPath</span></span>
  <span data-ttu-id="ff101-140">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ff101-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff101-141">Właściwość tylko do odczytu, która pobiera ciąg, który określa pełną ścieżkę otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="ff101-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a><span data-ttu-id="ff101-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="ff101-142">IsSaved</span></span>
  <span data-ttu-id="ff101-143">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ff101-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff101-144">Właściwości typu Boolean tylko do odczytu, która zwraca **$true** Jeśli plik został zapisany po ostatniej modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="ff101-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a><span data-ttu-id="ff101-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="ff101-145">IsUntitled</span></span>
  <span data-ttu-id="ff101-146">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ff101-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff101-147">Właściwości tylko do odczytu, która zwraca **$true** Jeśli plik nigdy nie został podany tytuł.</span><span class="sxs-lookup"><span data-stu-id="ff101-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="ff101-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff101-148">See Also</span></span>
- [<span data-ttu-id="ff101-149">ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="ff101-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="ff101-150">Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="ff101-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="ff101-151">Dotyczące modelu obiektów programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ff101-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="ff101-152">Hierarchia modelu obiektów ISE</span><span class="sxs-lookup"><span data-stu-id="ff101-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
