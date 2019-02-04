---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686992"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="f50ad-102">Ulepszenia debugowania skryptów programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="f50ad-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="f50ad-103">Szereg ulepszeń zostały wprowadzone w programie PowerShell 5.0, aby ulepszyć środowisko debugowania:</span><span class="sxs-lookup"><span data-stu-id="f50ad-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="f50ad-104">Przerwij wszystko</span><span class="sxs-lookup"><span data-stu-id="f50ad-104">Break All</span></span>

<span data-ttu-id="f50ad-105">Konsola programu PowerShell i Windows PowerShell ISE teraz umożliwiają wkroczenia do debugera do uruchamiania skryptów.</span><span class="sxs-lookup"><span data-stu-id="f50ad-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="f50ad-106">Działa to zarówno lokalnych, jak i zdalnych sesji.</span><span class="sxs-lookup"><span data-stu-id="f50ad-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="f50ad-107">W konsoli, naciśnij klawisz **Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="f50ad-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="f50ad-108">W środowisku ISE, naciśnij klawisz **Ctrl + B**, lub użyj **Debuguj -> Przerwij wszystko** polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="f50ad-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="f50ad-109">Zdalne debugowanie i zdalne edytowanie plików w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f50ad-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="f50ad-110">Windows PowerShell ISE umożliwia teraz otwierać i edytować pliki w sesji zdalnej za pomocą polecenia PSEdit.</span><span class="sxs-lookup"><span data-stu-id="f50ad-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="f50ad-111">Na przykład można otworzyć pliku do edycji z wiersza polecenia w sesji zdalnej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f50ad-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="f50ad-112">Ponadto można edytować i zapisać zmiany w pliku zdalnego, który jest automatycznie otwierany w środowisku Windows PowerShell ISE, po osiągnięciu punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="f50ad-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="f50ad-113">Można teraz debugować plik skryptu, który jest uruchomiony na komputerze zdalnym, Edytuj plik, aby naprawić błąd, a następnie ponownie uruchom zmodyfikowany skrypt.</span><span class="sxs-lookup"><span data-stu-id="f50ad-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="f50ad-114">Debugowanie skryptów zaawansowane</span><span class="sxs-lookup"><span data-stu-id="f50ad-114">Advanced Script Debugging</span></span>

<span data-ttu-id="f50ad-115">Istnieją nowe, zaawansowane funkcje debugowania, które umożliwiają dołączanie do każdego procesu komputer lokalny, który został załadowany programu Windows PowerShell i debugowania dowolnego obszarach działania w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="f50ad-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="f50ad-116">Debugowanie obszarem działania</span><span class="sxs-lookup"><span data-stu-id="f50ad-116">Runspace Debugging</span></span>

<span data-ttu-id="f50ad-117">Nowe polecenia cmdlet zostały dodane, umożliwiające listy obszary bieżącego działania w ramach procesu i dołączyć do tego obszaru działania dotyczące debugowania skryptów konsoli środowiska Windows PowerShell lub debugera ISE:</span><span class="sxs-lookup"><span data-stu-id="f50ad-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="f50ad-118">Get-obszarem działania</span><span class="sxs-lookup"><span data-stu-id="f50ad-118">Get-Runspace</span></span>
-   <span data-ttu-id="f50ad-119">Obszar działania debugowania</span><span class="sxs-lookup"><span data-stu-id="f50ad-119">Debug-Runspace</span></span>
-   <span data-ttu-id="f50ad-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f50ad-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="f50ad-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f50ad-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="f50ad-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f50ad-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="f50ad-123">Dołącz do procesu hostingu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="f50ad-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="f50ad-124">Teraz można dołączyć do procesu dowolnego komputera, który został załadowany w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f50ad-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="f50ad-125">Możesz to zrobić, należy wprowadzić w interaktywnej sesji z procesem, podobnie jak możesz wprowadzić do interaktywnej sesji zdalnej, uruchamiając polecenie cmdlet Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="f50ad-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="f50ad-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f50ad-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="f50ad-127">Zakończ PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f50ad-127">Exit-PSHostProcess</span></span>
