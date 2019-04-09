---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zarządzanie dyskami programu Windows PowerShell
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: 9ac5136fb28b450ea6397cab2f36082c50f22e1f
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293252"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="22323-103">Zarządzanie dyskami programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="22323-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="22323-104">A *dysk programu Windows PowerShell* prowadzi do lokalizacji magazynu danych, której będziesz mieć dostęp, np. dysku systemu plików, w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22323-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="22323-105">Dostawcy programu Windows PowerShell Utwórz niektórych dysków, takich jak system plików stacje dysków (w tym C: i D:), rejestrem dysków (HKCU: i HKLM:) i dysku certyfikatu (certyfikatu:), można także tworzyć własne dyski programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22323-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="22323-106">Dyski te są bardzo przydatne, ale są one dostępne tylko w ramach programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22323-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="22323-107">Nie masz dostępu do nich przy użyciu innych narzędzi Windows, takich jak Eksplorator plików lub Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="22323-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="22323-108">Windows PowerShell korzysta z rzeczownik, **PSDrive**, poleceń, które działają przy użyciu programu Windows PowerShell dysków.</span><span class="sxs-lookup"><span data-stu-id="22323-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="22323-109">Lista programu Windows PowerShell dysków w sesji środowiska Windows PowerShell, użyj **Get PSDrive** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22323-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

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

