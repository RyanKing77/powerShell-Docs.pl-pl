---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Bezpośrednie manipulowanie elementami
ms.openlocfilehash: 50aed569cf6b876297abe3cf1544eba70f6279ce
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030129"
---
# <a name="manipulating-items-directly"></a>Bezpośrednie manipulowanie elementami

Elementy, które widać w dysków programu Windows PowerShell, takie jak pliki i foldery na dyskach systemu plików i kluczy rejestru na dyskach rejestru programu Windows PowerShell, są nazywane *elementów* w programie Windows PowerShell. Polecenia cmdlet dotyczące pracy z nimi elementów ma rzeczownikiem **elementu** w nazwach.

Dane wyjściowe **Get-Command - rzeczownik elementu** polecenie pokazuje, że nie istnieją dziewięć poleceń cmdlet programu Windows PowerShell elementów.

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

## <a name="creating-new-items-new-item"></a>Tworzenie nowych elementów (nowy element)

Aby utworzyć nowy element w systemie plików, użyj **nowy element** polecenia cmdlet. Obejmują **ścieżki** parametr ze ścieżką do elementu, a **ItemType** parametru o wartości "file" lub "directory".

Na przykład, aby utworzyć nowy katalog o nazwie "New.Directory"in C:\\katalogu Temp, wpisz:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Aby utworzyć plik, zmień wartość **ItemType** parametr "file". Na przykład aby utworzyć plik o nazwie "więc Plik1.txt" w katalogu New.Directory, wpisz:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

Można użyć tej samej techniki, aby utworzyć nowy klucz rejestru. W rzeczywistości łatwiej utworzyć, ponieważ jedynym typem elementu w rejestrze systemu Windows jest kluczem jest klucz rejestru. (Wpisy rejestru są elementu *właściwości*.) Na przykład aby utworzyć klucz o nazwie "_testuj" w podkluczu CurrentVersion, wpisz:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Podczas wpisywania ścieżki rejestru, należy uwzględnić dwukropkiem ( **:** ) w programie Windows PowerShell dysku nazwy, HKLM: a HKCU:. Bez dwukropka programu Windows PowerShell nie może rozpoznać nazwę dysku w ścieżce.

## <a name="why-registry-values-are-not-items"></a>Dlaczego wartości rejestru nie są elementami

Kiedy używasz **Get-ChildItem** polecenia cmdlet w celu odszukania elementów w kluczu rejestru, nigdy nie zobaczysz wpisy rejestru rzeczywiste oraz ich wartości.

Na przykład klucz rejestru **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion\\Uruchom** zwykle zawiera wiele wpisów rejestru reprezentują aplikacje, które są uruchamiane podczas uruchamiania systemu.

Jednak jeśli używasz **Get-ChildItem** do wyszukania elementów podrzędnych w kluczu, zostanie wyświetlony wystarczy **OptionalComponents** podkluczy klucza:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Mimo że byłoby wygodne do traktowania wpisy rejestru jako elementy, nie można określić ścieżkę do wpisu rejestru w sposób, który gwarantuje, że jest ona unikatowa. Notacji ścieżki nie rozróżnia podklucza rejestru o nazwie **Uruchom** i **(opcja domyślna)** wpisu rejestru w **Uruchom** podklucza. Ponadto ponieważ nazwy wpisów rejestru może zawierać znak ukośnika odwrotnego ( **\\** ), gdyby wpisy rejestru elementów, a następnie nie można użyć notacji ścieżki, aby odróżnić wpis rejestru o nazwie  **Windows\\CurrentVersion\\Uruchom** z podklucza, który znajduje się w tej ścieżce.

## <a name="renaming-existing-items-rename-item"></a>Zmienianie nazw istniejących elementów (zmiana nazwy elementu)

Aby zmienić nazwę pliku lub folderu, należy użyć **Zmień nazwę elementu** polecenia cmdlet. Następujące polecenie zmienia nazwę **więc Plik1.txt** plik **fileOne.txt**.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

