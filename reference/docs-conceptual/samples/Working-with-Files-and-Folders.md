---
ms.date: 06/05/2017
keywords: PowerShell, polecenie cmdlet
title: Praca z plikami i folderami
ms.openlocfilehash: 743e261d2f5e8bfa39f2731fca7fea6e5678c711
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215521"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="2bd37-103">Praca z plikami i folderami</span><span class="sxs-lookup"><span data-stu-id="2bd37-103">Working with Files and Folders</span></span>

<span data-ttu-id="2bd37-104">Nawigowanie po dyskach programu Windows PowerShell i manipulowanie elementami na nich jest podobne do manipulowania plikami i folderami na dyskach fizycznych systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2bd37-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="2bd37-105">W tej sekcji omówiono sposób postępowania z określonymi zadaniami manipulowania plikami i folderami przy użyciu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2bd37-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="2bd37-106">Wyświetlanie listy wszystkich plików i folderów w folderze</span><span class="sxs-lookup"><span data-stu-id="2bd37-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="2bd37-107">Wszystkie elementy można pobrać bezpośrednio w folderze za pomocą polecenia **GET-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="2bd37-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="2bd37-108">Dodaj opcjonalny parametr **Force** , aby wyświetlić elementy ukryte lub systemowe.</span><span class="sxs-lookup"><span data-stu-id="2bd37-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="2bd37-109">Na przykład to polecenie wyświetla bezpośrednią zawartość dysku C programu Windows PowerShell, który jest taki sam jak dysk fizyczny systemu Windows C):</span><span class="sxs-lookup"><span data-stu-id="2bd37-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="2bd37-110">Polecenie wyświetla tylko bezpośrednio zawarte elementy, podobnie jak przy użyciu polecenia **dir** cmd. exe lub **ls** w powłoce systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="2bd37-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="2bd37-111">Aby wyświetlić zawarte elementy, należy również określić parametr **-rekursywny** .</span><span class="sxs-lookup"><span data-stu-id="2bd37-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="2bd37-112">(Może to potrwać bardzo długo.) Aby wyświetlić listę wszystkich elementów na dysku C:</span><span class="sxs-lookup"><span data-stu-id="2bd37-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="2bd37-113">Polecenie **GET-ChildItem** umożliwia filtrowanie elementów przy użyciu ich **ścieżki**, **filtrowania**, **dołączania**i **wykluczania** parametrów, ale są one zwykle oparte tylko na nazwie.</span><span class="sxs-lookup"><span data-stu-id="2bd37-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="2bd37-114">Można wykonać skomplikowane filtrowanie na podstawie innych właściwości elementów przy użyciu polecenia **WHERE-Object**.</span><span class="sxs-lookup"><span data-stu-id="2bd37-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="2bd37-115">Poniższe polecenie odnajduje wszystkie pliki wykonywalne w folderze Program Files, które zostały ostatnio zmodyfikowane po 1 października 2005 i które nie są mniejsze niż 1 megabajt ani większe niż 10 megabajtów:</span><span class="sxs-lookup"><span data-stu-id="2bd37-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="2bd37-116">Kopiowanie plików i folderów</span><span class="sxs-lookup"><span data-stu-id="2bd37-116">Copying Files and Folders</span></span>

<span data-ttu-id="2bd37-117">Kopiowanie jest wykonywane z **elementem Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="2bd37-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="2bd37-118">Następujące polecenie tworzy kopię zapasową c\\: Boot. ini do C\\: Boot. bak:</span><span class="sxs-lookup"><span data-stu-id="2bd37-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="2bd37-119">Jeśli plik docelowy już istnieje, próba kopiowania nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="2bd37-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="2bd37-120">Aby zastąpić istniejące miejsce docelowe, użyj parametru **Force** :</span><span class="sxs-lookup"><span data-stu-id="2bd37-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="2bd37-121">To polecenie działa nawet wtedy, gdy lokalizacja docelowa jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="2bd37-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="2bd37-122">Kopiowanie folderów działa w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="2bd37-122">Folder copying works the same way.</span></span> <span data-ttu-id="2bd37-123">To polecenie kopiuje folder c\\: temp\\TEST1 do nowego folderu c:\\temp\\DeleteMe rekursywnie:</span><span class="sxs-lookup"><span data-stu-id="2bd37-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="2bd37-124">Możesz również skopiować wybrane elementy.</span><span class="sxs-lookup"><span data-stu-id="2bd37-124">You can also copy a selection of items.</span></span> <span data-ttu-id="2bd37-125">Następujące polecenie kopiuje wszystkie pliki txt zawarte w dowolnym miejscu w c:\\dane do c:\\tekst\\tymczasowy:</span><span class="sxs-lookup"><span data-stu-id="2bd37-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="2bd37-126">Można nadal używać innych narzędzi do wykonywania kopii systemu plików.</span><span class="sxs-lookup"><span data-stu-id="2bd37-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="2bd37-127">XCOPY, ROBOCOPY i COM obiektów, takich jak **Scripting. FileSystemObject,** All Pracuj w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2bd37-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="2bd37-128">Na przykład można użyć klasy **com scripting** hosta skryptów systemu Windows, aby utworzyć kopię zapasową c\\: Boot. ini do c\\: Boot. bak:</span><span class="sxs-lookup"><span data-stu-id="2bd37-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="2bd37-129">Tworzenie plików i folderów</span><span class="sxs-lookup"><span data-stu-id="2bd37-129">Creating Files and Folders</span></span>

