---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Instalowanie aparatu programu Windows PowerShell 2.0
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: b625b61b4e191402074f57ea2e942f800dbbcd53
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058322"
---
# <a name="installing-the-windows-powershell-20-engine"></a>Instalowanie aparatu programu Windows PowerShell 2.0
W tym temacie wyjaśniono, jak instalowanie aparatu programu Windows PowerShell 2.0.

Windows PowerShell 3.0 jest przeznaczona do zgodne ze starszymi wersjami za pomocą programu Windows PowerShell 2.0. Polecenia cmdlet, dostawców, przystawki, moduły i skrypty napisana dla programu Windows PowerShell 2.0 uruchamiane bez zmian w programie Windows PowerShell 3.0 i Windows PowerShell 4.0. Jednak ze względu na zmiany w zasadach aktywacji środowiska uruchomieniowego w programie Microsoft .NET Framework 4, programy hosta programu Windows PowerShell, które zostały napisane dla programu Windows PowerShell 2.0 i kompilowane z Common Language Runtime (CLR) w wersji 2.0 nie można uruchomić bez modyfikacji w dalszej części wersje programu Windows PowerShell, który jest skompilowany przy użyciu środowiska CLR w wersji 4.0.

Aby zachować zgodność z poprzednimi wersjami z poleceń i programów hosta, które ma wpływ tych zmian, aparaty programu Windows PowerShell 2.0, programu Windows PowerShell 3.0 i Windows PowerShell 4.0 są zaprojektowane do uruchamiania side-by-side. Ponadto aparatu programu Windows PowerShell 2.0 znajduje się w systemie Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 i Windows Management Framework 3.0. Aparatu programu Windows PowerShell 2.0 jest przeznaczona do użycia tylko wtedy, gdy istniejący skrypt lub program hosta nie można uruchomić, ponieważ nie jest zgodny z programu Windows PowerShell 3.0, program Windows PowerShell 4.0 lub Microsoft .NET Framework 4. Takiej sytuacji powinny być rzadko.

Aparatu programu Windows PowerShell 2.0 to opcjonalna funkcja systemu Windows Server 2012 R2, Windows 8.1, Windows® 8 i Windows Server® 2012. We wcześniejszych wersjach systemu Windows po zainstalowaniu systemu Windows Management Framework 3.0, instalacja programu Windows PowerShell 3.0 całkowicie zastępuje instalacji programu Windows PowerShell 2.0 w katalogu instalacyjnym programu Windows PowerShell. Jednak aparatu programu Windows PowerShell 2.0 jest zachowywana.

Aby dowiedzieć się, jak uruchamianie aparatu programu Windows PowerShell 2.0, zobacz [uruchamianie aparatu programu Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>Windows 8.1 i Windows 8
W systemie Windows 8.1 i Windows 8 funkcja aparatu programu Windows PowerShell 2.0 jest domyślnie włączona. Jednak z niej korzystać, należy włączyć opcję dla programu Microsoft .NET Framework 3.5, która wymaga. W tej sekcji wyjaśniono również, jak włączyć funkcję aparatu programu Windows PowerShell 2.0, włączać i wyłączać.

#### <a name="to-turn-on-net-framework-35"></a>Aby włączyć program .NET Framework 3.5

1. Na **Start** ekranu, wpisz **funkcji Windows**.

2. Na **aplikacje** kliknij przycisk **ustawienia**, a następnie kliknij przycisk **Windows Włącz lub wyłącz funkcje**.

3. W **funkcji Windows** kliknij **.NET Framework 3.5 (w tym .NET 2.0 i 3.0** aby go zaznaczyć.

    Po wybraniu **.NET Framework 3.5 (w tym .NET 2.0 i 3.0**, wypełnia pole, aby wskazać, że wybrano tylko część funkcji. Jednak jest to wystarczające dla aparatu programu Windows PowerShell 2.0.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Aby włączyć aparatu programu Windows PowerShell 2.0, włączać i wyłączać

1. Na **Start** ekranu, wpisz **funkcji Windows**.

2. Na **aplikacje** kliknij przycisk **ustawienia**, a następnie kliknij przycisk **Windows Włącz lub wyłącz funkcje**.

3. W **funkcji Windows** rozwiń **programu Windows PowerShell 2.0** węzeł, a następnie kliknij przycisk **aparatu programu Windows PowerShell 2.0** pola zaznacz lub wyczyść to pole wyboru.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>W systemie Windows Server 2012 R2 i Windows Server 2012
Użyj poniższych procedur, aby dodać aparatu programu Windows PowerShell 2.0 i funkcji Microsoft .NET Framework 3.5. Aparatu programu Windows PowerShell 2.0 wymaga programu Microsoft .NET Framework 2.0.50727 co najmniej. To wymaganie jest spełnione przez Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>Można dodać funkcji .NET Framework 3.5

1. W **Menedżera serwera**, z **Zarządzaj** menu, wybierz opcję **Dodaj role i funkcje**.

    Lub **Menedżera serwera**, kliknij przycisk **wszystkie serwery**, kliknij prawym przyciskiem myszy nazwę serwera, a następnie wybierz **Dodaj role i funkcje**.

2. Na **typu instalacji** wybierz opcję **Instalacja oparta na rolach lub oparta na funkcjach**.

3. Na **funkcji** rozwiń **funkcje programu .NET Framework 3.5** a następnie wybierz węzeł **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)**.

    Inne opcje, w tym węźle nie są wymagane dla aparatu programu Windows PowerShell 2.0.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Można dodać funkcji aparatu programu Windows PowerShell 2.0

- W **Menedżera serwera**, z **Zarządzaj** menu, wybierz opcję **Dodaj role i funkcje**.

    Lub **Menedżera serwera**, kliknij przycisk **wszystkie serwery**, kliknij prawym przyciskiem myszy nazwę serwera, a następnie wybierz **Dodaj role i funkcje**.

- Na **typu instalacji** wybierz opcję **Instalacja oparta na rolach lub oparta na funkcjach**.

- Na **funkcji** rozwiń **programu Windows PowerShell (zainstalowane)** a następnie wybierz węzeł **aparatu programu Windows PowerShell 2.0**.

Aby dowiedzieć się, jak uruchamianie aparatu programu Windows PowerShell 2.0, zobacz [uruchamianie aparatu programu Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>W starszych systemach
[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) pakiet, który instaluje program Windows PowerShell 4.0 na Windows 7, Windows Server 2008 R2 i Windows Server 2012 zawiera aparatu programu Windows PowerShell 2.0. Aparatu programu Windows PowerShell 2.0 jest włączona i gotowa do użycia, jeśli to konieczne, bez dodatkowych instalacji, instalacji i konfiguracji.

Pakiet Windows Management Framework 3.0, który instaluje program Windows PowerShell 3.0 na Windows 7, Windows Server 2008 R2 i Windows Server 2008, obejmuje aparatu programu Windows PowerShell 2.0. Aparatu programu Windows PowerShell 2.0 jest włączona i gotowa do użycia, jeśli to konieczne, bez dodatkowych instalacji, instalacji i konfiguracji.

## <a name="see-also"></a>Zobacz też
- [Wymagania dotyczące programu PowerShell systemu Windows](Windows-PowerShell-System-Requirements.md)
- [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md)
- [Uruchamianie programu Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Uruchamianie aparatu programu Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)