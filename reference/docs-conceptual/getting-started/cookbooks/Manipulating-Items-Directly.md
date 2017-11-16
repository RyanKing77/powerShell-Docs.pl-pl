---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Bezpośrednie manipulowanie elementów"
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: d9aa95dcb0da2e8203cbe32d64b95bf33d914166
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="29735-103">Bezpośrednie manipulowanie elementów</span><span class="sxs-lookup"><span data-stu-id="29735-103">Manipulating Items Directly</span></span>
<span data-ttu-id="29735-104">Elementy, które widać w dyski środowiska Windows PowerShell, takie jak pliki i foldery na dyskach systemu plików i kluczy rejestru na dyskach rejestru programu Windows PowerShell, są nazywane *elementów* w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29735-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="29735-105">Polecenia cmdlet do pracy z nimi elementów ma rzeczownikiem **elementu** w nazwach.</span><span class="sxs-lookup"><span data-stu-id="29735-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="29735-106">Dane wyjściowe **Get-Command - rzeczownik elementu** polecenia zawiera dziewięć poleceń cmdlet programu Windows PowerShell elementu.</span><span class="sxs-lookup"><span data-stu-id="29735-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### <a name="creating-new-items-new-item"></a><span data-ttu-id="29735-107">Tworzenie nowych elementów (nowy element)</span><span class="sxs-lookup"><span data-stu-id="29735-107">Creating New Items (New-Item)</span></span>
<span data-ttu-id="29735-108">Aby utworzyć nowy element w systemie plików, użyj **nowy element** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29735-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="29735-109">Obejmują **ścieżki** parametr o ścieżkę do elementu i **ItemType** parametru o wartości "pliku" lub "directory".</span><span class="sxs-lookup"><span data-stu-id="29735-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="29735-110">Na przykład, aby utworzyć nowy katalog o nazwie "New.Directory"in dysku C:\\katalogu Temp, wpisz:</span><span class="sxs-lookup"><span data-stu-id="29735-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="29735-111">Aby utworzyć plik, zmień wartość **ItemType** parametr "file".</span><span class="sxs-lookup"><span data-stu-id="29735-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="29735-112">Na przykład aby utworzyć plik o nazwie "więc Plik1.txt" w katalogu New.Directory, wpisz:</span><span class="sxs-lookup"><span data-stu-id="29735-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="29735-113">Ta sama metoda umożliwia utworzenie nowego klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="29735-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="29735-114">Klucz rejestru jest w rzeczywistości ułatwiają tworzenie, ponieważ klucz jest tylko typ elementu w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="29735-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="29735-115">(Element są wpisy rejestru *właściwości*.) Na przykład aby utworzyć klucz o nazwie "_testowy" w podkluczu CurrentVersion, wpisz:</span><span class="sxs-lookup"><span data-stu-id="29735-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="29735-116">Podczas wpisywania ścieżki rejestru, należy uwzględnić dwukropkiem (**:**) w programie Windows PowerShell dysków nazwy, HKLM: i HKCU:.</span><span class="sxs-lookup"><span data-stu-id="29735-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="29735-117">Bez dwukropkiem programu Windows PowerShell nie może rozpoznać nazwę dysku w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="29735-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

### <a name="why-registry-values-are-not-items"></a><span data-ttu-id="29735-118">Dlaczego wartości rejestru nie są elementami</span><span class="sxs-lookup"><span data-stu-id="29735-118">Why Registry Values are not Items</span></span>
<span data-ttu-id="29735-119">Jeśli używasz **Get-ChildItem** polecenia cmdlet, aby znaleźć te elementy w kluczu rejestru, nie będzie widoczna wpisy rejestru rzeczywiste lub ich wartości.</span><span class="sxs-lookup"><span data-stu-id="29735-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="29735-120">Na przykład klucz rejestru **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion\\Uruchom** zwykle zawiera wiele wpisów rejestru reprezentują aplikacje, które są uruchamiane podczas uruchamiania systemu.</span><span class="sxs-lookup"><span data-stu-id="29735-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="29735-121">Jednak jeśli używasz **Get-ChildItem** do wyszukania elementów podrzędnych w kluczu, zobaczysz jest **OptionalComponents** podkluczy klucza:</span><span class="sxs-lookup"><span data-stu-id="29735-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="29735-122">Chociaż jest wygodne traktować wpisy rejestru jako elementy, nie można określić ścieżki do wpisu rejestru w sposób, który zapewnia, że jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="29735-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="29735-123">Notacja ścieżki nie rozróżnia podklucz rejestru o nazwie **Uruchom** i **(domyślna)** wpis rejestru w **Uruchom** podkluczu.</span><span class="sxs-lookup"><span data-stu-id="29735-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="29735-124">Ponadto ponieważ z rejestru wpis nazwy mogą zawierać ukośnika odwrotnego (**\\**), gdyby wpisy regsitry elementów, a następnie notacji ścieżki nie można użyć do odróżnienia wpis rejestru o nazwie  **Windows\\CurrentVersion\\Uruchom** z podklucza, który znajduje się w tej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="29735-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if regsitry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

