
# <a name="powershell-remoting-over-ssh"></a>Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH

## <a name="overview"></a>Przegląd

Komunikacja zdalna programu PowerShell zwykle używa funkcji WinRM do negocjowania połączenia i transport danych.
SSH została wybrana dla tej implementacji komunikacji zdalnej, ponieważ jest teraz dostępna dla systemów Linux i Windows Platform i zezwala na wartość true dla wielu platform komunikacji zdalnej programu PowerShell.
Jednak usługi WinRM udostępnia niezawodne modelu hostingu dla sesji zdalnej programu PowerShell, które ta implementacja jeszcze nie działa.
Co oznacza, że konfiguracja zdalnego punktu końcowego programu PowerShell oraz zestawu narzędziowego JEA (Just Enough Administration) nie jest jeszcze obsługiwany w tej implementacji.

Komunikacja zdalna programu PowerShell SSH umożliwia podstawowe komunikacji zdalnej sesji programu PowerShell między maszynami Windows i Linux.
Jest to zrobić przez utworzenie programu PowerShell, proces na komputerze docelowym jako podsystemu SSH hostingu.
Ostatecznie to będzie można zmienić na bardziej ogólnych modelu hostingu, podobnie do sposobu działania usługi WinRM w celu zapewnienia obsługi konfiguracji punktu końcowego oraz zestawu narzędziowego JEA.

`New-PSSession`, `Enter-PSSession` i `Invoke-Command` polecenia cmdlet zawierają już nowy parametr równa ułatwienia tego nowego połączenia zdalnego

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Ten nowy zestaw parametrów najprawdopodobniej ulegną zmianom, ale teraz pozwala na tworzenie SSH sterować można wchodzić w interakcje z poziomu wiersza polecenia lub wywołania poleceń i skryptów na.
Określ maszynie docelowej za pomocą parametru nazwy hosta i podaj nazwę użytkownika przy użyciu nazwy użytkownika.
Podczas interakcyjnego wykonywania polecenia cmdlet w wierszu polecenia programu PowerShell zostanie monit o podanie hasła.
Ale istnieje również możliwość używają uwierzytelniania kluczem SSH i podaj ścieżkę pliku klucza prywatnego za pomocą parametru atrybut KeyFilePath.

## <a name="general-setup-information"></a>Ustawienia ogólne informacje

