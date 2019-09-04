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
# <a name="working-with-files-and-folders"></a>Praca z plikami i folderami

Nawigowanie po dyskach programu Windows PowerShell i manipulowanie elementami na nich jest podobne do manipulowania plikami i folderami na dyskach fizycznych systemu Windows. W tej sekcji omówiono sposób postępowania z określonymi zadaniami manipulowania plikami i folderami przy użyciu programu PowerShell.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Wyświetlanie listy wszystkich plików i folderów w folderze

Wszystkie elementy można pobrać bezpośrednio w folderze za pomocą polecenia **GET-ChildItem**. Dodaj opcjonalny parametr **Force** , aby wyświetlić elementy ukryte lub systemowe. Na przykład to polecenie wyświetla bezpośrednią zawartość dysku C programu Windows PowerShell, który jest taki sam jak dysk fizyczny systemu Windows C):

```powershell
Get-ChildItem -Path C:\ -Force
```

Polecenie wyświetla tylko bezpośrednio zawarte elementy, podobnie jak przy użyciu polecenia **dir** cmd. exe lub **ls** w powłoce systemu UNIX. Aby wyświetlić zawarte elementy, należy również określić parametr **-rekursywny** . (Może to potrwać bardzo długo.) Aby wyświetlić listę wszystkich elementów na dysku C:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

Polecenie **GET-ChildItem** umożliwia filtrowanie elementów przy użyciu ich **ścieżki**, **filtrowania**, **dołączania**i **wykluczania** parametrów, ale są one zwykle oparte tylko na nazwie. Można wykonać skomplikowane filtrowanie na podstawie innych właściwości elementów przy użyciu polecenia **WHERE-Object**.

Poniższe polecenie odnajduje wszystkie pliki wykonywalne w folderze Program Files, które zostały ostatnio zmodyfikowane po 1 października 2005 i które nie są mniejsze niż 1 megabajt ani większe niż 10 megabajtów:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Kopiowanie plików i folderów

Kopiowanie jest wykonywane z **elementem Copy-Item**. Następujące polecenie tworzy kopię zapasową c\\: Boot. ini do C\\: Boot. bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Jeśli plik docelowy już istnieje, próba kopiowania nie powiedzie się. Aby zastąpić istniejące miejsce docelowe, użyj parametru **Force** :

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

To polecenie działa nawet wtedy, gdy lokalizacja docelowa jest tylko do odczytu.

Kopiowanie folderów działa w ten sam sposób. To polecenie kopiuje folder c\\: temp\\TEST1 do nowego folderu c:\\temp\\DeleteMe rekursywnie:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Możesz również skopiować wybrane elementy. Następujące polecenie kopiuje wszystkie pliki txt zawarte w dowolnym miejscu w c:\\dane do c:\\tekst\\tymczasowy:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Można nadal używać innych narzędzi do wykonywania kopii systemu plików. XCOPY, ROBOCOPY i COM obiektów, takich jak **Scripting. FileSystemObject,** All Pracuj w programie Windows PowerShell. Na przykład można użyć klasy **com scripting** hosta skryptów systemu Windows, aby utworzyć kopię zapasową c\\: Boot. ini do c\\: Boot. bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Tworzenie plików i folderów

Tworzenie nowych elementów działa tak samo we wszystkich dostawcach środowiska Windows PowerShell. Jeśli dostawca programu Windows PowerShell ma więcej niż jeden typ elementu — na przykład dostawca systemu plików Windows PowerShell rozróżnia katalogi i pliki — należy określić typ elementu.

To polecenie tworzy nowy folder C:\\temp\\nowy folder:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

To polecenie tworzy nowy pusty plik C:\\temp\\nowy folder\\plik. txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Usuwanie wszystkich plików i folderów w folderze

Można usunąć zawarte elementy za pomocą polecenia **Remove-Item**, ale zostanie wyświetlony monit o potwierdzenie usunięcia, jeśli element zawiera coś innego. Na przykład w przypadku próby usunięcia folderu C:\\temp\\DeleteMe zawierającego inne elementy program Windows PowerShell wyświetli monit o potwierdzenie przed usunięciem folderu:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Jeśli nie chcesz otrzymywać monitów dla każdego zawartego elementu, określ parametr **rekursywnie** :

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a>Mapowanie folderu lokalnego jako dysku

Możesz również zmapować folder lokalny przy użyciu polecenia **New-PSDrive** . Następujące polecenie tworzy dysk lokalny P: root w katalogu plików programu lokalnego, widoczny tylko w sesji programu PowerShell:

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

Podobnie jak w przypadku dysków sieciowych dyski mapowane w programie Windows PowerShell są natychmiast widoczne dla powłoki programu Windows PowerShell.
Aby można było utworzyć mapowany dysk widoczny w Eksploratorze plików, jest wymagany parametr **-utrwalanie** . Jednak w przypadku utrwalania mogą być używane tylko ścieżki zdalne.


## <a name="reading-a-text-file-into-an-array"></a>Odczytywanie pliku tekstowego do tablicy

Jeden z najpopularniejszych formatów przechowywania danych tekstowych znajduje się w pliku z osobnymi wierszami traktowanymi jako różne elementy danych. Za pomocą polecenia cmdlet **Get-Content** można odczytać cały plik w jednym kroku, jak pokazano poniżej:

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

Polecenie **Get-Content** już traktuje dane odczytane z pliku jako tablicę z jednym elementem na wiersz zawartości pliku. Możesz to potwierdzić, sprawdzając **Długość** zwróconej zawartości:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

To polecenie jest najbardziej przydatne do bezpośredniego pobierania list informacji do programu Windows PowerShell. Na przykład można przechowywać listę nazw komputerów lub adresów IP w pliku C:\\temp\\domainMembers. txt, z jedną nazwą w każdym wierszu pliku. Aby pobrać zawartość pliku i umieścić je w zmiennej **$Computers**, można użyć **Get-Content** :

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** jest teraz tablicą zawierającą nazwę komputera w każdym elemencie.
