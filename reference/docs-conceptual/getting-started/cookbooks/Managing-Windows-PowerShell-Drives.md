---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie dyskami programu Windows PowerShell
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: cfc5418e9d2efb1a786817e1b941d75e22291742
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951872"
---
# <a name="managing-windows-powershell-drives"></a>Zarządzanie dyskami programu Windows PowerShell

A *dysk programu Windows PowerShell* prowadzi do lokalizacji magazynu danych, której będziesz mieć dostęp, takich jak dysk systemu plików w programie Windows PowerShell. Dostawcy programu Windows PowerShell Utwórz niektórych dysków, takich jak system plików stacje dysków (w tym C: i D:), rejestru dysków (HKCU: i HKLM:) i dysku certyfikatu (Cert:), i tworzenia dysków programu Windows PowerShell. Dyski te są przydatne, ale są dostępne tylko w obrębie środowiska Windows PowerShell. Nie masz dostępu do nich przy użyciu innych narzędzi systemu Windows, takich jak Eksplorator plików lub Cmd.exe.

Program Windows PowerShell korzysta rzeczownik, **elementu PSDrive**, poleceń, które współpracują z programu Windows PowerShell dyski. Lista programu Windows PowerShell dysków w sesji środowiska Windows PowerShell, użyj **elementu PSDrive Get** polecenia cmdlet.

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

Mimo że dysków na ekranie różnią się z dyskami w systemie, listę będzie wyglądała podobnie do danych wyjściowych **elementu PSDrive Get** polecenia przedstawionych powyżej.

Dyski systemu plików są podzbiorem dyski środowiska Windows PowerShell. Można zidentyfikować dysków z systemem plików przez system plików wpis w kolumnie dostawcy. (Dysków systemu plików w programie Windows PowerShell są obsługiwane przez dostawcę programu Windows PowerShell w systemie plików).

Aby wyświetlić składnię **elementu PSDrive Get** polecenia cmdlet, wpisz **Get-Command** z **składni** parametru:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

**PSProvider** parametr umożliwia wyświetlenie tylko tych dysków programu Windows PowerShell, które są obsługiwane przez określonego dostawcy. Na przykład, aby wyświetlić dyski środowiska Windows PowerShell, które są obsługiwane przez dostawcę programu Windows PowerShell w systemie plików, wpisz **elementu PSDrive Get** z **PSProvider** parametr i  **System plików** wartość:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Aby wyświetlić dyski środowiska Windows PowerShell, które reprezentują gałęzi rejestru, użyj **PSProvider** parametr, aby wyświetlić tylko dyski programu Windows PowerShell, które są obsługiwane przez dostawcę rejestru systemu Windows PowerShell:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Można także użyć standardowych poleceń cmdlet lokalizacji z dyskami środowiska Windows PowerShell:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Dodawanie nowego środowiska Windows PowerShell dysków (nowego elementu PSDrive)

Można dodać dysków programu Windows PowerShell przy użyciu **elementu PSDrive nowy** polecenia. Aby wyświetlić składnię dla **elementu PSDrive nowy** polecenia, wprowadź **Get-Command** z **składni** parametru:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Aby utworzyć nowy dysk programu Windows PowerShell, należy podać trzy parametry:

- Nazwa dysku (możesz użyć dowolnego prawidłową nazwę środowiska Windows PowerShell)

- PSProvider (Użyj elementu "FileSystem" dla lokalizacji plików systemu i "Rejestru" w przypadku lokalizacji rejestru)

- Oznacza to, ścieżka do katalogu głównego nowego dysku w folderze głównym

Na przykład dysk o nazwie "Office", który jest zamapowany na folder, który zawiera aplikacje Microsoft Office na komputerze, na przykład można utworzyć **C:\\Program Files\\Microsoft Office\\OFFICE11**. Aby utworzyć dysk, wpisz następujące polecenie:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Ogólnie rzecz biorąc ścieżki nie jest rozróżniana.

Zobacz na nowy dysk programu Windows PowerShell, tak jak wszystkie dyski środowiska Windows PowerShell — za pomocą nazwy z dwukropkiem (**:**).

Dysk programu Windows PowerShell można wprowadzać wiele zadań znacznie prostsze. Na przykład niektóre z najważniejszych kluczy rejestru systemu Windows ma bardzo długi ścieżek, nadawania skomplikowane dostępu i trudne do zapamiętania. Informacje o konfiguracji krytyczne znajduje się w obszarze **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**. Do wyświetlania i zmieniania elementów w kluczu rejestru CurrentVersion, można utworzyć dysk programu Windows PowerShell, który jest osadzony w tym kluczu, wpisując:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Następnie możesz zmienić lokalizację do **cvkey:** dysków, tak jak każdy inny dysk: "

`PS> cd cvkey:`

lub:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

Polecenia cmdlet New-elementu PsDrive dodaje nowy dysk tylko do bieżącej sesji programu Windows PowerShell. Jeśli zamkniesz okno programu Windows PowerShell, nowego dysku zostaną utracone. Aby zapisać dysk programu Windows PowerShell, użyj polecenia cmdlet Export-konsoli można wyeksportować bieżącej sesji programu Windows PowerShell, a następnie użyj PowerShell.exe **PSConsoleFile** parametru do zaimportowania. Można również dodać nowy dysk do swojego profilu programu Windows PowerShell.

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Usuwanie środowiska Windows PowerShell dysków (elementu PSDrive Usuń)

Można usunąć dysków z programu Windows PowerShell za pomocą **elementu PSDrive Usuń** polecenia cmdlet. **Elementu PSDrive Usuń** polecenia cmdlet jest łatwy w użyciu; Aby usunąć określony dysk programu Windows PowerShell, wystarczy podać nazwę dysk programu Windows PowerShell.

Na przykład jeśli dodano **pakietu Office:** dysk programu Windows PowerShell, jak pokazano w **elementu PSDrive nowy** temacie, można ją usunąć, wpisując:

```powershell
Remove-PSDrive -Name Office
```

Aby usunąć **cvkey:** programu Windows PowerShell to dysk, również wyświetlane w **elementu PSDrive nowy** tematu, należy użyć następującego polecenia:

```powershell
Remove-PSDrive -Name cvkey
```

Łatwo usunąć dysk programu Windows PowerShell, ale nie można go usunąć, gdy są na dysku. Przykład:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a>Dodawanie i usuwanie dysków poza środowiska Windows PowerShell

Wykrywa, dysków z systemem plików, które zostały dodane lub usunięte w systemie Windows, w tym dyski sieciowe, które są mapowane, dysków USB, które są dołączone i dyski, które zostały usunięte za pomocą środowiska Windows PowerShell **net użyj** polecenia lub  **WScript.NetworkMapNetworkDrive** i **RemoveNetworkDrive** metody ze skryptu Windows Script Host (WSH).