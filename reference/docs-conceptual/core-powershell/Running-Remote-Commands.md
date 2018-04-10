---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Uruchamianie poleceń zdalnych
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: eb9f0ce0102de13d4fcd1d51f0e9174e9d5c340c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="running-remote-commands"></a><span data-ttu-id="67556-103">Uruchamianie poleceń zdalnych</span><span class="sxs-lookup"><span data-stu-id="67556-103">Running Remote Commands</span></span>

<span data-ttu-id="67556-104">Polecenia można wykonać na co najmniej setek komputerów za pomocą jednego polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67556-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="67556-105">Program Windows PowerShell obsługuje przetwarzania zdalnego przy użyciu różnych technologii, w tym usługi WMI, RPC i WS-Management.</span><span class="sxs-lookup"><span data-stu-id="67556-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-in-powershell-core"></a><span data-ttu-id="67556-106">Usługi zdalne środowiska PowerShell główną</span><span class="sxs-lookup"><span data-stu-id="67556-106">Remoting in PowerShell Core</span></span>

<span data-ttu-id="67556-107">Jądro programu PowerShell, nowszej wersji programu PowerShell w systemach Windows, system macOS i Linux, obsługuje usługi WMI, WS-Management i usług zdalnych SSH.</span><span class="sxs-lookup"><span data-stu-id="67556-107">PowerShell Core, the newer edition of PowerShell on Windows, macOS, and Linux, supports WMI, WS-Management, and SSH remoting.</span></span>
<span data-ttu-id="67556-108">(RPC nie jest już obsługiwany.)</span><span class="sxs-lookup"><span data-stu-id="67556-108">(RPC is no longer supported.)</span></span>

<span data-ttu-id="67556-109">Aby uzyskać więcej informacji na temat konfigurowania to zobacz:</span><span class="sxs-lookup"><span data-stu-id="67556-109">For more information on setting this up, see:</span></span>