<span data-ttu-id="2bd37-130">Tworzenie nowych elementów działa tak samo we wszystkich dostawcach środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2bd37-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="2bd37-131">Jeśli dostawca programu Windows PowerShell ma więcej niż jeden typ elementu — na przykład dostawca systemu plików Windows PowerShell rozróżnia katalogi i pliki — należy określić typ elementu.</span><span class="sxs-lookup"><span data-stu-id="2bd37-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="2bd37-132">To polecenie tworzy nowy folder C:\\temp\\nowy folder:</span><span class="sxs-lookup"><span data-stu-id="2bd37-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="2bd37-133">To polecenie tworzy nowy pusty plik C:\\temp\\nowy folder\\plik. txt</span><span class="sxs-lookup"><span data-stu-id="2bd37-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="2bd37-134">Usuwanie wszystkich plików i folderów w folderze</span><span class="sxs-lookup"><span data-stu-id="2bd37-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="2bd37-135">Można usunąć zawarte elementy za pomocą polecenia **Remove-Item**, ale zostanie wyświetlony monit o potwierdzenie usunięcia, jeśli element zawiera coś innego.</span><span class="sxs-lookup"><span data-stu-id="2bd37-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="2bd37-136">Na przykład w przypadku próby usunięcia folderu C:\\temp\\DeleteMe zawierającego inne elementy program Windows PowerShell wyświetli monit o potwierdzenie przed usunięciem folderu:</span><span class="sxs-lookup"><span data-stu-id="2bd37-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="2bd37-137">Jeśli nie chcesz otrzymywać monitów dla każdego zawartego elementu, określ parametr **rekursywnie** :</span><span class="sxs-lookup"><span data-stu-id="2bd37-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a><span data-ttu-id="2bd37-138">Mapowanie folderu lokalnego jako dysku</span><span class="sxs-lookup"><span data-stu-id="2bd37-138">Mapping a Local Folder as a drive</span></span>

<span data-ttu-id="2bd37-139">Możesz również zmapować folder lokalny przy użyciu polecenia **New-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="2bd37-139">You can also map a local folder, using the **New-PSDrive** command.</span></span> <span data-ttu-id="2bd37-140">Następujące polecenie tworzy dysk lokalny P: root w katalogu plików programu lokalnego, widoczny tylko w sesji programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="2bd37-140">The following command creates a local drive P: rooted in the local Program Files directory, visible only from the PowerShell session:</span></span>

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

<span data-ttu-id="2bd37-141">Podobnie jak w przypadku dysków sieciowych dyski mapowane w programie Windows PowerShell są natychmiast widoczne dla powłoki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2bd37-141">Just as with network drives, drives mapped within Windows PowerShell are immediately visible to the Windows PowerShell shell.</span></span>
<span data-ttu-id="2bd37-142">Aby można było utworzyć mapowany dysk widoczny w Eksploratorze plików, jest wymagany parametr **-utrwalanie** .</span><span class="sxs-lookup"><span data-stu-id="2bd37-142">In order to create a mapped drive visible from File Explorer, the parameter **-Persist** is needed.</span></span> <span data-ttu-id="2bd37-143">Jednak w przypadku utrwalania mogą być używane tylko ścieżki zdalne.</span><span class="sxs-lookup"><span data-stu-id="2bd37-143">However, only remote paths can be used with Persist.</span></span>


## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="2bd37-144">Odczytywanie pliku tekstowego do tablicy</span><span class="sxs-lookup"><span data-stu-id="2bd37-144">Reading a Text File into an Array</span></span>

<span data-ttu-id="2bd37-145">Jeden z najpopularniejszych formatów przechowywania danych tekstowych znajduje się w pliku z osobnymi wierszami traktowanymi jako różne elementy danych.</span><span class="sxs-lookup"><span data-stu-id="2bd37-145">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="2bd37-146">Za pomocą polecenia cmdlet **Get-Content** można odczytać cały plik w jednym kroku, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="2bd37-146">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="2bd37-147">Polecenie **Get-Content** już traktuje dane odczytane z pliku jako tablicę z jednym elementem na wiersz zawartości pliku.</span><span class="sxs-lookup"><span data-stu-id="2bd37-147">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="2bd37-148">Możesz to potwierdzić, sprawdzając **Długość** zwróconej zawartości:</span><span class="sxs-lookup"><span data-stu-id="2bd37-148">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="2bd37-149">To polecenie jest najbardziej przydatne do bezpośredniego pobierania list informacji do programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2bd37-149">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="2bd37-150">Na przykład można przechowywać listę nazw komputerów lub adresów IP w pliku C:\\temp\\domainMembers. txt, z jedną nazwą w każdym wierszu pliku.</span><span class="sxs-lookup"><span data-stu-id="2bd37-150">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="2bd37-151">Aby pobrać zawartość pliku i umieścić je w zmiennej **$Computers**, można użyć **Get-Content** :</span><span class="sxs-lookup"><span data-stu-id="2bd37-151">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="2bd37-152">**$Computers** jest teraz tablicą zawierającą nazwę komputera w każdym elemencie.</span><span class="sxs-lookup"><span data-stu-id="2bd37-152">**$Computers** is now an array containing a computer name in each element.</span></span>
