
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="1bfa6-101">Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH</span><span class="sxs-lookup"><span data-stu-id="1bfa6-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="1bfa6-102">Przegląd</span><span class="sxs-lookup"><span data-stu-id="1bfa6-102">Overview</span></span>

<span data-ttu-id="1bfa6-103">Komunikacja zdalna programu PowerShell zwykle używa funkcji WinRM do negocjowania połączenia i transport danych.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="1bfa6-104">SSH została wybrana dla tej implementacji komunikacji zdalnej, ponieważ jest teraz dostępna dla systemów Linux i Windows Platform i zezwala na wartość true dla wielu platform komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="1bfa6-105">Jednak usługi WinRM udostępnia niezawodne modelu hostingu dla sesji zdalnej programu PowerShell, które ta implementacja jeszcze nie działa.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="1bfa6-106">Co oznacza, że konfiguracja zdalnego punktu końcowego programu PowerShell oraz zestawu narzędziowego JEA (Just Enough Administration) nie jest jeszcze obsługiwany w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="1bfa6-107">Komunikacja zdalna programu PowerShell SSH umożliwia podstawowe komunikacji zdalnej sesji programu PowerShell między maszynami Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="1bfa6-108">Jest to zrobić przez utworzenie programu PowerShell, proces na komputerze docelowym jako podsystemu SSH hostingu.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="1bfa6-109">Ostatecznie to będzie można zmienić na bardziej ogólnych modelu hostingu, podobnie do sposobu działania usługi WinRM w celu zapewnienia obsługi konfiguracji punktu końcowego oraz zestawu narzędziowego JEA.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="1bfa6-110">`New-PSSession`, `Enter-PSSession` i `Invoke-Command` polecenia cmdlet zawierają już nowy parametr równa ułatwienia tego nowego połączenia zdalnego</span><span class="sxs-lookup"><span data-stu-id="1bfa6-110">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="1bfa6-111">Ten nowy zestaw parametrów najprawdopodobniej ulegną zmianom, ale teraz pozwala na tworzenie SSH sterować można wchodzić w interakcje z poziomu wiersza polecenia lub wywołania poleceń i skryptów na.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="1bfa6-112">Określ maszynie docelowej za pomocą parametru nazwy hosta i podaj nazwę użytkownika przy użyciu nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="1bfa6-113">Podczas interakcyjnego wykonywania polecenia cmdlet w wierszu polecenia programu PowerShell zostanie monit o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="1bfa6-114">Ale istnieje również możliwość używają uwierzytelniania kluczem SSH i podaj ścieżkę pliku klucza prywatnego za pomocą parametru atrybut KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="1bfa6-115">Ustawienia ogólne informacje</span><span class="sxs-lookup"><span data-stu-id="1bfa6-115">General setup information</span></span>

