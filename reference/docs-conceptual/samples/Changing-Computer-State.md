---
ms.date: 06/05/2017
keywords: PowerShell, polecenie cmdlet
title: Zmienianie stanu komputera
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386283"
---
# <a name="changing-computer-state"></a><span data-ttu-id="09655-103">Zmienianie stanu komputera</span><span class="sxs-lookup"><span data-stu-id="09655-103">Changing Computer State</span></span>

<span data-ttu-id="09655-104">Aby zresetować komputer w programie Windows PowerShell, należy użyć standardowego narzędzia wiersza polecenia, usługi WMI lub klasy CIM.</span><span class="sxs-lookup"><span data-stu-id="09655-104">To reset a computer in Windows PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span> <span data-ttu-id="09655-105">Chociaż używasz programu Windows PowerShell tylko do uruchamiania tego narzędzia, zapoznaj się z informacjami na temat zmiany stanu zasilacza komputera w programie Windows PowerShell. przedstawiono w nim pewne istotne informacje dotyczące pracy z narzędziami zewnętrznymi w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09655-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="09655-106">Blokowanie komputera</span><span class="sxs-lookup"><span data-stu-id="09655-106">Locking a Computer</span></span>

<span data-ttu-id="09655-107">Jedynym sposobem blokowania komputera bezpośrednio przy użyciu standardowych dostępnych narzędzi jest wywołanie funkcji **LockWorkstation ()** w **User32. dll**:</span><span class="sxs-lookup"><span data-stu-id="09655-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="09655-108">To polecenie natychmiast blokuje stację roboczą.</span><span class="sxs-lookup"><span data-stu-id="09655-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="09655-109">Używa *rundll32. exe*, który uruchamia biblioteki DLL systemu Windows (i zapisuje ich biblioteki do wielokrotnego użycia) do uruchamiania User32. dll, biblioteki funkcji zarządzania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="09655-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="09655-110">Po zablokowaniu stacji roboczej, gdy jest włączone szybkie przełączanie użytkowników, na przykład w systemie Windows XP, komputer wyświetla ekran logowania użytkownika zamiast uruchamiania wygaszacza ekranu bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="09655-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="09655-111">Aby zamknąć określone sesje na serwerze terminali, użyj narzędzia wiersza polecenia **tsshutdn. exe** .</span><span class="sxs-lookup"><span data-stu-id="09655-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="09655-112">Wylogowywanie z bieżącej sesji</span><span class="sxs-lookup"><span data-stu-id="09655-112">Logging Off the Current Session</span></span>

<span data-ttu-id="09655-113">Można użyć kilku różnych technik do wylogowywania sesji w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="09655-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="09655-114">Najprostszym sposobem jest użycie narzędzia wiersza polecenia Pulpit zdalny/Terminal Services, **Logoff. exe** (Aby uzyskać szczegółowe informacje, w wierszu poleceń programu Windows PowerShell wpisz **Logoff/?** ).</span><span class="sxs-lookup"><span data-stu-id="09655-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="09655-115">Aby wylogować bieżącą aktywną sesję, wpisz polecenie **Logoff** bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="09655-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="09655-116">Można również użyć narzędzia **Shutdown. exe** z opcją wylogowania:</span><span class="sxs-lookup"><span data-stu-id="09655-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="09655-117">Innym rozwiązaniem jest użycie usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="09655-117">Another option is to use WMI.</span></span> <span data-ttu-id="09655-118">Klasa Win32_OperatingSystem ma metodę Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="09655-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="09655-119">Wywoływanie metody z flagą 0 inicjuje wylogowanie:</span><span class="sxs-lookup"><span data-stu-id="09655-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="09655-120">Aby uzyskać więcej informacji i znaleźć inne funkcje metody Win32Shutdown, zobacz "Metoda Win32Shutdown klasy Win32_OperatingSystem" w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="09655-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

<span data-ttu-id="09655-121">Na koniec można użyć modelu CIM z tą samą klasą Win32_OperatingSystem, jak opisano powyżej w metodzie WMI.</span><span class="sxs-lookup"><span data-stu-id="09655-121">Finally you can use CIM with the same Win32_OperatingSystem class as described above in the WMI method.</span></span>

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="09655-122">Zamykanie lub ponowne uruchamianie komputera</span><span class="sxs-lookup"><span data-stu-id="09655-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="09655-123">Zamykanie i ponowne uruchamianie komputerów jest zwykle tymi samymi typami zadań.</span><span class="sxs-lookup"><span data-stu-id="09655-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="09655-124">Narzędzia, które wyłączają komputer, będą na ogół również ponownie uruchomione i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="09655-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="09655-125">Dostępne są dwie proste opcje ponownego uruchamiania komputera z programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09655-125">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="09655-126">Użyj programu TSShutdn. exe lub Shutdown. exe z odpowiednimi argumentami.</span><span class="sxs-lookup"><span data-stu-id="09655-126">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="09655-127">Możesz uzyskać szczegółowe informacje dotyczące użycia z programu **tsshutdn. exe/?**</span><span class="sxs-lookup"><span data-stu-id="09655-127">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="09655-128">lub **Shutdown. exe/?** .</span><span class="sxs-lookup"><span data-stu-id="09655-128">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="09655-129">Można również wykonywać operacje zamykania i ponownego uruchamiania bezpośrednio z programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="09655-129">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="09655-130">Aby zamknąć komputer, użyj polecenia Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="09655-130">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="09655-131">Aby ponownie uruchomić system operacyjny, użyj polecenia Uruchom ponownie komputer.</span><span class="sxs-lookup"><span data-stu-id="09655-131">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="09655-132">Aby wymusić natychmiastowe ponowne uruchomienie komputera, użyj parametru-Force.</span><span class="sxs-lookup"><span data-stu-id="09655-132">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
