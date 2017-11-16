---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Dyski Zarządzanie środowiska Windows PowerShell"
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: e2908246bb584291f04b67dc8635caec93d3b72e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="d02df-103">Dyski Zarządzanie środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d02df-103">Managing Windows PowerShell Drives</span></span>
<span data-ttu-id="d02df-104">A *dysk programu Windows PowerShell* prowadzi do lokalizacji magazynu danych, której będziesz mieć dostęp, takich jak dysk systemu plików w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d02df-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="d02df-105">Dostawcy programu Windows PowerShell Utwórz niektórych dysków, takich jak system plików stacje dysków (w tym C: i D:), rejestru dysków (HKCU: i HKLM:) i dysku certyfikatu (Cert:), i tworzenia dysków programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d02df-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="d02df-106">Dyski te są przydatne, ale są dostępne tylko w obrębie środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d02df-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="d02df-107">Nie masz dostępu do nich przy użyciu innych narzędzi systemu Windows, takich jak Eksplorator plików lub Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="d02df-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="d02df-108">Program Windows PowerShell korzysta rzeczownik, **elementu PSDrive**, poleceń, które współpracują z programu Windows PowerShell dyski.</span><span class="sxs-lookup"><span data-stu-id="d02df-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="d02df-109">Lista programu Windows PowerShell dysków w sesji środowiska Windows PowerShell, użyj **elementu PSDrive Get** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d02df-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

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

<span data-ttu-id="d02df-110">Mimo że dysków na ekranie różnią się z dyskami w systemie, listę będzie wyglądała podobnie do danych wyjściowych **elementu PSDrive Get** polecenia przedstawionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="d02df-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="d02df-111">Dyski systemu plików są podzbiorem dyski środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d02df-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="d02df-112">Można zidentyfikować dysków z systemem plików przez system plików wpis w kolumnie dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d02df-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="d02df-113">(Dysków systemu plików w programie Windows PowerShell są obsługiwane przez dostawcę programu Windows PowerShell w systemie plików).</span><span class="sxs-lookup"><span data-stu-id="d02df-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="d02df-114">Aby wyświetlić składnię **elementu PSDrive Get** polecenia cmdlet, wpisz **Get-Command** z **składni** parametru:</span><span class="sxs-lookup"><span data-stu-id="d02df-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="d02df-115">**PSProvider** parametr umożliwia wyświetlenie tylko tych dysków programu Windows PowerShell, które są obsługiwane przez określonego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="d02df-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="d02df-116">Na przykład, aby wyświetlić dyski środowiska Windows PowerShell, które są obsługiwane przez dostawcę programu Windows PowerShell w systemie plików, wpisz **elementu PSDrive Get** z **PSProvider** parametr i  **System plików** wartość:</span><span class="sxs-lookup"><span data-stu-id="d02df-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="d02df-117">Aby wyświetlić dyski środowiska Windows PowerShell, które reprezentują gałęzi rejestru, użyj **PSProvider** parametr, aby wyświetlić tylko dyski programu Windows PowerShell, które są obsługiwane przez dostawcę rejestru systemu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d02df-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

<pre>PS> Get-PSDrive -PSProvider Registry
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE</pre>

<span data-ttu-id="d02df-118">Można także użyć standardowych poleceń cmdlet lokalizacji z dyskami środowiska Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d02df-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

