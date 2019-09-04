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
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="df92d-103">Zarządzanie dyskami programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="df92d-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="df92d-104">*Dysk programu Windows PowerShell* to lokalizacja magazynu danych, do której można uzyskać dostęp do dysku systemu plików w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df92d-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="df92d-105">Dostawcy programu Windows PowerShell tworzą dyski, takie jak dyski systemu plików (w tym C: i D:), dyski rejestru (HKCU: i HKLM:) oraz dysk certyfikatu (certyfikat:) i można utworzyć własne dyski programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df92d-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="df92d-106">Te dyski są bardzo przydatne, ale są dostępne tylko w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df92d-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="df92d-107">Nie można uzyskać do nich dostępu przy użyciu innych narzędzi systemu Windows, takich jak Eksplorator plików lub cmd. exe.</span><span class="sxs-lookup"><span data-stu-id="df92d-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="df92d-108">Program Windows PowerShell korzysta z rzeczowników, **PSDrive**, dla poleceń, które działają z dyskami programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df92d-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="df92d-109">Aby uzyskać listę dysków programu Windows PowerShell w sesji programu Windows PowerShell, użyj polecenia cmdlet **Get-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="df92d-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

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

<span data-ttu-id="df92d-110">Mimo że dyski w wyświetlaczu różnią się w zależności od dysków w systemie, lista będzie wyglądać podobnie do danych wyjściowych polecenia **Get-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="df92d-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="df92d-111">Dyski systemu plików są podzbiorem dysków programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df92d-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="df92d-112">Dyski systemu plików można identyfikować według wpisu w kolumnie dostawca.</span><span class="sxs-lookup"><span data-stu-id="df92d-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="df92d-113">(Dyski systemu plików w programie Windows PowerShell są obsługiwane przez dostawcę systemu plików programu Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="df92d-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="df92d-114">Aby wyświetlić składnię polecenia cmdlet **Get-PSDrive** , wpisz polecenie **Get-Command** z parametrem **składni** :</span><span class="sxs-lookup"><span data-stu-id="df92d-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="df92d-115">Parametr **PSProvider** umożliwia wyświetlenie tylko dysków programu Windows PowerShell, które są obsługiwane przez określonego dostawcę.</span><span class="sxs-lookup"><span data-stu-id="df92d-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="df92d-116">Aby na przykład wyświetlić tylko dyski programu Windows PowerShell obsługiwane przez dostawcę systemu plików programu Windows PowerShell, wpisz polecenie **Get-PSDrive** z parametrem **PSProvider** i wartością systemu **plików** :</span><span class="sxs-lookup"><span data-stu-id="df92d-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="df92d-117">Aby wyświetlić dyski programu Windows PowerShell reprezentujące gałęzie rejestru, użyj parametru **PSProvider** , aby wyświetlić tylko dyski programu Windows PowerShell obsługiwane przez dostawcę rejestru programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="df92d-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="df92d-118">Można również użyć standardowych poleceń cmdlet lokalizacji z dyskami programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="df92d-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="df92d-119">Dodawanie nowych dysków programu Windows PowerShell (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="df92d-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="df92d-120">Możesz dodać własne dyski programu Windows PowerShell za pomocą polecenia **New-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="df92d-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="df92d-121">Aby uzyskać składnię polecenia **New-PSDrive** , wprowadź polecenie **Get-Command** z parametrem **składni** :</span><span class="sxs-lookup"><span data-stu-id="df92d-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="df92d-122">Aby utworzyć nowy dysk programu Windows PowerShell, należy podać trzy parametry:</span><span class="sxs-lookup"><span data-stu-id="df92d-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="df92d-123">Nazwa dysku (można użyć dowolnej prawidłowej nazwy programu Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="df92d-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="df92d-124">PSProvider (Użyj "FileSystem" dla lokalizacji systemu plików i "Registry" dla lokalizacji rejestru)</span><span class="sxs-lookup"><span data-stu-id="df92d-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="df92d-125">Katalog główny, czyli ścieżka do katalogu głównego nowego dysku</span><span class="sxs-lookup"><span data-stu-id="df92d-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="df92d-126">Można na przykład utworzyć dysk o nazwie "Office" mapowany do folderu zawierającego Microsoft Office aplikacje na komputerze, na przykład **C:\\program\\Files\\Microsoft Office Office11**.</span><span class="sxs-lookup"><span data-stu-id="df92d-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="df92d-127">Aby utworzyć dysk, wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="df92d-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="df92d-128">Ogólnie rzecz biorąc, ścieżki nie uwzględnia wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="df92d-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="df92d-129">Nowy dysk programu Windows PowerShell jest przywołuje się do wszystkich dysków programu Windows PowerShell — według nazwy i dwukropka ( **:** ).</span><span class="sxs-lookup"><span data-stu-id="df92d-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="df92d-130">Dysk programu Windows PowerShell może znacznie uprościć wykonywanie wielu zadań.</span><span class="sxs-lookup"><span data-stu-id="df92d-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="df92d-131">Na przykład niektóre najważniejsze klucze w rejestrze systemu Windows mają bardzo długie ścieżki, dzięki czemu trudno jest uzyskać dostęp i trudne do zapamiętania.</span><span class="sxs-lookup"><span data-stu-id="df92d-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="df92d-132">Krytyczne informacje o konfiguracji znajdują się **w\\obszarze HKEY_LOCAL_MACHINE\\Software\\\\Microsoft Windows CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="df92d-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="df92d-133">Aby wyświetlić i zmienić elementy w kluczu rejestru CurrentVersion, można utworzyć dysk programu Windows PowerShell, który jest odblokowany w tym kluczu, wpisując:</span><span class="sxs-lookup"><span data-stu-id="df92d-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="df92d-134">Następnie można zmienić lokalizację na dysk **cvkey:** tak jak każdy inny dysk:</span><span class="sxs-lookup"><span data-stu-id="df92d-134">You can then change location to the **cvkey:** drive as you would any other drive:</span></span>

```
PS> cd cvkey:
```

<span data-ttu-id="df92d-135">lub:</span><span class="sxs-lookup"><span data-stu-id="df92d-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="df92d-136">Polecenie cmdlet New-PsDrive dodaje nowy dysk tylko do bieżącej sesji programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df92d-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="df92d-137">Jeśli zamkniesz okno programu Windows PowerShell, nowy dysk zostanie utracony.</span><span class="sxs-lookup"><span data-stu-id="df92d-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="df92d-138">Aby zapisać dysk programu Windows PowerShell, użyj polecenia cmdlet Export-Console, aby wyeksportować bieżącą sesję programu Windows PowerShell, a następnie zaimportuj go za pomocą parametru **PSConsoleFile** PowerShell. exe.</span><span class="sxs-lookup"><span data-stu-id="df92d-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="df92d-139">Lub Dodaj nowy dysk do profilu środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df92d-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="df92d-140">Usuwanie dysków programu Windows PowerShell (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="df92d-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="df92d-141">Można usunąć dyski z programu Windows PowerShell za pomocą polecenia cmdlet **Remove-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="df92d-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="df92d-142">Polecenie cmdlet **Remove-PSDrive** jest łatwe w użyciu. Aby usunąć określony dysk programu Windows PowerShell, wystarczy podać nazwę dysku programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df92d-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="df92d-143">Na przykład, jeśli został dodany **pakiet Office:** Dysk programu Windows PowerShell, jak pokazano w temacie **New-PSDrive** , można go usunąć, wpisując:</span><span class="sxs-lookup"><span data-stu-id="df92d-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="df92d-144">Aby usunąć **cvkey:** Dysk programu Windows PowerShell, również przedstawiony w temacie **New-PSDrive** , użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="df92d-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="df92d-145">Można łatwo usunąć dysk programu Windows PowerShell, ale nie można go usunąć, gdy jesteś w stacji.</span><span class="sxs-lookup"><span data-stu-id="df92d-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="df92d-146">Przykład:</span><span class="sxs-lookup"><span data-stu-id="df92d-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="df92d-147">Dodawanie i usuwanie dysków poza programem Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="df92d-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="df92d-148">Program Windows PowerShell wykrywa dyski systemu plików, które są dodawane lub usuwane w systemie Windows, w tym dyski sieciowe, które są dołączone, a dyski, które są usuwane przy użyciu polecenia **net use** lub  **WScript. NetworkMapNetworkDrive** i **RemoveNetworkDrive** metody z skryptu hosta skryptów systemu Windows (WSH).</span><span class="sxs-lookup"><span data-stu-id="df92d-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>
