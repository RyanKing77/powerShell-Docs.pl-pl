---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Uruchamianie aparatu programu Windows PowerShell 2.0
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: 618745ff4865dd046acf46487e87c3ca0e324f95
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482968"
---
# <a name="starting-the-windows-powershell-20-engine"></a>Uruchamianie aparatu programu Windows PowerShell 2.0

W tej sekcji wyjaśniono, jak uruchomić aparat Windows PowerShell 2.0 na Windows 8.1, Windows Server 2012 R2, Windows 8 i Windows Server 2012 w tym aparat Windows PowerShell 2.0, a w innych systemach, w których program Windows PowerShell 2.0, środowiska Windows PowerShell 3.0 i 4.0 programu PowerShell systemu Windows są zainstalowane.

Windows PowerShell 4.0 i programu Windows PowerShell 3.0 są zaprojektowane jako wstecznie zgodne z programu Windows PowerShell 2.0. Polecenia cmdlet, dostawców przystawki, moduły i skrypty napisane dla systemu Windows PowerShell 2.0 uruchom niezmienione w programie Windows PowerShell 4.0 i programu Windows PowerShell 3.0. Jednak ze względu na zmiany w zasadach aktywacji środowiska wykonawczego Microsoft .NET Framework 4, programy hosta programu Windows PowerShell, które zostały napisane dla systemu Windows PowerShell 2.0 i skompilować z Common Language Runtime (CLR) 2.0 nie można uruchomić bez żadnych modyfikacji w systemie Windows PowerShell 3.0 lub programu Windows PowerShell 4.0, które są kompilowane przy użyciu CLR 4.0. Aparat Windows PowerShell 2.0 jest przeznaczona do użycia tylko w przypadku istniejącego skryptu lub nie można uruchomić programu host, ponieważ nie jest zgodny z programu Windows PowerShell 4.0, Windows PowerShell 3.0 lub Microsoft .NET Framework 4. Takiej sytuacji powinny być rzadko.

Wiele programów, które wymagają aparat Windows PowerShell 2.0 rozpoczynaj automatycznie. Te instrukcje są uwzględnione w rzadkich sytuacji, w których należy ręcznie uruchomić aparatu.

## <a name="installing-and-enabling-required-programs"></a>Zainstalowanie i włączenie wymaganych programów

Przed rozpoczęciem aparat Windows PowerShell 2.0, należy włączyć aparat programu Windows PowerShell 2.0 i programu Microsoft .NET Framework 3.5 z dodatkiem Service Pack 1. Aby uzyskać instrukcje, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).

Systemy, w którym [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) lub Windows Management Framework 3.0 są zainstalowane wszystkie wymagane składniki. Niezbędne jest żadna dalsza konfiguracja. Informacje o instalowaniu [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) lub Windows Management Framework 3.0, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Jak uruchomić aparat Windows PowerShell 2.0

Po uruchomieniu programu Windows PowerShell to najnowsza wersja uruchamia się domyślnie. Aby uruchomić środowisko Windows PowerShell z aparatem Windows PowerShell 2.0, należy użyć parametru wersji PowerShell.exe. Polecenie można uruchomić dowolnego wiersza polecenia, w tym programu Windows PowerShell i Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Jak uruchomić sesję zdalną z aparatem Windows PowerShell 2.0

Aby uruchomić aparat Windows PowerShell 2.0 w sesji zdalnej, należy utworzyć konfigurację sesji (znanej także jako "punkt końcowy") na komputerze zdalnym, który ładuje aparat Windows PowerShell 2.0. Konfiguracja sesji jest zapisywany na komputerze zdalnym i może służyć przez innych użytkowników autoryzowanych do utworzenia sesji, które używają aparatu Windows PowerShell 2.0.

To jest zaawansowanym zadaniem, które jest zazwyczaj wykonywane przez administratora systemu.

W poniższej procedurze użyto **PSVersion** parametr [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) polecenia cmdlet, aby utworzyć konfigurację sesji, która używa aparat Windows PowerShell 2.0. Można również użyć **PowerShellVersion** parametr [PSSessionConfigurationFile nowy](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) polecenia cmdlet, aby utworzyć plik konfiguracji sesji dla sesji, który ładuje aparat Windows PowerShell 2.0 i można użyć **PSVersion** parametr [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) parametr, aby zmienić konfigurację sesji, aby korzystać z aparatu Windows PowerShell 2.0.

Aby uzyskać więcej informacji o plikach konfiguracji sesji, zobacz [informacje o plikach](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Informacje o konfiguracjach sesji, w tym konfiguracji i zabezpieczeń, zobacz [informacje o konfiguracjach sesji [4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Aby rozpocząć sesję zdalną programu Windows PowerShell 2.0

1. Aby utworzyć konfigurację sesji, który wymaga aparatu Windows PowerShell 2.0, należy użyć **PSVersion** parametr [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) polecenia cmdlet o wartości "2.0". Uruchom to polecenie na komputerze, na "po stronie serwera" lub na końcu odbieranego połączenia.

   Następujące przykładowe polecenie tworzy PS2 konfiguracji sesji na komputerze Serwer01. Do uruchamiania tego polecenia, uruchom program Windows PowerShell 4.0 lub programu Windows PowerShell 3.0 z **Uruchom jako administrator** opcji.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Aby utworzyć sesję, na komputerze Serwer01, który korzysta z konfiguracji sesji PS2, użyj **ConfigurationName** parametru polecenia cmdlet, których tworzenie sesji zdalnej, takich jak [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) polecenia cmdlet.

   Po uruchomieniu sesji, która korzysta z konfiguracji sesji, aparat Windows PowerShell 2.0 jest ładowane automatycznie do sesji.

   Następujące polecenie uruchamia sesję na komputerze Serwer01, który korzysta z konfiguracji sesji PS2. Polecenie zapisuje tę sesję w zmiennej $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Jak uruchomić zadanie w tle z aparatem Windows PowerShell 2.0

Aby rozpocząć wykonywanie zadania w tle aparat Windows PowerShell 2.0, należy użyć **PSVersion** parametr [zadania rozpoczęcia](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) polecenia cmdlet.

Następujące polecenie uruchamia zadanie w tle z aparatem Windows PowerShell 2.0

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Aby uzyskać więcej informacji na temat zadań w tle, zobacz [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).