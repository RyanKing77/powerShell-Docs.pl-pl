---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Ulepszenia debugowania skryptów programu PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856175"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="765e2-103">Ulepszenia debugowania skryptów programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="765e2-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="765e2-104">PowerShell 5.0 zawiera kilka ulepszeń, które usprawniają środowisko debugowania.</span><span class="sxs-lookup"><span data-stu-id="765e2-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="765e2-105">Przerwij wszystko</span><span class="sxs-lookup"><span data-stu-id="765e2-105">Break All</span></span>

<span data-ttu-id="765e2-106">Konsola programu PowerShell i środowisku PowerShell ISE teraz umożliwiają wkroczenia do debugera do uruchamiania skryptów.</span><span class="sxs-lookup"><span data-stu-id="765e2-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="765e2-107">Działa to zarówno lokalnych, jak i zdalnych sesji.</span><span class="sxs-lookup"><span data-stu-id="765e2-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="765e2-108">W konsoli, naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>Przerwij</kbd>.</span><span class="sxs-lookup"><span data-stu-id="765e2-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="765e2-109">W środowisku ISE, naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>B</kbd>, lub użyj **Debuguj -> Przerwij wszystko** polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="765e2-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="765e2-110">Zdalne debugowanie i zdalne edytowanie plików w środowisku PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="765e2-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="765e2-111">Program PowerShell ISE umożliwia teraz otwierać i edytować pliki w sesji zdalnej za pomocą polecenia PSEdit.</span><span class="sxs-lookup"><span data-stu-id="765e2-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="765e2-112">Na przykład można otworzyć pliku do edycji z wiersza polecenia w sesji zdalnej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="765e2-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="765e2-113">Ponadto można edytować i zapisać zmiany w pliku zdalnego, który jest automatycznie otwierany w środowisku PowerShell ISE, po osiągnięciu punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="765e2-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="765e2-114">Można teraz debugować plik skryptu, który jest uruchomiony na komputerze zdalnym, Edytuj plik, aby naprawić błąd, a następnie ponownie uruchom zmodyfikowany skrypt.</span><span class="sxs-lookup"><span data-stu-id="765e2-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="765e2-115">Debugowanie skryptów zaawansowane</span><span class="sxs-lookup"><span data-stu-id="765e2-115">Advanced Script Debugging</span></span>

<span data-ttu-id="765e2-116">Istnieją nowe, zaawansowane funkcje debugowania, które umożliwiają dołączanie do każdego procesu komputer lokalny, który został załadowany PowerShell i debugowania dowolnego obszarach działania w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="765e2-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="765e2-117">Debugowanie obszarem działania</span><span class="sxs-lookup"><span data-stu-id="765e2-117">Runspace Debugging</span></span>

<span data-ttu-id="765e2-118">Nowe polecenia cmdlet zostały dodane, umożliwiające listy obszary bieżącego działania w ramach procesu i dołączyć do tego obszaru działania dotyczące debugowania skryptów konsolę programu PowerShell lub środowisku PowerShell ISE debugera:</span><span class="sxs-lookup"><span data-stu-id="765e2-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="765e2-119">Get-obszarem działania</span><span class="sxs-lookup"><span data-stu-id="765e2-119">Get-Runspace</span></span>
- <span data-ttu-id="765e2-120">Obszar działania debugowania</span><span class="sxs-lookup"><span data-stu-id="765e2-120">Debug-Runspace</span></span>
- <span data-ttu-id="765e2-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="765e2-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="765e2-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="765e2-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="765e2-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="765e2-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="765e2-124">Dołącz do procesu hostingu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="765e2-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="765e2-125">Teraz można dołączyć do procesu dowolnego komputera, który został załadowany PowerShell.</span><span class="sxs-lookup"><span data-stu-id="765e2-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="765e2-126">Można to zrobić, należy wprowadzić w interaktywnej sesji z procesem hosta.</span><span class="sxs-lookup"><span data-stu-id="765e2-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="765e2-127">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="765e2-127">For more information, see:</span></span>

- [<span data-ttu-id="765e2-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="765e2-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="765e2-129">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="765e2-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
