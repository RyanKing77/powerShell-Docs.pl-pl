---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Zmienianie stanu komputera
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: f8a2ed6a1a0390021eb633c9af64a725146ad136
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984208"
---
# <a name="changing-computer-state"></a><span data-ttu-id="1fd05-103">Zmienianie stanu komputera</span><span class="sxs-lookup"><span data-stu-id="1fd05-103">Changing Computer State</span></span>

<span data-ttu-id="1fd05-104">Można zresetować komputera w programie Windows PowerShell, użyj standardowych narzędzi wiersza polecenia lub klasy WMI.</span><span class="sxs-lookup"><span data-stu-id="1fd05-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="1fd05-105">Mimo, że używasz programu Windows PowerShell tylko po to, aby uruchomić narzędzie, jak zmienić stanu zasilania komputera w programie Windows PowerShell ilustruje niektóre ważne informacje o pracy z zewnętrznych narzędzi w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fd05-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="1fd05-106">Blokowanie komputera</span><span class="sxs-lookup"><span data-stu-id="1fd05-106">Locking a Computer</span></span>

<span data-ttu-id="1fd05-107">Jedynym sposobem, aby zablokować komputer bezpośrednio przy użyciu standardowych narzędzi dostępnych jest wywołanie **LockWorkstation()** działa w programach **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="1fd05-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="1fd05-108">To polecenie natychmiast blokuje stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="1fd05-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="1fd05-109">Używa ona *rundll32.exe*, który uruchamia Windows biblioteki dll (i zapisuje ich bibliotek do wielokrotnego użytku) do uruchamiania user32.dll, bibliotekę funkcji zarządzania Windows.</span><span class="sxs-lookup"><span data-stu-id="1fd05-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="1fd05-110">Gdy możesz zablokować stacji roboczej podczas szybkiego przełączania użytkowników jest włączone, takie jak Windows XP, komputer wyświetli ekran logowania użytkownika, a nie od bieżącego użytkownika wygaszacz ekranu.</span><span class="sxs-lookup"><span data-stu-id="1fd05-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="1fd05-111">Aby zamknąć określonej sesji na serwerze terminali, należy użyć **tsshutdn.exe** narzędzie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1fd05-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="1fd05-112">Trwa wylogowywanie w bieżącej sesji</span><span class="sxs-lookup"><span data-stu-id="1fd05-112">Logging Off the Current Session</span></span>

<span data-ttu-id="1fd05-113">Aby wylogować sesji w systemie lokalnym, można użyć kilku różnych technik.</span><span class="sxs-lookup"><span data-stu-id="1fd05-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="1fd05-114">Najprostszym sposobem jest użycie narzędzia wiersza polecenia zdalnego pulpitu/usługi terminalowe **logoff.exe** (Aby uzyskać szczegółowe informacje w wierszu polecenia programu Windows PowerShell wpisz **wylogowania /?**).</span><span class="sxs-lookup"><span data-stu-id="1fd05-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="1fd05-115">Aby wylogować się z bieżącej aktywnej sesji, wpisz **wylogowania** bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="1fd05-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="1fd05-116">Można również użyć **shutdown.exe** narzędzia z opcją jego wylogowania:</span><span class="sxs-lookup"><span data-stu-id="1fd05-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="1fd05-117">Trzecią opcją jest korzystanie z usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="1fd05-117">A third option is to use WMI.</span></span> <span data-ttu-id="1fd05-118">Klasy Win32_OperatingSystem ma metodę Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="1fd05-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="1fd05-119">Wywoływanie metody z flagą 0 inicjuje wylogowaniu:</span><span class="sxs-lookup"><span data-stu-id="1fd05-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="1fd05-120">Aby uzyskać więcej informacji i znaleźć inne funkcje Metoda Win32Shutdown zobacz "Win32Shutdown metody z klasy Win32_OperatingSystem" w bibliotece MSDN.</span><span class="sxs-lookup"><span data-stu-id="1fd05-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="1fd05-121">Zamykanie lub ponowne uruchomienie komputera</span><span class="sxs-lookup"><span data-stu-id="1fd05-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="1fd05-122">Zamykanie i ponowne uruchamianie komputerów są zwykle te same typy zadań.</span><span class="sxs-lookup"><span data-stu-id="1fd05-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="1fd05-123">Narzędzia, które zamykanie komputera uruchomi ogólnie ją ponownie także — i odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="1fd05-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="1fd05-124">Istnieją dwie proste opcje ponownego uruchamiania komputera za pomocą programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fd05-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="1fd05-125">Za pomocą Tsshutdn.exe lub Shutdown.exe odpowiednie argumenty.</span><span class="sxs-lookup"><span data-stu-id="1fd05-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="1fd05-126">Można uzyskać informacji o szczegółowym zestawieniem użycia **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="1fd05-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="1fd05-127">lub **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="1fd05-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="1fd05-128">Możesz również wykonać zamknięcia i ponownego uruchamiania działania bezpośrednio z programu Windows PowerShell również.</span><span class="sxs-lookup"><span data-stu-id="1fd05-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="1fd05-129">Aby wyłączyć komputer, użyj polecenia Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="1fd05-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="1fd05-130">Aby ponownie uruchomić system operacyjny, użyj polecenia Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="1fd05-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="1fd05-131">Aby wymusić natychmiastowe ponowne uruchomienie komputera, użyj parametru - Force.</span><span class="sxs-lookup"><span data-stu-id="1fd05-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
