---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Wymagania systemowe programu PowerShell systemu Windows
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: 33824eac4de28de97990ffa1ea2500e61e03e847
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2017
---
# <a name="windows-powershell-system-requirements"></a>Wymagania systemowe programu PowerShell systemu Windows
Ten temat zawiera wymagania systemowe programu Windows PowerShell 3.0, programu Windows PowerShell 4.0 i programu Windows PowerShell 5.0 oraz funkcje specjalne, takie jak Windows PowerShell Integrated Scripting Environment (ISE), poleceń CIM i przepływów pracy.

Windows® 8.1 i Windows Server® 2012 R2 zawierają wszystkich wymaganych programów. W tym temacie jest przeznaczona dla użytkowników wcześniejszych wersjach systemu Windows.

## <a name="operating-system-requirements"></a>Wymagania dotyczące systemu operacyjnego
Windows PowerShell 5.0 uruchamia się w następujących wersjach systemu Windows.

- Windows Server 2016, instalowane domyślnie

- Windows Server 2012 R2, zainstaluj [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) do uruchomienia programu Windows PowerShell 5.0

- Instalowanie systemu Windows Server 2012, [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) do uruchomienia programu Windows PowerShell 5.0

- Zainstaluj system Windows Server 2008 R2 z dodatkiem Service Pack 1 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) do uruchomienia programu Windows PowerShell 5.0

- Windows 8.1

- Zainstaluj system Windows 7 z dodatkiem Service Pack 1 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) do uruchomienia programu Windows PowerShell 5.0

Windows PowerShell 4.0 jest uruchamiany w następujących wersjach systemu Windows.

- Windows 8.1, instalowane domyślnie

- Windows Server 2012 R2, instalowane domyślnie

- Windows® 7 z dodatkiem Service Pack 1, zainstaluj [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) do uruchomienia programu Windows PowerShell 4.0

- Instalowanie systemu Windows Server® 2008 R2 z dodatkiem Service Pack 1 [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) do uruchomienia programu Windows PowerShell 4.0

Program Windows PowerShell 3.0 jest uruchamiany w następujących wersjach systemu Windows.

- Windows 8, zainstalowana domyślnie

- Windows Server 2012, instalowane domyślnie

- Windows® 7 z dodatkiem Service Pack 1, zainstaluj [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) do uruchomienia programu Windows PowerShell 3.0

- Instalowanie systemu Windows Server® 2008 R2 z dodatkiem Service Pack 1 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) do uruchomienia programu Windows PowerShell 3.0

- Instalowanie systemu Windows Server 2008 z dodatkiem Service Pack 2, [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) do uruchomienia programu Windows PowerShell 3.0

## <a name="microsoft-net-framework-requirements"></a>Wymagania dotyczące programu Microsoft .NET Framework
Windows PowerShell 5.0 wymaga pełnej instalacji programu Microsoft .NET Framework 4.5. Windows 8.1 i Windows Server 2012 R2 obejmują Microsoft .NET Framework 4.5 domyślnie.

Windows PowerShell 4.0 wymaga pełnej instalacji programu Microsoft .NET Framework 4.5. Windows 8.1 i Windows Server 2012 R2 obejmują Microsoft .NET Framework 4.5 domyślnie.

Program Windows PowerShell 3.0 wymaga pełnej instalacji programu Microsoft .NET Framework 4. Windows 8 i Windows Server 2012 obejmują Microsoft .NET Framework 4.5 domyślnie, która spełnia tego wymagania.

Aby zainstalować program Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), zobacz [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) na Microsoft Download Center.

