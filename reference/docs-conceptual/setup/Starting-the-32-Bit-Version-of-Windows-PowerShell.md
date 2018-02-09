---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Uruchamianie 32-bitowej wersji programu Windows PowerShell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2018
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>Uruchamianie 32-bitowej wersji programu Windows PowerShell
Podczas instalowania programu Windows PowerShell na komputerze 64-bitowym **programu Windows PowerShell (x86)**, jest zainstalowany 32-bitowej wersji programu Windows PowerShell, oprócz wersji 64-bitowej. Po uruchomieniu programu Windows PowerShell domyślnie uruchamia wersję 64-bitowych.

Jednak czasami konieczne może być uruchomienie **programu Windows PowerShell (x86)**, takie jak podczas korzystania z modułu, który wymaga 32-bitowej wersji lub podczas łączenia w zdalnie do komputera 32-bitowych.

Aby uruchomić 32-bitowej wersji programu Windows PowerShell, użyj dowolnej z następujących procedur.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- Na **Start** ekranu, wpisz **programu Windows PowerShell (x86)**. Kliknij przycisk **programu Windows PowerShell x86** kafelka.

- W **Menedżera serwera**, z **narzędzia** menu, wybierz opcję **programu Windows PowerShell (x86)**.

- Na pulpicie kliknij przycisk Ustaw kursor w prawym górnym rogu **wyszukiwania**, typ **PowerShell x86** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.

- Za pomocą wiersza polecenia wpisz polecenie:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- Na **Start** ekranu, wpisz **PowerShell** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.

- W **Menedżera serwera**, z **narzędzia** menu, wybierz opcję **programu Windows PowerShell (x86)**.

- Na pulpicie kliknij przycisk Ustaw kursor w prawym górnym rogu **wyszukiwania**, typ **PowerShell** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.

- Za pomocą wiersza polecenia wpisz polecenie:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>In Windows® 8.1

- Na **Start** ekranu, wpisz **programu Windows PowerShell (x86)**. Kliknij przycisk **programu Windows PowerShell x86** kafelka.

- Jeśli używasz [narzędzi administracji zdalnej serwera](http://go.microsoft.com/fwlink/?LinkID=304145) dla Windows 8.1, można również otworzyć programu Windows PowerShell x86 z **ManagerTools serwera** menu. Wybierz **programu Windows PowerShell (x86)**.

- Na pulpicie kliknij przycisk Ustaw kursor w prawym górnym rogu **wyszukiwania**, typ **PowerShell x86** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.
   
- Za pomocą wiersza polecenia wpisz polecenie:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- Na **Start** ekranu, ustaw kursor w prawym górnym rogu kliknij pozycję **ustawienia**, kliknij przycisk **Kafelki**, a następnie przenieść **Pokaż narzędzia administracyjne** suwaka Yes (tak). Następnie wpisz **PowerShell** i kliknij przycisk **programu Windows PowerShell (x86)**.

- Jeśli używasz [narzędzi administracji zdalnej serwera](http://www.microsoft.com/download/details.aspx?id=28972) dla systemu Windows 8, można również otworzyć programu Windows PowerShell x86 z **ManagerTools serwera** menu. Wybierz **programu Windows PowerShell (x86)**.

- Na **Start** ekranu lub pulpit, wpisz **PowerShell (x86)** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.

- Za pomocą wiersza polecenia wpisz polecenie:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

