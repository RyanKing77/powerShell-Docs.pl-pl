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
# <a name="the-isefile-object"></a><span data-ttu-id="f455a-103">Obiekt ISEFile</span><span class="sxs-lookup"><span data-stu-id="f455a-103">The ISEFile Object</span></span>

<span data-ttu-id="f455a-104">**ISEFile** obiekt reprezentuje plików w Windows PowerShell® zintegrowane Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f455a-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="f455a-105">Jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="f455a-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="f455a-106">Ten temat zawiera element członkowski metod i właściwości elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f455a-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="f455a-107">**$PsISE.CurrentFile** i pliki w kolekcji plików w kartę programu PowerShell są wszystkie wystąpienia klasy Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="f455a-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="f455a-108">Metody</span><span class="sxs-lookup"><span data-stu-id="f455a-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="f455a-109">Zapisz\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="f455a-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="f455a-110">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="f455a-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f455a-111">Zapisuje plik na dysku.</span><span class="sxs-lookup"><span data-stu-id="f455a-111">Saves the file to disk.</span></span>

<span data-ttu-id="f455a-112">**\[saveEncoding\]**  — wartość opcjonalna [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalny znak kodowanie parametr służący do zapisanego pliku.</span><span class="sxs-lookup"><span data-stu-id="f455a-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="f455a-113">Wartość domyślna to **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="f455a-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="f455a-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="f455a-114">Exceptions</span></span>

- <span data-ttu-id="f455a-115">**System.IO.IOException**: Nie można zapisać pliku.</span><span class="sxs-lookup"><span data-stu-id="f455a-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="f455a-116">Zapisz jako\(nazwy pliku, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="f455a-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="f455a-117">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="f455a-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f455a-118">Zapisuje plik przy użyciu określonej nazwy pliku i kodowanie.</span><span class="sxs-lookup"><span data-stu-id="f455a-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="f455a-119">**Nazwa pliku** -String nazwa ma być używany do zapisania pliku.</span><span class="sxs-lookup"><span data-stu-id="f455a-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="f455a-120">**\[saveEncoding\]**  — wartość opcjonalna [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalny znak kodowanie parametr służący do zapisanego pliku.</span><span class="sxs-lookup"><span data-stu-id="f455a-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="f455a-121">Wartość domyślna to **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="f455a-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="f455a-122">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="f455a-122">Exceptions</span></span>

- <span data-ttu-id="f455a-123">**System.ArgumentNullException**: **Filename** parametr ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="f455a-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="f455a-124">**System.ArgumentException**: **Filename** parametr jest pusty.</span><span class="sxs-lookup"><span data-stu-id="f455a-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="f455a-125">**System.IO.IOException**: Nie można zapisać pliku.</span><span class="sxs-lookup"><span data-stu-id="f455a-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="f455a-126">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f455a-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="f455a-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f455a-127">DisplayName</span></span>

<span data-ttu-id="f455a-128">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="f455a-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f455a-129">Właściwość tylko do odczytu, która pobiera ciąg, który zawiera nazwę wyświetlaną tego pliku.</span><span class="sxs-lookup"><span data-stu-id="f455a-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="f455a-130">Nazwa jest wyświetlana na **pliku** kartę w górnej części edytora.</span><span class="sxs-lookup"><span data-stu-id="f455a-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="f455a-131">Obecność gwiazdki \( \* \) na końcu nazwy wskazuje, że plik ma zmiany, które nie zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="f455a-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="f455a-132">Edytor</span><span class="sxs-lookup"><span data-stu-id="f455a-132">Editor</span></span>

<span data-ttu-id="f455a-133">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="f455a-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f455a-134">Właściwość tylko do odczytu, która pobiera [obiekt edytora](The-ISEEditor-Object.md) używany dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="f455a-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="f455a-135">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="f455a-135">Encoding</span></span>

<span data-ttu-id="f455a-136">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="f455a-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f455a-137">Właściwość tylko do odczytu, oryginalnym kodowanie pliku.</span><span class="sxs-lookup"><span data-stu-id="f455a-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="f455a-138">Jest to **System.Text.Encoding** obiektu.</span><span class="sxs-lookup"><span data-stu-id="f455a-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="f455a-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="f455a-139">FullPath</span></span>

<span data-ttu-id="f455a-140">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="f455a-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f455a-141">Właściwość tylko do odczytu, która pobiera ciąg, który określa pełną ścieżkę otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="f455a-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="f455a-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="f455a-142">IsSaved</span></span>

<span data-ttu-id="f455a-143">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="f455a-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f455a-144">Właściwość logiczna przeznaczony tylko do odczytu, która zwraca **$true** Jeśli plik został zapisany po ostatniej modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f455a-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="f455a-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="f455a-145">IsUntitled</span></span>

<span data-ttu-id="f455a-146">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="f455a-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f455a-147">Właściwość tylko do odczytu, która zwraca **$true** Jeśli plik nigdy nie został podany tytuł.</span><span class="sxs-lookup"><span data-stu-id="f455a-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="f455a-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f455a-148">See Also</span></span>

- [<span data-ttu-id="f455a-149">The ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="f455a-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="f455a-150">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f455a-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f455a-151">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="f455a-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
