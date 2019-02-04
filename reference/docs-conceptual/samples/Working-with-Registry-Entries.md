---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z wpisami rejestru
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686810"
---
# <a name="working-with-registry-entries"></a>Praca z wpisami rejestru

Ponieważ wpisy rejestru są właściwości kluczy, a w efekcie nie mogą być bezpośrednio przeglądane, musimy wykonać nieco innego podejścia, podczas pracy z nimi.

### <a name="listing-registry-entries"></a>Wyświetlanie listy wpisów rejestru

Istnieje wiele różnych sposobów, aby zbadać wpisów rejestru. Najprostszym sposobem jest uzyskanie nazw właściwości skojarzone z kluczem. Na przykład, aby zobaczyć nazwy wpisów w kluczu rejestru `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, użyj `Get-Item`. Klucze rejestru mają właściwość o nazwie ogólne "Właściwości", znajduje się lista wpisów rejestru w kluczu.
Następujące polecenie wybiera właściwość właściwości i rozwija elementów, dlatego, że są one wyświetlane na liście:

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Aby wyświetlić wpisy rejestru w postaci bardziej czytelny, użyj `Get-ItemProperty`:

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

Możesz użyć `*.*` notacji odwoływania się do bieżącej lokalizacji. Możesz użyć `Set-Location` można zmienić na **CurrentVersion** rejestru kontenera pierwszy:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Alternatywnie, można użyć wbudowanych PSDrive HKLM z `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Następnie można użyć `*.*` notacji dla bieżącej lokalizacji wyświetlić listę właściwości bez określenia pełnej ścieżki:

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Ścieżka rozszerzenia działa tak samo, jak w systemie plików, dzięki czemu z tej lokalizacji można uzyskać **zmieniona właściwość elementu** dla `HKLM:\SOFTWARE\Microsoft\Windows\Help` przy użyciu `Get-ItemProperty -Path ..\Help`.

### <a name="getting-a-single-registry-entry"></a>Pobieranie jednego wpisu rejestru

Jeśli chcesz pobrać określonego wpisu w kluczu rejestru, można użyć jednej z kilku możliwych podejść. W tym przykładzie wyszukuje wartość **DevicePath** w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Przy użyciu `Get-ItemProperty`, użyj **ścieżki** parametru do określenia nazwy klucza i **nazwa** parametru, aby określić nazwę **DevicePath** wpisu.

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
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
> Mimo że `Get-ItemProperty` ma **filtru**, **Include**, i **wykluczyć** parametrów, nie można ich używać do filtrowania według nazwy właściwości. Te parametry można znaleźć klucze rejestru, które są ścieżki elementów ale nie wpisów rejestru. Wpisy rejestru, które są właściwości elementu.

Innym rozwiązaniem jest za pomocą narzędzia wiersza polecenia Reg.exe. Aby uzyskać pomoc dotyczącą reg.exe, wpisz `reg.exe /?` polecenie w wierszu polecenia. Aby znaleźć wpisu DevicePath, użyj reg.exe, jak pokazano w następującym poleceniu:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Można również użyć **WshShell** obiekt COM, jak również znaleźć niektóre wpisy rejestru, mimo że ta metoda nie działa z dużych danych binarnych lub nazwy wpisów rejestru, które obejmują znaki, takie jak "\\"). Dołącz nazwę właściwości ścieżki elementu z \\ separatora:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a>Ustawianie jednego wpisu rejestru

Jeśli chcesz zmienić określonego wpisu w kluczu rejestru, można użyć jednej z kilku możliwych podejść. Ten przykład modyfikuje **ścieżki** wpis w `HKEY_CURRENT_USER\Environment`. **Ścieżki** wejścia Określa lokalizację plików wykonywalnych.

1. Pobieranie bieżącej wartości **ścieżki** przy użyciu wpisu `Get-ItemProperty`.
2. Dodaj nową wartość, oddzielając je za pomocą `;`.
3. Użyj `Set-ItemProperty` przy użyciu określonego klucza, wpis nazwy i wartości, aby zmodyfikować wpis rejestru.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Mimo że `Set-ItemProperty` ma **filtru**, **Include**, i **wykluczyć** parametrów, nie można ich używać do filtrowania według nazwy właściwości. Parametry te dotyczą klucze rejestru — służą do ścieżki elementu — i nie wpisy rejestru — służą do właściwości elementu.

Innym rozwiązaniem jest za pomocą narzędzia wiersza polecenia Reg.exe. Aby uzyskać pomoc dotyczącą reg.exe, wpisz **reg.exe /?**
w wierszu polecenia.

Następujący przykład zmienia **ścieżki** zgłoszenia przez usunięcie ścieżki dodane w powyższym przykładzie.
`Get-ItemProperty` nadal służy do pobierania bieżącą wartość, aby uniknąć konieczności przeanalizować ciągu zwróconego przez `reg query`. **Podciąg** i **LastIndexOf** metody są używane do pobierania ścieżki ostatniego dodane do **ścieżki** wpisu.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a>Tworzenie nowych wpisów rejestru

Aby dodać nowy wpis o nazwie "PowerShellPath" do **CurrentVersion** użycia klucza, `New-ItemProperty` przy użyciu ścieżki do klucza, wprowadzona nazwa i wartość wpisu. W tym przykładzie pobierzemy wartości zmiennej środowiska Windows PowerShell `$PSHome`, który przechowuje ścieżki do katalogu instalacyjnego dla środowiska Windows PowerShell.

Można dodać nowy wpis do klucza przy użyciu następującego polecenia, a polecenie zwraca też wartość informacji na temat nowego wpisu:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
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
|MultiString|Wielowierszowy ciąg|
|Ciąg|Dowolną wartość ciągu|
|QWord|8 bajtów danych binarnych|

> [!NOTE]
> Można dodać wpis rejestru do wielu lokalizacji, określając szereg wartości **ścieżki** parametru:

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Można również zastąpić istniejące wartości wpisu rejestru, dodając **życie** parametru do dowolnego `New-ItemProperty` polecenia.

### <a name="renaming-registry-entries"></a>Zmiana nazwy wpisów rejestru

Aby zmienić nazwę **PowerShellPath** wpis "PSHome", użyj `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Aby wyświetlić wartość, których nazwy zostały zmienione, należy dodać **PassThru** do polecenia.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Usuwanie wpisów rejestru

Aby usunąć PSHome i PowerShellPath wpisy rejestru, użyj `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