### <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="29735-125">Zmienianie nazw istniejących elementów (zmiana nazwy elementu)</span><span class="sxs-lookup"><span data-stu-id="29735-125">Renaming Existing Items (Rename-Item)</span></span>
<span data-ttu-id="29735-126">Aby zmienić nazwę pliku lub folderu, użyj **zmiany nazwy elementu** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29735-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="29735-127">Polecenie zmienia nazwę **więc Plik1.txt** pliku **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="29735-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="29735-128">**Zmiany nazwy elementu** polecenia cmdlet można zmienić nazwę pliku lub folderu, ale nie można przenieść elementu.</span><span class="sxs-lookup"><span data-stu-id="29735-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="29735-129">Polecenie nie powiedzie się, ponieważ próbuje on przenieść go z katalogu New.Directory do katalogu Temp.</span><span class="sxs-lookup"><span data-stu-id="29735-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a><span data-ttu-id="29735-130">Przenoszenie elementów (Przenieś element)</span><span class="sxs-lookup"><span data-stu-id="29735-130">Moving Items (Move-Item)</span></span>
<span data-ttu-id="29735-131">Aby przenieść plik lub folder, użyj **Przenieś element** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29735-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="29735-132">Na przykład następujące polecenie z dysku C: Przenosi katalogu New.Directory\\katalogu tymczasowego w katalogu głównym dysku C:.</span><span class="sxs-lookup"><span data-stu-id="29735-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="29735-133">Aby sprawdzić, czy element został przeniesiony, obejmują **PassThru** parametr **Przenieś element** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29735-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="29735-134">Bez **Passthru**, **Przenieś element** polecenie cmdlet nie wyświetla żadnych wyników.</span><span class="sxs-lookup"><span data-stu-id="29735-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a><span data-ttu-id="29735-135">Kopiowanie elementów (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="29735-135">Copying Items (Copy-Item)</span></span>
<span data-ttu-id="29735-136">Jeśli znasz operacje kopiowania w innych powłoki, może się okazać zachowanie **Copy-Item** polecenia cmdlet programu Windows PowerShell umożliwia być nietypowe.</span><span class="sxs-lookup"><span data-stu-id="29735-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="29735-137">Podczas kopiowania elementu z jednej lokalizacji do innej, domyślnie Copy-Item nie kopiuje jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="29735-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="29735-138">Na przykład, jeśli kopiujesz **New.Directory** z dysku C: do dysku C: katalogu\\katalogu temp, polecenie powiedzie się, ale nie są kopiowane pliki w katalogu New.Directory.</span><span class="sxs-lookup"><span data-stu-id="29735-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="29735-139">Podczas wyświetlania zawartości **C:\\temp\\New.Directory**, można zauważyć, że nie zawiera on plików:</span><span class="sxs-lookup"><span data-stu-id="29735-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="29735-140">Dlaczego nie **Copy-Item** polecenia cmdlet skopiuj zawartość do nowej lokalizacji?</span><span class="sxs-lookup"><span data-stu-id="29735-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="29735-141">**Copy-Item** polecenia cmdlet zaprojektowano tak, aby wartość była ogólna; nie jest tylko do kopiowania plików i folderów.</span><span class="sxs-lookup"><span data-stu-id="29735-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="29735-142">Ponadto nawet w przypadku kopiowania plików i folderów, możesz skopiować tylko kontenera, a nie do elementów.</span><span class="sxs-lookup"><span data-stu-id="29735-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="29735-143">Aby skopiować całą zawartość folderu, obejmują **Recurse** parametr **Copy-Item** polecenia cmdlet w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="29735-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="29735-144">Jeśli zostały już skopiowane katalogu bez jego zawartość, Dodaj **życie** parametr, który służy do zastępowania pustym folderze.</span><span class="sxs-lookup"><span data-stu-id="29735-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### <a name="deleting-items-remove-item"></a><span data-ttu-id="29735-145">Usuwanie elementów (Usuń element)</span><span class="sxs-lookup"><span data-stu-id="29735-145">Deleting Items (Remove-Item)</span></span>
<span data-ttu-id="29735-146">Aby usunąć pliki i foldery, użyj **Usuń element** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29735-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="29735-147">Polecenia cmdlet programu Windows PowerShell, takie jak **Usuń element**, który ułatwia znaczące, nieodwracalne zmiany często monit o potwierdzenie po wprowadzeniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="29735-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="29735-148">Na przykład, jeśli próbujesz usunąć **New.Directory** folderu, pojawi się monit o potwierdzenie polecenia, ponieważ folder zawiera pliki:</span><span class="sxs-lookup"><span data-stu-id="29735-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="29735-149">Ponieważ **tak** jest odpowiedź domyślnej, usuń folder i jego pliki, naciśnij klawisz **Enter** klucza.</span><span class="sxs-lookup"><span data-stu-id="29735-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="29735-150">Aby usunąć folder bez potwierdzenie, użyj **-Recurse** parametru.</span><span class="sxs-lookup"><span data-stu-id="29735-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```
PS> Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a><span data-ttu-id="29735-151">Wykonywanie elementów (Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="29735-151">Executing Items (Invoke-Item)</span></span>
<span data-ttu-id="29735-152">Program Windows PowerShell korzysta **elementu Invoke** polecenia cmdlet do wykonania domyślnej akcji dla pliku lub folderu.</span><span class="sxs-lookup"><span data-stu-id="29735-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="29735-153">Ta akcja domyślna jest określana przez domyślny program obsługi aplikacji w rejestrze. Efekt jest taki sam, jak gdyby dwukrotnym kliknięciu elementu w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="29735-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="29735-154">Załóżmy na przykład, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="29735-154">For example, suppose you run the following command:</span></span>

```
PS> Invoke-Item C:\WINDOWS
```

<span data-ttu-id="29735-155">Okno Eksploratora, który znajduje się w C:\\systemu Windows zostanie wyświetlony tylko tak, jakby była podwójnie dysku C:\\folderu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="29735-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="29735-156">Jeśli musisz wywołać **Boot.ini** pliku w systemie Windows Vista — przed:</span><span class="sxs-lookup"><span data-stu-id="29735-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```
PS> Invoke-Item C:\boot.ini
```

<span data-ttu-id="29735-157">Jeśli typ pliku .ini jest skojarzony z Notatnika, pliku boot.ini zostanie otwarty w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="29735-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>