<span data-ttu-id="1bfa6-116">Protokół SSH jest wymagany do zainstalowania na wszystkich komputerach.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="1bfa6-117">Należy zainstalować zarówno klienta (`ssh.exe`) i serwera (`sshd.exe`), dzięki czemu możesz eksperymentować z wywołaniem funkcji zdalnych do i z maszyny.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-117">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="1bfa6-118">Dla Windows należy zainstalować [Win32 OpenSSH z serwisu GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="1bfa6-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="1bfa6-119">Dla systemu Linux należy zainstalować SSH (takie jak serwer sshd) odpowiednie dla danej platformy.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="1bfa6-120">Należy również najnowszych kompilacji programu PowerShell lub pakietu z usługi GitHub o funkcja komunikacji zdalnej SSH.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="1bfa6-121">Podsystemy SSH jest używany do ustanawiania proces programu PowerShell na komputerze zdalnym, a serwer SSH będzie trzeba skonfigurować dla tego.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="1bfa6-122">Ponadto należy włączyć uwierzytelnianie przy użyciu hasła i opcjonalnie klucza uwierzytelniania przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="1bfa6-123">Instalacja na komputerze Windows</span><span class="sxs-lookup"><span data-stu-id="1bfa6-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="1bfa6-124">Zainstaluj najnowszą wersję programu [program PowerShell Core Windows]</span><span class="sxs-lookup"><span data-stu-id="1bfa6-124">Install the latest version of [PowerShell Core for Windows]</span></span>
   - <span data-ttu-id="1bfa6-125">Można stwierdzić, jeśli ma on Obsługa komunikacji zdalnej SSH, analizując parametr ustawia `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="1bfa6-125">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

1. <span data-ttu-id="1bfa6-126">Zainstaluj najnowszą kompilację [Win32 OpenSSH] z usługi GitHub za pomocą instrukcji [instalacji]</span><span class="sxs-lookup"><span data-stu-id="1bfa6-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="1bfa6-127">Edytowanie pliku sshd_config w lokalizacji, w którym instalowane Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="1bfa6-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
   - <span data-ttu-id="1bfa6-128">Upewnij się, że włączone jest uwierzytelnianie przy użyciu hasła</span><span class="sxs-lookup"><span data-stu-id="1bfa6-128">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    > <span data-ttu-id="1bfa6-129">Brak usterkę w OpenSSH dla Windows uniemożliwiający pracujących w ścieżki pliku wykonywalnego podsystemu miejsc do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-129">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
    > <span data-ttu-id="1bfa6-130">Zobacz [ten problem w serwisie GitHub, aby uzyskać więcej informacji](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="1bfa6-130">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

    <span data-ttu-id="1bfa6-131">Rozwiązanie polega na Utwórz Link symboliczny do katalogu instalacyjnego programu Powershell, który nie zawiera spacji:</span><span class="sxs-lookup"><span data-stu-id="1bfa6-131">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    <span data-ttu-id="1bfa6-132">a następnie wprowadź go w podsystemie:</span><span class="sxs-lookup"><span data-stu-id="1bfa6-132">and then enter it in the subsystem:</span></span>

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="1bfa6-133">Opcjonalnie włączyć uwierzytelnianie za pomocą klucza</span><span class="sxs-lookup"><span data-stu-id="1bfa6-133">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="1bfa6-134">Uruchom ponownie usługę sshd</span><span class="sxs-lookup"><span data-stu-id="1bfa6-134">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="1bfa6-135">Dodaj ścieżkę zainstalowanym OpenSSH do swojej zmiennej Env ścieżki</span><span class="sxs-lookup"><span data-stu-id="1bfa6-135">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
   - <span data-ttu-id="1bfa6-136">Powinno to być wzdłuż linii `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="1bfa6-136">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="1bfa6-137">Dzięki temu ssh.exe ma zostać odnaleziona</span><span class="sxs-lookup"><span data-stu-id="1bfa6-137">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="1bfa6-138">Ustawienia na komputerze z systemem Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="1bfa6-138">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="1bfa6-139">Zainstaluj najnowszą kompilację [program PowerShell Core dla systemu Linux] z usługi GitHub</span><span class="sxs-lookup"><span data-stu-id="1bfa6-139">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