Aby zainstalować pełnej instalacji programu Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), zobacz [Microsoft .NET Framework 4 (Instalator internetowy)](http://go.microsoft.com/fwlink/?LinkID=212931) na Microsoft Download Center.

## <a name="windows-management-framework-40"></a>Oprogramowanie Windows Management Framework 4.0
Windows PowerShell 5.0 wymaga systemu Windows Management Framework 4.0 być preinstalowany w systemie Windows Server 2008 R2 z dodatkiem SP1 i Windows 7 z dodatkiem SP1.

## <a name="ws-management-30"></a>Usługi WS-Management 3.0
Windows PowerShell 3.0 i Windows PowerShell 4.0 wymagają 3.0 WS-Management, który obsługuje usługi WinRM i protokołu o WSMan. Ten program znajduje się w Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 i Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>Instrumentacja zarządzania Windows 3.0
Program Windows PowerShell 3.0 i Windows PowerShell 4.0 wymagają 3.0 Instrumentacji zarządzania Windows (WMI). Ten program znajduje się w Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 i Windows Management Framework 3.0. Jeśli ten program nie jest zainstalowany na komputerze, nie należy uruchamiać funkcje, które wymagają usługi WMI, takich jak polecenia modelu wspólnych informacji.

## <a name="common-language-runtime-40"></a>Aparat plików wykonywalnych języka wspólnego 4.0
Program Windows PowerShell 3.0, programu Windows PowerShell 4.0 i programu Windows PowerShell 5.0 są kompilowane przed Common Language Runtime (CLR) 4.0.

## <a name="graphical-user-interface-requirements"></a>Wymagania interfejsu graficznego użytkownika
Program Windows PowerShell jest aplikacji opartych na konsoli, który nie wymaga graficznego interfejsu użytkownika. W efekcie jest dobrze nadaje na komputerach, które nie mają ekrany lub monitorów lub interfejsu użytkownika, takie jak opcji instalacji Server Core systemu Windows Server 2012 R2 lub Windows Server 2012.

Jednak niektóre elementy, takie jak, wymagają graficznego interfejsu użytkownika. Aby uzyskać więcej informacji zobacz temat pomocy dla każdego elementu.

- Windows PowerShell Integrated Scripting Environment (ISE)

- Polecenia cmdlet

    1.  [Element GridView poza](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Pokaż polecenia](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Pokaż ControlPanelItem](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Pokaż EventLog](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- Parametry

    1.  **ShowWindow** parametr [Get-Help](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenia cmdlet.

    2.  **ShowSecurityDescriptorUI** parametr [Register-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) i [Set-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) polecenia cmdlet.

## <a name="windows-powershell-engine-requirements"></a>Wymagania dotyczące aparatu programu PowerShell systemu Windows
Windows PowerShell 4.0 została zaprojektowana jako wstecznie zgodne z programu Windows PowerShell 3.0 i Windows PowerShell 2.0. Polecenia cmdlet, dostawców przystawki, moduły i skrypty napisane dla systemu Windows PowerShell 2.0 i programu Windows PowerShell 3.0 uruchom niezmienione w programie Windows PowerShell 4.0.

Jednak ze względu na zmiany w zasadach aktywacji środowiska wykonawczego Microsoft .NET Framework 4, programy hosta programu Windows PowerShell, które zostały napisane dla systemu Windows PowerShell 2.0 i skompilować z Common Language Runtime (CLR) 2.0 nie można uruchomić bez żadnych modyfikacji w systemie Windows PowerShell 3.0, który jest skompilowana przy użyciu CLR 4.0.

Aparat programu Windows PowerShell 2.0 wymaga programu Microsoft .NET Framework 2.0.50727 co najmniej. To wymaganie jest spełnione przez program Microsoft .NET Framework 3.5 z dodatkiem Service Pack 1. To wymaganie nie jest spełnione przez program Microsoft .NET Framework 4 i nowszych wersjach systemu Microsoft .NET Framework.

Aby uzyskać informacje dotyczące dodawania lub instalowanie aparatu programu Windows PowerShell 2.0 i dodawanie lub instalowanie wymagane wersje architektury Microsoft .NET Framework, zobacz [instalowanie aparat Windows PowerShell 2.0](Installing-the-Windows-PowerShell-2.0-Engine.md). Aby uzyskać informacje dotyczące uruchamiania aparatu programu Windows PowerShell 2.0, zobacz [uruchamianie aparat Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Środowisko preinstalacyjne systemu Windows
Program Windows PowerShell 2.0, Windows PowerShell 3.0 i Windows PowerShell 4.0 w przypadku uruchamiania w środowisku preinstalacji systemu Windows (Windows PE). Następujące polecenia cmdlet nie są obsługiwane.

- [Polecenia cmdlet usługi (BITS) inteligentnego transferu w tle](http://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-dziennika zdarzeń](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Zapisz pomocy](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Aktualizacja Pomocy](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Ponadto **WinRM** usługi nie jest dostępny w środowisku Windows PE.

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie do korzystania z programu Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md)
- [Uruchamianie środowiska Windows PowerShell](Starting-Windows-PowerShell.md)

