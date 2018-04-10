---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: dee5e8206c61d79faadf8573a82c74d4ac0fb8e0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="1bcf7-102">Ulepszenia debugowania skryptów programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bcf7-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="1bcf7-103">Wiele ulepszeń zostały wprowadzone w programie PowerShell 5.0 udoskonalenie debugowania:</span><span class="sxs-lookup"><span data-stu-id="1bcf7-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="1bcf7-104">Przerwij wszystkie</span><span class="sxs-lookup"><span data-stu-id="1bcf7-104">Break All</span></span>

<span data-ttu-id="1bcf7-105">Konsola programu PowerShell i Windows PowerShell ISE teraz umożliwiają wkroczenia do debugera do uruchamiania skryptów.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="1bcf7-106">Działa to zarówno lokalnych, jak i zdalnych sesji.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="1bcf7-107">W konsoli, naciśnij klawisz **klawisze Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="1bcf7-108">ISE, naciśnij klawisz **Ctrl + B**, lub użyj **debugowanie -> Przerwij wszystkie** polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="1bcf7-109">Debugowanie zdalne i zdalne edytowanie plików w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="1bcf7-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="1bcf7-110">Windows PowerShell ISE umożliwia teraz otworzyć i edytować pliki w sesji zdalnej, uruchamiając polecenie PSEdit.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="1bcf7-111">Na przykład można otworzyć pliku do edycji z wiersza polecenia w sesji zdalnej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1bcf7-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="1bcf7-112">Ponadto można edytować i zapisać zmiany w pliku zdalnego, który jest automatycznie otwierane w programie Windows PowerShell ISE po trafieniu punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="1bcf7-113">Teraz możesz debugowania pliku skryptu, który jest uruchomiony na komputerze zdalnym, edytować plik, aby naprawić błąd, a następnie ponownie uruchom zmodyfikowanego skryptu.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="1bcf7-114">Debugowanie skryptów zaawansowane</span><span class="sxs-lookup"><span data-stu-id="1bcf7-114">Advanced Script Debugging</span></span>

<span data-ttu-id="1bcf7-115">Istnieją nowe, zaawansowane funkcje debugowania, które umożliwiają dołączanie do każdy proces komputera lokalnego, który został załadowany środowiska Windows PowerShell i debugowania dowolnych obszarach działania w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="1bcf7-116">Debugowanie obszaru działania</span><span class="sxs-lookup"><span data-stu-id="1bcf7-116">Runspace Debugging</span></span>

<span data-ttu-id="1bcf7-117">Nowe polecenia cmdlet dodano umożliwiające listę obszarach bieżącego działania w ramach procesu i dołączyć do tego obszaru działania do debugowania skryptów konsoli środowiska Windows PowerShell lub debugera ISE:</span><span class="sxs-lookup"><span data-stu-id="1bcf7-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="1bcf7-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="1bcf7-118">Get-Runspace</span></span>
-   <span data-ttu-id="1bcf7-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="1bcf7-119">Debug-Runspace</span></span>
-   <span data-ttu-id="1bcf7-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="1bcf7-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="1bcf7-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="1bcf7-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="1bcf7-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="1bcf7-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="1bcf7-123">Dołączanie do procesu hostingu środowiska PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bcf7-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="1bcf7-124">Teraz można dołączyć do procesu dowolnego komputera, który ma środowiska Windows PowerShell, załadować.</span><span class="sxs-lookup"><span data-stu-id="1bcf7-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="1bcf7-125">W tym celu należy wprowadzić w sesji interaktywnej z procesem, podobnie jak wprowadzić w sesji interaktywnej zdalnego przy użyciu polecenia cmdlet Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="1bcf7-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="1bcf7-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="1bcf7-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="1bcf7-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="1bcf7-127">Exit-PSHostProcess</span></span>