Protokół SSH jest wymagany do zainstalowania na wszystkich komputerach.
Należy zainstalować zarówno klienta (`ssh.exe`) i serwera (`sshd.exe`), dzięki czemu możesz eksperymentować z wywołaniem funkcji zdalnych do i z maszyny.
Dla Windows należy zainstalować [Win32 OpenSSH z serwisu GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Dla systemu Linux należy zainstalować SSH (takie jak serwer sshd) odpowiednie dla danej platformy.
Należy również najnowszych kompilacji programu PowerShell lub pakietu z usługi GitHub o funkcja komunikacji zdalnej SSH.
Podsystemy SSH jest używany do ustanawiania proces programu PowerShell na komputerze zdalnym, a serwer SSH będzie trzeba skonfigurować dla tego.
Ponadto należy włączyć uwierzytelnianie przy użyciu hasła i opcjonalnie klucza uwierzytelniania przy użyciu.

## <a name="setup-on-windows-machine"></a>Instalacja na komputerze Windows

1. Zainstaluj najnowszą wersję programu [program PowerShell Core Windows]
   - Można stwierdzić, jeśli ma on Obsługa komunikacji zdalnej SSH, analizując parametr ustawia `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Zainstaluj najnowszą kompilację [Win32 OpenSSH] z usługi GitHub za pomocą instrukcji [instalacji]
3. Edytowanie pliku sshd_config w lokalizacji, w którym instalowane Win32 OpenSSH
   - Upewnij się, że włączone jest uwierzytelnianie przy użyciu hasła

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    Brak usterkę w OpenSSH dla Windows uniemożliwiający pracujących w ścieżki pliku wykonywalnego podsystemu miejsc do magazynowania.
    Zobacz [ten problem w serwisie GitHub, aby uzyskać więcej informacji](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

    Rozwiązanie polega na Utwórz Link symboliczny do katalogu instalacyjnego programu Powershell, który nie zawiera spacji:

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    a następnie wprowadź go w podsystemie:

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - Opcjonalnie włączyć uwierzytelnianie za pomocą klucza

   ```
   PubkeyAuthentication yes
   ```

4. Uruchom ponownie usługę sshd

   ```powershell
   Restart-Service sshd
   ```

5. Dodaj ścieżkę zainstalowanym OpenSSH do swojej zmiennej Env ścieżki
   - Powinno to być wzdłuż linii `C:\Program Files\OpenSSH\`
   - Dzięki temu ssh.exe ma zostać odnaleziona

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Ustawienia na komputerze z systemem Linux (Ubuntu 14.04)

1. Zainstaluj najnowszą kompilację [program PowerShell Core dla systemu Linux] z usługi GitHub
2. Zainstaluj [Ubuntu SSH] zgodnie z potrzebami

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Edytowanie pliku sshd_config w lokalizacji /etc/ssh
   - Upewnij się, że włączone jest uwierzytelnianie przy użyciu hasła

   ```
   PasswordAuthentication yes
   ```

   - Dodaj wpis podsystem PowerShell

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Opcjonalnie włączyć uwierzytelnianie za pomocą klucza

   ```
   PubkeyAuthentication yes
   ```

4. Uruchom ponownie usługę sshd

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a>Instalacja na komputerze z systemem MacOS

1. Zainstaluj najnowszą kompilację [program PowerShell Core dla systemu MacOS]
   - Upewnij się, że komunikacja zdalna SSH jest włączona, wykonując następujące czynności:
     - Otwórz `System Preferences`
     - Kliknij pozycję `Sharing`
     - Sprawdź `Remote Login` — powinna być widoczna nazwa `Remote Login: On`
     - Zezwalaj na dostęp do odpowiednich użytkowników
2. Edytuj `sshd_config` pliku w lokalizacji `/private/etc/ssh/sshd_config`
   - Użyj ulubionego edytora lub

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Upewnij się, że włączone jest uwierzytelnianie przy użyciu hasła

     ```
     PasswordAuthentication yes
     ```

   - Dodaj wpis podsystem PowerShell

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Opcjonalnie włączyć uwierzytelnianie za pomocą klucza

     ```
     PubkeyAuthentication yes
     ```

3. Uruchom ponownie usługę sshd

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a>Przykładowy komunikacji zdalnej programu PowerShell

Najprostszym sposobem przetestowania komunikacji zdalnej jest po prostu spróbuj na jednym komputerze.
W tym miejscu I utworzy sesji zdalnej, wróć do tego samego komputera w usłudze box systemu Linux.
Zwróć uwagę, że używam poleceń cmdlet programu PowerShell z poziomu wiersza polecenia, widzimy wyświetli monit z pytaniem sprawdzić, na komputerze-hoście, a także monitów o hasło protokołu SSH.
Możesz zrobić to samo w Windows maszynę, aby upewnić się, że komunikacja zdalna działa istnieje, a następnie zdalnego między maszynami, po prostu modyfikując nazwę hosta.

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

### <a name="known-issues"></a>Znane problemy

- polecenie "sudo" nie działa w sesji zdalnej do maszyny z systemem Linux.

## <a name="see-also"></a>Zobacz też

[Program PowerShell Core dla Windows](../setup/installing-powershell-core-on-windows.md#msi)

[Program PowerShell Core w systemie Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[Program PowerShell Core dla systemu MacOS](../setup/installing-powershell-core-on-macos.md)

[Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)

[Instalacja](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)