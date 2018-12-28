---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z wpisami rejestru
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405372"
---
# <a name="working-with-registry-entries"></a>Praca z wpisami rejestru

Ponieważ wpisy rejestru są właściwości kluczy, a w efekcie nie mogą być bezpośrednio przeglądane, musimy wykonać nieco innego podejścia, podczas pracy z nimi.

### <a name="listing-registry-entries"></a>Wyświetlanie listy wpisów rejestru

Istnieje wiele różnych sposobów, aby zbadać wpisów rejestru. Najprostszym sposobem jest uzyskanie nazw właściwości skojarzone z kluczem. Na przykład, aby zobaczyć nazwy wpisów w kluczu rejestru **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**, użyj **elementu Get** . Klucze rejestru mają właściwość o nazwie ogólne "Właściwości", znajduje się lista wpisów rejestru w kluczu. Następujące polecenie wybiera właściwość właściwości i rozwija elementów, dlatego, że są one wyświetlane na liście:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Aby wyświetlić wpisy rejestru w postaci bardziej czytelny, użyj **Get-zmieniona właściwość elementu**:

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

Właściwości związane z programu Windows PowerShell dla klucza są wszystkie prefiks "PS", takich jak **PSPath**, **PSParentPath**, **PSChildName**, i **PSProvider** .

Można użyć "**.**" notation odwoływania się do bieżącej lokalizacji. Możesz użyć **Ustawianie lokalizacji** można zmienić na **CurrentVersion** rejestru kontenera pierwszy:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Alternatywnie, można użyć wbudowanych PSDrive HKLM z **Ustawianie lokalizacji**:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Następnie można użyć "**.**" notacji dla bieżącej lokalizacji wyświetlić listę właściwości bez określenia pełnej ścieżki:

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Ścieżka rozszerzenia działa tak samo, jak w systemie plików, dzięki czemu z tej lokalizacji można uzyskać **zmieniona właściwość elementu** dla **HKLM:\\oprogramowania\\Microsoft\\Windows \\Pomocy** przy użyciu **Get-zmieniona właściwość elementu — ścieżka... \\Pomocy**.

### <a name="getting-a-single-registry-entry"></a>Pobieranie jednego wpisu rejestru

Jeśli chcesz pobrać określonego wpisu w kluczu rejestru, można użyć jednej z kilku możliwych podejść. W tym przykładzie wyszukuje wartość **DevicePath** w **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**.

Za pomocą **Get-zmieniona właściwość elementu**, użyj **ścieżki** parametru do określenia nazwy klucza i **nazwa** parametru, aby określić nazwę **DevicePath** wpisu.

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

To polecenie zwraca standardowe właściwości programu Windows PowerShell, jak również **DevicePath** właściwości.

> [!NOTE]
> Mimo że **Get-zmieniona właściwość elementu** ma **filtru**, **Include**, i **wykluczyć** parametrów, nie można ich używać do filtrowania według nazwy właściwości. Parametry te dotyczą klucze rejestru — służą do ścieżki elementu — i nie wpisy rejestru — służą do właściwości elementu.

Innym rozwiązaniem jest za pomocą narzędzia wiersza polecenia Reg.exe. Aby uzyskać pomoc dotyczącą reg.exe, wpisz **reg.exe /?** w wierszu polecenia. Aby znaleźć wpisu DevicePath, użyj reg.exe, jak pokazano w następującym poleceniu:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Można również użyć **WshShell COM** obiektu również znaleźć niektóre wpisy rejestru, mimo że ta metoda nie działa z dużych danych binarnych lub nazwy wpisów rejestru, które obejmują znaki, takie jak "\\"). Dołącz nazwę właściwości ścieżki elementu z \\ separatora:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Tworzenie nowych wpisów rejestru

Aby dodać nowy wpis o nazwie "PowerShellPath" do **CurrentVersion** użycia klucza, **New-zmieniona właściwość elementu** przy użyciu ścieżki do klucza, wprowadzona nazwa i wartość wpisu. W tym przykładzie pobierzemy wartości zmiennej środowiska Windows PowerShell **$PSHome**, który przechowuje ścieżki do katalogu instalacyjnego dla środowiska Windows PowerShell.

Można dodać nowy wpis do klucza przy użyciu następującego polecenia, a polecenie zwraca też wartość informacji na temat nowego wpisu:

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

**PropertyType** musi być nazwą **Microsoft.Win32.RegistryValueKind** składowej wyliczenia z poniższej tabeli:

|Wartość PropertyType|Znaczenie|
|----------------------|-----------|
|Binarny|Dane binarne|
|DWord|Liczba, która jest nieprawidłowa UInt32|
|ExpandString|Ciąg, który może zawierać zmienne środowiskowe, które są dynamicznie powiększane|
|FixedLength|Wielowierszowy ciąg|
|Ciąg|Dowolną wartość ciągu|
|QWord|8 bajtów danych binarnych|

> [!NOTE]
> Można dodać wpis rejestru do wielu lokalizacji, określając szereg wartości **ścieżki** parametru:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Można również zastąpić istniejące wartości wpisu rejestru, dodając **życie** parametru do dowolnego **New-zmieniona właściwość elementu** polecenia.

### <a name="renaming-registry-entries"></a>Zmiana nazwy wpisów rejestru

Aby zmienić nazwę **PowerShellPath** wpis "PSHome", użyj **Rename-zmieniona właściwość elementu**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Aby wyświetlić wartość, których nazwy zostały zmienione, należy dodać **PassThru** do polecenia.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Usuwanie wpisów rejestru

Aby usunąć PSHome i PowerShellPath wpisy rejestru, użyj **Remove-zmieniona właściwość elementu**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```