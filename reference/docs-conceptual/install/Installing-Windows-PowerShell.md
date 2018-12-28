---
ms.date: 08/09/2017
keywords: programu PowerShell, polecenia cmdlet, pobierania, instalacji, konfiguracji, systemu windows 10, systemu windows 8.1, systemu windows 8.0, windows 7
title: Instalowanie programu Windows PowerShell
ms.openlocfilehash: 1630ba445c88953b2729232ae7d80afa326f25e6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404946"
---
# <a name="installing-windows-powershell"></a>Instalowanie programu Windows PowerShell

Program Windows PowerShell jest zainstalowane domyślnie w każdym Windows, począwszy od Windows 7 z dodatkiem SP1 i Windows Server 2008 R2 z dodatkiem SP1.

Jeśli interesuje Cię w programie PowerShell 6 lub nowszej, musisz zainstalować program PowerShell Core, zamiast programu Windows PowerShell. W tym temacie [Instalowanie programu PowerShell Core w Windows](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Znajdowanie programu PowerShell w systemie Windows 10, 8.1, 8.0 i 7

Czasami lokalizowanie środowiska PowerShell ISE (zintegrowane środowisko obsługi skryptów) w Windows lub konsoli może być trudne, przemieszcza się w jej lokalizację używaną wersję systemu Windows do następnego.

Poniższe tabele powinien pomóc programu PowerShell w wersji Windows.
Wszystkie wersje wymienione w tym miejscu są oryginalnej wersji udostępniona żadnych aktualizacji.

### <a name="for-console"></a>Dla konsoli

Wersja | Lokalizacja
-- | --
10 systemu Windows | Kliknij lewym dolnym ikona narożnika Windows, zacznij pisać, programu PowerShell
Windows 8.1, 8.0 | Na ekranie startowym Rozpocznij wpisywanie programu PowerShell.<br/>Jeśli na komputerze stacjonarnym, ikonę po lewej stronie dolnym rogu Windows, zacznij pisać, programu PowerShell
Windows 7 z dodatkiem SP1 | Kliknij lewym dolnym Windows ikona narożnika, w menu start pole wyszukiwania, wpisując programu PowerShell

### <a name="for-ise"></a>Dla środowiska ISE

Wersja | Lokalizacja
-- | --
10 systemu Windows | Kliknij ikonę Windows rogu niższe po lewej stronie, zacznij pisać środowiska ISE
Windows 8.1, 8.0 | Na ekranie startowym wpisz **PowerShell ISE**.<br/>Jeśli na komputerze stacjonarnym, kliknij lewym dolnym rogu Windows ikony, wpisz **PowerShell ISE**
Windows 7 z dodatkiem SP1 | Kliknij lewym dolnym Windows ikona narożnika, w menu start pole wyszukiwania, wpisując programu PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>Znajdowanie programu PowerShell w wersji systemu Windows Server

Począwszy od systemu Windows Server 2008 R2, system operacyjny Windows można zainstalować bez graficznego interfejsu użytkownika (GUI).
Wersje systemu Windows Server bez graficznego interfejsu użytkownika noszą **Core** oraz wersje przy użyciu graficznego interfejsu użytkownika o nazwie **pulpitu**.

### <a name="windows-server-core-editions"></a>Wersje systemu Windows Server Core

We wszystkich wersjach Core podczas logowania do serwera uzyskasz okno wiersza polecenia programu Windows.

Typ `powershell` i naciśnij klawisz **ENTER** można uruchomić programu PowerShell w sesji wiersza polecenia.
Typ `exit` aby zakończyć sesję programu PowerShell i powrócić do wiersza polecenia.

### <a name="windows-server-desktop-editions"></a>Wersje systemu Windows Server pulpitu

We wszystkich wersjach pulpitu kliknij ikonę Windows po lewej stronie dolnym rogu, zacznij pisać, programu PowerShell.
Otrzymujesz zarówno w konsoli, jak i opcji ISE.

Jedynym wyjątkiem od reguły powyżej jest środowiska ISE w systemie Windows Server 2008 R2 SP1 w tym przypadku kliknij ikonę Windows po lewej stronie dolnym rogu, wpisz w środowisku PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Jak sprawdzić wersję programu PowerShell

Aby znaleźć zainstalowanej wersji programu PowerShell, uruchom konsolę programu PowerShell (lub środowiska ISE) i typ `$PSVersionTable` i naciśnij klawisz **ENTER**. Wyszukaj `PSVersion` wartość.

## <a name="upgrading-existing-windows-powershell"></a>Uaktualnianie istniejącego środowiska Windows PowerShell

Pakiet instalacyjny dla programu PowerShell jest dostarczany w instalacji programu WMF.
Wersję Instalatora programu WMF zgodna z wersją programu PowerShell nie ma żadnych Instalator autonomiczny dla środowiska Windows PowerShell.

Jeśli musisz zaktualizować istniejącej wersji programu PowerShell, w Windows, skorzystaj z poniższej tabeli Instalatora dla wersji programu PowerShell, które chcesz zaktualizować, aby zlokalizować.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
System Windows 10 (zobacz Note1)<br/>Windows Server 2016 | - | - | - | zainstalowany
Windows 8.1<br/>Windows Server 2012 R2 | - | zainstalowany | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | zainstalowany | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 z dodatkiem SP1<br/>Windows Server 2008 R2 z dodatkiem SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> Na początkowej wersji systemu Windows 10 w usłudze Aktualizacje automatyczne są włączone programu PowerShell zostanie zaktualizowany w wersji 5.0, 5.1.
>
> Jeśli oryginalna wersja systemu Windows 10 nie zostaną zaktualizowane za pomocą aktualizacji Windows, która wersja programu PowerShell to 5.0.

## <a name="need-azure-powershell"></a>Potrzebujesz programu Azure PowerShell

Jeśli szukasz **programu Azure PowerShell**, możesz rozpocząć [Omówienie programu Azure PowerShell](/powershell/azure/overview).

W przeciwnym razie może być konieczne jest [Instalowanie i konfigurowanie programu Azure PowerShell](/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Zobacz też

[Wymagania dotyczące programu PowerShell systemu Windows](Windows-PowerShell-System-Requirements.md)

[Uruchamianie programu Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)