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
# <a name="running-remote-commands"></a>Uruchamianie poleceń zdalnych
Polecenia można wykonać na co najmniej setek komputerów za pomocą jednego polecenia programu Windows PowerShell. Program Windows PowerShell obsługuje przetwarzania zdalnego przy użyciu różnych technologii, w tym usługi WMI, RPC i WS-Management.

## <a name="remoting-without-configuration"></a>Komunikację zdalną bez konfiguracji
Wiele poleceń cmdlet programu Windows PowerShell ma parametr ComputerName, który umożliwia zbieranie danych i zmienić ustawienia, na co najmniej jeden komputer zdalny. We wszystkich systemach operacyjnych Windows, które środowiska Windows PowerShell obsługuje bez żadnej specjalnej konfiguracji korzystają z różnych technologii komunikacji i wiele pracy.

Te polecenia cmdlet obejmują:
* [Uruchom ponownie komputer](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Połączenie testowe](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Wyczyść EventLog](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-dziennika zdarzeń](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get poprawki](https://go.microsoft.com/fwlink/?LinkId=821586)
  - [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Ustawianie usługi](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

Zazwyczaj polecenia cmdlet, które obsługują komunikację zdalną bez specjalnej konfiguracji ma parametr ComputerName, a nie ma parametru sesji. Aby znaleźć te polecenia cmdlet w sesji, wpisz:

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Komunikacji zdalnej programu Windows PowerShell
Komunikacji zdalnej programu Windows PowerShell, która używa protokołu WS-Management, można uruchomić wszystkie polecenia programu Windows PowerShell na jednym lub wielu komputerach zdalnych. Umożliwia ustanowienie połączenia trwałe, sesje interakcyjne 1:1 i uruchamiać skrypty na wielu komputerach.

Aby użyć komunikacji zdalnej programu Windows PowerShell, komputer zdalny musi być skonfigurowany do zdalnego zarządzania. Aby uzyskać więcej informacji, w tym instrukcje, zobacz [o wymagania dotyczące zdalnego](https://technet.microsoft.com/en-us/library/dd315349.aspx).

Po skonfigurowaniu komunikacji zdalnej programu Windows PowerShell, wiele strategii komunikacji zdalnej są dostępne. W pozostałej części tego dokumentu zawiera tylko niektóre z nich. Aby uzyskać więcej informacji, zobacz [o zdalnego](https://technet.microsoft.com/en-us/library/dd347744.aspx) i [o zdalnego — często zadawane pytania](https://technet.microsoft.com/en-us/library/dd347744.aspx).

### <a name="start-an-interactive-session"></a>Uruchomić sesji interaktywnej
Aby uruchomić sesji interaktywnej z jednym komputerem zdalnym, należy użyć [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) polecenia cmdlet.
Na przykład aby rozpocząć sesji interaktywnej Serwer01 komputerem zdalnym, wpisz:

```
Enter-PSSession Server01
```

Aby wyświetlić nazwę komputera, do którego są podłączeni zmiany wiersza polecenia. Następnie uruchom wszystkie wpisywane w wierszu polecenia na komputerze zdalnym, a wyniki są wyświetlane na komputerze lokalnym.

Aby zakończyć sesję interaktywne, wpisz:

```
Exit-PSSession
```

Aby uzyskać więcej informacji na temat polecenia cmdlet Enter-PSSession i zakończenia-PSSession, zobacz [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) i [zakończenia-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).

### <a name="run-a-remote-command"></a>Uruchom polecenia zdalnego
Aby uruchomić dowolnego polecenia na jednym lub wielu komputerach zdalnych, należy użyć [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) polecenia cmdlet.
Na przykład, aby uruchomić [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) do Serwer01 i serwer02 komputerów zdalnych, wpisz polecenie:

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

Dane wyjściowe są zwracane do komputera.

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
Aby uzyskać więcej informacji na temat polecenia cmdlet Invoke-Command, zobacz [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="run-a-script"></a>Uruchom skrypt
Aby uruchomić skrypt na jednym lub wielu komputerach zdalnych, użyj parametru FilePath polecenia cmdlet Invoke-Command. Skrypt nie może być dostępny na komputerze lokalnym. Wyniki są zwracane do komputera lokalnego.

Na przykład następujące polecenie uruchamia skrypt DiskCollect.ps1 na komputerach zdalnych Serwer01 i serwer02.

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

Aby uzyskać więcej informacji na temat polecenia cmdlet Invoke-Command, zobacz [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="establish-a-persistent-connection"></a>Ustanowić trwałe połączenie
Na uruchomieniu serii pokrewnych poleceń, które udostępniają danych, utworzenia sesji na komputerze zdalnym, a następnie uruchom polecenia w sesji, który utworzono za pomocą polecenia cmdlet Invoke-Command. Aby utworzyć sesję zdalną, należy użyć polecenia cmdlet New-PSSession.

Na przykład następujące polecenie tworzy sesję zdalną na komputerze Serwer01 i innej sesji zdalnej na komputerze serwer02. Obiektów sesji jest zapisywany w zmiennej $s.

```
$s = New-PSSession -ComputerName Server01, Server02
```

Teraz, gdy sesje są ustalone, możesz uruchomić dowolne polecenie w nich. I ponieważ sesje są trwałe, można zbierać dane w jednym poleceniu i używany w kolejnych poleceniach.

Na przykład następujące polecenie uruchamia polecenie Get-poprawki w sesji w zmiennej $s i zapisuje wyniki w zmiennej $h. Zmienna $h zostało utworzone w każdej sesji w $s, ale nie istnieje w lokalnej sesji.

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

Teraz można używać danych za pomocą zmiennej $h w kolejnych poleceniach, takie jak następujące. Wyniki są wyświetlane na komputerze lokalnym.

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Zaawansowane usługi zdalne
Zdalne zarządzanie programu Windows PowerShell rozpoczyna właśnie w tym miejscu. Za pomocą poleceń cmdlet, instalowane przy użyciu programu Windows PowerShell, można ustanowić i skonfigurować zdalnej sesji z lokalnymi i zdalnymi zakończeń tworzenia dostosowanego i ograniczeniami sesji, Zezwalaj użytkownikom na zaimportować polecenia w sesji zdalnej, które aktualnie ma uruchomiony niejawnie w sesji zdalnej, należy skonfigurować zabezpieczenia sesję zdalną i o wiele więcej.

W celu ułatwienia konfiguracji zdalnej, Windows PowerShell zawiera dostawcy usługi WSMan. WSMAN: dysk, który tworzy dostawcę umożliwia przechodzenie przez hierarchię ustawień konfiguracyjnych na komputerze lokalnym i komputerach zdalnych.
Aby uzyskać więcej informacji o WSMan dostawcy, zobacz [dostawcy o WSMan](https://technet.microsoft.com/en-us/library/dd819476.aspx) i [polecenia cmdlet dotyczące protokołu WS-Management](https://technet.microsoft.com/en-us/library/dd819481.aspx), lub w konsoli środowiska Windows PowerShell, wpisz "Get-Help wsman".

Aby uzyskać więcej informacji, zobacz:
- [Temat zdalnego — często zadawane pytania](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Aby uzyskać pomoc dotyczącą usług zdalnych błędy, zobacz [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).

## <a name="see-also"></a>Zobacz też
- [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS Management_Cmdlets](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [Nowe PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Dostawca o WSMan](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)