**Zmień nazwę elementu** polecenia cmdlet można zmienić nazwę pliku lub folderu, ale go nie można przenieść elementu. Następujące polecenie kończy się niepowodzeniem, ponieważ próbuje przenieść plik z katalogu New.Directory katalogu Temp.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a>Przenoszenie elementów (przenoszenie elementów)

Aby przenieść plik lub folder, należy użyć **Przenieś element** polecenia cmdlet.

Na przykład następujące polecenie powoduje katalogu New.Directory z C:\\katalogu tymczasowego w katalogu głównym dysku C:. Aby sprawdzić, czy element został przeniesiony, należy dołączyć **PassThru** parametru **Przenieś element** polecenia cmdlet. Bez **Passthru**, **Przenieś element** polecenie cmdlet nie powoduje wyświetlenia żadnych wyników.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a>Kopiowanie elementów (Copy-Item)

Jeśli znasz operacje kopiowania w innych powłoki zachowanie może się okazać **Copy-Item** polecenia cmdlet programu Windows PowerShell jako nietypowe. Podczas kopiowania elementu z jednej lokalizacji do innej, domyślnie Copy-Item nie kopiuje jego zawartość.

Na przykład, jeśli kopiujesz **New.Directory** katalogu z dysku C: na dysku C:\\katalogu tymczasowego, polecenie zakończy się pomyślnie, ale nie są kopiowane pliki w katalogu New.Directory.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Podczas wyświetlania zawartości **C:\\temp\\New.Directory**, można zauważyć, że nie zawiera on plików:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Dlaczego nie **Copy-Item** polecenia cmdlet skopiuj zawartość do nowej lokalizacji?

**Copy-Item** polecenia cmdlet została opracowana jako ogólne, a nie tylko do kopiowania plików i folderów. Ponadto nawet wtedy, gdy kopiowanie plików i folderów, można kopiować tylko kontenera i nie elementy znajdujące się w nim.

Aby skopiować całą zawartość folderu, należy dołączyć **Recurse** parametru **Copy-Item** polecenia cmdlet w poleceniu. Jeśli zostały już skopiowane katalogu bez jego zawartości, należy dodać **życie** parametr, który umożliwia zastąpienie pustego folderu.

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

## <a name="deleting-items-remove-item"></a>Usuwanie elementów (Usuń element)

Aby usunąć pliki i foldery, użyj **Remove-Item** polecenia cmdlet. Polecenia cmdlet programu Windows PowerShell, takie jak **Remove-Item**, które można wprowadzać znaczące, nieodwracalne zmiany często wyświetli monit o potwierdzenie po wprowadzeniu polecenia. Na przykład, jeśli zostanie podjęta próba usunięcia **New.Directory** folderu, użytkownik jest monitowany o potwierdzenie polecenia, ponieważ folder zawiera pliki:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Ponieważ **tak** jest domyślną odpowiedź, aby usunąć folder i jego pliki, naciśnij klawisz **Enter** klucza. Aby usunąć folder bez potwierdzania, użyj **-Recurse** parametru.

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a>Wykonywanie elementów (wywołania elementów)

Używa programu Windows PowerShell **Invoke-Item** polecenia cmdlet do wykonania akcji domyślna dla pliku lub folderu. Ta akcja domyślna jest określana przez domyślny program obsługi aplikacji w rejestrze. Efekt jest taki sam, jak po dwukrotnym kliknięciu element w Eksploratorze plików.

Załóżmy na przykład, uruchom następujące polecenie:

```powershell
Invoke-Item C:\WINDOWS
```

Okno Eksploratora, który znajduje się w C:\\Windows pojawi się po prostu tak, jakby było kliknął C:\\folderu Windows.

Jeśli wywołujesz **Boot.ini** pliku w systemie przed Windows Vista:

```powershell
Invoke-Item C:\boot.ini
```

Jeśli typ pliku .ini jest skojarzony z Notatnika, plik boot.ini zostanie otwarty w Notatniku.
