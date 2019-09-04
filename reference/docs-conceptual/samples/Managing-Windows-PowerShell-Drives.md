---
ms.date: 06/05/2017
keywords: PowerShell, polecenie cmdlet
title: Zarządzanie dyskami programu Windows PowerShell
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215512"
---
# <a name="managing-windows-powershell-drives"></a>Zarządzanie dyskami programu Windows PowerShell

*Dysk programu Windows PowerShell* to lokalizacja magazynu danych, do której można uzyskać dostęp do dysku systemu plików w programie Windows PowerShell. Dostawcy programu Windows PowerShell tworzą dyski, takie jak dyski systemu plików (w tym C: i D:), dyski rejestru (HKCU: i HKLM:) oraz dysk certyfikatu (certyfikat:) i można utworzyć własne dyski programu Windows PowerShell. Te dyski są bardzo przydatne, ale są dostępne tylko w programie Windows PowerShell. Nie można uzyskać do nich dostępu przy użyciu innych narzędzi systemu Windows, takich jak Eksplorator plików lub cmd. exe.

Program Windows PowerShell korzysta z rzeczowników, **PSDrive**, dla poleceń, które działają z dyskami programu Windows PowerShell. Aby uzyskać listę dysków programu Windows PowerShell w sesji programu Windows PowerShell, użyj polecenia cmdlet **Get-PSDrive** .

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

Mimo że dyski w wyświetlaczu różnią się w zależności od dysków w systemie, lista będzie wyglądać podobnie do danych wyjściowych polecenia **Get-PSDrive** .

Dyski systemu plików są podzbiorem dysków programu Windows PowerShell. Dyski systemu plików można identyfikować według wpisu w kolumnie dostawca. (Dyski systemu plików w programie Windows PowerShell są obsługiwane przez dostawcę systemu plików programu Windows PowerShell).

Aby wyświetlić składnię polecenia cmdlet **Get-PSDrive** , wpisz polecenie **Get-Command** z parametrem **składni** :

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

Parametr **PSProvider** umożliwia wyświetlenie tylko dysków programu Windows PowerShell, które są obsługiwane przez określonego dostawcę. Aby na przykład wyświetlić tylko dyski programu Windows PowerShell obsługiwane przez dostawcę systemu plików programu Windows PowerShell, wpisz polecenie **Get-PSDrive** z parametrem **PSProvider** i wartością systemu **plików** :

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Aby wyświetlić dyski programu Windows PowerShell reprezentujące gałęzie rejestru, użyj parametru **PSProvider** , aby wyświetlić tylko dyski programu Windows PowerShell obsługiwane przez dostawcę rejestru programu Windows PowerShell:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Można również użyć standardowych poleceń cmdlet lokalizacji z dyskami programu Windows PowerShell:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Dodawanie nowych dysków programu Windows PowerShell (New-PSDrive)

Możesz dodać własne dyski programu Windows PowerShell za pomocą polecenia **New-PSDrive** . Aby uzyskać składnię polecenia **New-PSDrive** , wprowadź polecenie **Get-Command** z parametrem **składni** :

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Aby utworzyć nowy dysk programu Windows PowerShell, należy podać trzy parametry:

- Nazwa dysku (można użyć dowolnej prawidłowej nazwy programu Windows PowerShell)

- PSProvider (Użyj "FileSystem" dla lokalizacji systemu plików i "Registry" dla lokalizacji rejestru)

- Katalog główny, czyli ścieżka do katalogu głównego nowego dysku

Można na przykład utworzyć dysk o nazwie "Office" mapowany do folderu zawierającego Microsoft Office aplikacje na komputerze, na przykład **C:\\program\\Files\\Microsoft Office Office11**. Aby utworzyć dysk, wpisz następujące polecenie:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Ogólnie rzecz biorąc, ścieżki nie uwzględnia wielkości liter.

Nowy dysk programu Windows PowerShell jest przywołuje się do wszystkich dysków programu Windows PowerShell — według nazwy i dwukropka ( **:** ).

Dysk programu Windows PowerShell może znacznie uprościć wykonywanie wielu zadań. Na przykład niektóre najważniejsze klucze w rejestrze systemu Windows mają bardzo długie ścieżki, dzięki czemu trudno jest uzyskać dostęp i trudne do zapamiętania. Krytyczne informacje o konfiguracji znajdują się **w\\obszarze HKEY_LOCAL_MACHINE\\Software\\\\Microsoft Windows CurrentVersion**. Aby wyświetlić i zmienić elementy w kluczu rejestru CurrentVersion, można utworzyć dysk programu Windows PowerShell, który jest odblokowany w tym kluczu, wpisując:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Następnie można zmienić lokalizację na dysk **cvkey:** tak jak każdy inny dysk:

```
PS> cd cvkey:
```

lub:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

Polecenie cmdlet New-PsDrive dodaje nowy dysk tylko do bieżącej sesji programu Windows PowerShell. Jeśli zamkniesz okno programu Windows PowerShell, nowy dysk zostanie utracony. Aby zapisać dysk programu Windows PowerShell, użyj polecenia cmdlet Export-Console, aby wyeksportować bieżącą sesję programu Windows PowerShell, a następnie zaimportuj go za pomocą parametru **PSConsoleFile** PowerShell. exe. Lub Dodaj nowy dysk do profilu środowiska Windows PowerShell.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Usuwanie dysków programu Windows PowerShell (Remove-PSDrive)

Można usunąć dyski z programu Windows PowerShell za pomocą polecenia cmdlet **Remove-PSDrive** . Polecenie cmdlet **Remove-PSDrive** jest łatwe w użyciu. Aby usunąć określony dysk programu Windows PowerShell, wystarczy podać nazwę dysku programu Windows PowerShell.

Na przykład, jeśli został dodany **pakiet Office:** Dysk programu Windows PowerShell, jak pokazano w temacie **New-PSDrive** , można go usunąć, wpisując:

```powershell
Remove-PSDrive -Name Office
```

Aby usunąć **cvkey:** Dysk programu Windows PowerShell, również przedstawiony w temacie **New-PSDrive** , użyj następującego polecenia:

```powershell
Remove-PSDrive -Name cvkey
```

Można łatwo usunąć dysk programu Windows PowerShell, ale nie można go usunąć, gdy jesteś w stacji. Przykład:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Dodawanie i usuwanie dysków poza programem Windows PowerShell

Program Windows PowerShell wykrywa dyski systemu plików, które są dodawane lub usuwane w systemie Windows, w tym dyski sieciowe, które są dołączone, a dyski, które są usuwane przy użyciu polecenia **net use** lub  **WScript. NetworkMapNetworkDrive** i **RemoveNetworkDrive** metody z skryptu hosta skryptów systemu Windows (WSH).
