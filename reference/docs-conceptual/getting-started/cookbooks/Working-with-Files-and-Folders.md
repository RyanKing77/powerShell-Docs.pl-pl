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
---
# <a name="working-with-files-and-folders"></a>Praca z plikami i folderami

Nawigować przez dyski środowiska Windows PowerShell i operowanie nimi elementów na nich jest podobny do manipulowania plików i folderów na dyskach fizycznych systemu Windows. W tej sekcji omówiono sposób postępowania z określonych plików i folderów zadań manipulowania przy użyciu programu PowerShell.

### <a name="listing-all-the-files-and-folders-within-a-folder"></a>Wyświetlanie listy wszystkich plików i folderów w folderze

Wszystkie elementy można uzyskać bezpośrednio w folderze, za pomocą **Get-ChildItem**. Dodaj opcjonalny **życie** parametru do wyświetlania ukryte lub elementów systemu. Na przykład to polecenie wyświetla zawartość bezpośredniego systemu Windows PowerShell dysk C (która jest taka sama jak dysk fizyczny w systemie Windows C):

```powershell
Get-ChildItem -Path C:\ -Force
```

Polecenie wyświetla tylko bezpośrednio zawartych w niej elementów, podobnie jak przy użyciu jego Cmd.exe **DIR** polecenia lub **ls** w powłoce systemu UNIX. Aby pokazać zawartych w niej elementów, należy określić **-Recurse** również parametr. (To może potrwać bardzo długo). Aby wyświetlić listę wszystkich elementów na dysku C:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem** można filtrować elementy z jego **ścieżki**, **filtru**, **Include**, i **wykluczyć** parametrów, ale te są zwykle tylko na podstawie nazwy. Można wykonać złożone filtrowanie na podstawie innych właściwości elementów za pomocą **Where-Object**.

Poniższe polecenie umożliwia znalezienie wszystkich plików wykonywalnych w folderze Program Files, który ostatniej modyfikacji po 1 października 2005 i które nie są mniejsze niż 1 megabajt ani większa niż 10 megabajtów:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a>Kopiowanie plików i folderów

Kopiowanie wykonuje się za pomocą **Copy-Item**. Następujące polecenie tworzy kopię zapasową C:\\boot.ini do folderu C:\\boot.bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Jeśli plik docelowy już istnieje, próba skopiowania zakończy się niepowodzeniem. Aby zastąpić istniejące docelowego, użyj **życie** parametru:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

To polecenie działa nawet wtedy, gdy lokalizacją docelową jest tylko do odczytu.

Kopiowanie folderu działa tak samo. To polecenie powoduje skopiowanie folderu C:\\temp\\test1 do nowego folderu C:\\temp\\rekursywnie DeleteMe:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Ponadto można kopiować zaznaczenia elementów. Polecenie kopiuje wszystkie pliki .txt zawarte w dowolnym miejscu w c:\\danych do folderu c:\\temp\\tekst:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Można nadal używać innych narzędzi do wykonywania kopii systemu plików. XCOPY ROBOCOPY i COM obiekty, takie jak **Scripting.FileSystemObject,** wszystkie pracy w programie Windows PowerShell. Na przykład można użyć Host skryptów systemu Windows **Scripting.FileSystem COM** klasa do tworzenia kopii zapasowych C:\\boot.ini do folderu C:\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

### <a name="creating-files-and-folders"></a>Tworzenie plików i folderów

Tworzenie nowych elementów działa tak samo na wszystkich dostawców środowiska Windows PowerShell. Jeśli dostawca programu Windows PowerShell zawiera więcej niż jeden typ elementu — na przykład dostawcy środowiska Windows PowerShell w systemie plików rozróżnia katalogów i plików — należy określić typ elementu.

To polecenie tworzy nowy folder C:\\temp\\nowego folderu:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

To polecenie tworzy nowy pusty plik C:\\temp\\nowy Folder\\plik.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a>Usunięcie wszystkich plików i folderów w folderze

Można usunąć zawartych w niej elementów przy użyciu **Usuń element**, ale pojawi się monit o potwierdzenie usunięcia, jeśli element zawiera coś innego. Na przykład, jeśli próba usunięcia folderu C:\\temp\\DeleteMe, który zawiera inne elementy programu Windows PowerShell monituje o potwierdzenie przed usunięciem folderu:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Jeśli nie zostanie wyświetlony monit o poszczególnych elementów zawartych w niej, określ **Recurse** parametru:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Mapowanie folderu lokalnego jako dostępny dysk systemu Windows

Folder lokalny, można również mapować przy użyciu **subst** polecenia. Poniższe polecenie tworzy dysk lokalny, który P: umieszczone w lokalnym katalogu Program Files:

```powershell
subst p: $env:programfiles
```

Tak jak w przypadku dysków sieciowych dyski mapowane w przy użyciu programu Windows PowerShell **subst** są od razu widoczne powłoki Windows PowerShell.

### <a name="reading-a-text-file-into-an-array"></a>Odczytywanie pliku tekstowego do tablicy

Jest jednym z formatów magazynu częściej stosowana w przypadku danych tekstowych w pliku z osobnych wierszach traktowane jako elementy danych distinct. **Pobrania zawartości** polecenia cmdlet można odczytać całego pliku w jednym kroku, jak pokazano poniżej:

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

**Get-Content** już traktuje dane odczytane z pliku jako tablicę o jeden element w jednym wierszu zawartości pliku. Można to potwierdzić, sprawdzając **długość** zwrócony zawartości:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

To polecenie jest najbardziej przydatny w przypadku uzyskiwania listy informacji w programie Windows PowerShell bezpośrednio. Na przykład może przechowywać listę nazw komputerów lub adresy IP w pliku C:\\temp\\domainMembers.txt o nazwie jeden w każdym wierszu pliku. Można użyć **pobrania zawartości** można pobrać zawartości pliku i umieść je w zmiennej **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** jest teraz tablicę zawierającą nazwę komputera w każdym elemencie.
