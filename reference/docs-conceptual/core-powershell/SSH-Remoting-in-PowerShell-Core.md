# <a name="powershell-remoting-over-ssh"></a>Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH

## <a name="overview"></a>Przegląd

Usługi zdalne środowiska PowerShell zwykle używa usługi WinRM negocjowania połączenia i transportu danych.
SSH została wybrana dla tej implementacji komunikacji zdalnej, ponieważ jest teraz dostępna dla platform zarówno systemu Linux i Windows i umożliwia obsługę zdalną środowiska PowerShell dla wielu platform wartość true.
Jednak WinRM udostępnia niezawodny modelu hostingu dla sesji zdalnej programu PowerShell, które ta implementacja jeszcze nie działa.
Co oznacza, że konfiguracja zdalnego punktu końcowego programu PowerShell i JEA (tylko tyle Administracja) nie jest jeszcze obsługiwana w tej implementacji.

Usługi zdalne środowiska PowerShell SSH umożliwia podstawowe komunikacji zdalnej sesji programu PowerShell między komputerami z systemem Windows i Linux.
Jest to zrobić przez utworzenie programu PowerShell, proces na komputerze docelowym jako podsystemu SSH hostingu.
Ostatecznie to będzie można zmienić na bardziej ogólne modelu hostingu, podobnie jak WinRM działa w celu zapewnienia obsługi konfiguracji punktu końcowego i JEA.

Polecenia cmdlet New-PSSession, Enter-PSSession i Invoke-Command jest nowy parametr ustawioną ułatwienia tego nowego połączenia zdalnego

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Ten nowy zestaw parametrów prawdopodobnie ulegnie zmianie, ale teraz służy do tworzenia SSH PSSessions można interakcyjnie z wiersza polecenia lub wywołania poleceń i skryptów na.
Możesz określić komputer docelowy przy użyciu parametru nazwy hosta i podaj nazwę użytkownika z nazwą użytkownika.
Podczas interakcyjnego uruchamiania polecenia cmdlet w wierszu polecenia programu PowerShell pojawi się monit o podanie hasła.
Ale masz opcję, aby używać uwierzytelniania klucza SSH i podaj ścieżkę pliku klucza prywatnego za pomocą parametru ściezka do pliku klucza.

## <a name="general-setup-information"></a>Informacje ogólne

SSH jest musi być zainstalowany na wszystkich komputerach.
Należy zainstalować klienta (ssh.exe) i serwera (sshd.exe), dzięki czemu możesz eksperymentować z usługami zdalnymi do i z maszyn.
Dla systemu Windows, musisz zainstalować [OpenSSH Win32 z usługi GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
W systemie Linux należy zainstalować SSH (takie jak serwer sshd) odpowiednią dla danej platformy.
Należy również ostatnie kompilacji programu PowerShell lub pakietu z usługi GitHub o SSH funkcja komunikacji zdalnej.
Podsystemy SSH jest używany do ustanawiania procesu programu PowerShell na komputerze zdalnym i należy skonfigurować tego serwera SSH.
Ponadto należy włączyć uwierzytelnianie hasła i opcjonalnie klucza uwierzytelniania przy użyciu.

## <a name="setup-on-windows-machine"></a>Instalacja na komputerze z systemem Windows

1. Zainstaluj najnowszą wersję pakietu [Core programu PowerShell dla systemu Windows]
    - Można określić, czy obsługa komunikacji zdalnej SSH analizując parametr ustawia New-PSSession

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. Zainstaluj najnowszą [Win32 OpenSSH] kompilacji z witryny GitHub przy użyciu [instalacji] instrukcje
1. Edytuj plik sshd_config w lokalizacji, w którym zainstalowano Win32 OpenSSH
    - Upewnij się, że jest włączone uwierzytelnianie hasła

    ```
    PasswordAuthentication yes
    ```

    - Dodaj wpis podsystemu programu PowerShell, Zastąp `c:/program files/powershell/6.0.0/pwsh.exe` z poprawną ścieżkę do wersji, którego chcesz użyć

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - Opcjonalnie włączyć uwierzytelnianie za pomocą klucza

    ```
    PubkeyAuthentication yes
    ```

1. Uruchom ponownie usługę sshd

    ```powershell
    Restart-Service sshd
    ```

1. Dodaj ścieżkę zainstalowanym OpenSSH do Twojej zmiennej Env ścieżki
    - To pole powinno być wzdłuż linii `C:\Program Files\OpenSSH\`
    - Dzięki temu ssh.exe do znalezienia

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Ustawienia na komputerze z systemem Linux (Ubuntu 14.04)

1. Zainstaluj najnowszą [programu PowerShell dla systemu Linux] kompilacji z witryny GitHub
1. Zainstaluj [Ubuntu SSH] zgodnie z potrzebami

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. Edytuj plik sshd_config w lokalizacji /etc/ssh
    - Upewnij się, że jest włączone uwierzytelnianie hasła

    ```
    PasswordAuthentication yes
    ```

    - Dodaj wpis podsystemu środowiska PowerShell

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - Opcjonalnie włączyć uwierzytelnianie za pomocą klucza

    ```
    PubkeyAuthentication yes
    ```

1. Uruchom ponownie usługę sshd

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a>Instalacja na komputerze MacOS

1. Zainstaluj najnowszą [programu PowerShell dla MacOS] kompilacji
    - Upewnij się, że usługi zdalne SSH jest włączone, wykonaj następujące czynności:
      - Otwórz `System Preferences`
      - Kliknij pozycję `Sharing`
      - Sprawdź `Remote Login` — zostanie wyświetlony komunikat `Remote Login: On`
      - Zezwalaj na dostęp do odpowiednich użytkowników
1. Edytuj `sshd_config` pliku w lokalizacji `/private/etc/ssh/sshd_config`
    - Edytor ulubionych lub

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - Upewnij się, że jest włączone uwierzytelnianie hasła

    ```
    PasswordAuthentication yes
    ```

    - Dodaj wpis podsystemu środowiska PowerShell

    ```
    Subsystem powershell /usr/local/bin/powershell -sshs -NoLogo -NoProfile
    ```

    - Opcjonalnie włączyć uwierzytelnianie za pomocą klucza

    ```
    PubkeyAuthentication yes
    ```

1. Uruchom ponownie usługę sshd

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a>Przykład komunikację zdalną środowiska PowerShell

Najprostszym sposobem test komunikacji zdalnej jest po prostu Wypróbuj ją na jednym komputerze.
W tym miejscu I utworzy sesji zdalnej, wróć do tego samego komputera w polu Linux.
Zwróć uwagę, że używam poleceń cmdlet programu PowerShell z wiersza polecenia, widzimy wyświetla monit z pytaniem sprawdzić komputer-host, a także monitów o hasło SSH.
Możesz to zrobić to samo na maszynę z systemem Windows upewnij się, że usługi zdalne działa, a następnie zdalne między komputerami, zmieniając po prostu nazwę hosta.

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

### <a name="known-issues"></a>Znane problemy

1. polecenie sudo nie działa w sesji zdalnej dla systemu Linux maszyny.

[Core programu PowerShell dla systemu Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH
[instalacji]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[programu PowerShell dla systemu Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[programu PowerShell dla MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012