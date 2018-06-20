---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Instalowanie aparatu programu Windows PowerShell 2.0
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: 0b3282a1a67886509e749af0f499c47fe7a99411
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952345"
---
# <a name="installing-the-windows-powershell-20-engine"></a>Instalowanie aparatu programu Windows PowerShell 2.0
W tym temacie wyjaśniono, jak zainstalować aparat Windows PowerShell 2.0.

Program Windows PowerShell 3.0 została zaprojektowana jako wstecznie zgodne z programu Windows PowerShell 2.0. Polecenia cmdlet, dostawców przystawki, moduły i skrypty napisane dla systemu Windows PowerShell 2.0 uruchom bez zmian w środowisku Windows PowerShell 3.0 i Windows PowerShell 4.0. Jednak ze względu na zmiany w zasadach aktywacji środowiska wykonawczego Microsoft .NET Framework 4, programy hosta programu Windows PowerShell, które zostały napisane dla systemu Windows PowerShell 2.0 i skompilować z Common Language Runtime (CLR) 2.0 nie można uruchomić bez żadnych modyfikacji w później wersje programu Windows PowerShell, który jest skompilowana przy użyciu CLR 4.0.

Aby zachować zgodność z poprzednimi wersjami z poleceniami i hostowanie programów, których dotyczy tych zmian, programu Windows PowerShell 2.0, Windows PowerShell 3.0 i Windows PowerShell 4.0 aparaty są przeznaczone do uruchamiania side-by-side. Ponadto aparat Windows PowerShell 2.0 znajduje się w systemie Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 i Windows Management Framework 3.0. Aparat Windows PowerShell 2.0 jest przeznaczona do użycia tylko w przypadku istniejącego skryptu lub nie można uruchomić programu host, ponieważ nie jest zgodny z programu Windows PowerShell 3.0, programu Windows PowerShell 4.0 lub Microsoft .NET Framework 4. Takiej sytuacji powinny być rzadko.

Aparat Windows PowerShell 2.0 jest opcjonalna funkcja systemu Windows Server 2012 R2, Windows 8.1, Windows® 8 i Windows Server® 2012. We wcześniejszych wersjach systemu Windows po zainstalowaniu systemu Windows Management Framework 3.0, instalacja programu Windows PowerShell 3.0 całkowicie zastępuje instalacji programu Windows PowerShell 2.0 w katalogu instalacyjnym programu Windows PowerShell. Aparat Windows PowerShell 2.0 zostanie jednak utrzymane.

Aby uzyskać informacje dotyczące uruchamiania aparat Windows PowerShell 2.0, zobacz [uruchamianie aparat Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>Windows 8.1 i Windows 8
W systemie Windows 8.1 i Windows 8 funkcja aparat programu Windows PowerShell 2.0 jest domyślnie włączona. Jednak aby go użyć, należy włączyć opcję dla programu Microsoft .NET Framework 3.5, która wymaga. W tej sekcji wyjaśniono również, jak włączyć lub wyłączyć aparat programu Windows PowerShell 2.0.

#### <a name="to-turn-on-net-framework-35"></a>Aby włączyć program .NET Framework 3.5

1. Na **Start** ekranu, wpisz **funkcje systemu Windows**.

2. Na **aplikacje** kliknij przycisk **ustawienia**, a następnie kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows**.

3. W **funkcje systemu Windows** kliknij **.NET Framework 3.5 (w tym .NET 2.0 i 3.0** aby go wybrać.

    Po wybraniu **.NET Framework 3.5 (w tym .NET 2.0 i 3.0**, pole wypełnia, aby wskazać, że tylko część funkcji jest zaznaczona. Jednak jest wystarczająca dla aparat Windows PowerShell 2.0.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Aby włączyć aparat Windows PowerShell 2.0 i wyłączyć

1. Na **Start** ekranu, wpisz **funkcje systemu Windows**.

2. Na **aplikacje** kliknij przycisk **ustawienia**, a następnie kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows**.

3. W **funkcje systemu Windows** rozwiń **programu Windows PowerShell 2.0** węzeł, a następnie kliknij przycisk **aparat programu Windows PowerShell 2.0** pole, aby wybrać albo go wyczyścić.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>W systemie Windows Server 2012 R2 i Windows Server 2012
Użyj poniższych procedur, aby dodać aparat programu Windows PowerShell 2.0 i funkcji programu Microsoft .NET Framework 3.5. Aparat Windows PowerShell 2.0 wymaga programu Microsoft .NET Framework 2.0.50727 co najmniej. To wymaganie jest spełnione przez program Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>Aby dodać funkcję .NET Framework 3.5

1. W **Menedżera serwera**, z **Zarządzaj** menu, wybierz opcję **Dodaj role i funkcje**.

    Lub **Menedżera serwera**, kliknij przycisk **wszystkie serwery**, kliknij prawym przyciskiem myszy nazwę serwera, a następnie wybierz **Dodaj role i funkcje**.

2. Na **typu instalacji** wybierz pozycję **Instalacja roli lub funkcji**.

3. Na **funkcje** rozwiń pozycję **funkcje platformy .NET Framework 3.5** a następnie wybierz węzeł **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)**.

    Inne opcje, w tym węźle nie są wymagane dla aparatu Windows PowerShell 2.0.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Aby dodać funkcję aparat programu Windows PowerShell 2.0

- W **Menedżera serwera**, z **Zarządzaj** menu, wybierz opcję **Dodaj role i funkcje**.

    Lub **Menedżera serwera**, kliknij przycisk **wszystkie serwery**, kliknij prawym przyciskiem myszy nazwę serwera, a następnie wybierz **Dodaj role i funkcje**.

- Na **typu instalacji** wybierz pozycję **Instalacja roli lub funkcji**.

- Na **funkcje** rozwiń pozycję **środowiska Windows PowerShell (zainstalowano)** a następnie wybierz węzeł **aparat programu Windows PowerShell 2.0**.

Aby uzyskać informacje dotyczące uruchamiania aparat Windows PowerShell 2.0, zobacz [uruchamianie aparat Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>W starszych systemach
[Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) pakiet, który instaluje program Windows PowerShell 4.0 na system Windows 7, Windows Server 2008 R2 i Windows Server 2012 zawiera aparat Windows PowerShell 2.0. Aparat Windows PowerShell 2.0 jest włączona i gotowa do użycia, jeśli to konieczne, bez konieczności instalacji dodatkowych, instalacji i konfiguracji.

Pakiet Windows Management Framework 3.0, który instaluje program Windows PowerShell 3.0 na system Windows 7, Windows Server 2008 R2 i Windows Server 2008, obejmuje aparat Windows PowerShell 2.0. Aparat Windows PowerShell 2.0 jest włączona i gotowa do użycia, jeśli to konieczne, bez konieczności instalacji dodatkowych, instalacji i konfiguracji.

## <a name="see-also"></a>Zobacz też
- [Wymagania systemowe programu PowerShell systemu Windows](Windows-PowerShell-System-Requirements.md)
- [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md)
- [Uruchamianie środowiska Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Uruchamianie aparatu programu Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md)