<span data-ttu-id="22323-110">Chociaż dyski na wyświetlaczu różnią się z stacje w systemie, lista będzie wyglądać podobnie do danych wyjściowych **Get PSDrive** przedstawionego powyżej polecenia.</span><span class="sxs-lookup"><span data-stu-id="22323-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="22323-111">Dyski systemu plików są podzbiorem dysków programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22323-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="22323-112">Można zidentyfikować dysków z systemem plików we wpisie systemu plików, w kolumnie dostawcy.</span><span class="sxs-lookup"><span data-stu-id="22323-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="22323-113">(Dysków z systemem plików w programie Windows PowerShell są obsługiwane przez dostawcę systemu plików programu Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="22323-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="22323-114">Aby wyświetlić składnię **Get PSDrive** polecenia cmdlet, wpisz **Get-Command** polecenia **składni** parametru:</span><span class="sxs-lookup"><span data-stu-id="22323-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="22323-115">**PSProvider** parametr umożliwia wyświetlenie tylko tych z programu Windows PowerShell dyski, które są obsługiwane przez określonego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="22323-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="22323-116">Na przykład, aby wyświetlić tylko dyski programu Windows PowerShell, które są obsługiwane przez dostawcę systemu plików programu Windows PowerShell, wpisz **Get PSDrive** polecenia **PSProvider** parametr i  **System plików** wartość:</span><span class="sxs-lookup"><span data-stu-id="22323-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="22323-117">Aby wyświetlić dyski programu Windows PowerShell, które reprezentują gałęzi rejestru, użyj **PSProvider** parametru, aby wyświetlić tylko dyski programu Windows PowerShell, które są obsługiwane przez dostawcę programu Windows PowerShell rejestru:</span><span class="sxs-lookup"><span data-stu-id="22323-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="22323-118">Umożliwia także standardowych poleceń cmdlet lokalizacji z stacje programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="22323-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="22323-119">Dodawanie nowych Windows PowerShell dyski (nowe PSDrive)</span><span class="sxs-lookup"><span data-stu-id="22323-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="22323-120">Można dodać dysków programu Windows PowerShell, za pomocą **New PSDrive** polecenia.</span><span class="sxs-lookup"><span data-stu-id="22323-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="22323-121">Aby wyświetlić składnię dla **New PSDrive** polecenia, wprowadź **Get-Command** polecenia **składni** parametru:</span><span class="sxs-lookup"><span data-stu-id="22323-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="22323-122">Aby utworzyć nowy dysk programu Windows PowerShell, należy podać trzy parametry:</span><span class="sxs-lookup"><span data-stu-id="22323-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="22323-123">Nazwa dysku (możesz użyć Dowolna prawidłowa nazwa środowiska Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="22323-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="22323-124">PSProvider (Użyj "System plików" dla lokalizacji systemu plików i "Rejestru" w lokalizacji rejestru)</span><span class="sxs-lookup"><span data-stu-id="22323-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="22323-125">Oznacza to ścieżki do katalogu głównego nowego dysku w katalogu głównym</span><span class="sxs-lookup"><span data-stu-id="22323-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="22323-126">Na przykład dysk o nazwie "Office", który jest zamapowany do folderu, który zawiera aplikacje Microsoft Office na komputerze, na przykład można utworzyć **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="22323-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="22323-127">Aby utworzyć dysk, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="22323-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="22323-128">Ogólnie rzecz biorąc ścieżek nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="22323-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="22323-129">Możesz odwołać się do nowy dysk programu Windows PowerShell, tak jak wszystkie dyski programu Windows PowerShell — za pomocą nazwy z dwukropkiem (**:**).</span><span class="sxs-lookup"><span data-stu-id="22323-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="22323-130">Dysk programu Windows PowerShell można wykonać wiele zadań znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="22323-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="22323-131">Na przykład niektóre z najważniejszych kluczy w rejestrze systemu Windows mają bardzo długich ścieżek, kłopotliwe dostępu i trudne do zapamiętania, dzięki czemu.</span><span class="sxs-lookup"><span data-stu-id="22323-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="22323-132">Informacje o konfiguracji krytycznych znajduje się w obszarze **HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="22323-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="22323-133">Do wyświetlania i zmieniania elementów w kluczu rejestru CurrentVersion, możesz utworzyć dysk programu Windows PowerShell, który jest ścieżką w tego klucza, wpisując:</span><span class="sxs-lookup"><span data-stu-id="22323-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="22323-134">Następnie można zmienić lokalizację, aby **cvkey:** dysku, tak jak każdy inny dysk:''</span><span class="sxs-lookup"><span data-stu-id="22323-134">You can then change location to the **cvkey:** drive as you would any other drive:\`\`</span></span>

`PS> cd cvkey:`

<span data-ttu-id="22323-135">lub:</span><span class="sxs-lookup"><span data-stu-id="22323-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="22323-136">Polecenie cmdlet New-PsDrive dodaje nowy dysk tylko do bieżącej sesji programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22323-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="22323-137">Jeśli zamkniesz okno programu Windows PowerShell, nowego dysku zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="22323-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="22323-138">Aby zapisać dysk programu Windows PowerShell, użyj polecenia cmdlet Export-konsoli można wyeksportować bieżącej sesji programu Windows PowerShell, a następnie użyj PowerShell.exe **PSConsoleFile** parametru, aby go zaimportować.</span><span class="sxs-lookup"><span data-stu-id="22323-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="22323-139">Lub Dodaj nowy dysk do Twojego profilu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22323-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="22323-140">Usuwanie środowiska Windows PowerShell dyski (Usuń PSDrive)</span><span class="sxs-lookup"><span data-stu-id="22323-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="22323-141">Dyski można usunąć za pomocą programu Windows PowerShell, za pomocą **PSDrive Usuń** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22323-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="22323-142">**PSDrive Usuń** polecenia cmdlet jest łatwa w użyciu; Aby usunąć określony dysk programu Windows PowerShell, wystarczy podać nazwę dysk programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22323-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="22323-143">Na przykład, jeśli dodano **pakietu Office:** Dysk programu Windows PowerShell, jak pokazano na **New PSDrive** tematu, możesz go usunąć, wpisując:</span><span class="sxs-lookup"><span data-stu-id="22323-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="22323-144">Aby usunąć **cvkey:** Programu Windows PowerShell to dysk, również w pokazywane **PSDrive nowy** tematu, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="22323-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="22323-145">Można łatwo usunąć dysk programu Windows PowerShell, ale nie można go usunąć, gdy jesteś w stacji dysków.</span><span class="sxs-lookup"><span data-stu-id="22323-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="22323-146">Przykład:</span><span class="sxs-lookup"><span data-stu-id="22323-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="22323-147">Dodawanie i usuwanie dysków poza programem Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="22323-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="22323-148">Wykrywa, dysków z systemem plików, które są dodawane lub usuwane w Windows, w tym dyski sieciowe, które są mapowane, dyski USB, które są dołączone i dyski, które są usuwane przy użyciu programu Windows PowerShell **net użyj** polecenia lub  **WScript.NetworkMapNetworkDrive** i **RemoveNetworkDrive** metody pochodzące ze skryptu Windows Script Host (WSH).</span><span class="sxs-lookup"><span data-stu-id="22323-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>