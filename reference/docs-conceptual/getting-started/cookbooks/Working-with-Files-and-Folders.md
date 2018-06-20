---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z plikami i folderami
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 6b1fcd438570c8708aa87e4b213f33474921d5f8
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201023"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="53392-103">Praca z plikami i folderami</span><span class="sxs-lookup"><span data-stu-id="53392-103">Working with Files and Folders</span></span>

<span data-ttu-id="53392-104">Nawigować przez dyski środowiska Windows PowerShell i operowanie nimi elementów na nich jest podobny do manipulowania plików i folderów na dyskach fizycznych systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="53392-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="53392-105">W tej sekcji omówiono sposób postępowania z określonych plików i folderów zadań manipulowania przy użyciu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53392-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

### <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="53392-106">Wyświetlanie listy wszystkich plików i folderów w folderze</span><span class="sxs-lookup"><span data-stu-id="53392-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="53392-107">Wszystkie elementy można uzyskać bezpośrednio w folderze, za pomocą **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="53392-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="53392-108">Dodaj opcjonalny **życie** parametru do wyświetlania ukryte lub elementów systemu.</span><span class="sxs-lookup"><span data-stu-id="53392-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="53392-109">Na przykład to polecenie wyświetla zawartość bezpośredniego systemu Windows PowerShell dysk C (która jest taka sama jak dysk fizyczny w systemie Windows C):</span><span class="sxs-lookup"><span data-stu-id="53392-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="53392-110">Polecenie wyświetla tylko bezpośrednio zawartych w niej elementów, podobnie jak przy użyciu jego Cmd.exe **DIR** polecenia lub **ls** w powłoce systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="53392-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="53392-111">Aby pokazać zawartych w niej elementów, należy określić **-Recurse** również parametr.</span><span class="sxs-lookup"><span data-stu-id="53392-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="53392-112">(To może potrwać bardzo długo). Aby wyświetlić listę wszystkich elementów na dysku C:</span><span class="sxs-lookup"><span data-stu-id="53392-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="53392-113">**Get-ChildItem** można filtrować elementy z jego **ścieżki**, **filtru**, **Include**, i **wykluczyć** parametrów, ale te są zwykle tylko na podstawie nazwy.</span><span class="sxs-lookup"><span data-stu-id="53392-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="53392-114">Można wykonać złożone filtrowanie na podstawie innych właściwości elementów za pomocą **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="53392-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="53392-115">Poniższe polecenie umożliwia znalezienie wszystkich plików wykonywalnych w folderze Program Files, który ostatniej modyfikacji po 1 października 2005 i które nie są mniejsze niż 1 megabajt ani większa niż 10 megabajtów:</span><span class="sxs-lookup"><span data-stu-id="53392-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a><span data-ttu-id="53392-116">Kopiowanie plików i folderów</span><span class="sxs-lookup"><span data-stu-id="53392-116">Copying Files and Folders</span></span>

<span data-ttu-id="53392-117">Kopiowanie wykonuje się za pomocą **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="53392-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="53392-118">Następujące polecenie tworzy kopię zapasową C:\\boot.ini do folderu C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="53392-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="53392-119">Jeśli plik docelowy już istnieje, próba skopiowania zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="53392-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="53392-120">Aby zastąpić istniejące docelowego, użyj **życie** parametru:</span><span class="sxs-lookup"><span data-stu-id="53392-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="53392-121">To polecenie działa nawet wtedy, gdy lokalizacją docelową jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="53392-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="53392-122">Kopiowanie folderu działa tak samo.</span><span class="sxs-lookup"><span data-stu-id="53392-122">Folder copying works the same way.</span></span> <span data-ttu-id="53392-123">To polecenie powoduje skopiowanie folderu C:\\temp\\test1 do nowego folderu C:\\temp\\rekursywnie DeleteMe:</span><span class="sxs-lookup"><span data-stu-id="53392-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="53392-124">Ponadto można kopiować zaznaczenia elementów.</span><span class="sxs-lookup"><span data-stu-id="53392-124">You can also copy a selection of items.</span></span> <span data-ttu-id="53392-125">Polecenie kopiuje wszystkie pliki .txt zawarte w dowolnym miejscu w c:\\danych do folderu c:\\temp\\tekst:</span><span class="sxs-lookup"><span data-stu-id="53392-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="53392-126">Można nadal używać innych narzędzi do wykonywania kopii systemu plików.</span><span class="sxs-lookup"><span data-stu-id="53392-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="53392-127">XCOPY ROBOCOPY i COM obiekty, takie jak **Scripting.FileSystemObject,** wszystkie pracy w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53392-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="53392-128">Na przykład można użyć Host skryptów systemu Windows **Scripting.FileSystem COM** klasa do tworzenia kopii zapasowych C:\\boot.ini do folderu C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="53392-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

