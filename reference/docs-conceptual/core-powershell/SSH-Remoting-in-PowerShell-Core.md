# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="8a1b5-101">Usługi zdalne środowiska PowerShell za pomocą protokołu SSH</span><span class="sxs-lookup"><span data-stu-id="8a1b5-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="8a1b5-102">Przegląd</span><span class="sxs-lookup"><span data-stu-id="8a1b5-102">Overview</span></span>

<span data-ttu-id="8a1b5-103">Usługi zdalne środowiska PowerShell zwykle używa usługi WinRM negocjowania połączenia i transportu danych.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="8a1b5-104">SSH została wybrana dla tej implementacji komunikacji zdalnej, ponieważ jest teraz dostępna dla platform zarówno systemu Linux i Windows i umożliwia obsługę zdalną środowiska PowerShell dla wielu platform wartość true.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="8a1b5-105">Jednak WinRM udostępnia niezawodny modelu hostingu dla sesji zdalnej programu PowerShell, które ta implementacja jeszcze nie działa.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="8a1b5-106">Co oznacza, że konfiguracja zdalnego punktu końcowego programu PowerShell i JEA (tylko tyle Administracja) nie jest jeszcze obsługiwana w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="8a1b5-107">Usługi zdalne środowiska PowerShell SSH umożliwia podstawowe komunikacji zdalnej sesji programu PowerShell między komputerami z systemem Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="8a1b5-108">Jest to zrobić przez utworzenie programu PowerShell, proces na komputerze docelowym jako podsystemu SSH hostingu.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="8a1b5-109">Ostatecznie to będzie można zmienić na bardziej ogólne modelu hostingu, podobnie jak WinRM działa w celu zapewnienia obsługi konfiguracji punktu końcowego i JEA.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="8a1b5-110">Polecenia cmdlet New-PSSession, Enter-PSSession i Invoke-Command jest nowy parametr ustawioną ułatwienia tego nowego połączenia zdalnego</span><span class="sxs-lookup"><span data-stu-id="8a1b5-110">The New-PSSession, Enter-PSSession and Invoke-Command cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="8a1b5-111">Ten nowy zestaw parametrów prawdopodobnie ulegnie zmianie, ale teraz służy do tworzenia SSH PSSessions można interakcyjnie z wiersza polecenia lub wywołania poleceń i skryptów na.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="8a1b5-112">Możesz określić komputer docelowy przy użyciu parametru nazwy hosta i podaj nazwę użytkownika z nazwą użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="8a1b5-113">Podczas interakcyjnego uruchamiania polecenia cmdlet w wierszu polecenia programu PowerShell pojawi się monit o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="8a1b5-114">Ale masz opcję, aby używać uwierzytelniania klucza SSH i podaj ścieżkę pliku klucza prywatnego za pomocą parametru ściezka do pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="8a1b5-115">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="8a1b5-115">General setup information</span></span>

