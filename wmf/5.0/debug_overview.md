---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: aaf1809277f072c82e5a1a862ea64b75586e32d1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="30bd0-102">Ulepszenia debugowania skryptu PowerShell</span><span class="sxs-lookup"><span data-stu-id="30bd0-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="30bd0-103">Wiele ulepszeń zostały wprowadzone w programie PowerShell 5.0 udoskonalenie debugowania:</span><span class="sxs-lookup"><span data-stu-id="30bd0-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="30bd0-104">Przerwij wszystkie</span><span class="sxs-lookup"><span data-stu-id="30bd0-104">Break All</span></span>

<span data-ttu-id="30bd0-105">Konsola programu PowerShell i Windows PowerShell ISE teraz umożliwiają wkroczenia do debugera do uruchamiania skryptów.</span><span class="sxs-lookup"><span data-stu-id="30bd0-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="30bd0-106">Działa to zarówno lokalnych, jak i zdalnych sesji.</span><span class="sxs-lookup"><span data-stu-id="30bd0-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="30bd0-107">W konsoli, naciśnij klawisz **klawisze Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="30bd0-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="30bd0-108">ISE, naciśnij klawisz **Ctrl + B**, lub użyj **debugowanie -> Przerwij wszystkie** polecenia menu.</span><span class="sxs-lookup"><span data-stu-id="30bd0-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="30bd0-109">Debugowanie zdalne i zdalne edytowanie plików w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="30bd0-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="30bd0-110">Windows PowerShell ISE umożliwia teraz otworzyć i edytować pliki w sesji zdalnej, uruchamiając polecenie PSEdit.</span><span class="sxs-lookup"><span data-stu-id="30bd0-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="30bd0-111">Na przykład można otworzyć pliku do edycji z wiersza polecenia w sesji zdalnej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="30bd0-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="30bd0-112">Ponadto można edytować i zapisać zmiany w pliku zdalnego, który jest automatycznie otwierane w programie Windows PowerShell ISE po trafieniu punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="30bd0-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="30bd0-113">Teraz możesz debugowania pliku skryptu, który jest uruchomiony na komputerze zdalnym, edytować plik, aby naprawić błąd, a następnie ponownie uruchom zmodyfikowanego skryptu.</span><span class="sxs-lookup"><span data-stu-id="30bd0-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="30bd0-114">Debugowanie skryptów zaawansowane</span><span class="sxs-lookup"><span data-stu-id="30bd0-114">Advanced Script Debugging</span></span>

<span data-ttu-id="30bd0-115">Istnieją nowe, zaawansowane funkcje debugowania, które umożliwiają dołączanie do każdy proces komputera lokalnego, który został załadowany środowiska Windows PowerShell i debugowania dowolnych obszarach działania w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="30bd0-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="30bd0-116">Debugowanie obszaru działania</span><span class="sxs-lookup"><span data-stu-id="30bd0-116">Runspace Debugging</span></span>

<span data-ttu-id="30bd0-117">Nowe polecenia cmdlet dodano umożliwiające listę obszarach bieżącego działania w ramach procesu i dołączyć do tego obszaru działania do debugowania skryptów konsoli środowiska Windows PowerShell lub debugera ISE:</span><span class="sxs-lookup"><span data-stu-id="30bd0-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="30bd0-118">Get-obszaru działania</span><span class="sxs-lookup"><span data-stu-id="30bd0-118">Get-Runspace</span></span>
-   <span data-ttu-id="30bd0-119">Obszarze działania debugowania</span><span class="sxs-lookup"><span data-stu-id="30bd0-119">Debug-Runspace</span></span>
-   <span data-ttu-id="30bd0-120">Włącz RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="30bd0-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="30bd0-121">Wyłącz RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="30bd0-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="30bd0-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="30bd0-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="30bd0-123">Dołączanie do procesu hostingu środowiska PowerShell</span><span class="sxs-lookup"><span data-stu-id="30bd0-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="30bd0-124">Teraz można dołączyć do procesu dowolnego komputera, który ma środowiska Windows PowerShell, załadować.</span><span class="sxs-lookup"><span data-stu-id="30bd0-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="30bd0-125">W tym celu należy wprowadzić w sesji interaktywnej z procesem, podobnie jak wprowadzić w sesji interaktywnej zdalnego przy użyciu polecenia cmdlet Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="30bd0-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="30bd0-126">Wprowadź PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="30bd0-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="30bd0-127">PSHostProcess zakończenia</span><span class="sxs-lookup"><span data-stu-id="30bd0-127">Exit-PSHostProcess</span></span>

