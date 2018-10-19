---
title: Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH
description: Komunikacji zdalnej w programie PowerShell Core przy użyciu protokołu SSH
ms.date: 08/14/2018
ms.openlocfilehash: 842e67e96661bca8be54aab33cbc11aa23dbd1c0
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49451069"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="e0770-103">Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH</span><span class="sxs-lookup"><span data-stu-id="e0770-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="e0770-104">Przegląd</span><span class="sxs-lookup"><span data-stu-id="e0770-104">Overview</span></span>

<span data-ttu-id="e0770-105">Komunikacja zdalna programu PowerShell zwykle używa funkcji WinRM do negocjowania połączenia i transport danych.</span><span class="sxs-lookup"><span data-stu-id="e0770-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="e0770-106">Protokół SSH jest teraz dostępny dla platform Linux i Windows i zezwala na wartość true dla wielu platform komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0770-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="e0770-107">Usługa WinRM zapewnia niezawodne modelu hostingu dla sesji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0770-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="e0770-108">Konfiguracja zdalnego punktu końcowego oraz zestawu narzędziowego JEA (Just Enough Administration) opartego na SSH komunikacji zdalnej nie obsługuje obecnie.</span><span class="sxs-lookup"><span data-stu-id="e0770-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="e0770-109">Komunikacja zdalna SSH umożliwia podstawowe komunikacji zdalnej sesji programu PowerShell między maszynami Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="e0770-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="e0770-110">SSH Remoting tworzy proces hosta programu PowerShell na komputerze docelowym jako podsystemu SSH.</span><span class="sxs-lookup"><span data-stu-id="e0770-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="e0770-111">Po pewnym czasie będzie wdrażamy ogólny model hostingu, podobnie jak usługi WinRM do obsługi konfiguracji punktu końcowego oraz zestawu narzędziowego JEA.</span><span class="sxs-lookup"><span data-stu-id="e0770-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="e0770-112">`New-PSSession`, `Enter-PSSession`, I `Invoke-Command` polecenia cmdlet zawierają już nowy parametr skonfigurowane do obsługi tego nowego połączenia zdalnego.</span><span class="sxs-lookup"><span data-stu-id="e0770-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="e0770-113">Aby utworzyć sesję zdalną, należy określić na komputerze docelowym z `HostName` parametru i podaj nazwę użytkownika z `UserName`.</span><span class="sxs-lookup"><span data-stu-id="e0770-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="e0770-114">Podczas interakcyjnego wykonywania polecenia cmdlet, zostanie wyświetlony monit o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="e0770-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="e0770-115">Można także użyć uwierzytelniania klucza SSH przy użyciu pliku klucza prywatnego za pomocą `KeyFilePath` parametru.</span><span class="sxs-lookup"><span data-stu-id="e0770-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="e0770-116">Ustawienia ogólne informacje</span><span class="sxs-lookup"><span data-stu-id="e0770-116">General setup information</span></span>

