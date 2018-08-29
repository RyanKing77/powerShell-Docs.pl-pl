---
title: Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH
description: Komunikacji zdalnej w programie PowerShell Core przy użyciu protokołu SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1de034d667aa9a377e5460e7eb474402c690cb42
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133835"
---
# <a name="powershell-remoting-over-ssh"></a>Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH

## <a name="overview"></a>Przegląd

Komunikacja zdalna programu PowerShell zwykle używa funkcji WinRM do negocjowania połączenia i transport danych. Protokół SSH jest teraz dostępny dla platform Linux i Windows i zezwala na wartość true dla wielu platform komunikacji zdalnej programu PowerShell.

Usługa WinRM zapewnia niezawodne modelu hostingu dla sesji zdalnej programu PowerShell. który tego wdrożenia opartego na SSH wywołaniem funkcji zdalnych nie aktualnie obsługuje konfigurację zdalnego punktu końcowego oraz zestawu narzędziowego JEA (Just Enough Administration).

Komunikacja zdalna SSH umożliwia podstawowe komunikacji zdalnej sesji programu PowerShell między maszynami Windows i Linux. SSH Remoting tworzy proces hosta programu PowerShell na komputerze docelowym jako podsystemu SSH.
Po pewnym czasie będzie wdrażamy ogólny model hostingu, podobnie jak usługi WinRM do obsługi konfiguracji punktu końcowego oraz zestawu narzędziowego JEA.

`New-PSSession`, `Enter-PSSession`, I `Invoke-Command` polecenia cmdlet zawierają już nowy parametr skonfigurowane do obsługi tego nowego połączenia zdalnego.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Aby utworzyć sesję zdalną, należy określić na komputerze docelowym z `HostName` parametru i podaj nazwę użytkownika z `UserName`. Podczas interakcyjnego wykonywania polecenia cmdlet, zostanie wyświetlony monit o podanie hasła. Można także użyć uwierzytelniania klucza SSH przy użyciu pliku klucza prywatnego za pomocą `KeyFilePath` parametru.

## <a name="general-setup-information"></a>Ustawienia ogólne informacje

SSH musi być zainstalowany na wszystkich komputerach. Zainstaluj klienta SSH (`ssh.exe`) i serwera (`sshd.exe`) aby można było zdalnego, do i z maszyny. Windows, można zainstalować [Win32 OpenSSH z serwisu GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
W przypadku systemu Linux Zainstaluj SSH (takie jak serwer sshd) odpowiednie dla danej platformy. Należy również zainstalować program PowerShell Core z witryny GitHub można pobrać funkcja komunikacji zdalnej SSH. Serwer SSH musi być skonfigurowany do utworzenia podsystemie SSH do hostowania proces programu PowerShell na komputerze zdalnym. Należy również skonfigurować Włącz haseł lub uwierzytelniania opartego na kluczu.

## <a name="set-up-on-windows-machine"></a>Skonfiguruj na komputerze Windows

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
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Brak usterkę w OpenSSH dla Windows uniemożliwiający pracujących w ścieżki pliku wykonywalnego podsystemu miejsc do magazynowania. Aby uzyskać więcej informacji, zobacz [problem w usłudze GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Rozwiązanie polega na Utwórz Link symboliczny do katalogu instalacyjnego programu Powershell, który nie ma miejsca do magazynowania:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     a następnie wprowadź go w podsystemie:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Opcjonalnie włączyć uwierzytelnianie za pomocą klucza

     ```
     PubkeyAuthentication yes
     ```

4. Uruchom ponownie usługę sshd

   ```powershell
   Restart-Service sshd
   ```

5. Dodaj ścieżkę zainstalowanym OpenSSH do zmiennej środowiskowej Path. Na przykład `C:\Program Files\OpenSSH\`. Ten wpis umożliwia ssh.exe ma zostać odnaleziona.

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>Skonfiguruj na komputerze z systemem Linux (Ubuntu 14.04)

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

## <a name="set-up-on-macos-machine"></a>Na komputerze z systemem MacOS

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

Najprostszym sposobem przetestowania komunikacji zdalnej jest do wypróbowania tej funkcji na jednym komputerze. W tym przykładzie utworzymy sesji zdalnej, wróć do tej samej maszyny z systemem Linux. Firma Microsoft przy użyciu programu PowerShell, poleceń cmdlet interaktywnie, więc widzimy monity z protokołu SSH z pytaniem sprawdzić komputer-host i monitem o podanie hasła. Możesz zrobić to samo na komputerze Windows Aby upewnić się, że komunikacja zdalna działa. Następnie zdalnego między maszynami, zmieniając nazwę hosta.

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

### <a name="known-issues"></a>Znane problemy

Polecenie "sudo" nie działa w sesji zdalnej do maszyny z systemem Linux.

## <a name="see-also"></a>Zobacz też

[Program PowerShell Core dla Windows](../setup/installing-powershell-core-on-windows.md#msi)

[Program PowerShell Core w systemie Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[Program PowerShell Core dla systemu MacOS](../setup/installing-powershell-core-on-macos.md)

[Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)

[Instalacja](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