<pre>PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location
Path
----
HKLM:\SOFTWARE\Microsoft</pre>

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="d02df-119">Dodawanie nowego środowiska Windows PowerShell dysków (nowego elementu PSDrive)</span><span class="sxs-lookup"><span data-stu-id="d02df-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>
<span data-ttu-id="d02df-120">Można dodać dysków programu Windows PowerShell przy użyciu **elementu PSDrive nowy** polecenia.</span><span class="sxs-lookup"><span data-stu-id="d02df-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="d02df-121">Aby wyświetlić składnię dla **elementu PSDrive nowy** polecenia, wprowadź **Get-Command** z **składni** parametru:</span><span class="sxs-lookup"><span data-stu-id="d02df-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="d02df-122">Aby utworzyć nowy dysk programu Windows PowerShell, należy podać trzy parametry:</span><span class="sxs-lookup"><span data-stu-id="d02df-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="d02df-123">Nazwa dysku (możesz użyć dowolnego prawidłową nazwę środowiska Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="d02df-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="d02df-124">PSProvider (Użyj elementu "FileSystem" dla lokalizacji plików systemu i "Rejestru" w przypadku lokalizacji rejestru)</span><span class="sxs-lookup"><span data-stu-id="d02df-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="d02df-125">Oznacza to, ścieżka do katalogu głównego nowego dysku w folderze głównym</span><span class="sxs-lookup"><span data-stu-id="d02df-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="d02df-126">Na przykład dysk o nazwie "Office", który jest zamapowany na folder, który zawiera aplikacje Microsoft Office na komputerze, na przykład można utworzyć **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="d02df-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="d02df-127">Aby utworzyć dysk, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d02df-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="d02df-128">Ogólnie rzecz biorąc ścieżki nie jest rozróżniana.</span><span class="sxs-lookup"><span data-stu-id="d02df-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="d02df-129">Zobacz na nowy dysk programu Windows PowerShell, tak jak wszystkie dyski środowiska Windows PowerShell — za pomocą nazwy z dwukropkiem (**:**).</span><span class="sxs-lookup"><span data-stu-id="d02df-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="d02df-130">Dysk programu Windows PowerShell można wprowadzać wiele zadań znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="d02df-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="d02df-131">Na przykład niektóre z najważniejszych kluczy rejestru systemu Windows ma bardzo długi ścieżek, nadawania skomplikowane dostępu i trudne do zapamiętania.</span><span class="sxs-lookup"><span data-stu-id="d02df-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="d02df-132">Informacje o konfiguracji krytyczne znajduje się w obszarze **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="d02df-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="d02df-133">Do wyświetlania i zmieniania elementów w kluczu rejestru CurrentVersion, można utworzyć dysk programu Windows PowerShell, który jest osadzony w tym kluczu, wpisując:</span><span class="sxs-lookup"><span data-stu-id="d02df-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

<pre>PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...</pre>

<span data-ttu-id="d02df-134">Następnie możesz zmienić lokalizację do **cvkey:** dysków, tak jak każdy inny dysk: "</span><span class="sxs-lookup"><span data-stu-id="d02df-134">You can then change location to the **cvkey:** drive as you would any other drive:``</span></span>

`PS> cd cvkey:`

<span data-ttu-id="d02df-135">lub:</span><span class="sxs-lookup"><span data-stu-id="d02df-135">or:</span></span>

<pre>PS> Set-Location cvkey: -PassThru
Path
----
cvkey:\</pre>

<span data-ttu-id="d02df-136">Polecenia cmdlet New-elementu PsDrive dodaje nowy dysk tylko do bieżącej sesji programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d02df-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="d02df-137">Jeśli zamkniesz okno programu Windows PowerShell, nowego dysku zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="d02df-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="d02df-138">Aby zapisać dysk programu Windows PowerShell, użyj polecenia cmdlet Export-konsoli można wyeksportować bieżącej sesji programu Windows PowerShell, a następnie użyj PowerShell.exe **PSConsoleFile** parametru do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="d02df-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="d02df-139">Można również dodać nowy dysk do swojego profilu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d02df-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="d02df-140">Usuwanie środowiska Windows PowerShell dysków (elementu PSDrive Usuń)</span><span class="sxs-lookup"><span data-stu-id="d02df-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>
<span data-ttu-id="d02df-141">Można usunąć dysków z programu Windows PowerShell za pomocą **elementu PSDrive Usuń** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d02df-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="d02df-142">**Elementu PSDrive Usuń** polecenia cmdlet jest łatwy w użyciu; Aby usunąć określony dysk programu Windows PowerShell, wystarczy podać nazwę dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d02df-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="d02df-143">Na przykład jeśli dodano **pakietu Office:** dysk programu Windows PowerShell, jak pokazano w **elementu PSDrive nowy** temacie, można ją usunąć, wpisując:</span><span class="sxs-lookup"><span data-stu-id="d02df-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```
PS> Remove-PSDrive -Name Office
```

<span data-ttu-id="d02df-144">Aby usunąć **cvkey:** programu Windows PowerShell to dysk, również wyświetlane w **elementu PSDrive nowy** tematu, należy użyć następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d02df-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```
PS> Remove-PSDrive -Name cvkey
```

<span data-ttu-id="d02df-145">Łatwo usunąć dysk programu Windows PowerShell, ale nie można go usunąć, gdy są na dysku.</span><span class="sxs-lookup"><span data-stu-id="d02df-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="d02df-146">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d02df-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="d02df-147">Dodawanie i usuwanie dysków poza środowiska Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d02df-147">Adding and Removing Drives Outside Windows PowerShell</span></span>
<span data-ttu-id="d02df-148">Wykrywa, dysków z systemem plików, które zostały dodane lub usunięte w systemie Windows, w tym dyski sieciowe, które są mapowane, dysków USB, które są dołączone i dyski, które zostały usunięte za pomocą środowiska Windows PowerShell **net użyj** polecenia lub  **WScript.NetworkMapNetworkDrive** i **RemoveNetworkDrive** metody ze skryptu Windows Script Host (WSH).</span><span class="sxs-lookup"><span data-stu-id="d02df-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>