### <a name="creating-files-and-folders"></a><span data-ttu-id="53392-129">Tworzenie plików i folderów</span><span class="sxs-lookup"><span data-stu-id="53392-129">Creating Files and Folders</span></span>

<span data-ttu-id="53392-130">Tworzenie nowych elementów działa tak samo na wszystkich dostawców środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53392-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="53392-131">Jeśli dostawca programu Windows PowerShell zawiera więcej niż jeden typ elementu — na przykład dostawcy środowiska Windows PowerShell w systemie plików rozróżnia katalogów i plików — należy określić typ elementu.</span><span class="sxs-lookup"><span data-stu-id="53392-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="53392-132">To polecenie tworzy nowy folder C:\\temp\\nowego folderu:</span><span class="sxs-lookup"><span data-stu-id="53392-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="53392-133">To polecenie tworzy nowy pusty plik C:\\temp\\nowy Folder\\plik.txt</span><span class="sxs-lookup"><span data-stu-id="53392-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="53392-134">Usunięcie wszystkich plików i folderów w folderze</span><span class="sxs-lookup"><span data-stu-id="53392-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="53392-135">Można usunąć zawartych w niej elementów przy użyciu **Usuń element**, ale pojawi się monit o potwierdzenie usunięcia, jeśli element zawiera coś innego.</span><span class="sxs-lookup"><span data-stu-id="53392-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="53392-136">Na przykład, jeśli próba usunięcia folderu C:\\temp\\DeleteMe, który zawiera inne elementy programu Windows PowerShell monituje o potwierdzenie przed usunięciem folderu:</span><span class="sxs-lookup"><span data-stu-id="53392-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="53392-137">Jeśli nie zostanie wyświetlony monit o poszczególnych elementów zawartych w niej, określ **Recurse** parametru:</span><span class="sxs-lookup"><span data-stu-id="53392-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="53392-138">Mapowanie folderu lokalnego jako dostępny dysk systemu Windows</span><span class="sxs-lookup"><span data-stu-id="53392-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="53392-139">Folder lokalny, można również mapować przy użyciu **subst** polecenia.</span><span class="sxs-lookup"><span data-stu-id="53392-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="53392-140">Poniższe polecenie tworzy dysk lokalny, który P: umieszczone w lokalnym katalogu Program Files:</span><span class="sxs-lookup"><span data-stu-id="53392-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="53392-141">Tak jak w przypadku dysków sieciowych dyski mapowane w przy użyciu programu Windows PowerShell **subst** są od razu widoczne powłoki Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53392-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

### <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="53392-142">Odczytywanie pliku tekstowego do tablicy</span><span class="sxs-lookup"><span data-stu-id="53392-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="53392-143">Jest jednym z formatów magazynu częściej stosowana w przypadku danych tekstowych w pliku z osobnych wierszach traktowane jako elementy danych distinct.</span><span class="sxs-lookup"><span data-stu-id="53392-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="53392-144">**Pobrania zawartości** polecenia cmdlet można odczytać całego pliku w jednym kroku, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="53392-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="53392-145">**Get-Content** już traktuje dane odczytane z pliku jako tablicę o jeden element w jednym wierszu zawartości pliku.</span><span class="sxs-lookup"><span data-stu-id="53392-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="53392-146">Można to potwierdzić, sprawdzając **długość** zwrócony zawartości:</span><span class="sxs-lookup"><span data-stu-id="53392-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="53392-147">To polecenie jest najbardziej przydatny w przypadku uzyskiwania listy informacji w programie Windows PowerShell bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="53392-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="53392-148">Na przykład może przechowywać listę nazw komputerów lub adresy IP w pliku C:\\temp\\domainMembers.txt o nazwie jeden w każdym wierszu pliku.</span><span class="sxs-lookup"><span data-stu-id="53392-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="53392-149">Można użyć **pobrania zawartości** można pobrać zawartości pliku i umieść je w zmiennej **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="53392-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="53392-150">**$Computers** jest teraz tablicę zawierającą nazwę komputera w każdym elemencie.</span><span class="sxs-lookup"><span data-stu-id="53392-150">**$Computers** is now an array containing a computer name in each element.</span></span>