<span data-ttu-id="e0770-117">SSH musi być zainstalowany na wszystkich komputerach.</span><span class="sxs-lookup"><span data-stu-id="e0770-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="e0770-118">Zainstaluj klienta SSH (`ssh.exe`) i serwera (`sshd.exe`) aby można było zdalnego, do i z maszyny.</span><span class="sxs-lookup"><span data-stu-id="e0770-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="e0770-119">Windows, można zainstalować [Win32 OpenSSH z serwisu GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="e0770-119">For Windows, install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="e0770-120">W przypadku systemu Linux Zainstaluj SSH (takie jak serwer sshd) odpowiednie dla danej platformy.</span><span class="sxs-lookup"><span data-stu-id="e0770-120">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="e0770-121">Należy również zainstalować program PowerShell Core z witryny GitHub można pobrać funkcja komunikacji zdalnej SSH.</span><span class="sxs-lookup"><span data-stu-id="e0770-121">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="e0770-122">Serwer SSH musi być skonfigurowany do utworzenia podsystemie SSH do hostowania proces programu PowerShell na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="e0770-122">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="e0770-123">Należy również skonfigurować Włącz haseł lub uwierzytelniania opartego na kluczu.</span><span class="sxs-lookup"><span data-stu-id="e0770-123">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="e0770-124">Skonfiguruj na komputerze Windows</span><span class="sxs-lookup"><span data-stu-id="e0770-124">Set up on Windows Machine</span></span>

1. <span data-ttu-id="e0770-125">Zainstaluj najnowszą wersję [programu PowerShell Core dla Windows](../setup/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="e0770-125">Install the latest version of [PowerShell Core for Windows](../setup/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="e0770-126">Można stwierdzić, jeśli ma on Obsługa komunikacji zdalnej SSH, analizując parametr ustawia `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="e0770-126">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="e0770-127">Zainstaluj najnowszą wersję [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) kompilacji z GitHub przy użyciu [instalacji](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH) instrukcje</span><span class="sxs-lookup"><span data-stu-id="e0770-127">Install the latest [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases) build from GitHub using the [installation](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH) instructions</span></span>
3. <span data-ttu-id="e0770-128">Edytuj znajdujący się w pliku sshd_config `%ProgramData%\ssh`.</span><span class="sxs-lookup"><span data-stu-id="e0770-128">Edit the sshd_config file located at `%ProgramData%\ssh`.</span></span>

   - <span data-ttu-id="e0770-129">Upewnij się, że włączone jest uwierzytelnianie przy użyciu hasła</span><span class="sxs-lookup"><span data-stu-id="e0770-129">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="e0770-130">Brak usterkę w OpenSSH dla Windows uniemożliwiający pracujących w ścieżki pliku wykonywalnego podsystemu miejsc do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="e0770-130">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="e0770-131">Aby uzyskać więcej informacji, zobacz [problem w usłudze GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="e0770-131">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="e0770-132">Rozwiązanie polega na Utwórz Link symboliczny do katalogu instalacyjnego programu Powershell, który nie ma miejsca do magazynowania:</span><span class="sxs-lookup"><span data-stu-id="e0770-132">One solution is to create a symlink to the Powershell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="e0770-133">a następnie wprowadź go w podsystemie:</span><span class="sxs-lookup"><span data-stu-id="e0770-133">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="e0770-134">Opcjonalnie włączyć uwierzytelnianie za pomocą klucza</span><span class="sxs-lookup"><span data-stu-id="e0770-134">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="e0770-135">Uruchom ponownie usługę sshd</span><span class="sxs-lookup"><span data-stu-id="e0770-135">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="e0770-136">Dodaj ścieżkę zainstalowanym OpenSSH do zmiennej środowiskowej Path.</span><span class="sxs-lookup"><span data-stu-id="e0770-136">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="e0770-137">Na przykład `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="e0770-137">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="e0770-138">Ten wpis umożliwia ssh.exe ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="e0770-138">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="e0770-139">Skonfiguruj na komputerze z systemem Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="e0770-139">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="e0770-140">Zainstaluj najnowszą wersję [programu PowerShell Core dla systemu Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) kompilacji z usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="e0770-140">Install the latest [PowerShell Core for Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="e0770-141">Zainstaluj [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) zgodnie z potrzebami</span><span class="sxs-lookup"><span data-stu-id="e0770-141">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="e0770-142">Edytowanie pliku sshd_config w lokalizacji /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="e0770-142">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="e0770-143">Upewnij się, że włączone jest uwierzytelnianie przy użyciu hasła</span><span class="sxs-lookup"><span data-stu-id="e0770-143">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="e0770-144">Dodaj wpis podsystem PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0770-144">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="e0770-145">Opcjonalnie włączyć uwierzytelnianie za pomocą klucza</span><span class="sxs-lookup"><span data-stu-id="e0770-145">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="e0770-146">Uruchom ponownie usługę sshd</span><span class="sxs-lookup"><span data-stu-id="e0770-146">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="e0770-147">Na komputerze z systemem MacOS</span><span class="sxs-lookup"><span data-stu-id="e0770-147">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="e0770-148">Zainstaluj najnowszą wersję [programu PowerShell Core dla systemu MacOS](../setup/installing-powershell-core-on-macos.md) kompilacji</span><span class="sxs-lookup"><span data-stu-id="e0770-148">Install the latest [PowerShell Core for MacOS](../setup/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="e0770-149">Upewnij się, że komunikacja zdalna SSH jest włączona, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e0770-149">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="e0770-150">Otwórz `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="e0770-150">Open `System Preferences`</span></span>
     - <span data-ttu-id="e0770-151">Kliknij pozycję `Sharing`</span><span class="sxs-lookup"><span data-stu-id="e0770-151">Click on `Sharing`</span></span>
     - <span data-ttu-id="e0770-152">Sprawdź `Remote Login` — powinna być widoczna nazwa `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="e0770-152">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="e0770-153">Zezwalaj na dostęp do odpowiednich użytkowników</span><span class="sxs-lookup"><span data-stu-id="e0770-153">Allow access to appropriate users</span></span>

2. <span data-ttu-id="e0770-154">Edytuj `sshd_config` pliku w lokalizacji `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="e0770-154">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="e0770-155">Użyj ulubionego edytora lub</span><span class="sxs-lookup"><span data-stu-id="e0770-155">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="e0770-156">Upewnij się, że włączone jest uwierzytelnianie przy użyciu hasła</span><span class="sxs-lookup"><span data-stu-id="e0770-156">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="e0770-157">Dodaj wpis podsystem PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0770-157">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="e0770-158">Opcjonalnie włączyć uwierzytelnianie za pomocą klucza</span><span class="sxs-lookup"><span data-stu-id="e0770-158">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="e0770-159">Uruchom ponownie usługę sshd</span><span class="sxs-lookup"><span data-stu-id="e0770-159">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="e0770-160">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="e0770-160">Authentication</span></span>

<span data-ttu-id="e0770-161">Komunikacja zdalna programu PowerShell za pomocą protokołu SSH opiera się na Wymiana uwierzytelniania między klientem SSH i usługę SSH i nie implementuje żadnych schematów uwierzytelniania sam.</span><span class="sxs-lookup"><span data-stu-id="e0770-161">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="e0770-162">Oznacza to, że wszelkie schematów uwierzytelniania skonfigurowany, w tym usługi uwierzytelnianie wieloskładnikowe jest obsługiwane przez SSH i niezależna od programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0770-162">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="e0770-163">Na przykład można skonfigurować usługę SSH, aby wymagać uwierzytelniania klucza publicznego, a także hasła jednorazowego w celu zwiększenia poziomu bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="e0770-163">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="e0770-164">Konfiguracja usługi Multi-Factor authentication jest poza zakresem niniejszej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="e0770-164">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="e0770-165">Zajrzyj do dokumentacji dla protokołu SSH na temat sposobu poprawnie skonfigurować uwierzytelnianie wieloskładnikowe i sprawdzić jego poprawność działa poza programem PowerShell przed podjęciem próby korzystania z komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0770-165">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="e0770-166">Przykładowy komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0770-166">PowerShell Remoting Example</span></span>

<span data-ttu-id="e0770-167">Najprostszym sposobem przetestowania komunikacji zdalnej jest do wypróbowania tej funkcji na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e0770-167">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="e0770-168">W tym przykładzie utworzymy sesji zdalnej, wróć do tej samej maszyny z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="e0770-168">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="e0770-169">Firma Microsoft przy użyciu programu PowerShell, poleceń cmdlet interaktywnie, więc widzimy monity z protokołu SSH z pytaniem sprawdzić komputer-host i monitem o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="e0770-169">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="e0770-170">Możesz zrobić to samo na komputerze Windows Aby upewnić się, że komunikacja zdalna działa.</span><span class="sxs-lookup"><span data-stu-id="e0770-170">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="e0770-171">Następnie zdalnego między maszynami, zmieniając nazwę hosta.</span><span class="sxs-lookup"><span data-stu-id="e0770-171">Then remote between machines by changing the host name.</span></span>

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
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

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

### <a name="known-issues"></a><span data-ttu-id="e0770-172">Znane problemy</span><span class="sxs-lookup"><span data-stu-id="e0770-172">Known Issues</span></span>

<span data-ttu-id="e0770-173">Polecenie "sudo" nie działa w sesji zdalnej do maszyny z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="e0770-173">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0770-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0770-174">See Also</span></span>

[<span data-ttu-id="e0770-175">Program PowerShell Core dla Windows</span><span class="sxs-lookup"><span data-stu-id="e0770-175">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="e0770-176">Program PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="e0770-176">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="e0770-177">Program PowerShell Core dla systemu MacOS</span><span class="sxs-lookup"><span data-stu-id="e0770-177">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="e0770-178">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="e0770-178">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="e0770-179">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="e0770-179">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