1. <span data-ttu-id="1bfa6-140">Zainstaluj [Ubuntu SSH] zgodnie z potrzebami</span><span class="sxs-lookup"><span data-stu-id="1bfa6-140">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="1bfa6-141">Edytowanie pliku sshd_config w lokalizacji /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="1bfa6-141">Edit the sshd_config file at location /etc/ssh</span></span>
   - <span data-ttu-id="1bfa6-142">Upewnij się, że włączone jest uwierzytelnianie przy użyciu hasła</span><span class="sxs-lookup"><span data-stu-id="1bfa6-142">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="1bfa6-143">Dodaj wpis podsystem PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bfa6-143">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="1bfa6-144">Opcjonalnie włączyć uwierzytelnianie za pomocą klucza</span><span class="sxs-lookup"><span data-stu-id="1bfa6-144">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="1bfa6-145">Uruchom ponownie usługę sshd</span><span class="sxs-lookup"><span data-stu-id="1bfa6-145">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="1bfa6-146">Instalacja na komputerze z systemem MacOS</span><span class="sxs-lookup"><span data-stu-id="1bfa6-146">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="1bfa6-147">Zainstaluj najnowszą kompilację [program PowerShell Core dla systemu MacOS]</span><span class="sxs-lookup"><span data-stu-id="1bfa6-147">Install the latest [PowerShell Core for MacOS] build</span></span>
   - <span data-ttu-id="1bfa6-148">Upewnij się, że komunikacja zdalna SSH jest włączona, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1bfa6-148">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="1bfa6-149">Otwórz `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="1bfa6-149">Open `System Preferences`</span></span>
     - <span data-ttu-id="1bfa6-150">Kliknij pozycję `Sharing`</span><span class="sxs-lookup"><span data-stu-id="1bfa6-150">Click on `Sharing`</span></span>
     - <span data-ttu-id="1bfa6-151">Sprawdź `Remote Login` — powinna być widoczna nazwa `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="1bfa6-151">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="1bfa6-152">Zezwalaj na dostęp do odpowiednich użytkowników</span><span class="sxs-lookup"><span data-stu-id="1bfa6-152">Allow access to appropriate users</span></span>
1. <span data-ttu-id="1bfa6-153">Edytuj `sshd_config` pliku w lokalizacji `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="1bfa6-153">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
   - <span data-ttu-id="1bfa6-154">Użyj ulubionego edytora lub</span><span class="sxs-lookup"><span data-stu-id="1bfa6-154">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="1bfa6-155">Upewnij się, że włączone jest uwierzytelnianie przy użyciu hasła</span><span class="sxs-lookup"><span data-stu-id="1bfa6-155">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="1bfa6-156">Dodaj wpis podsystem PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bfa6-156">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="1bfa6-157">Opcjonalnie włączyć uwierzytelnianie za pomocą klucza</span><span class="sxs-lookup"><span data-stu-id="1bfa6-157">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

1. <span data-ttu-id="1bfa6-158">Uruchom ponownie usługę sshd</span><span class="sxs-lookup"><span data-stu-id="1bfa6-158">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="1bfa6-159">Przykładowy komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bfa6-159">PowerShell Remoting Example</span></span>

<span data-ttu-id="1bfa6-160">Najprostszym sposobem przetestowania komunikacji zdalnej jest po prostu spróbuj na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-160">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="1bfa6-161">W tym miejscu I utworzy sesji zdalnej, wróć do tego samego komputera w usłudze box systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-161">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="1bfa6-162">Zwróć uwagę, że używam poleceń cmdlet programu PowerShell z poziomu wiersza polecenia, widzimy wyświetli monit z pytaniem sprawdzić, na komputerze-hoście, a także monitów o hasło protokołu SSH.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-162">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="1bfa6-163">Możesz zrobić to samo w Windows maszynę, aby upewnić się, że komunikacja zdalna działa istnieje, a następnie zdalnego między maszynami, po prostu modyfikując nazwę hosta.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-163">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

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
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
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

### <a name="known-issues"></a><span data-ttu-id="1bfa6-164">Znane problemy</span><span class="sxs-lookup"><span data-stu-id="1bfa6-164">Known Issues</span></span>

- <span data-ttu-id="1bfa6-165">polecenie "sudo" nie działa w sesji zdalnej do maszyny z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="1bfa6-165">sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bfa6-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bfa6-166">See Also</span></span>

[<span data-ttu-id="1bfa6-167">Program PowerShell Core dla Windows</span><span class="sxs-lookup"><span data-stu-id="1bfa6-167">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="1bfa6-168">Program PowerShell Core w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="1bfa6-168">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="1bfa6-169">Program PowerShell Core dla systemu MacOS</span><span class="sxs-lookup"><span data-stu-id="1bfa6-169">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="1bfa6-170">Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="1bfa6-170">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="1bfa6-171">Instalacja</span><span class="sxs-lookup"><span data-stu-id="1bfa6-171">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="1bfa6-172">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="1bfa6-172">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)