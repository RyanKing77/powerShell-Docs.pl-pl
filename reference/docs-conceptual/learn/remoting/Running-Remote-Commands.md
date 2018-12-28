---
ms.date: 08/14/2018
keywords: polecenia cmdlet programu PowerShell
title: Uruchamianie poleceń zdalnych
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405473"
---
# <a name="running-remote-commands"></a>Uruchamianie poleceń zdalnych

Możesz uruchamiać polecenia w jednym węźle lub setek komputerów za pomocą jednego polecenia programu PowerShell. Program Windows PowerShell obsługuje przetwarzania zdalnego przy użyciu różnych technologii, takich jak usługi WMI, RPC i WS-Management.

Program PowerShell Core obsługuje WMI, usługi WS-Management i usług zdalnych SSH. RPC nie jest już obsługiwana.

Aby uzyskać więcej informacji na temat komunikacji zdalnej w programie PowerShell Core zobacz następujące artykuły:

- [SSH komunikacji zdalnej w programie PowerShell Core][ssh-remoting]
- [Komunikacja zdalna usługi WS-Management, w programie PowerShell Core][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Komunikacji zdalnej programu Windows PowerShell bez konfiguracji

Wiele poleceń cmdlet programu Windows PowerShell ma parametr ComputerName, który umożliwia zbieranie danych i zmienić ustawienia, na co najmniej jeden komputer zdalny. Te polecenia cmdlet Użyj różnych protokołów komunikacyjnych i działa we wszystkich systemach operacyjnych Windows, bez żadnej specjalnej konfiguracji.

Te polecenia cmdlet obejmują:

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Wyczyść w dzienniku zdarzeń](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

Zazwyczaj polecenia cmdlet, które obsługują komunikację zdalną bez specjalnej konfiguracji ma parametr ComputerName, a nie ma parametr sesji. Aby znaleźć te polecenia cmdlet w sesji, wpisz:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Komunikacji zdalnej programu Windows PowerShell

Przy użyciu protokołu WS-Management, komunikacji zdalnej programu Windows PowerShell umożliwiają uruchamianie dowolnego polecenia programu Windows PowerShell na co najmniej jeden komputer zdalny. Możesz ustanowienia połączeń trwałych, uruchamiania interaktywnych sesji i uruchamiać skrypty na komputerach zdalnych.

Aby użyć komunikacji zdalnej programu Windows PowerShell, należy określić komputer zdalny do zdalnego zarządzania.
Aby uzyskać więcej informacji, w tym instrukcje, zobacz [o wymagania dotyczące zdalnego](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Po skonfigurowaniu komunikacji zdalnej programu Windows PowerShell wiele strategii komunikacji zdalnej są dostępne dla Ciebie.
W tym artykule wymieniono kilka z nich. Aby uzyskać więcej informacji, zobacz [o zdalnym](/powershell/module/microsoft.powershell.core/about/about_remote).

### <a name="start-an-interactive-session"></a>Rozpoczynania interaktywnej sesji

Aby rozpocząć interaktywnej sesji z jednym komputerem zdalnym, użyj [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) polecenia cmdlet.
Na przykład rozpoczynania interaktywnej sesji z komputerem zdalnym Serwer01, wpisz:

```powershell
Enter-PSSession Server01
```

Zmiany wiersza polecenia, aby wyświetlić nazwę komputera zdalnego. Wszystkie wpisywane w wierszu polecenia Uruchom na komputerze zdalnym, a wyniki są wyświetlane na komputerze lokalnym.

Aby zakończyć interaktywną sesję, wpisz:

```powershell
Exit-PSSession
```

Aby uzyskać więcej informacji na temat polecenia cmdlet Enter-PSSession i PSSession zakończenia zobacz:

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [PSSession zakończenia](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Uruchom polecenie zdalne

Aby uruchomić polecenie na co najmniej jeden komputer, użyj [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) polecenia cmdlet. Na przykład, aby uruchomić [Get UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) Serwer01 i serwer02 komputerów zdalnych, wpisz polecenie:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

Dane wyjściowe są zwracane do komputera.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Uruchamianie skryptu

Aby uruchomić skrypt w jeden lub wiele komputerów zdalnych, należy użyć parametru FilePath `Invoke-Command` polecenia cmdlet. Skryptu musi być na lub jest dostępny na komputerze lokalnym. Wyniki są zwracane do komputera lokalnego.

Na przykład następujące polecenie uruchamia skrypt DiskCollect.ps1 na komputerach zdalnych, Serwer01 i serwer02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Ustanowienia połączeń trwałych

Użyj `New-PSSession` polecenia cmdlet, aby utworzyć trwały sesji na komputerze zdalnym. Poniższy przykład tworzy sesje zdalne Serwer01 i serwer02. Obiektów sesji są przechowywane w `$s` zmiennej.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Teraz, gdy sesje są ustanowione, możesz uruchomić dowolne polecenie w nich. I sesje są trwałe, można zbierać dane z jednego polecenia i używać go w innym poleceniu.

Na przykład następujące polecenie uruchamia polecenie Get-HotFix w sesji w zmiennej $s i zapisuje wyniki w zmiennej $h. Utworzono zmienną $h we wszystkich sesjach w $s, ale nie istnieje w lokalnej sesji.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Teraz możesz używać danych w `$h` zmiennej z innymi poleceniami w tej samej sesji. Wyniki są wyświetlane na komputerze lokalnym. Przykład:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Zaawansowane komunikacji zdalnej.

Zdalne zarządzanie programu Windows PowerShell po prostu zaczyna się tutaj. Korzystając z poleceń cmdlet zainstalowanych za pomocą programu Windows PowerShell, można ustanowić i skonfigurować zdalnej sesji z lokalnymi i zdalnymi kończy się tworzenie dostosowanych i objęty ograniczeniami sesji, umożliwia użytkownikom import poleceń w sesji zdalnej, które faktycznie uruchomić niejawnie w sesji zdalnej, należy skonfigurować zabezpieczenia sesję zdalną i o wiele więcej.

Program Windows PowerShell zawiera dostawcę usługi WS-Management. Tworzy dostawcę `WSMAN:` dysku, który pozwala nawigować po hierarchii ustawień konfiguracji na komputerze lokalnym i na komputerach zdalnych.

Aby uzyskać więcej informacji na temat dostawcy usługi WS-Management, zobacz [dostawcy usługi WS-Management](https://technet.microsoft.com/library/dd819476.aspx) i [polecenia cmdlet dotyczące usługi WS-Management](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), lub w konsoli programu Windows PowerShell, wpisz `Get-Help wsman`.

Aby uzyskać więcej informacji, zobacz:

- [Temat zdalnego — często zadawane pytania](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Aby uzyskać pomoc dotyczącą błędów usługami zdalnymi, zobacz [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Zobacz też

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Dostawca usługi WS-Management](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md