<span data-ttu-id="8a1b5-116">SSH jest musi być zainstalowany na wszystkich komputerach.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="8a1b5-117">Należy zainstalować klienta (ssh.exe) i serwera (sshd.exe), dzięki czemu możesz eksperymentować z usługami zdalnymi do i z maszyn.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-117">You should install both client (ssh.exe) and server (sshd.exe) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="8a1b5-118">Dla systemu Windows, musisz zainstalować [OpenSSH Win32 z usługi GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="8a1b5-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="8a1b5-119">W systemie Linux należy zainstalować SSH (takie jak serwer sshd) odpowiednią dla danej platformy.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="8a1b5-120">Należy również ostatnie kompilacji programu PowerShell lub pakietu z usługi GitHub o SSH funkcja komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="8a1b5-121">Podsystemy SSH jest używany do ustanawiania procesu programu PowerShell na komputerze zdalnym i należy skonfigurować tego serwera SSH.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="8a1b5-122">Ponadto należy włączyć uwierzytelnianie hasła i opcjonalnie klucza uwierzytelniania przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="8a1b5-123">Instalacja na komputerze z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="8a1b5-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="8a1b5-124">[Zainstaluj najnowszą wersję programu PowerShell Core dla systemu Windows] []</span><span class="sxs-lookup"><span data-stu-id="8a1b5-124">[Install the latest version of PowerShell Core for Windows][]</span></span>
    - <span data-ttu-id="8a1b5-125">Można określić, czy obsługa komunikacji zdalnej SSH analizując parametr ustawia New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8a1b5-125">You can tell if it has the SSH remoting support by looking at the parameter sets for New-PSSession</span></span>
    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```
1. <span data-ttu-id="8a1b5-126">Zainstaluj najnowszą [Win32 OpenSSH] kompilacji z witryny GitHub przy użyciu [instalacji] instrukcje</span><span class="sxs-lookup"><span data-stu-id="8a1b5-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="8a1b5-127">Edytuj plik sshd_config w lokalizacji, w którym zainstalowano Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="8a1b5-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
    - <span data-ttu-id="8a1b5-128">Upewnij się, że jest włączone uwierzytelnianie hasła</span><span class="sxs-lookup"><span data-stu-id="8a1b5-128">Make sure password authentication is enabled</span></span>
    ```none
    PasswordAuthentication yes
    ```
    - <span data-ttu-id="8a1b5-129">Dodaj wpis podsystemu programu PowerShell, Zastąp `c:/program files/powershell/6.0.0/pwsh.exe` z poprawną ścieżkę do wersji, którego chcesz użyć</span><span class="sxs-lookup"><span data-stu-id="8a1b5-129">Add a PowerShell subsystem entry, replace `c:/program files/powershell/6.0.0/pwsh.exe` with the correct path to the version you want to use</span></span>
    ```none
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```
    - <span data-ttu-id="8a1b5-130">Opcjonalnie włączyć uwierzytelnianie za pomocą klucza</span><span class="sxs-lookup"><span data-stu-id="8a1b5-130">Optionally enable key authentication</span></span>
    ```none
    PubkeyAuthentication yes
    ```
1. <span data-ttu-id="8a1b5-131">Uruchom ponownie usługę sshd</span><span class="sxs-lookup"><span data-stu-id="8a1b5-131">Restart the sshd service</span></span>
    ```powershell
    Restart-Service sshd
    ```
1. <span data-ttu-id="8a1b5-132">Dodaj ścieżkę zainstalowanym OpenSSH do Twojej zmiennej Env ścieżki</span><span class="sxs-lookup"><span data-stu-id="8a1b5-132">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
    - <span data-ttu-id="8a1b5-133">To pole powinno być wzdłuż linii`C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="8a1b5-133">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
    - <span data-ttu-id="8a1b5-134">Dzięki temu ssh.exe do znalezienia</span><span class="sxs-lookup"><span data-stu-id="8a1b5-134">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="8a1b5-135">Ustawienia na komputerze z systemem Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="8a1b5-135">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="8a1b5-136">Zainstaluj najnowszą [programu PowerShell dla systemu Linux] kompilacji z witryny GitHub</span><span class="sxs-lookup"><span data-stu-id="8a1b5-136">Install the latest [PowerShell for Linux] build from GitHub</span></span>
1. <span data-ttu-id="8a1b5-137">Zainstaluj [Ubuntu SSH] zgodnie z potrzebami</span><span class="sxs-lookup"><span data-stu-id="8a1b5-137">Install [Ubuntu SSH] as needed</span></span>
    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```
1. <span data-ttu-id="8a1b5-138">Edytuj plik sshd_config w lokalizacji /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="8a1b5-138">Edit the sshd_config file at location /etc/ssh</span></span>
    - <span data-ttu-id="8a1b5-139">Upewnij się, że jest włączone uwierzytelnianie hasła</span><span class="sxs-lookup"><span data-stu-id="8a1b5-139">Make sure password authentication is enabled</span></span>
    ```none
    PasswordAuthentication yes
    ```
    - <span data-ttu-id="8a1b5-140">Dodaj wpis podsystemu środowiska PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a1b5-140">Add a PowerShell subsystem entry</span></span>
    ```none
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```
    - <span data-ttu-id="8a1b5-141">Opcjonalnie włączyć uwierzytelnianie za pomocą klucza</span><span class="sxs-lookup"><span data-stu-id="8a1b5-141">Optionally enable key authentication</span></span>
    ```none
    PubkeyAuthentication yes
    ```
1. <span data-ttu-id="8a1b5-142">Uruchom ponownie usługę sshd</span><span class="sxs-lookup"><span data-stu-id="8a1b5-142">Restart the sshd service</span></span>
    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="8a1b5-143">Instalacja na komputerze MacOS</span><span class="sxs-lookup"><span data-stu-id="8a1b5-143">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="8a1b5-144">Zainstaluj najnowszą [programu PowerShell dla MacOS] kompilacji</span><span class="sxs-lookup"><span data-stu-id="8a1b5-144">Install the latest [PowerShell for MacOS] build</span></span>
    - <span data-ttu-id="8a1b5-145">Upewnij się, że usługi zdalne SSH jest włączone, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8a1b5-145">Make sure SSH Remoting is enabled by following these steps:</span></span>
      - <span data-ttu-id="8a1b5-146">Otwórz`System Preferences`</span><span class="sxs-lookup"><span data-stu-id="8a1b5-146">Open `System Preferences`</span></span>
      - <span data-ttu-id="8a1b5-147">Kliknij pozycję`Sharing`</span><span class="sxs-lookup"><span data-stu-id="8a1b5-147">Click on `Sharing`</span></span>
      - <span data-ttu-id="8a1b5-148">Sprawdź `Remote Login` — zostanie wyświetlony komunikat`Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="8a1b5-148">Check `Remote Login` - Should say `Remote Login: On`</span></span>
      - <span data-ttu-id="8a1b5-149">Zezwalaj na dostęp do odpowiednich użytkowników</span><span class="sxs-lookup"><span data-stu-id="8a1b5-149">Allow access to appropriate users</span></span>
