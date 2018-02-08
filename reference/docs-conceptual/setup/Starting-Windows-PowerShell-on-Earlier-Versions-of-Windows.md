---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Uruchamianie środowiska Windows PowerShell we wcześniejszych wersjach systemu Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a>Uruchamianie środowiska Windows PowerShell we wcześniejszych wersjach systemu Windows
W tej sekcji wyjaśniono, jak można uruchomić programu Windows PowerShell i Windows PowerShell Integrated Scripting Environment (ISE) na Windows® 7, Windows Server® 2008 R2 i Windows Server® 2008. Ponadto wyjaśniono, jak włączyć funkcję opcjonalne dla programu Windows PowerShell ISE w programie Windows PowerShell 2.0 w systemie Windows Server® 2008 R2 i Windows Server® 2008.

Aby zainstalować program Windows PowerShell 4.0 w obsługiwanych systemach, Pobierz i zainstaluj [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).

Aby zainstalować program Windows PowerShell 3.0 w obsługiwanych systemach, Pobierz i zainstaluj [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Jak uruchomić środowisko Windows PowerShell we wcześniejszych wersjach systemu Windows
Użyj dowolnej z następujących metod, aby uruchomić zainstalowana wersja programu Windows PowerShell 3.0 lub Windows PowerShell 4.0, jeśli to możliwe.

#### <a name="from-the-start-menu"></a>Z Start Menu

- Kliknij przycisk **Start**, typ **PowerShell**, a następnie kliknij przycisk **programu Windows PowerShell**.

- Z **Start** menu, kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij przycisk **środowiska Windows PowerShell**  folder, a następnie kliknij przycisk **programu Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>W wierszu polecenia

- Cmd.exe, środowiska Windows PowerShell lub programu Windows PowerShell ISE Aby uruchomić środowisko Windows PowerShell, wpisz:

    ```
    PowerShell
    ```

    Aby dostosować sesji umożliwia także parametry PowerShell.exe program. Aby uzyskać więcej informacji, zobacz [PowerShell.exe pomocy](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Z administracyjne uprawnień ("Uruchom jako administrator")

1. Kliknij przycisk **Start**, typ **PowerShell**, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako administrator**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Uruchamianie programu Windows PowerShell ISE we wcześniejszych wersjach systemu Windows
Użyj dowolnej z następujących metod, aby uruchomić program Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Z Start Menu

- Kliknij przycisk **Start**, typ **ISE**, a następnie kliknij przycisk **programu Windows PowerShell ISE**.

- Z **Start** menu, kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij przycisk **środowiska Windows PowerShell**  folder, a następnie kliknij przycisk **programu Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>W wierszu polecenia

- Cmd.exe, środowiska Windows PowerShell lub programu Windows PowerShell ISE Aby uruchomić środowisko Windows PowerShell, wpisz:

    ```
    PowerShell_ISE
    ```

    lub

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Z administracyjne uprawnień ("Uruchom jako administrator")

1. Kliknij przycisk **Start**, typ **ISE**, kliknij prawym przyciskiem myszy **programu Windows PowerShell ISE**, a następnie kliknij przycisk **Uruchom jako administrator**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Włączanie programu Windows PowerShell ISE we wcześniejszych wersjach systemu Windows
W programie Windows PowerShell 4.0 i programu Windows PowerShell 3.0 programu Windows PowerShell ISE jest włączona domyślnie we wszystkich wersjach systemu Windows. Jeśli nie jest jeszcze włączone, system Windows Management Framework 4.0 lub Windows Management Framework 3.0 włączy ją.

W programie Windows PowerShell 2.0 Windows PowerShell ISE jest włączona domyślnie w systemie Windows 7. Jednak w systemie Windows Server 2008 R2 i Windows Server 2008 jest funkcją opcjonalną.

Aby włączyć program Windows PowerShell ISE w programie Windows PowerShell 2.0 w systemie Windows Server 2008 R2 lub Windows Server 2008, należy użyć następującej procedury.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Aby włączyć Windows PowerShell Integrated Scripting Environment (ISE)

1. Uruchom Menedżera serwera.

2. Kliknij przycisk **funkcje** , a następnie kliknij przycisk **Dodaj funkcje**.

3. Na stronie Wybieranie funkcji kliknij system Windows PowerShell Integrated Scripting Environment (ISE).

