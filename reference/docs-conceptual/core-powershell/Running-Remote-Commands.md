---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Uruchamianie poleceń zdalnych"
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 5cf9690b8fe4549a99186f172cb6f0de156a4dea
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="running-remote-commands"></a><span data-ttu-id="1f6ca-103">Uruchamianie poleceń zdalnych</span><span class="sxs-lookup"><span data-stu-id="1f6ca-103">Running Remote Commands</span></span>
<span data-ttu-id="1f6ca-104">Polecenia można wykonać na co najmniej setek komputerów za pomocą jednego polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="1f6ca-105">Program Windows PowerShell obsługuje przetwarzania zdalnego przy użyciu różnych technologii, w tym usługi WMI, RPC i WS-Management.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="1f6ca-106">Komunikację zdalną bez konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1f6ca-106">Remoting Without Configuration</span></span>
<span data-ttu-id="1f6ca-107">Wiele poleceń cmdlet programu Windows PowerShell ma parametr ComputerName, który umożliwia zbieranie danych i zmienić ustawienia, na co najmniej jeden komputer zdalny.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-107">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="1f6ca-108">We wszystkich systemach operacyjnych Windows, które środowiska Windows PowerShell obsługuje bez żadnej specjalnej konfiguracji korzystają z różnych technologii komunikacji i wiele pracy.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-108">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="1f6ca-109">Te polecenia cmdlet obejmują:</span><span class="sxs-lookup"><span data-stu-id="1f6ca-109">These cmdlets include:</span></span>
* [<span data-ttu-id="1f6ca-110">Uruchom ponownie komputer</span><span class="sxs-lookup"><span data-stu-id="1f6ca-110">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="1f6ca-111">Połączenie testowe</span><span class="sxs-lookup"><span data-stu-id="1f6ca-111">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="1f6ca-112">Wyczyść EventLog</span><span class="sxs-lookup"><span data-stu-id="1f6ca-112">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="1f6ca-113">Get-dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="1f6ca-113">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="1f6ca-114">Get poprawki</span><span class="sxs-lookup"><span data-stu-id="1f6ca-114">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
  - [<span data-ttu-id="1f6ca-115">Get-Process</span><span class="sxs-lookup"><span data-stu-id="1f6ca-115">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="1f6ca-116">Get-Service</span><span class="sxs-lookup"><span data-stu-id="1f6ca-116">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="1f6ca-117">Ustawianie usługi</span><span class="sxs-lookup"><span data-stu-id="1f6ca-117">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="1f6ca-118">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="1f6ca-118">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="1f6ca-119">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="1f6ca-119">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="1f6ca-120">Zazwyczaj polecenia cmdlet, które obsługują komunikację zdalną bez specjalnej konfiguracji ma parametr ComputerName, a nie ma parametru sesji.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-120">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="1f6ca-121">Aby znaleźć te polecenia cmdlet w sesji, wpisz:</span><span class="sxs-lookup"><span data-stu-id="1f6ca-121">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="1f6ca-122">Komunikacji zdalnej programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f6ca-122">Windows PowerShell Remoting</span></span>
<span data-ttu-id="1f6ca-123">Komunikacji zdalnej programu Windows PowerShell, która używa protokołu WS-Management, można uruchomić wszystkie polecenia programu Windows PowerShell na jednym lub wielu komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-123">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="1f6ca-124">Umożliwia ustanowienie połączenia trwałe, sesje interakcyjne 1:1 i uruchamiać skrypty na wielu komputerach.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-124">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="1f6ca-125">Aby użyć komunikacji zdalnej programu Windows PowerShell, komputer zdalny musi być skonfigurowany do zdalnego zarządzania.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-125">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="1f6ca-126">Aby uzyskać więcej informacji, w tym instrukcje, zobacz [o wymagania dotyczące zdalnego](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="1f6ca-126">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="1f6ca-127">Po skonfigurowaniu komunikacji zdalnej programu Windows PowerShell, wiele strategii komunikacji zdalnej są dostępne.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-127">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="1f6ca-128">W pozostałej części tego dokumentu zawiera tylko niektóre z nich.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-128">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="1f6ca-129">Aby uzyskać więcej informacji, zobacz [o zdalnego](https://technet.microsoft.com/en-us/library/dd347744.aspx) i [o zdalnego — często zadawane pytania](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="1f6ca-129">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="1f6ca-130">Uruchomić sesji interaktywnej</span><span class="sxs-lookup"><span data-stu-id="1f6ca-130">Start an Interactive Session</span></span>
<span data-ttu-id="1f6ca-131">Aby uruchomić sesji interaktywnej z jednym komputerem zdalnym, należy użyć [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-131">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="1f6ca-132">Na przykład aby rozpocząć sesji interaktywnej Serwer01 komputerem zdalnym, wpisz:</span><span class="sxs-lookup"><span data-stu-id="1f6ca-132">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="1f6ca-133">Aby wyświetlić nazwę komputera, do którego są podłączeni zmiany wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-133">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="1f6ca-134">Następnie uruchom wszystkie wpisywane w wierszu polecenia na komputerze zdalnym, a wyniki są wyświetlane na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-134">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="1f6ca-135">Aby zakończyć sesję interaktywne, wpisz:</span><span class="sxs-lookup"><span data-stu-id="1f6ca-135">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="1f6ca-136">Aby uzyskać więcej informacji na temat polecenia cmdlet Enter-PSSession i zakończenia-PSSession, zobacz [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) i [zakończenia-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="1f6ca-136">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="1f6ca-137">Uruchom polecenia zdalnego</span><span class="sxs-lookup"><span data-stu-id="1f6ca-137">Run a Remote Command</span></span>
<span data-ttu-id="1f6ca-138">Aby uruchomić dowolnego polecenia na jednym lub wielu komputerach zdalnych, należy użyć [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-138">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="1f6ca-139">Na przykład, aby uruchomić [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) do Serwer01 i serwer02 komputerów zdalnych, wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="1f6ca-139">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="1f6ca-140">Dane wyjściowe są zwracane do komputera.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-140">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="1f6ca-141">Aby uzyskać więcej informacji na temat polecenia cmdlet Invoke-Command, zobacz [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="1f6ca-141">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="1f6ca-142">Uruchom skrypt</span><span class="sxs-lookup"><span data-stu-id="1f6ca-142">Run a Script</span></span>
<span data-ttu-id="1f6ca-143">Aby uruchomić skrypt na jednym lub wielu komputerach zdalnych, użyj parametru FilePath polecenia cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-143">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="1f6ca-144">Skrypt nie może być dostępny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-144">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="1f6ca-145">Wyniki są zwracane do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-145">The results are returned to your local computer.</span></span>

<span data-ttu-id="1f6ca-146">Na przykład następujące polecenie uruchamia skrypt DiskCollect.ps1 na komputerach zdalnych Serwer01 i serwer02.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-146">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="1f6ca-147">Aby uzyskać więcej informacji na temat polecenia cmdlet Invoke-Command, zobacz [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="1f6ca-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="1f6ca-148">Ustanowić trwałe połączenie</span><span class="sxs-lookup"><span data-stu-id="1f6ca-148">Establish a Persistent Connection</span></span>
<span data-ttu-id="1f6ca-149">Na uruchomieniu serii pokrewnych poleceń, które udostępniają danych, utworzenia sesji na komputerze zdalnym, a następnie uruchom polecenia w sesji, który utworzono za pomocą polecenia cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-149">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="1f6ca-150">Aby utworzyć sesję zdalną, należy użyć polecenia cmdlet New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-150">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="1f6ca-151">Na przykład następujące polecenie tworzy sesję zdalną na komputerze Serwer01 i innej sesji zdalnej na komputerze serwer02.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-151">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="1f6ca-152">Obiektów sesji jest zapisywany w zmiennej $s.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-152">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="1f6ca-153">Teraz, gdy sesje są ustalone, możesz uruchomić dowolne polecenie w nich.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-153">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="1f6ca-154">I ponieważ sesje są trwałe, można zbierać dane w jednym poleceniu i używany w kolejnych poleceniach.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-154">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="1f6ca-155">Na przykład następujące polecenie uruchamia polecenie Get-poprawki w sesji w zmiennej $s i zapisuje wyniki w zmiennej $h.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-155">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="1f6ca-156">Zmienna $h zostało utworzone w każdej sesji w $s, ale nie istnieje w lokalnej sesji.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-156">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="1f6ca-157">Teraz można używać danych za pomocą zmiennej $h w kolejnych poleceniach, takie jak następujące.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-157">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="1f6ca-158">Wyniki są wyświetlane na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-158">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="1f6ca-159">Zaawansowane usługi zdalne</span><span class="sxs-lookup"><span data-stu-id="1f6ca-159">Advanced Remoting</span></span>
<span data-ttu-id="1f6ca-160">Zdalne zarządzanie programu Windows PowerShell rozpoczyna właśnie w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-160">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="1f6ca-161">Za pomocą poleceń cmdlet, instalowane przy użyciu programu Windows PowerShell, można ustanowić i skonfigurować zdalnej sesji z lokalnymi i zdalnymi zakończeń tworzenia dostosowanego i ograniczeniami sesji, Zezwalaj użytkownikom na zaimportować polecenia w sesji zdalnej, które aktualnie ma uruchomiony niejawnie w sesji zdalnej, należy skonfigurować zabezpieczenia sesję zdalną i o wiele więcej.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-161">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="1f6ca-162">W celu ułatwienia konfiguracji zdalnej, Windows PowerShell zawiera dostawcy usługi WSMan.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-162">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="1f6ca-163">WSMAN: dysk, który tworzy dostawcę umożliwia przechodzenie przez hierarchię ustawień konfiguracyjnych na komputerze lokalnym i komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="1f6ca-163">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="1f6ca-164">Aby uzyskać więcej informacji o WSMan dostawcy, zobacz [dostawcy o WSMan](https://technet.microsoft.com/en-us/library/dd819476.aspx) i [polecenia cmdlet dotyczące protokołu WS-Management](https://technet.microsoft.com/en-us/library/dd819481.aspx), lub w konsoli środowiska Windows PowerShell, wpisz "Get-Help wsman".</span><span class="sxs-lookup"><span data-stu-id="1f6ca-164">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="1f6ca-165">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="1f6ca-165">For more information, see:</span></span>
- [<span data-ttu-id="1f6ca-166">Temat zdalnego — często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="1f6ca-166">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="1f6ca-167">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f6ca-167">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="1f6ca-168">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="1f6ca-168">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="1f6ca-169">Aby uzyskać pomoc dotyczącą usług zdalnych błędy, zobacz [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="1f6ca-169">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f6ca-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f6ca-170">See Also</span></span>
- [<span data-ttu-id="1f6ca-171">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1f6ca-171">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="1f6ca-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="1f6ca-172">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="1f6ca-173">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="1f6ca-173">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="1f6ca-174">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="1f6ca-174">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="1f6ca-175">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="1f6ca-175">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="1f6ca-176">about_WS Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="1f6ca-176">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="1f6ca-177">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1f6ca-177">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="1f6ca-178">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="1f6ca-178">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="1f6ca-179">Nowe PSSession</span><span class="sxs-lookup"><span data-stu-id="1f6ca-179">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="1f6ca-180">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f6ca-180">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="1f6ca-181">Dostawca o WSMan</span><span class="sxs-lookup"><span data-stu-id="1f6ca-181">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)
