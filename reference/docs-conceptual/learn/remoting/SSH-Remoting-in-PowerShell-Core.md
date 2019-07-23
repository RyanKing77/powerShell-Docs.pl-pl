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
# <a name="powershell-remoting-over-ssh"></a>Obsługa zdalna programu PowerShell za pośrednictwem protokołu SSH

## <a name="overview"></a>Omówienie

Komunikacja zdalna programu PowerShell zwykle używa usługi WinRM do negocjacji połączeń i transportu danych. Protokół SSH jest teraz dostępny dla platform Linux i Windows i umożliwia obsługę komunikacji zdalnej dla wieloplatformowego programu PowerShell.

Usługa WinRM udostępnia niezawodny model hostingu dla sesji zdalnych programu PowerShell. Komunikacja zdalna oparta na protokole SSH nie obsługuje obecnie konfiguracji i JEA zdalnego punktu końcowego.

Komunikacja zdalna SSH umożliwia wykonywanie podstawowych sesji programu PowerShell dla komunikacji zdalnej między komputerami z systemem Windows i Linux. Komunikacja zdalna SSH tworzy proces hosta programu PowerShell na maszynie docelowej jako podsystem SSH. Ostatecznie zaimplementujemy ogólny model hostingu podobny do usługi WinRM, aby obsługiwał konfigurację punktów końcowych i JEA.

Polecenia cmdlet `Enter-PSSession` ,i`Invoke-Command` mają teraz nowy zestaw parametrów do obsługi nowego połączenia zdalnego. `New-PSSession`

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Aby utworzyć sesję zdalną, należy określić maszynę docelową `HostName` z parametrem i podać nazwę użytkownika `UserName`przy użyciu. Gdy uruchamiasz polecenia cmdlet interaktywnie, zostanie wyświetlony monit o podanie hasła. Można również użyć uwierzytelniania klucza SSH przy użyciu pliku klucza prywatnego z `KeyFilePath` parametrem.

## <a name="general-setup-information"></a>Ogólne informacje o instalacji

Protokół SSH musi być zainstalowany na wszystkich komputerach. Zainstaluj klienta SSH (`ssh.exe`) i serwer (`sshd.exe`), aby móc zdalnie z maszyn i z nich. OpenSSH dla systemu Windows jest teraz dostępny w systemie Windows 10 Build 1809 i Windows Server 2019. Aby uzyskać więcej informacji, zobacz [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview). W przypadku systemu Linux Zainstaluj protokół SSH (w tym serwer SSHD) odpowiednie dla danej platformy. Musisz również zainstalować program PowerShell Core z usługi GitHub, aby uzyskać funkcję komunikacji zdalnej SSH. Serwer SSH musi być skonfigurowany tak, aby utworzyć podsystem SSH do hostowania procesu programu PowerShell na maszynie zdalnej. Należy również skonfigurować opcję Włącz uwierzytelnianie hasła lub klucza.

## <a name="set-up-on-windows-machine"></a>Konfiguracja na komputerze z systemem Windows

