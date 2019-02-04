---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Uruchamianie programu Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688322"
---
# <a name="starting-windows-powershell"></a>Uruchamianie programu Windows PowerShell
Program PowerShell jest skryptów dll aparat, który jest osadzony na wielu hostach.  Najbardziej typowe hosta, który będzie uruchamiany są interaktywne wiersza polecenia PowerShell.exe i PowerShell_ISE.exe interaktywne środowisko obsługi skryptów.

Aby rozpocząć Windows PowerShell® w systemie Windows Server® 2012 R2, Windows 8.1, Windows Server 2012 i Windows 8, zobacz [typowe zadania zarządzania i nawigacja](https://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Jak uruchomić program Windows PowerShell we wcześniejszych wersjach systemu Windows

W tej sekcji wyjaśniono, jak można uruchomić programu Windows PowerShell i Windows PowerShell zintegrowane Scripting Environment (ISE) na Windows® 7, Windows Server® 2008 R2 i Windows Server® 2008. Wyjaśniono również sposób włączania opcjonalna funkcja w środowisku Windows PowerShell ISE w programie Windows PowerShell 2.0 w systemie Windows Server® 2008 R2 i Windows Server® 2008.

Użyj dowolnej z następujących metod można uruchomić zainstalowana wersja programu Windows PowerShell 3.0 lub Windows PowerShell 4.0, jeśli ma to zastosowanie.

#### <a name="from-the-start-menu"></a>Z Start Menu

- Kliknij przycisk **Start**, typ **PowerShell**, a następnie kliknij przycisk **programu Windows PowerShell**.
- Z **Start** menu, kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij przycisk **programu Windows PowerShell**  folder, a następnie kliknij **programu Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>W wierszu polecenia

Cmd.exe, programu Windows PowerShell lub programu Windows PowerShell ISE Aby uruchomić program Windows PowerShell, wpisz:

```
PowerShell
```

Można również użyć parametrów PowerShell.exe program do dostosowywania sesji. Aby uzyskać więcej informacji, zobacz [Pomoc wiersza polecenia PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Za pomocą administracyjne uprawnień ("Uruchom jako administrator")

Kliknij przycisk **Start**, typ **PowerShell**, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako administrator**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Jak uruchomić program Windows PowerShell ISE we wcześniejszych wersjach systemu Windows

Użyj dowolnej z następujących metod, aby uruchomić program Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Z Start Menu

- Kliknij przycisk **Start**, typ **ISE**, a następnie kliknij przycisk **środowiska Windows PowerShell ISE**.
- Z **Start** menu, kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij przycisk **programu Windows PowerShell**  folder, a następnie kliknij **środowiska Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>W wierszu polecenia

Cmd.exe, programu Windows PowerShell lub programu Windows PowerShell ISE Aby uruchomić program Windows PowerShell, wpisz:

```
PowerShell_ISE
```

lub

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Za pomocą administracyjne uprawnień ("Uruchom jako administrator")

Kliknij przycisk **Start**, typ **ISE**, kliknij prawym przyciskiem myszy **środowiska Windows PowerShell ISE**, a następnie kliknij przycisk **Uruchom jako administrator**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Włączania środowiska Windows PowerShell ISE we wcześniejszych wersjach systemu Windows

W programie Windows PowerShell 4.0 i programu Windows PowerShell 3.0 program Windows PowerShell ISE jest domyślnie włączona, we wszystkich wersjach systemu Windows. Jeśli nie jest już włączony, Windows Management Framework 4.0 lub Windows Management Framework 3.0 włączy ją.

W programie Windows PowerShell 2.0 programu Windows PowerShell ISE jest włączona domyślnie w systemie Windows 7. Jednak w systemie Windows Server 2008 R2 i Windows Server 2008 to opcjonalna funkcja.

Aby włączyć program Windows PowerShell ISE w programie Windows PowerShell 2.0 w systemie Windows Server 2008 R2 lub Windows Server 2008, należy użyć następującej procedury.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Aby włączyć Windows PowerShell zintegrowane Scripting Environment (ISE)

1. Uruchom Menedżera serwera.
2. Kliknij przycisk **funkcji** a następnie kliknij przycisk **Dodaj funkcje**.
3. Na stronie Wybieranie funkcji kliknij Windows PowerShell zintegrowane Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Uruchamianie 32-bitowej wersji programu Windows PowerShell

Po zainstalowaniu programu Windows PowerShell na komputerze 64-bitowych **programu Windows PowerShell (x86)**, 32-bitowej wersji programu Windows PowerShell jest zainstalowany, oprócz wersji 64-bitowych. Po uruchomieniu programu Windows PowerShell, domyślnie uruchamia wersję 64-bitowych.

Jednak czasami konieczne może być uruchomienie **programu Windows PowerShell (x86)**, takie jak podczas korzystania z modułu, która wymaga 32-bitowej wersji lub nawiązywania połączenia zdalnego na komputerze 32-bitowych.

Aby rozpocząć 32-bitowej wersji programu Windows PowerShell, użyj dowolnej z następujących procedur.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- Na **Start** ekranu, wpisz **programu Windows PowerShell (x86)**. Kliknij przycisk **programu Windows PowerShell x86** kafelka.
- W **Menedżera serwera**, z **narzędzia** menu, wybierz opcję **programu Windows PowerShell (x86)**.
- Na pulpicie, ustaw kursor w prawym górnym rogu kliknij **wyszukiwania**, typ **PowerShell x86** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.
- Za pomocą wiersza polecenia wpisz: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- Na **Start** ekranu, wpisz **PowerShell** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.
- W **Menedżera serwera**, z **narzędzia** menu, wybierz opcję **programu Windows PowerShell (x86)**.
- Na pulpicie, ustaw kursor w prawym górnym rogu kliknij **wyszukiwania**, typ **PowerShell** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.
- Za pomocą wiersza polecenia wpisz: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>In Windows® 8.1

- Na **Start** ekranu, wpisz **programu Windows PowerShell (x86)**. Kliknij przycisk **programu Windows PowerShell x86** kafelka.
- Jeśli używasz [narzędzia administracji zdalnej serwera](https://go.microsoft.com/fwlink/?LinkID=304145) dla Windows 8.1, możesz również otworzyć program Windows PowerShell x86 z **ManagerTools serwera** menu.
  Wybierz **programu Windows PowerShell (x86)**.
- Na pulpicie, ustaw kursor w prawym górnym rogu kliknij **wyszukiwania**, typ **PowerShell x86** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.
- Za pomocą wiersza polecenia wpisz: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- Na **Start** ekranu, ustaw kursor w prawym górnym rogu, kliknij przycisk **ustawienia**, kliknij przycisk **Kafelki**, a następnie przenieść **Pokaż narzędzia administracyjne** suwaka Yes (tak). Następnie wpisz **PowerShell** i kliknij przycisk **programu Windows PowerShell (x86)**.
- Jeśli używasz [narzędzia administracji zdalnej serwera](https://www.microsoft.com/download/details.aspx?id=28972) dla systemu Windows 8, można również otworzyć program Windows PowerShell x86 z **ManagerTools serwera** menu. Wybierz **programu Windows PowerShell (x86)**.
- Na **Start** ekranu lub pulpit, wpisz **PowerShell (x86)** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.
- Za pomocą wiersza polecenia wpisz: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`