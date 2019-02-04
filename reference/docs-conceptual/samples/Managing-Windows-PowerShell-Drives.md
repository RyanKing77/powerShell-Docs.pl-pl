---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie dyskami programu Windows PowerShell
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: cfc5418e9d2efb1a786817e1b941d75e22291742
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685186"
---
# <a name="managing-windows-powershell-drives"></a>Zarządzanie dyskami programu Windows PowerShell

A *dysk programu Windows PowerShell* prowadzi do lokalizacji magazynu danych, której będziesz mieć dostęp, np. dysku systemu plików, w programie Windows PowerShell. Dostawcy programu Windows PowerShell Utwórz niektórych dysków, takich jak system plików stacje dysków (w tym C: i D:), rejestrem dysków (HKCU: i HKLM:) i dysku certyfikatu (certyfikatu:), można także tworzyć własne dyski programu Windows PowerShell. Dyski te są bardzo przydatne, ale są one dostępne tylko w ramach programu Windows PowerShell. Nie masz dostępu do nich przy użyciu innych narzędzi Windows, takich jak Eksplorator plików lub Cmd.exe.

Windows PowerShell korzysta z rzeczownik, **PSDrive**, poleceń, które działają przy użyciu programu Windows PowerShell dysków. Lista programu Windows PowerShell dysków w sesji środowiska Windows PowerShell, użyj **Get PSDrive** polecenia cmdlet.

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

Chociaż dyski na wyświetlaczu różnią się z stacje w systemie, lista będzie wyglądać podobnie do danych wyjściowych **Get PSDrive** przedstawionego powyżej polecenia.

Dyski systemu plików są podzbiorem dysków programu Windows PowerShell. Można zidentyfikować dysków z systemem plików we wpisie systemu plików, w kolumnie dostawcy. (Dysków z systemem plików w programie Windows PowerShell są obsługiwane przez dostawcę systemu plików programu Windows PowerShell).

Aby wyświetlić składnię **Get PSDrive** polecenia cmdlet, wpisz **Get-Command** polecenia **składni** parametru:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

**PSProvider** parametr umożliwia wyświetlenie tylko tych z programu Windows PowerShell dyski, które są obsługiwane przez określonego dostawcy. Na przykład, aby wyświetlić tylko dyski programu Windows PowerShell, które są obsługiwane przez dostawcę systemu plików programu Windows PowerShell, wpisz **Get PSDrive** polecenia **PSProvider** parametr i  **System plików** wartość:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Aby wyświetlić dyski programu Windows PowerShell, które reprezentują gałęzi rejestru, użyj **PSProvider** parametru, aby wyświetlić tylko dyski programu Windows PowerShell, które są obsługiwane przez dostawcę programu Windows PowerShell rejestru:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Umożliwia także standardowych poleceń cmdlet lokalizacji z stacje programu Windows PowerShell:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Dodawanie nowych Windows PowerShell dyski (nowe PSDrive)

Można dodać dysków programu Windows PowerShell, za pomocą **New PSDrive** polecenia. Aby wyświetlić składnię dla **New PSDrive** polecenia, wprowadź **Get-Command** polecenia **składni** parametru:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Aby utworzyć nowy dysk programu Windows PowerShell, należy podać trzy parametry:

- Nazwa dysku (możesz użyć Dowolna prawidłowa nazwa środowiska Windows PowerShell)

- PSProvider (Użyj "System plików" dla lokalizacji systemu plików i "Rejestru" w lokalizacji rejestru)

- Oznacza to ścieżki do katalogu głównego nowego dysku w katalogu głównym

Na przykład dysk o nazwie "Office", który jest zamapowany do folderu, który zawiera aplikacje Microsoft Office na komputerze, na przykład można utworzyć **C:\\Program Files\\Microsoft Office\\OFFICE11**. Aby utworzyć dysk, wpisz następujące polecenie:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Ogólnie rzecz biorąc ścieżek nie jest rozróżniana wielkość liter.

Możesz odwołać się do nowy dysk programu Windows PowerShell, tak jak wszystkie dyski programu Windows PowerShell — za pomocą nazwy z dwukropkiem (**:**).

Dysk programu Windows PowerShell można wykonać wiele zadań znacznie prostsze. Na przykład niektóre z najważniejszych kluczy w rejestrze systemu Windows mają bardzo długich ścieżek, kłopotliwe dostępu i trudne do zapamiętania, dzięki czemu. Informacje o konfiguracji krytycznych znajduje się w obszarze **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**. Do wyświetlania i zmieniania elementów w kluczu rejestru CurrentVersion, możesz utworzyć dysk programu Windows PowerShell, który jest ścieżką w tego klucza, wpisując:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Następnie można zmienić lokalizację, aby **cvkey:** dysku, tak jak każdy inny dysk:''

`PS> cd cvkey:`

lub:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

Polecenie cmdlet New-PsDrive dodaje nowy dysk tylko do bieżącej sesji programu Windows PowerShell. Jeśli zamkniesz okno programu Windows PowerShell, nowego dysku zostaną utracone. Aby zapisać dysk programu Windows PowerShell, użyj polecenia cmdlet Export-konsoli można wyeksportować bieżącej sesji programu Windows PowerShell, a następnie użyj PowerShell.exe **PSConsoleFile** parametru, aby go zaimportować. Lub Dodaj nowy dysk do Twojego profilu programu Windows PowerShell.

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Usuwanie środowiska Windows PowerShell dyski (Usuń PSDrive)

Dyski można usunąć za pomocą programu Windows PowerShell, za pomocą **PSDrive Usuń** polecenia cmdlet. **PSDrive Usuń** polecenia cmdlet jest łatwa w użyciu; Aby usunąć określony dysk programu Windows PowerShell, wystarczy podać nazwę dysk programu Windows PowerShell.

Na przykład, jeśli dodano **pakietu Office:** Dysk programu Windows PowerShell, jak pokazano na **New PSDrive** tematu, możesz go usunąć, wpisując:

```powershell
Remove-PSDrive -Name Office
```

Aby usunąć **cvkey:** Programu Windows PowerShell to dysk, również w pokazywane **PSDrive nowy** tematu, użyj następującego polecenia:

```powershell
Remove-PSDrive -Name cvkey
```

Można łatwo usunąć dysk programu Windows PowerShell, ale nie można go usunąć, gdy jesteś w stacji dysków. Przykład:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a>Dodawanie i usuwanie dysków poza programem Windows PowerShell

Wykrywa, dysków z systemem plików, które są dodawane lub usuwane w Windows, w tym dyski sieciowe, które są mapowane, dyski USB, które są dołączone i dyski, które są usuwane przy użyciu programu Windows PowerShell **net użyj** polecenia lub  **WScript.NetworkMapNetworkDrive** i **RemoveNetworkDrive** metody pochodzące ze skryptu Windows Script Host (WSH).