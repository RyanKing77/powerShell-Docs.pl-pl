---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 24549720b8bc35435882533b0eb138de432ede65
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320877"
---
# <a name="the-isefile-object"></a><span data-ttu-id="865f8-103">Obiekt ISEFile</span><span class="sxs-lookup"><span data-stu-id="865f8-103">The ISEFile Object</span></span>

<span data-ttu-id="865f8-104">**ISEFile** obiekt reprezentuje plików w Windows PowerShell® zintegrowane Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="865f8-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="865f8-105">Jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="865f8-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="865f8-106">Ten temat zawiera element członkowski metod i właściwości elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="865f8-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="865f8-107">**$PsISE.CurrentFile** i pliki w kolekcji plików w kartę programu PowerShell są wszystkie wystąpienia klasy Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="865f8-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="865f8-108">Metody</span><span class="sxs-lookup"><span data-stu-id="865f8-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="865f8-109">Zapisz\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="865f8-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="865f8-110">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="865f8-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="865f8-111">Zapisuje plik na dysku.</span><span class="sxs-lookup"><span data-stu-id="865f8-111">Saves the file to disk.</span></span>

<span data-ttu-id="865f8-112">**\[saveEncoding\]**  — wartość opcjonalna [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalny znak kodowanie parametr służący do zapisanego pliku.</span><span class="sxs-lookup"><span data-stu-id="865f8-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="865f8-113">Wartość domyślna to **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="865f8-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="865f8-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="865f8-114">Exceptions</span></span>

- <span data-ttu-id="865f8-115">**System.IO.IOException**: nie można zapisać pliku.</span><span class="sxs-lookup"><span data-stu-id="865f8-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="865f8-116">Zapisz jako\(nazwy pliku, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="865f8-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="865f8-117">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="865f8-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="865f8-118">Zapisuje plik przy użyciu określonej nazwy pliku i kodowanie.</span><span class="sxs-lookup"><span data-stu-id="865f8-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="865f8-119">**Nazwa pliku** -String nazwa ma być używany do zapisania pliku.</span><span class="sxs-lookup"><span data-stu-id="865f8-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="865f8-120">**\[saveEncoding\]**  — wartość opcjonalna [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcjonalny znak kodowanie parametr służący do zapisanego pliku.</span><span class="sxs-lookup"><span data-stu-id="865f8-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="865f8-121">Wartość domyślna to **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="865f8-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="865f8-122">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="865f8-122">Exceptions</span></span>

- <span data-ttu-id="865f8-123">**System.ArgumentNullException**: **filename** parametr ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="865f8-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="865f8-124">**System.ArgumentException**: **filename** parametr jest pusty.</span><span class="sxs-lookup"><span data-stu-id="865f8-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="865f8-125">**System.IO.IOException**: nie można zapisać pliku.</span><span class="sxs-lookup"><span data-stu-id="865f8-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="865f8-126">Właściwości</span><span class="sxs-lookup"><span data-stu-id="865f8-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="865f8-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="865f8-127">DisplayName</span></span>

<span data-ttu-id="865f8-128">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="865f8-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="865f8-129">Właściwość tylko do odczytu, która pobiera ciąg, który zawiera nazwę wyświetlaną tego pliku.</span><span class="sxs-lookup"><span data-stu-id="865f8-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="865f8-130">Nazwa jest wyświetlana na **pliku** kartę w górnej części edytora.</span><span class="sxs-lookup"><span data-stu-id="865f8-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="865f8-131">Obecność gwiazdki \( \* \) na końcu nazwy wskazuje, że plik ma zmiany, które nie zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="865f8-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="865f8-132">Edytor</span><span class="sxs-lookup"><span data-stu-id="865f8-132">Editor</span></span>

<span data-ttu-id="865f8-133">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="865f8-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="865f8-134">Właściwość tylko do odczytu, która pobiera [obiekt edytora](The-ISEEditor-Object.md) używany dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="865f8-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="865f8-135">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="865f8-135">Encoding</span></span>

<span data-ttu-id="865f8-136">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="865f8-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="865f8-137">Właściwość tylko do odczytu, oryginalnym kodowanie pliku.</span><span class="sxs-lookup"><span data-stu-id="865f8-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="865f8-138">Jest to **System.Text.Encoding** obiektu.</span><span class="sxs-lookup"><span data-stu-id="865f8-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="865f8-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="865f8-139">FullPath</span></span>

<span data-ttu-id="865f8-140">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="865f8-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="865f8-141">Właściwość tylko do odczytu, która pobiera ciąg, który określa pełną ścieżkę otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="865f8-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="865f8-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="865f8-142">IsSaved</span></span>

<span data-ttu-id="865f8-143">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="865f8-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="865f8-144">Właściwość logiczna przeznaczony tylko do odczytu, która zwraca **$true** Jeśli plik został zapisany po ostatniej modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="865f8-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="865f8-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="865f8-145">IsUntitled</span></span>

<span data-ttu-id="865f8-146">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="865f8-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="865f8-147">Właściwość tylko do odczytu, która zwraca **$true** Jeśli plik nigdy nie został podany tytuł.</span><span class="sxs-lookup"><span data-stu-id="865f8-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="865f8-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="865f8-148">See Also</span></span>

- [<span data-ttu-id="865f8-149">ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="865f8-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="865f8-150">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="865f8-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="865f8-151">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="865f8-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)