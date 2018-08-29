---
ms.date: 08/14/2018
keywords: polecenia cmdlet programu PowerShell
title: Uruchamianie poleceń zdalnych
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133830"
---
# <a name="running-remote-commands"></a><span data-ttu-id="4474a-103">Uruchamianie poleceń zdalnych</span><span class="sxs-lookup"><span data-stu-id="4474a-103">Running Remote Commands</span></span>

<span data-ttu-id="4474a-104">Możesz uruchamiać polecenia w jednym węźle lub setek komputerów za pomocą jednego polecenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4474a-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="4474a-105">Program Windows PowerShell obsługuje przetwarzania zdalnego przy użyciu różnych technologii, takich jak usługi WMI, RPC i WS-Management.</span><span class="sxs-lookup"><span data-stu-id="4474a-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="4474a-106">Program PowerShell Core obsługuje WMI, usługi WS-Management i usług zdalnych SSH.</span><span class="sxs-lookup"><span data-stu-id="4474a-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="4474a-107">RPC nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="4474a-107">RPC is no longer supported.</span></span>

<span data-ttu-id="4474a-108">Aby uzyskać więcej informacji na temat komunikacji zdalnej w programie PowerShell Core zobacz następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="4474a-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="4474a-109">[SSH komunikacji zdalnej w programie PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="4474a-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="4474a-110">[Komunikacja zdalna usługi WS-Management, w programie PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="4474a-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="4474a-111">Komunikacji zdalnej programu Windows PowerShell bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4474a-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="4474a-112">Wiele poleceń cmdlet programu Windows PowerShell ma parametr ComputerName, który umożliwia zbieranie danych i zmienić ustawienia, na co najmniej jeden komputer zdalny.</span><span class="sxs-lookup"><span data-stu-id="4474a-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="4474a-113">Te polecenia cmdlet Użyj różnych protokołów komunikacyjnych i działa we wszystkich systemach operacyjnych Windows, bez żadnej specjalnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4474a-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="4474a-114">Te polecenia cmdlet obejmują:</span><span class="sxs-lookup"><span data-stu-id="4474a-114">These cmdlets include:</span></span>

- [<span data-ttu-id="4474a-115">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="4474a-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="4474a-116">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="4474a-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="4474a-117">Wyczyść w dzienniku zdarzeń</span><span class="sxs-lookup"><span data-stu-id="4474a-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="4474a-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="4474a-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="4474a-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="4474a-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="4474a-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="4474a-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="4474a-121">Get-Service</span><span class="sxs-lookup"><span data-stu-id="4474a-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="4474a-122">Set-Service</span><span class="sxs-lookup"><span data-stu-id="4474a-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="4474a-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="4474a-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="4474a-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="4474a-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="4474a-125">Zazwyczaj polecenia cmdlet, które obsługują komunikację zdalną bez specjalnej konfiguracji ma parametr ComputerName, a nie ma parametr sesji.</span><span class="sxs-lookup"><span data-stu-id="4474a-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="4474a-126">Aby znaleźć te polecenia cmdlet w sesji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="4474a-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="4474a-127">Komunikacji zdalnej programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4474a-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="4474a-128">Przy użyciu protokołu WS-Management, komunikacji zdalnej programu Windows PowerShell umożliwiają uruchamianie dowolnego polecenia programu Windows PowerShell na co najmniej jeden komputer zdalny.</span><span class="sxs-lookup"><span data-stu-id="4474a-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="4474a-129">Możesz ustanowienia połączeń trwałych, uruchamiania interaktywnych sesji i uruchamiać skrypty na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="4474a-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="4474a-130">Aby użyć komunikacji zdalnej programu Windows PowerShell, należy określić komputer zdalny do zdalnego zarządzania.</span><span class="sxs-lookup"><span data-stu-id="4474a-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="4474a-131">Aby uzyskać więcej informacji, w tym instrukcje, zobacz [o wymagania dotyczące zdalnego](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="4474a-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="4474a-132">Po skonfigurowaniu komunikacji zdalnej programu Windows PowerShell wiele strategii komunikacji zdalnej są dostępne dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="4474a-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="4474a-133">W tym artykule wymieniono kilka z nich.</span><span class="sxs-lookup"><span data-stu-id="4474a-133">This article lists just a few of them.</span></span> <span data-ttu-id="4474a-134">Aby uzyskać więcej informacji, zobacz [o zdalnym](/powershell/module/microsoft.powershell.core/about/about_remote).</span><span class="sxs-lookup"><span data-stu-id="4474a-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="4474a-135">Rozpoczynania interaktywnej sesji</span><span class="sxs-lookup"><span data-stu-id="4474a-135">Start an Interactive Session</span></span>

<span data-ttu-id="4474a-136">Aby rozpocząć interaktywnej sesji z jednym komputerem zdalnym, użyj [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4474a-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="4474a-137">Na przykład rozpoczynania interaktywnej sesji z komputerem zdalnym Serwer01, wpisz:</span><span class="sxs-lookup"><span data-stu-id="4474a-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="4474a-138">Zmiany wiersza polecenia, aby wyświetlić nazwę komputera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="4474a-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="4474a-139">Wszystkie wpisywane w wierszu polecenia Uruchom na komputerze zdalnym, a wyniki są wyświetlane na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4474a-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="4474a-140">Aby zakończyć interaktywną sesję, wpisz:</span><span class="sxs-lookup"><span data-stu-id="4474a-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="4474a-141">Aby uzyskać więcej informacji na temat polecenia cmdlet Enter-PSSession i PSSession zakończenia zobacz:</span><span class="sxs-lookup"><span data-stu-id="4474a-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="4474a-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="4474a-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="4474a-143">PSSession zakończenia</span><span class="sxs-lookup"><span data-stu-id="4474a-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="4474a-144">Uruchom polecenie zdalne</span><span class="sxs-lookup"><span data-stu-id="4474a-144">Run a Remote Command</span></span>

<span data-ttu-id="4474a-145">Aby uruchomić polecenie na co najmniej jeden komputer, użyj [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4474a-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="4474a-146">Na przykład, aby uruchomić [Get UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) Serwer01 i serwer02 komputerów zdalnych, wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="4474a-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="4474a-147">Dane wyjściowe są zwracane do komputera.</span><span class="sxs-lookup"><span data-stu-id="4474a-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="4474a-148">Uruchamianie skryptu</span><span class="sxs-lookup"><span data-stu-id="4474a-148">Run a Script</span></span>

<span data-ttu-id="4474a-149">Aby uruchomić skrypt w jeden lub wiele komputerów zdalnych, należy użyć parametru FilePath `Invoke-Command` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4474a-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="4474a-150">Skryptu musi być na lub jest dostępny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4474a-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="4474a-151">Wyniki są zwracane do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="4474a-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="4474a-152">Na przykład następujące polecenie uruchamia skrypt DiskCollect.ps1 na komputerach zdalnych, Serwer01 i serwer02.</span><span class="sxs-lookup"><span data-stu-id="4474a-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="4474a-153">Ustanowienia połączeń trwałych</span><span class="sxs-lookup"><span data-stu-id="4474a-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="4474a-154">Użyj `New-PSSession` polecenia cmdlet, aby utworzyć trwały sesji na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="4474a-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="4474a-155">Poniższy przykład tworzy sesje zdalne Serwer01 i serwer02.</span><span class="sxs-lookup"><span data-stu-id="4474a-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="4474a-156">Obiektów sesji są przechowywane w `$s` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4474a-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="4474a-157">Teraz, gdy sesje są ustanowione, możesz uruchomić dowolne polecenie w nich.</span><span class="sxs-lookup"><span data-stu-id="4474a-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="4474a-158">I sesje są trwałe, można zbierać dane z jednego polecenia i używać go w innym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="4474a-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="4474a-159">Na przykład następujące polecenie uruchamia polecenie Get-HotFix w sesji w zmiennej $s i zapisuje wyniki w zmiennej $h.</span><span class="sxs-lookup"><span data-stu-id="4474a-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="4474a-160">Utworzono zmienną $h we wszystkich sesjach w $s, ale nie istnieje w lokalnej sesji.</span><span class="sxs-lookup"><span data-stu-id="4474a-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="4474a-161">Teraz możesz używać danych w `$h` zmiennej z innymi poleceniami w tej samej sesji.</span><span class="sxs-lookup"><span data-stu-id="4474a-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="4474a-162">Wyniki są wyświetlane na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4474a-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="4474a-163">Przykład:</span><span class="sxs-lookup"><span data-stu-id="4474a-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="4474a-164">Zaawansowane komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="4474a-164">Advanced Remoting</span></span>

<span data-ttu-id="4474a-165">Zdalne zarządzanie programu Windows PowerShell po prostu zaczyna się tutaj.</span><span class="sxs-lookup"><span data-stu-id="4474a-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="4474a-166">Korzystając z poleceń cmdlet zainstalowanych za pomocą programu Windows PowerShell, można ustanowić i skonfigurować zdalnej sesji z lokalnymi i zdalnymi kończy się tworzenie dostosowanych i objęty ograniczeniami sesji, umożliwia użytkownikom import poleceń w sesji zdalnej, które faktycznie uruchomić niejawnie w sesji zdalnej, należy skonfigurować zabezpieczenia sesję zdalną i o wiele więcej.</span><span class="sxs-lookup"><span data-stu-id="4474a-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="4474a-167">Program Windows PowerShell zawiera dostawcę usługi WS-Management.</span><span class="sxs-lookup"><span data-stu-id="4474a-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="4474a-168">Tworzy dostawcę `WSMAN:` dysku, który pozwala nawigować po hierarchii ustawień konfiguracji na komputerze lokalnym i na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="4474a-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="4474a-169">Aby uzyskać więcej informacji na temat dostawcy usługi WS-Management, zobacz [dostawcy usługi WS-Management](https://technet.microsoft.com/library/dd819476.aspx) i [polecenia cmdlet dotyczące usługi WS-Management](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), lub w konsoli programu Windows PowerShell, wpisz `Get-Help wsman`.</span><span class="sxs-lookup"><span data-stu-id="4474a-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="4474a-170">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="4474a-170">For more information, see:</span></span>

- [<span data-ttu-id="4474a-171">Temat zdalnego — często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="4474a-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="4474a-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4474a-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="4474a-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="4474a-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="4474a-174">Aby uzyskać pomoc dotyczącą błędów usługami zdalnymi, zobacz [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="4474a-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="4474a-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4474a-175">See Also</span></span>

- [<span data-ttu-id="4474a-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="4474a-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="4474a-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="4474a-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="4474a-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="4474a-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="4474a-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="4474a-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="4474a-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="4474a-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="4474a-181">about_WS Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="4474a-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="4474a-182">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="4474a-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="4474a-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="4474a-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="4474a-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="4474a-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="4474a-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4474a-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="4474a-186">Dostawca usługi WS-Management</span><span class="sxs-lookup"><span data-stu-id="4474a-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md