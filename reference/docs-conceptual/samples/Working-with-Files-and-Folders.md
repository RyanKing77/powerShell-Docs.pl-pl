---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z plikami i folderami
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: a8d57a1c269d95e692db6c3f1ae10df49e305e4e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685053"
---
# <a name="working-with-files-and-folders"></a>Praca z plikami i folderami

Nawigowanie przy użyciu programu Windows PowerShell dysków i manipulowanie elementami na nich jest podobny do manipulowania plików i folderów na dyskach fizycznych Windows. W tej sekcji omówiono sposób postępowania z określonych plików i folderów zadaniach przy użyciu programu PowerShell.

### <a name="listing-all-the-files-and-folders-within-a-folder"></a>Wyświetlanie listy wszystkich plików i folderów w folderze

Wszystkie elementy można uzyskać bezpośrednio z poziomu folderu, za pomocą **Get-ChildItem**. Dodaj opcjonalny **życie** parametru do wyświetlania ukryte lub systemu elementów. Na przykład to polecenie wyświetla zawartość bezpośredniego programu Windows PowerShell dysku C, (która jest taka sama jak dysk fizyczny w Windows C):

```powershell
Get-ChildItem -Path C:\ -Force
```

Polecenie wyświetla listę tylko bezpośrednio zawartych elementów, podobnie jak przy użyciu przez Cmd.exe **DIR** polecenia lub **ls** w powłoce systemu UNIX. Aby pokazać zawartych w niej elementów, należy określić **-Recurse** również parametr. (Może to potrwać bardzo długo). Aby wyświetlić listę wszystkich elementów na dysku C:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Polecenie GET-ChildItem** można filtrować elementy z jego **ścieżki**, **filtru**, **Include**, i **wykluczyć** parametrów, ale te są Zazwyczaj tylko na podstawie nazwy. Można wykonywać złożone filtrowanie na podstawie innych właściwości elementów za pomocą **Where-Object**.

Następujące polecenie umożliwia znalezienie wszystkich plików wykonywalnych w folderze Program Files, który był ostatnio modyfikowany po 1 października 2005 i które są mniejsze niż 1 MB ani większa niż 10 MB:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a>Kopiowanie plików i folderów

Kopiowanie odbywa się za pomocą **Copy-Item**. Następujące polecenie tworzy kopię zapasową C:\\pliku boot.ini, do C:\\boot.bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Jeśli plik docelowy już istnieje, próba skopiowania kończy się niepowodzeniem. Aby zastąpić istniejące miejsca docelowego, użyj **życie** parametru:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

To polecenie działa, nawet wtedy, gdy obiektem docelowym jest tylko do odczytu.

Kopiowanie folderów działa tak samo. To polecenie powoduje skopiowanie folderu C:\\temp\\test1 do nowego folderu C:\\temp\\rekursywnie DeleteMe:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Ponadto można kopiować zaznaczenia elementów. Następujące polecenie kopiuje wszystkie pliki txt, zawartych w dowolnym miejscu w c:\\danych c:\\temp\\tekstu:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Można nadal używać innych narzędzi do wykonywania kopii systemu plików. XCOPY, ROBOCOPY i COM obiekty, takie jak **Scripting.FileSystemObject,** wszystkie robocze w programie Windows PowerShell. Na przykład, można użyć hosta skryptów Windows **Scripting.FileSystem COM** klasy, aby utworzyć kopię zapasową C:\\pliku boot.ini, do C:\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

### <a name="creating-files-and-folders"></a>Tworzenie plików i folderów

Tworzenie nowych elementów działa tak samo na wszystkich dostawców środowiska Windows PowerShell. Jeśli dostawca programu Windows PowerShell ma więcej niż jeden typ elementu — na przykład dostawcy systemu plików Windows PowerShell rozróżnia katalogów i plików, należy określić typ elementu.

To polecenie umożliwia utworzenie nowego folderu C:\\temp\\nowego folderu:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

To polecenie tworzy nowy, pusty plik C:\\temp\\nowy Folder\\plik.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a>Usuwanie wszystkich plików i folderów w folderze

Można usunąć zawartych w niej elementów przy użyciu **Remove-Item**, ale użytkownik jest monitowany o potwierdzenie usunięcia, jeśli element zawiera coś innego. Na przykład, jeśli próba usunięcia folderu C:\\temp\\DeleteMe, który zawiera inne elementy, programu Windows PowerShell wyświetli monit o potwierdzenie przed usunięciem folderu:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Jeśli nie chcesz monit dla każdego elementu zawarte, należy określić **Recurse** parametru:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Mapowanie folderu lokalnego jako dostępny dysk Windows

Można również mapować folderem lokalnym przy użyciu **subst** polecenia. Następujące polecenie tworzy dysk lokalny, w których dostęp do konta root P: w lokalnym katalogu Program Files:

```powershell
subst p: $env:programfiles
```

Podobnie jak w przypadku dysków sieciowych dyski mapowane w obrębie za pomocą programu Windows PowerShell **subst** są widoczne natychmiast powłoki Windows PowerShell.

### <a name="reading-a-text-file-into-an-array"></a>Odczytywanie pliku tekstowego do tablicy

Jednym z bardziej powszechne formaty magazynu danych tekstowych jest w pliku przy użyciu osobnych wierszach traktowane jako elementy danych distinct. **Pobrania zawartości** polecenia cmdlet można odczytać całego pliku, w jednym kroku, jak pokazano poniżej:

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

**Get-Content** już traktuje dane odczytane z pliku jako tablica z jednym elementem dla każdego wiersza w zawartości pliku. Można to potwierdzić, sprawdzając **długość** zwracanej zawartości:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

To polecenie jest najbardziej przydatne w celu uzyskania listy informacji w programie Windows PowerShell bezpośrednio. Na przykład można przechowywać listę nazw komputerów lub adresy IP w pliku C:\\temp\\domainMembers.txt o nazwie jednym w każdym wierszu w pliku. Możesz użyć **pobrania zawartości** do pobierania zawartości pliku i umieść je w zmiennej **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** jest teraz tablicę zawierającą nazwę komputera, w każdym elemencie.
