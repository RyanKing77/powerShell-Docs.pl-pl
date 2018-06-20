---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z wpisami rejestru
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952379"
---
# <a name="working-with-registry-entries"></a>Praca z wpisami rejestru

Ponieważ wpisy rejestru są właściwości kluczy, a w efekcie nie może być bezpośrednio przeglądany, musimy wykonać nieco inny sposób podczas pracy z nimi.

### <a name="listing-registry-entries"></a>Wyświetlanie listy wpisów rejestru

Istnieje wiele różnych sposobów Sprawdź wpisy rejestru. Najprostszym sposobem jest można pobrać nazw właściwości skojarzone z kluczem. Na przykład, aby wyświetlić nazwy wpisów w kluczu rejestru **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**, użyj **elementu Get** . Klucze rejestru ma właściwości o nazwie ogólne "Właściwości", który jest lista wpisy rejestru w kluczu. Polecenie wybiera właściwości property i rozwija elementów, dzięki czemu są one wyświetlane na liście:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Aby wyświetlić wpisy rejestru w bardziej czytelnej postaci, użyj **Get-ItemProperty**:

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

Właściwości związane z programu Windows PowerShell dla klucza są wszystkie prefiksem "PS", takie jak **PSPath**, **PSParentPath**, **PSChildName**, i **PSProvider** .

Można użyć "**.**" notation odwoływania się do bieżącej lokalizacji. Można użyć **lokalizacją zestawu** można zmienić na **CurrentVersion** kontenera rejestru pierwszy:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Alternatywnie można użyć wbudowanych elementu PSDrive HKLM z **lokalizacją zestawu**:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Następnie można użyć "**.**" notation dla bieżącej lokalizacji do listy właściwości bez określania Pełna ścieżka:

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Ścieżka rozszerzenia działa tak samo jak w systemie plików, więc w tej lokalizacji można uzyskać **ItemProperty** dla **HKLM:\\oprogramowania\\Microsoft\\systemu Windows \\Pomocy** za pomocą **Get ItemProperty-ścieżki. \\Pomocy**.

### <a name="getting-a-single-registry-entry"></a>Pobieranie jednego wpisu rejestru

Jeśli chcesz pobrać określonego wpisu w kluczu rejestru, można użyć jednej z kilku metod możliwe. W tym przykładzie wyszukuje wartość **DevicePath** w **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**.

Przy użyciu **Get-ItemProperty**, użyj **ścieżki** parametr, aby określić nazwę klucza i **nazwa** parametr, aby określić nazwę **DevicePath** wpisu.

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

To polecenie zwraca standardowe właściwości środowiska Windows PowerShell, jak również **DevicePath** właściwości.

> [!NOTE]
> Mimo że **Get-ItemProperty** ma **filtru**, **Include**, i **wykluczyć** parametrów, nie można użyć do filtrowania według nazwy właściwości. Tych parametrów można znaleźć kluczy rejestru — które są ścieżki elementu — i nie wpisy rejestru — które są właściwości elementu.

Innym rozwiązaniem jest za pomocą narzędzia wiersza polecenia Reg.exe. Aby uzyskać pomoc dotyczącą reg.exe, wpisz **reg.exe /?** w wierszu polecenia. Aby znaleźć wpisu DevicePath, należy użyć reg.exe, jak pokazano w poniższym poleceniu:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Można również użyć **WshShell COM** obiektu, tak aby zawierał niektórych wpisów rejestru, mimo że ta metoda nie działa z dużych danych binarnych lub z nazwami wpis rejestru, które zawierają znaki, takie jak "\\"). Dołącz nazwę właściwości do ścieżki elementu z \\ separatora:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Tworzenie nowych wpisów rejestru

Aby dodać nowy wpis o nazwie "PowerShellPath" do **CurrentVersion** użycie kluczy, **ItemProperty nowy** ścieżkę do klucza, wpis nazwy i wartości wpisu. Na przykład teraz nastąpi przekierowanie do wartości zmiennej środowiska Windows PowerShell **$PSHome**, który przechowuje ścieżkę do katalogu instalacyjnego środowiska Windows PowerShell.

Można dodać nowy wpis do klucza za pomocą następującego polecenia, a polecenie zwraca też wartość informacji o nowy wpis:

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

**PropertyType** musi być nazwą **Microsoft.Win32.RegistryValueKind** element członkowski wyliczenia z następującej tabeli:

|Wartość elementu PropertyType|Znaczenie|
|----------------------|-----------|
|Binarny|Dane binarne|
|DWord|Liczbę, która jest nieprawidłowa UInt32|
|ExpandString|Ciąg, który może zawierać zmienne środowiskowe, które zostaną rozwinięte dynamicznie|
|Kolumny|Wielowierszowy ciąg|
|Ciąg|Dowolną wartością ciągu|
|QWord|8 bajtów danych binarnych|

> [!NOTE]
> W wielu lokalizacjach można dodać wpis rejestru, określając tablicę wartości **ścieżki** parametru:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Można również zastąpić istniejące wartości wpisu rejestru, dodając **życie** parametru do dowolnego **ItemProperty nowy** polecenia.

### <a name="renaming-registry-entries"></a>Zmiana nazwy wpisy rejestru

Aby zmienić nazwę **PowerShellPath** wpisu "PSHome", użyj **ItemProperty zmiany nazwy**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Aby wyświetlić wartość zmieniono nazwę, Dodaj **PassThru** do polecenia parametr.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Usuwanie wpisów rejestru

Aby usunąć wpisy rejestru PSHome i PowerShellPath, użyj **ItemProperty Usuń**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```