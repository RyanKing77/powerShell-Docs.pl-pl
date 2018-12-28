---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Uruchamianie aparatu programu Windows PowerShell 2.0
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: f5dd01cd93095fe15cc7e57f97f4b2920e580c22
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405294"
---
# <a name="starting-the-windows-powershell-20-engine"></a>Uruchamianie aparatu programu Windows PowerShell 2.0

W tej sekcji wyjaśniono, jak można uruchomić aparatu programu Windows PowerShell 2.0 na Windows 8.1, Windows Server 2012 R2, Windows 8 i Windows Server 2012, obejmujących aparatu programu Windows PowerShell 2.0, a w innych systemach, na które Windows PowerShell 2.0, programu Windows PowerShell 3.0 i 4.0 programu PowerShell Windows są zainstalowane.

Windows PowerShell 4.0 i programu Windows PowerShell 3.0 są przeznaczone do zgodne ze starszymi wersjami za pomocą programu Windows PowerShell 2.0. Polecenia cmdlet, dostawców, przystawki, moduły i skrypty napisana dla programu Windows PowerShell 2.0 uruchamiane bez zmian w programie Windows PowerShell 4.0 i programu Windows PowerShell 3.0. Jednak ze względu na zmiany w zasadach aktywacji środowiska uruchomieniowego w programie Microsoft .NET Framework 4, programy hosta programu Windows PowerShell, które zostały napisane dla programu Windows PowerShell 2.0 i kompilowane z Common Language Runtime (CLR) w wersji 2.0 nie można uruchomić bez modyfikacji w Windows Program PowerShell 3.0 lub Windows PowerShell 4.0, które są kompilowane przy użyciu środowiska CLR w wersji 4.0. Aparatu programu Windows PowerShell 2.0 jest przeznaczona do użycia tylko wtedy, gdy istniejący skrypt lub program hosta nie można uruchomić, ponieważ nie jest zgodny z programu Windows PowerShell 4.0, Windows PowerShell 3.0 lub Microsoft .NET Framework 4. Takiej sytuacji powinny być rzadko.

Wiele programów, które wymagają aparatu programu Windows PowerShell 2.0 rozpoczynaj automatycznie. Te instrukcje są uwzględnione w rzadkich sytuacjach, w których należy ręcznie uruchomić aparatu.

## <a name="installing-and-enabling-required-programs"></a>Instalowanie i włączanie wymagane programy

Przed rozpoczęciem aparatu programu Windows PowerShell 2.0, należy włączyć aparatu programu Windows PowerShell 2.0 i Microsoft .NET Framework 3.5 z dodatkiem Service Pack 1. Aby uzyskać instrukcje, zobacz [Instalowanie programu Windows PowerShell](../install/Installing-Windows-PowerShell.md).

Systemy, na które Windows Management Framework 4.0 lub Windows Management Framework 3.0 są zainstalowane znajdują się wszystkie wymagane składniki. Żadna dalsza konfiguracja jest to konieczne. Aby uzyskać informacje o instalowaniu [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) lub Windows Management Framework 3.0, zobacz [Instalowanie programu Windows PowerShell](../install/Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Jak uruchomić aparatu programu Windows PowerShell 2.0

Po uruchomieniu programu Windows PowerShell to najnowsza wersja uruchamia się domyślnie. Aby uruchomić program Windows PowerShell przy użyciu aparatu programu Windows PowerShell 2.0, należy użyć parametru wersji PowerShell.exe. Polecenie można uruchomić dowolnego wiersza polecenia, w tym programu Windows PowerShell i Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Jak uruchomić sesję zdalną z aparatu programu Windows PowerShell 2.0

Aby uruchomić aparatu programu Windows PowerShell 2.0 w sesji zdalnej, należy utworzyć konfigurację sesji (znany także jako "punkt końcowy") na komputerze zdalnym, który ładuje aparatu programu Windows PowerShell 2.0. Konfiguracja sesji jest zapisywany na komputerze zdalnym i może służyć przez innych użytkowników autoryzowanych do tworzenia sesji, które używają aparatu programu Windows PowerShell 2.0.

Jest zaawansowanym zadaniem, które jest zazwyczaj wykonywane przez administratora systemu.

W poniższej procedurze użyto **PSVersion** parametru [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) polecenia cmdlet, aby utworzyć konfigurację sesji, która używa aparatu programu Windows PowerShell 2.0. Można również użyć **PowerShellVersion** parametru [New PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) polecenia cmdlet, aby utworzyć plik konfiguracji sesji dla sesji, który ładuje aparatu programu Windows PowerShell 2.0 i Możesz użyć **PSVersion** parametru [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) parametru, aby zmienić konfigurację sesji, aby użyć aparatu programu Windows PowerShell 2.0.

Aby uzyskać więcej informacji o plikach konfiguracji sesji, zobacz [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Aby uzyskać informacje na temat konfiguracji sesji, w tym ustawienia i zabezpieczenia, zobacz [informacje o konfiguracjach sesji [4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Aby rozpocząć sesję zdalną programu Windows PowerShell 2.0

1. Aby utworzyć konfigurację sesji, która wymaga aparatu programu Windows PowerShell 2.0, użyj **PSVersion** parametru [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) polecenia cmdlet z wartością "w wersji 2.0". Uruchom następujące polecenie na komputerze "po stronie serwera" lub odbieranie koniec połączenia.

   Następujące przykładowe polecenie umożliwia utworzenie konfiguracji sesji PS2 komputera Serwer01. Do uruchomienia tego polecenia, uruchom program Windows PowerShell 4.0 lub programu Windows PowerShell 3.0 za pomocą **Uruchom jako administrator** opcji.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Aby utworzyć sesję komputera Serwer01, który korzysta z konfiguracji sesji PS2, użyj **ConfigurationName** parametru polecenia cmdlet, które Tworzenie sesji zdalnej, takich jak [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) polecenia cmdlet.

   Po uruchomieniu sesji, która korzysta z konfiguracji sesji aparatu programu Windows PowerShell 2.0 jest automatycznie ładowany do sesji.

   Następujące polecenie uruchamia sesję komputera Serwer01, który korzysta z konfiguracji sesji PS2. Polecenie zapisuje tę sesję w zmiennej $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Jak uruchomić zadanie w tle za pomocą aparatu programu Windows PowerShell 2.0

Aby rozpocząć zadanie w tle za pomocą aparatu programu Windows PowerShell 2.0, użyj **PSVersion** parametru [zadanie rozpoczęcia](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) polecenia cmdlet.

Następujące polecenie uruchamia zadanie w tle za pomocą aparatu programu Windows PowerShell 2.0

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Aby uzyskać więcej informacji na temat zadań w tle, zobacz [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).