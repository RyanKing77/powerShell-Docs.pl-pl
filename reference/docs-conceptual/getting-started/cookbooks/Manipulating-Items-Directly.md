---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Bezpośrednie manipulowanie elementami
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 688f9194bd16793331325999c69e88df3e94c976
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="manipulating-items-directly"></a>Bezpośrednie manipulowanie elementami

Elementy, które widać w dyski środowiska Windows PowerShell, takie jak pliki i foldery na dyskach systemu plików i kluczy rejestru na dyskach rejestru programu Windows PowerShell, są nazywane *elementów* w programie Windows PowerShell. Polecenia cmdlet do pracy z nimi elementów ma rzeczownikiem **elementu** w nazwach.

Dane wyjściowe **Get-Command - rzeczownik elementu** polecenia zawiera dziewięć poleceń cmdlet programu Windows PowerShell elementu.

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

### <a name="creating-new-items-new-item"></a>Tworzenie nowych elementów (nowy element)

Aby utworzyć nowy element w systemie plików, użyj **nowy element** polecenia cmdlet. Obejmują **ścieżki** parametr o ścieżkę do elementu i **ItemType** parametru o wartości "pliku" lub "directory".

Na przykład, aby utworzyć nowy katalog o nazwie "New.Directory"in dysku C:\\katalogu Temp, wpisz:

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

Ta sama metoda umożliwia utworzenie nowego klucza rejestru. Klucz rejestru jest w rzeczywistości ułatwiają tworzenie, ponieważ klucz jest tylko typ elementu w rejestrze systemu Windows. (Element są wpisy rejestru *właściwości*.) Na przykład aby utworzyć klucz o nazwie "_testowy" w podkluczu CurrentVersion, wpisz:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Podczas wpisywania ścieżki rejestru, należy uwzględnić dwukropkiem (**:**) w programie Windows PowerShell dysków nazwy, HKLM: i HKCU:. Bez dwukropkiem programu Windows PowerShell nie może rozpoznać nazwę dysku w ścieżce.

### <a name="why-registry-values-are-not-items"></a>Dlaczego wartości rejestru nie są elementami

Jeśli używasz **Get-ChildItem** polecenia cmdlet, aby znaleźć te elementy w kluczu rejestru, nie będzie widoczna wpisy rejestru rzeczywiste lub ich wartości.

Na przykład klucz rejestru **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion\\Uruchom** zwykle zawiera wiele wpisów rejestru reprezentują aplikacje, które są uruchamiane podczas uruchamiania systemu.

Jednak jeśli używasz **Get-ChildItem** do wyszukania elementów podrzędnych w kluczu, zobaczysz jest **OptionalComponents** podkluczy klucza:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Chociaż jest wygodne traktować wpisy rejestru jako elementy, nie można określić ścieżki do wpisu rejestru w sposób, który zapewnia, że jest unikatowa. Notacja ścieżki nie rozróżnia podklucz rejestru o nazwie **Uruchom** i **(domyślna)** wpis rejestru w **Uruchom** podkluczu. Ponadto ponieważ z rejestru wpis nazwy mogą zawierać ukośnika odwrotnego (**\\**), gdyby wpisy regsitry elementów, a następnie notacji ścieżki nie można użyć do odróżnienia wpis rejestru o nazwie  **Windows\\CurrentVersion\\Uruchom** z podklucza, który znajduje się w tej ścieżce.

### <a name="renaming-existing-items-rename-item"></a>Zmienianie nazw istniejących elementów (zmiana nazwy elementu)

Aby zmienić nazwę pliku lub folderu, użyj **zmiany nazwy elementu** polecenia cmdlet. Polecenie zmienia nazwę **więc Plik1.txt** pliku **fileOne.txt**.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

**Zmiany nazwy elementu** polecenia cmdlet można zmienić nazwę pliku lub folderu, ale nie można przenieść elementu. Polecenie nie powiedzie się, ponieważ próbuje on przenieść go z katalogu New.Directory do katalogu Temp.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a>Przenoszenie elementów (Przenieś element)

Aby przenieść plik lub folder, użyj **Przenieś element** polecenia cmdlet.

Na przykład następujące polecenie z dysku C: Przenosi katalogu New.Directory\\katalogu tymczasowego w katalogu głównym dysku C:. Aby sprawdzić, czy element został przeniesiony, obejmują **PassThru** parametr **Przenieś element** polecenia cmdlet. Bez **Passthru**, **Przenieś element** polecenie cmdlet nie wyświetla żadnych wyników.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a>Kopiowanie elementów (Copy-Item)

Jeśli znasz operacje kopiowania w innych powłoki, może się okazać zachowanie **Copy-Item** polecenia cmdlet programu Windows PowerShell umożliwia być nietypowe. Podczas kopiowania elementu z jednej lokalizacji do innej, domyślnie Copy-Item nie kopiuje jego zawartość.

Na przykład, jeśli kopiujesz **New.Directory** z dysku C: do dysku C: katalogu\\katalogu temp, polecenie powiedzie się, ale nie są kopiowane pliki w katalogu New.Directory.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Podczas wyświetlania zawartości **C:\\temp\\New.Directory**, można zauważyć, że nie zawiera on plików:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Dlaczego nie **Copy-Item** polecenia cmdlet skopiuj zawartość do nowej lokalizacji?

**Copy-Item** polecenia cmdlet zaprojektowano tak, aby wartość była ogólna; nie jest tylko do kopiowania plików i folderów. Ponadto nawet w przypadku kopiowania plików i folderów, możesz skopiować tylko kontenera, a nie do elementów.

Aby skopiować całą zawartość folderu, obejmują **Recurse** parametr **Copy-Item** polecenia cmdlet w poleceniu. Jeśli zostały już skopiowane katalogu bez jego zawartość, Dodaj **życie** parametr, który służy do zastępowania pustym folderze.

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

### <a name="deleting-items-remove-item"></a>Usuwanie elementów (Usuń element)

Aby usunąć pliki i foldery, użyj **Usuń element** polecenia cmdlet. Polecenia cmdlet programu Windows PowerShell, takie jak **Usuń element**, który ułatwia znaczące, nieodwracalne zmiany często monit o potwierdzenie po wprowadzeniu polecenia. Na przykład, jeśli próbujesz usunąć **New.Directory** folderu, pojawi się monit o potwierdzenie polecenia, ponieważ folder zawiera pliki:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Ponieważ **tak** jest odpowiedź domyślnej, usuń folder i jego pliki, naciśnij klawisz **Enter** klucza. Aby usunąć folder bez potwierdzenie, użyj **-Recurse** parametru.

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a>Wykonywanie elementów (Invoke-Item)

Program Windows PowerShell korzysta **elementu Invoke** polecenia cmdlet do wykonania domyślnej akcji dla pliku lub folderu. Ta akcja domyślna jest określana przez domyślny program obsługi aplikacji w rejestrze. Efekt jest taki sam, jak gdyby dwukrotnym kliknięciu elementu w Eksploratorze plików.

Załóżmy na przykład, uruchom następujące polecenie:

```powershell
Invoke-Item C:\WINDOWS
```

Okno Eksploratora, który znajduje się w C:\\systemu Windows zostanie wyświetlony tylko tak, jakby była podwójnie dysku C:\\folderu systemu Windows.

Jeśli musisz wywołać **Boot.ini** pliku w systemie Windows Vista — przed:

```powershell
Invoke-Item C:\boot.ini
```

Jeśli typ pliku .ini jest skojarzony z Notatnika, pliku boot.ini zostanie otwarty w Notatniku.