1. <span data-ttu-id="8a1b5-150">Edytuj `sshd_config` pliku w lokalizacji`/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="8a1b5-150">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
    - <span data-ttu-id="8a1b5-151">Edytor ulubionych lub</span><span class="sxs-lookup"><span data-stu-id="8a1b5-151">Use your favorite editor or</span></span>
    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```
    - <span data-ttu-id="8a1b5-152">Upewnij się, że jest włączone uwierzytelnianie hasła</span><span class="sxs-lookup"><span data-stu-id="8a1b5-152">Make sure password authentication is enabled</span></span>
    ```none
    PasswordAuthentication yes
    ```
    - <span data-ttu-id="8a1b5-153">Dodaj wpis podsystemu środowiska PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a1b5-153">Add a PowerShell subsystem entry</span></span>
    ```none
    Subsystem powershell /usr/local/bin/powershell -sshs -NoLogo -NoProfile
    ```
    - <span data-ttu-id="8a1b5-154">Opcjonalnie włączyć uwierzytelnianie za pomocą klucza</span><span class="sxs-lookup"><span data-stu-id="8a1b5-154">Optionally enable key authentication</span></span>
    ```none
    PubkeyAuthentication yes
    ```
1. <span data-ttu-id="8a1b5-155">Uruchom ponownie usługę sshd</span><span class="sxs-lookup"><span data-stu-id="8a1b5-155">Restart the sshd service</span></span>
    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="8a1b5-156">Przykład komunikację zdalną środowiska PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a1b5-156">PowerShell Remoting Example</span></span>

<span data-ttu-id="8a1b5-157">Najprostszym sposobem test komunikacji zdalnej jest po prostu Wypróbuj ją na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-157">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="8a1b5-158">W tym miejscu I utworzy sesji zdalnej, wróć do tego samego komputera w polu Linux.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-158">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="8a1b5-159">Zwróć uwagę, że używam poleceń cmdlet programu PowerShell z wiersza polecenia, widzimy wyświetla monit z pytaniem sprawdzić komputer-host, a także monitów o hasło SSH.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-159">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="8a1b5-160">Możesz to zrobić to samo na maszynę z systemem Windows upewnij się, że usługi zdalne działa, a następnie zdalne między komputerami, zmieniając po prostu nazwę hosta.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-160">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
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

### <a name="known-issues"></a><span data-ttu-id="8a1b5-161">Znane problemy</span><span class="sxs-lookup"><span data-stu-id="8a1b5-161">Known Issues</span></span>

1. <span data-ttu-id="8a1b5-162">polecenie sudo nie działa w sesji zdalnej dla systemu Linux maszyny.</span><span class="sxs-lookup"><span data-stu-id="8a1b5-162">sudo command does not work in remote session to Linux machine.</span></span>

[PowerShell for Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH
[instalacji]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[programu PowerShell dla systemu Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[programu PowerShell dla MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012
