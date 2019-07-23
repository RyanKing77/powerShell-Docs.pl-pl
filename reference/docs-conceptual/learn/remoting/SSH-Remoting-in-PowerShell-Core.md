---
title: Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH
description: Komunikacja zdalna w programie PowerShell Core przy użyciu protokołu SSH
ms.date: 08/14/2018
ms.openlocfilehash: d994a3888b9a372b803a65666634775a8905d63a
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372141"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="9512d-103">Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH</span><span class="sxs-lookup"><span data-stu-id="9512d-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="9512d-104">Omówienie</span><span class="sxs-lookup"><span data-stu-id="9512d-104">Overview</span></span>

<span data-ttu-id="9512d-105">Komunikacja zdalna programu PowerShell zwykle używa usługi WinRM do negocjacji połączeń i transportu danych.</span><span class="sxs-lookup"><span data-stu-id="9512d-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="9512d-106">Protokół SSH jest teraz dostępny dla platform Linux i Windows i umożliwia obsługę komunikacji zdalnej dla wieloplatformowego programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9512d-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="9512d-107">Usługa WinRM udostępnia niezawodny model hostingu dla sesji zdalnych programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9512d-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="9512d-108">Komunikacja zdalna oparta na protokole SSH nie obsługuje obecnie konfiguracji i JEA zdalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9512d-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="9512d-109">Komunikacja zdalna SSH umożliwia wykonywanie podstawowych sesji programu PowerShell dla komunikacji zdalnej między komputerami z systemem Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="9512d-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="9512d-110">Komunikacja zdalna SSH tworzy proces hosta programu PowerShell na maszynie docelowej jako podsystem SSH.</span><span class="sxs-lookup"><span data-stu-id="9512d-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span> <span data-ttu-id="9512d-111">Ostatecznie zaimplementujemy ogólny model hostingu podobny do usługi WinRM, aby obsługiwał konfigurację punktów końcowych i JEA.</span><span class="sxs-lookup"><span data-stu-id="9512d-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="9512d-112">Polecenia cmdlet `Enter-PSSession` ,i`Invoke-Command` mają teraz nowy zestaw parametrów do obsługi nowego połączenia zdalnego. `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="9512d-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="9512d-113">Aby utworzyć sesję zdalną, należy określić maszynę docelową `HostName` z parametrem i podać nazwę użytkownika `UserName`przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="9512d-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="9512d-114">Gdy uruchamiasz polecenia cmdlet interaktywnie, zostanie wyświetlony monit o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="9512d-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="9512d-115">Można również użyć uwierzytelniania klucza SSH przy użyciu pliku klucza prywatnego z `KeyFilePath` parametrem.</span><span class="sxs-lookup"><span data-stu-id="9512d-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="9512d-116">Ogólne informacje o instalacji</span><span class="sxs-lookup"><span data-stu-id="9512d-116">General setup information</span></span>

<span data-ttu-id="9512d-117">Protokół SSH musi być zainstalowany na wszystkich komputerach.</span><span class="sxs-lookup"><span data-stu-id="9512d-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="9512d-118">Zainstaluj klienta SSH (`ssh.exe`) i serwer (`sshd.exe`), aby móc zdalnie z maszyn i z nich.</span><span class="sxs-lookup"><span data-stu-id="9512d-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="9512d-119">OpenSSH dla systemu Windows jest teraz dostępny w systemie Windows 10 Build 1809 i Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="9512d-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="9512d-120">Aby uzyskać więcej informacji, zobacz [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="9512d-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="9512d-121">W przypadku systemu Linux Zainstaluj protokół SSH (w tym serwer SSHD) odpowiednie dla danej platformy.</span><span class="sxs-lookup"><span data-stu-id="9512d-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="9512d-122">Musisz również zainstalować program PowerShell Core z usługi GitHub, aby uzyskać funkcję komunikacji zdalnej SSH.</span><span class="sxs-lookup"><span data-stu-id="9512d-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="9512d-123">Serwer SSH musi być skonfigurowany tak, aby utworzyć podsystem SSH do hostowania procesu programu PowerShell na maszynie zdalnej.</span><span class="sxs-lookup"><span data-stu-id="9512d-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="9512d-124">Należy również skonfigurować opcję Włącz uwierzytelnianie hasła lub klucza.</span><span class="sxs-lookup"><span data-stu-id="9512d-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="9512d-125">Konfiguracja na komputerze z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="9512d-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="9512d-126">Zainstaluj najnowszą wersję programu [PowerShell Core dla systemu Windows](../../install/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="9512d-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="9512d-127">Możesz określić, czy ma ona obsługę komunikacji zdalnej SSH, przeglądając zestawy parametrów dla`New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="9512d-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="9512d-128">Zainstaluj najnowszą wersję Win32 OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="9512d-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="9512d-129">Instrukcje instalacji znajdują się w temacie [instalacja programu OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="9512d-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="9512d-130">Edytuj plik znajdujący się `$env:ProgramData\ssh`w lokalizacji. `sshd_config`</span><span class="sxs-lookup"><span data-stu-id="9512d-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="9512d-131">Upewnij się, że uwierzytelnianie hasła jest włączone</span><span class="sxs-lookup"><span data-stu-id="9512d-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="9512d-132">Wystąpił błąd w OpenSSH dla systemu Windows, który uniemożliwia pracę w ścieżkach wykonywalnych podsystemu.</span><span class="sxs-lookup"><span data-stu-id="9512d-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="9512d-133">Aby uzyskać więcej informacji, zobacz [problem w usłudze GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="9512d-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="9512d-134">Jednym z rozwiązań jest utworzenie link symboliczny w katalogu instalacyjnym programu PowerShell, który nie zawiera spacji:</span><span class="sxs-lookup"><span data-stu-id="9512d-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="9512d-135">a następnie wprowadź ją w podsystemie:</span><span class="sxs-lookup"><span data-stu-id="9512d-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="9512d-136">Opcjonalnie Włącz uwierzytelnianie klucza</span><span class="sxs-lookup"><span data-stu-id="9512d-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="9512d-137">Uruchom ponownie usługę SSHD</span><span class="sxs-lookup"><span data-stu-id="9512d-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="9512d-138">Dodaj ścieżkę, gdzie OpenSSH jest zainstalowana w zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="9512d-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="9512d-139">Na przykład `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="9512d-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="9512d-140">Ten wpis umożliwia znalezienie pliku SSH. exe.</span><span class="sxs-lookup"><span data-stu-id="9512d-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1604-machine"></a><span data-ttu-id="9512d-141">Konfiguracja na komputerze z systemem Linux (Ubuntu 16,04)</span><span class="sxs-lookup"><span data-stu-id="9512d-141">Set up on Linux (Ubuntu 16.04) Machine</span></span>

1. <span data-ttu-id="9512d-142">Zainstaluj najnowszą kompilację [programu PowerShell Core dla systemu Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) z usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="9512d-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) build from GitHub</span></span>
2. <span data-ttu-id="9512d-143">Zainstaluj [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) zgodnie z wymaganiami</span><span class="sxs-lookup"><span data-stu-id="9512d-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="9512d-144">Edytuj plik sshd_config w lokalizacji/etc/ssh</span><span class="sxs-lookup"><span data-stu-id="9512d-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="9512d-145">Upewnij się, że uwierzytelnianie hasła jest włączone</span><span class="sxs-lookup"><span data-stu-id="9512d-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="9512d-146">Dodawanie wpisu podsystemu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="9512d-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="9512d-147">Opcjonalnie Włącz uwierzytelnianie klucza</span><span class="sxs-lookup"><span data-stu-id="9512d-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="9512d-148">Uruchom ponownie usługę SSHD</span><span class="sxs-lookup"><span data-stu-id="9512d-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="9512d-149">Konfiguracja na maszynie MacOS</span><span class="sxs-lookup"><span data-stu-id="9512d-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="9512d-150">Zainstaluj najnowszą wersję [programu PowerShell Core dla kompilacji MacOS](../../install/installing-powershell-core-on-macos.md)</span><span class="sxs-lookup"><span data-stu-id="9512d-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="9512d-151">Upewnij się, że komunikacja zdalna SSH jest włączona, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9512d-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="9512d-152">Otwórz`System Preferences`</span><span class="sxs-lookup"><span data-stu-id="9512d-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="9512d-153">Kliknij pozycję`Sharing`</span><span class="sxs-lookup"><span data-stu-id="9512d-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="9512d-154">Sprawdzenie `Remote Login` — należy powiedzieć`Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="9512d-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="9512d-155">Zezwalaj na dostęp do odpowiednich użytkowników</span><span class="sxs-lookup"><span data-stu-id="9512d-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="9512d-156">`sshd_config` Edytuj plik w lokalizacji`/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="9512d-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="9512d-157">Użyj swojego ulubionego edytora lub</span><span class="sxs-lookup"><span data-stu-id="9512d-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="9512d-158">Upewnij się, że uwierzytelnianie hasła jest włączone</span><span class="sxs-lookup"><span data-stu-id="9512d-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="9512d-159">Dodawanie wpisu podsystemu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="9512d-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="9512d-160">Opcjonalnie Włącz uwierzytelnianie klucza</span><span class="sxs-lookup"><span data-stu-id="9512d-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="9512d-161">Uruchom ponownie usługę SSHD</span><span class="sxs-lookup"><span data-stu-id="9512d-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="9512d-162">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="9512d-162">Authentication</span></span>

<span data-ttu-id="9512d-163">Komunikacja zdalna programu PowerShell za pośrednictwem protokołu SSH polega na wymianie uwierzytelniania między klientem SSH i usługą SSH i nie implementuje żadnego ze schematów uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="9512d-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span> <span data-ttu-id="9512d-164">Oznacza to, że wszystkie skonfigurowane schematy uwierzytelniania, w tym uwierzytelnianie wieloskładnikowe, są obsługiwane przez protokół SSH i niezależne od programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9512d-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="9512d-165">Można na przykład skonfigurować usługę SSH, aby wymagała uwierzytelniania klucza publicznego oraz hasła jednorazowego w celu zwiększenia bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="9512d-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span> <span data-ttu-id="9512d-166">Konfiguracja usługi uwierzytelniania wieloskładnikowego jest poza zakresem tej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="9512d-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="9512d-167">Zapoznaj się z dokumentacją protokołu SSH, aby poprawnie skonfigurować uwierzytelnianie wieloskładnikowe i sprawdzić, czy działa on poza programem PowerShell, przed podjęciem próby użycia go z usługami zdalnymi programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9512d-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="9512d-168">Przykład komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="9512d-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="9512d-169">Najprostszym sposobem testowania komunikacji zdalnej jest wypróbowanie jej na pojedynczym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9512d-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="9512d-170">W tym przykładzie utworzysz sesję zdalną z powrotem do tej samej maszyny z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="9512d-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="9512d-171">Używamy poleceń cmdlet programu PowerShell interaktywnie, więc zobaczymy monity z prośbą o zweryfikowanie komputera-hosta i monitowanie o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="9512d-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="9512d-172">Tę samą funkcję można wykonać na komputerze z systemem Windows, aby upewnić się, że komunikacja zdalna działa.</span><span class="sxs-lookup"><span data-stu-id="9512d-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="9512d-173">Następnie możesz zdalnie między maszynami, zmieniając nazwę hosta.</span><span class="sxs-lookup"><span data-stu-id="9512d-173">Then remote between machines by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="9512d-174">Znane problemy</span><span class="sxs-lookup"><span data-stu-id="9512d-174">Known Issues</span></span>

<span data-ttu-id="9512d-175">Polecenie sudo nie działa w sesji zdalnej z maszyną z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="9512d-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="9512d-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9512d-176">See Also</span></span>

[<span data-ttu-id="9512d-177">Program PowerShell Core dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9512d-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="9512d-178">Program PowerShell Core dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="9512d-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="9512d-179">Rdzeń programu PowerShell dla MacOS</span><span class="sxs-lookup"><span data-stu-id="9512d-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="9512d-180">OpenSSH dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9512d-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="9512d-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="9512d-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
