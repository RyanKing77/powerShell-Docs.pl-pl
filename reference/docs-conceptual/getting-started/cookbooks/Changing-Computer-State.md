---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zmienianie stanu komputera
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: 3d3983c6d9e9b11db62bd71805da51be83331fdb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="changing-computer-state"></a><span data-ttu-id="1c40e-103">Zmienianie stanu komputera</span><span class="sxs-lookup"><span data-stu-id="1c40e-103">Changing Computer State</span></span>

<span data-ttu-id="1c40e-104">Resetowanie komputera w programie Windows PowerShell, przy użyciu standardowego narzędzia wiersza polecenia lub klasy WMI.</span><span class="sxs-lookup"><span data-stu-id="1c40e-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="1c40e-105">Mimo że używasz programu Windows PowerShell do uruchamiania narzędzia tylko, poznanie zmiany stanu zasilania komputera w programie Windows PowerShell ilustruje niektóre ważne informacje o pracy z zewnętrznych narzędzi w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c40e-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="1c40e-106">Blokowanie komputera</span><span class="sxs-lookup"><span data-stu-id="1c40e-106">Locking a Computer</span></span>

<span data-ttu-id="1c40e-107">Jest jedynym sposobem, aby zablokować komputer bezpośrednio przy użyciu standardowych narzędzi dostępnych do wywołania **LockWorkstation()** działać w **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="1c40e-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="1c40e-108">To polecenie natychmiast blokuje stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="1c40e-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="1c40e-109">Używa *rundll32.exe*, który uruchamia biblioteki DLL systemu Windows (i zapisanie ich biblioteki do wielokrotnego użytku) do uruchamiania user32.dll, biblioteka funkcji zarządzania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1c40e-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="1c40e-110">Po zablokowaniu stacji roboczej włączonym szybkiego przełączania użytkowników, takich jak w systemie Windows XP, komputer wyświetla ekran logowania użytkownika, a nie rozpoczyna wygaszacz ekranu bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1c40e-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="1c40e-111">Aby zamknąć określonej sesji na serwer terminali, należy użyć **tsshutdn.exe** narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1c40e-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="1c40e-112">Wylogowywanie bieżącej sesji</span><span class="sxs-lookup"><span data-stu-id="1c40e-112">Logging Off the Current Session</span></span>

<span data-ttu-id="1c40e-113">Można użyć kilku różnych technik wylogowywanie sesji w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="1c40e-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="1c40e-114">Najprostszym sposobem jest użycie narzędzia wiersza polecenia usługi zdalnego pulpitu/Terminal **logoff.exe** (Aby uzyskać więcej informacji, w wierszu polecenia programu Windows PowerShell wpisz **wylogowanie /?**).</span><span class="sxs-lookup"><span data-stu-id="1c40e-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="1c40e-115">Aby wylogować się z bieżącym aktywnej sesji, wpisz **wylogowywania** bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="1c40e-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="1c40e-116">Można również użyć **shutdown.exe** narzędzie z opcją jego wylogowaniu:</span><span class="sxs-lookup"><span data-stu-id="1c40e-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="1c40e-117">Trzecia opcja jest korzystanie z usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="1c40e-117">A third option is to use WMI.</span></span> <span data-ttu-id="1c40e-118">Klasy Win32_OperatingSystem ma metodę Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="1c40e-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="1c40e-119">Wywoływanie metody z ustawioną flagą 0 inicjuje wylogowaniu:</span><span class="sxs-lookup"><span data-stu-id="1c40e-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="1c40e-120">Aby uzyskać więcej informacji, a także znalezienia innych funkcji Metoda Win32Shutdown zobacz "Win32Shutdown metoda z klasy Win32_OperatingSystem" w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="1c40e-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="1c40e-121">Wyłączanie lub ponowne uruchomienie komputera</span><span class="sxs-lookup"><span data-stu-id="1c40e-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="1c40e-122">Zamykanie i ponowne uruchamianie komputerów są zwykle te same rodzaje zadań.</span><span class="sxs-lookup"><span data-stu-id="1c40e-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="1c40e-123">Narzędzia, które zamykanie komputera zazwyczaj uruchomi go również — i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="1c40e-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="1c40e-124">Dostępne są dwie opcje prostego do ponownego uruchomienia komputera w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c40e-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="1c40e-125">Za pomocą Tsshutdn.exe lub Shutdown.exe odpowiednie argumenty.</span><span class="sxs-lookup"><span data-stu-id="1c40e-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="1c40e-126">Można uzyskać informacji o szczegółowe dane użycia **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="1c40e-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="1c40e-127">lub **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="1c40e-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="1c40e-128">Można również wykonać zamknięcia i ponownego uruchamiania działania za pomocą **Win32_OperatingSystem** bezpośrednio z Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c40e-128">You can also perform shutdown and restart operations by using **Win32_OperatingSystem** directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="1c40e-129">Aby wyłączyć komputer, należy użyć metody Win32Shutdown z **1** flagi.</span><span class="sxs-lookup"><span data-stu-id="1c40e-129">To shut down the computer, use the Win32Shutdown method with the **1** flag.</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

<span data-ttu-id="1c40e-130">Aby ponownie uruchomić system operacyjny, należy użyć metody Win32Shutdown z **2** flagi.</span><span class="sxs-lookup"><span data-stu-id="1c40e-130">To restart the operating system, use the Win32Shutdown method with the **2** flag.</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```