* <span data-ttu-id="67556-110">[SSH komunikację zdalną środowiska PowerShell główną][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="67556-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="67556-111">[Usługi zdalne WSMan główną programu PowerShell][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="67556-111">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="67556-112">Komunikację zdalną bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="67556-112">Remoting Without Configuration</span></span>

<span data-ttu-id="67556-113">Wiele poleceń cmdlet programu Windows PowerShell ma parametr ComputerName, który umożliwia zbieranie danych i zmienić ustawienia, na co najmniej jeden komputer zdalny.</span><span class="sxs-lookup"><span data-stu-id="67556-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="67556-114">We wszystkich systemach operacyjnych Windows, które środowiska Windows PowerShell obsługuje bez żadnej specjalnej konfiguracji korzystają z różnych technologii komunikacji i wiele pracy.</span><span class="sxs-lookup"><span data-stu-id="67556-114">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="67556-115">Te polecenia cmdlet obejmują:</span><span class="sxs-lookup"><span data-stu-id="67556-115">These cmdlets include:</span></span>

* [<span data-ttu-id="67556-116">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="67556-116">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="67556-117">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="67556-117">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="67556-118">Wyczyść EventLog</span><span class="sxs-lookup"><span data-stu-id="67556-118">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="67556-119">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="67556-119">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="67556-120">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="67556-120">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
* [<span data-ttu-id="67556-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="67556-121">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="67556-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="67556-122">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="67556-123">Set-Service</span><span class="sxs-lookup"><span data-stu-id="67556-123">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="67556-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="67556-124">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="67556-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="67556-125">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="67556-126">Zazwyczaj polecenia cmdlet, które obsługują komunikację zdalną bez specjalnej konfiguracji ma parametr ComputerName, a nie ma parametru sesji.</span><span class="sxs-lookup"><span data-stu-id="67556-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="67556-127">Aby znaleźć te polecenia cmdlet w sesji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="67556-127">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="67556-128">Komunikacji zdalnej programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="67556-128">Windows PowerShell Remoting</span></span>

<span data-ttu-id="67556-129">Komunikacji zdalnej programu Windows PowerShell, która używa protokołu WS-Management, można uruchomić wszystkie polecenia programu Windows PowerShell na jednym lub wielu komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="67556-129">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="67556-130">Umożliwia ustanowienie połączenia trwałe, sesje interakcyjne 1:1 i uruchamiać skrypty na wielu komputerach.</span><span class="sxs-lookup"><span data-stu-id="67556-130">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="67556-131">Aby użyć komunikacji zdalnej programu Windows PowerShell, komputer zdalny musi być skonfigurowany do zdalnego zarządzania.</span><span class="sxs-lookup"><span data-stu-id="67556-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="67556-132">Aby uzyskać więcej informacji, w tym instrukcje, zobacz [o wymagania dotyczące zdalnego](https://technet.microsoft.com/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="67556-132">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/library/dd315349.aspx).</span></span>

<span data-ttu-id="67556-133">Po skonfigurowaniu komunikacji zdalnej programu Windows PowerShell, wiele strategii komunikacji zdalnej są dostępne.</span><span class="sxs-lookup"><span data-stu-id="67556-133">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="67556-134">W pozostałej części tego dokumentu zawiera tylko niektóre z nich.</span><span class="sxs-lookup"><span data-stu-id="67556-134">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="67556-135">Aby uzyskać więcej informacji, zobacz [o zdalnego](https://technet.microsoft.com/library/dd347744.aspx) i [o zdalnego — często zadawane pytania](https://technet.microsoft.com/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="67556-135">For more information, see [About Remote](https://technet.microsoft.com/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="67556-136">Uruchomić sesji interaktywnej</span><span class="sxs-lookup"><span data-stu-id="67556-136">Start an Interactive Session</span></span>

<span data-ttu-id="67556-137">Aby uruchomić sesji interaktywnej z jednym komputerem zdalnym, należy użyć [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67556-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="67556-138">Na przykład aby rozpocząć sesji interaktywnej Serwer01 komputerem zdalnym, wpisz:</span><span class="sxs-lookup"><span data-stu-id="67556-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="67556-139">Aby wyświetlić nazwę komputera, do którego są podłączeni zmiany wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="67556-139">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="67556-140">Następnie uruchom wszystkie wpisywane w wierszu polecenia na komputerze zdalnym, a wyniki są wyświetlane na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="67556-140">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="67556-141">Aby zakończyć sesję interaktywne, wpisz:</span><span class="sxs-lookup"><span data-stu-id="67556-141">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="67556-142">Aby uzyskać więcej informacji na temat polecenia cmdlet Enter-PSSession i zakończenia-PSSession, zobacz [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) i [zakończenia-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="67556-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="67556-143">Uruchom polecenia zdalnego</span><span class="sxs-lookup"><span data-stu-id="67556-143">Run a Remote Command</span></span>

<span data-ttu-id="67556-144">Aby uruchomić dowolnego polecenia na jednym lub wielu komputerach zdalnych, należy użyć [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67556-144">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="67556-145">Na przykład, aby uruchomić [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) do Serwer01 i serwer02 komputerów zdalnych, wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="67556-145">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="67556-146">Dane wyjściowe są zwracane do komputera.</span><span class="sxs-lookup"><span data-stu-id="67556-146">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

<span data-ttu-id="67556-147">Aby uzyskać więcej informacji na temat polecenia cmdlet Invoke-Command, zobacz [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="67556-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="67556-148">Uruchom skrypt</span><span class="sxs-lookup"><span data-stu-id="67556-148">Run a Script</span></span>

<span data-ttu-id="67556-149">Aby uruchomić skrypt na jednym lub wielu komputerach zdalnych, użyj parametru FilePath polecenia cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="67556-149">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="67556-150">Skrypt nie może być dostępny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="67556-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="67556-151">Wyniki są zwracane do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="67556-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="67556-152">Na przykład następujące polecenie uruchamia skrypt DiskCollect.ps1 na komputerach zdalnych Serwer01 i serwer02.</span><span class="sxs-lookup"><span data-stu-id="67556-152">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="67556-153">Aby uzyskać więcej informacji na temat polecenia cmdlet Invoke-Command, zobacz [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="67556-153">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="67556-154">Ustanowić trwałe połączenie</span><span class="sxs-lookup"><span data-stu-id="67556-154">Establish a Persistent Connection</span></span>

<span data-ttu-id="67556-155">Na uruchomieniu serii pokrewnych poleceń, które udostępniają danych, utworzenia sesji na komputerze zdalnym, a następnie uruchom polecenia w sesji, który utworzono za pomocą polecenia cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="67556-155">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="67556-156">Aby utworzyć sesję zdalną, należy użyć polecenia cmdlet New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="67556-156">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="67556-157">Na przykład następujące polecenie tworzy sesję zdalną na komputerze Serwer01 i innej sesji zdalnej na komputerze serwer02.</span><span class="sxs-lookup"><span data-stu-id="67556-157">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="67556-158">Obiektów sesji jest zapisywany w zmiennej $s.</span><span class="sxs-lookup"><span data-stu-id="67556-158">It saves the session objects in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="67556-159">Teraz, gdy sesje są ustalone, możesz uruchomić dowolne polecenie w nich.</span><span class="sxs-lookup"><span data-stu-id="67556-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="67556-160">I ponieważ sesje są trwałe, można zbierać dane w jednym poleceniu i używany w kolejnych poleceniach.</span><span class="sxs-lookup"><span data-stu-id="67556-160">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="67556-161">Na przykład następujące polecenie uruchamia polecenie Get-poprawki w sesji w zmiennej $s i zapisuje wyniki w zmiennej $h.</span><span class="sxs-lookup"><span data-stu-id="67556-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="67556-162">Zmienna $h zostało utworzone w każdej sesji w $s, ale nie istnieje w lokalnej sesji.</span><span class="sxs-lookup"><span data-stu-id="67556-162">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="67556-163">Teraz można używać danych za pomocą zmiennej $h w kolejnych poleceniach, takie jak następujące.</span><span class="sxs-lookup"><span data-stu-id="67556-163">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="67556-164">Wyniki są wyświetlane na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="67556-164">The results are displayed on the local computer.</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="67556-165">Zaawansowane usługi zdalne</span><span class="sxs-lookup"><span data-stu-id="67556-165">Advanced Remoting</span></span>

<span data-ttu-id="67556-166">Zdalne zarządzanie programu Windows PowerShell rozpoczyna właśnie w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="67556-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="67556-167">Za pomocą poleceń cmdlet, instalowane przy użyciu programu Windows PowerShell, można ustanowić i skonfigurować zdalnej sesji z lokalnymi i zdalnymi zakończeń tworzenia dostosowanego i ograniczeniami sesji, Zezwalaj użytkownikom na zaimportować polecenia w sesji zdalnej, które aktualnie ma uruchomiony niejawnie w sesji zdalnej, należy skonfigurować zabezpieczenia sesję zdalną i o wiele więcej.</span><span class="sxs-lookup"><span data-stu-id="67556-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="67556-168">W celu ułatwienia konfiguracji zdalnej, Windows PowerShell zawiera dostawcy usługi WSMan.</span><span class="sxs-lookup"><span data-stu-id="67556-168">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="67556-169">WSMAN: dysk, który tworzy dostawcę umożliwia przechodzenie przez hierarchię ustawień konfiguracyjnych na komputerze lokalnym i komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="67556-169">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="67556-170">Aby uzyskać więcej informacji o WSMan dostawcy, zobacz [dostawcy o WSMan](https://technet.microsoft.com/en-us/library/dd819476.aspx) i [polecenia cmdlet dotyczące protokołu WS-Management](https://technet.microsoft.com/en-us/library/dd819481.aspx), lub w konsoli środowiska Windows PowerShell, wpisz "Get-Help wsman".</span><span class="sxs-lookup"><span data-stu-id="67556-170">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="67556-171">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="67556-171">For more information, see:</span></span>

- [<span data-ttu-id="67556-172">Temat zdalnego — często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="67556-172">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="67556-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="67556-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="67556-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="67556-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="67556-175">Aby uzyskać pomoc dotyczącą usług zdalnych błędy, zobacz [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="67556-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="67556-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67556-176">See Also</span></span>

- [<span data-ttu-id="67556-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="67556-177">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="67556-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="67556-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="67556-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="67556-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="67556-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="67556-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="67556-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="67556-181">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="67556-182">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="67556-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="67556-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="67556-183">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="67556-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="67556-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="67556-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="67556-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="67556-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="67556-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="67556-187">Dostawca o WSMan</span><span class="sxs-lookup"><span data-stu-id="67556-187">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md