1. Zainstaluj najnowszą wersję programu [PowerShell Core dla systemu Windows](../../install/installing-powershell-core-on-windows.md#msi)

   - Możesz określić, czy ma ona obsługę komunikacji zdalnej SSH, przeglądając zestawy parametrów dla`New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Zainstaluj najnowszą wersję Win32 OpenSSH. Instrukcje instalacji znajdują się w temacie [instalacja programu OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).
3. Edytuj plik znajdujący się `$env:ProgramData\ssh`w lokalizacji. `sshd_config`

   - Upewnij się, że uwierzytelnianie hasła jest włączone

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Wystąpił błąd w OpenSSH dla systemu Windows, który uniemożliwia pracę w ścieżkach wykonywalnych podsystemu. Aby uzyskać więcej informacji, zobacz [problem w usłudze GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Jednym z rozwiązań jest utworzenie link symboliczny w katalogu instalacyjnym programu PowerShell, który nie zawiera spacji:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     a następnie wprowadź ją w podsystemie:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Opcjonalnie Włącz uwierzytelnianie klucza

     ```
     PubkeyAuthentication yes
     ```

4. Uruchom ponownie usługę SSHD

   ```powershell
   Restart-Service sshd
   ```

5. Dodaj ścieżkę, gdzie OpenSSH jest zainstalowana w zmiennej środowiskowej PATH. Na przykład `C:\Program Files\OpenSSH\`. Ten wpis umożliwia znalezienie pliku SSH. exe.

## <a name="set-up-on-linux-ubuntu-1604-machine"></a>Konfiguracja na komputerze z systemem Linux (Ubuntu 16,04)

1. Zainstaluj najnowszą kompilację [programu PowerShell Core dla systemu Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) z usługi GitHub
2. Zainstaluj [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) zgodnie z wymaganiami

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Edytuj plik sshd_config w lokalizacji/etc/ssh

   - Upewnij się, że uwierzytelnianie hasła jest włączone

   ```
   PasswordAuthentication yes
   ```

   - Dodawanie wpisu podsystemu programu PowerShell

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Opcjonalnie Włącz uwierzytelnianie klucza

   ```
   PubkeyAuthentication yes
   ```

4. Uruchom ponownie usługę SSHD

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Konfiguracja na maszynie MacOS

1. Zainstaluj najnowszą wersję [programu PowerShell Core dla kompilacji MacOS](../../install/installing-powershell-core-on-macos.md)

   - Upewnij się, że komunikacja zdalna SSH jest włączona, wykonując następujące czynności:
     - Otwórz`System Preferences`
     - Kliknij pozycję`Sharing`
     - Sprawdzenie `Remote Login` — należy powiedzieć`Remote Login: On`
     - Zezwalaj na dostęp do odpowiednich użytkowników

2. `sshd_config` Edytuj plik w lokalizacji`/private/etc/ssh/sshd_config`

   - Użyj swojego ulubionego edytora lub

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Upewnij się, że uwierzytelnianie hasła jest włączone

     ```
     PasswordAuthentication yes
     ```

   - Dodawanie wpisu podsystemu programu PowerShell

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Opcjonalnie Włącz uwierzytelnianie klucza

     ```
     PubkeyAuthentication yes
     ```

3. Uruchom ponownie usługę SSHD

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Uwierzytelnianie

Komunikacja zdalna programu PowerShell za pośrednictwem protokołu SSH polega na wymianie uwierzytelniania między klientem SSH i usługą SSH i nie implementuje żadnego ze schematów uwierzytelniania. Oznacza to, że wszystkie skonfigurowane schematy uwierzytelniania, w tym uwierzytelnianie wieloskładnikowe, są obsługiwane przez protokół SSH i niezależne od programu PowerShell. Można na przykład skonfigurować usługę SSH, aby wymagała uwierzytelniania klucza publicznego oraz hasła jednorazowego w celu zwiększenia bezpieczeństwa. Konfiguracja usługi uwierzytelniania wieloskładnikowego jest poza zakresem tej dokumentacji. Zapoznaj się z dokumentacją protokołu SSH, aby poprawnie skonfigurować uwierzytelnianie wieloskładnikowe i sprawdzić, czy działa on poza programem PowerShell, przed podjęciem próby użycia go z usługami zdalnymi programu PowerShell.

## <a name="powershell-remoting-example"></a>Przykład komunikacji zdalnej programu PowerShell

Najprostszym sposobem testowania komunikacji zdalnej jest wypróbowanie jej na pojedynczym komputerze. W tym przykładzie utworzysz sesję zdalną z powrotem do tej samej maszyny z systemem Linux. Używamy poleceń cmdlet programu PowerShell interaktywnie, więc zobaczymy monity z prośbą o zweryfikowanie komputera-hosta i monitowanie o podanie hasła. Tę samą funkcję można wykonać na komputerze z systemem Windows, aby upewnić się, że komunikacja zdalna działa. Następnie możesz zdalnie między maszynami, zmieniając nazwę hosta.

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

### <a name="known-issues"></a>Znane problemy

Polecenie sudo nie działa w sesji zdalnej z maszyną z systemem Linux.

## <a name="see-also"></a>Zobacz też

[Program PowerShell Core dla systemu Windows](../../install/installing-powershell-core-on-windows.md#msi)

[Program PowerShell Core dla systemu Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[Rdzeń programu PowerShell dla MacOS](../../install/installing-powershell-core-on-macos.md)

[OpenSSH dla systemu Windows](/windows-server/administration/openssh/openssh_overview)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
