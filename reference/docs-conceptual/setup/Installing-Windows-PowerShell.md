---
ms.date: 08/09/2017
keywords: środowiska PowerShell, polecenia cmdlet, pobierania, instalacji, ustawienia, systemu windows 10, windows 8.1, windows 8.0, windows 7
title: Instalowanie programu Windows PowerShell
ms.openlocfilehash: 89f0f689ebfcd34dd4c8ec3824ec8ab4bddc34d9
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="installing-windows-powershell"></a>Instalowanie programu Windows PowerShell
Środowisko Windows PowerShell jest zainstalowane domyślnie w każdym systemie Windows począwszy od systemu Windows 7 z dodatkiem SP1 i Windows Server 2008 R2 z dodatkiem SP1.

Jeśli interesuje Cię w programie PowerShell 6 i nowsze, należy zainstalować podstawowy PowerShell zamiast programu Windows PowerShell. W tym temacie [instalacji podstawowej programu PowerShell w systemie Windows](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Znajdowanie programu PowerShell w systemie Windows 10, 8.1, 8.0 i 7

Czasami lokalizowanie programu PowerShell ISE (zintegrowane środowisko obsługi skryptów) w systemie Windows lub konsoli może być trudne, zgodnie z jego lokalizacji są przenoszone z jednej wersji systemu Windows do następnego.

Poniższe tabele powinny pomóc w znalezieniu programu PowerShell w wersji systemu Windows.
Wszystkie wersje wymienione w tym miejscu są oryginalnej wersji zwolnione z żadnych aktualizacji.

### <a name="for-console"></a>Dla konsoli

Wersja | Lokalizacja
-- | --
10 systemu Windows | Kliknij ikonę Windows rogu niższe po lewej stronie, zacznij pisać programu PowerShell
Windows 8.1, 8.0 | Na ekranie startowym zacznij pisać programu PowerShell.<br/>Jeśli na pulpicie ikonę po lewej stronie dolnym rogu systemu Windows, zacznij pisać programu PowerShell
Windows 7 z dodatkiem SP1 | Lewym dolnym rogu systemu Windows na kliknij ikonę, start pole wyszukiwania, wpisując polecenie programu PowerShell

### <a name="for-ise"></a>Dla środowiska ISE

Wersja | Lokalizacja
-- | --
10 systemu Windows | Kliknij ikonę Windows rogu niższe po lewej stronie, zacznij pisać ISE
Windows 8.1, 8.0 | Na ekranie startowym wpisz **PowerShell ISE**.<br/>Jeśli na pulpicie kliknij dolnym rogu Windows ikony, wpisz **PowerShell ISE**
Windows 7 z dodatkiem SP1 | Lewym dolnym rogu systemu Windows na kliknij ikonę, start pole wyszukiwania, wpisując polecenie programu PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>Znajdowanie programu PowerShell w wersji systemu Windows Server

Począwszy od systemu Windows Server 2008 R2, systemu operacyjnego można zainstalować bez graficzny interfejs użytkownika (GUI).
Wersje systemu Windows Server bez graficznego interfejsu użytkownika są nazywane **Core** oraz wersje z graficznym interfejsem użytkownika o nazwie **pulpitu**.

### <a name="windows-server-core-editions"></a>Wersje systemu Windows Server Core

We wszystkich wersjach Core podczas logowania do serwera można uzyskać okno wiersza polecenia systemu Windows.

Typ `powershell` i naciśnij klawisz **ENTER** można uruchomić w sesji wiersza polecenia programu PowerShell.
Typ `exit` zakończyć sesję programu PowerShell, a następnie wróć do wiersza polecenia.

### <a name="windows-server-desktop-editions"></a>Wersje pulpitu systemu Windows Server

We wszystkich wersjach pulpitu kliknij ikonę po lewej stronie Windows rogu niższe, zacznij pisać programu PowerShell.
Otrzymasz zarówno konsoli i opcje ISE.

Jedynym wyjątkiem od reguły powyżej jest ISE w systemie Windows Server 2008 R2 SP1 w takim przypadku kliknij po lewej stronie ikony systemu Windows dolnym rogu, wpisz PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Jak sprawdzić wersję środowiska PowerShell

Aby znaleźć zainstalowanych wersji programu PowerShell, uruchom konsolę programu PowerShell (lub ISE) i typ `$PSVersionTable` i naciśnij klawisz **ENTER**. Wyszukaj `PSVersion` wartość.

## <a name="upgrading-existing-windows-powershell"></a>Uaktualnianie istniejącego środowiska Windows PowerShell

Pakiet instalacyjny dla programu PowerShell jest dostarczany w instalacji programu WMF.
Wersja Instalatora WMF zgodna wersja programu PowerShell; nie ma żadnych Autonomiczny Instalator dla środowiska Windows PowerShell.

Jeśli musisz zaktualizować istniejącej wersji programu PowerShell, w systemie Windows, skorzystaj z poniższej tabeli Instalator dla używanej wersji programu PowerShell, które chcesz zaktualizować, aby zlokalizować.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (zobacz Note1)<br/>Windows Server 2016 | - | - | - | zainstalowany
Windows 8.1<br/>Windows Server 2012 R2 | - | zainstalowany | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | zainstalowany | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 z dodatkiem SP1<br/>Windows Server 2008 R2 z dodatkiem SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> **Należy pamiętać, 1**:
  >>
  >> Na początkowej wersji systemu Windows 10 w usłudze Aktualizacje automatyczne są włączone programu PowerShell zostanie zaktualizowany w wersji 5.0 lub 5.1.
  >>
  >> Jeśli oryginalna wersja systemu Windows 10 nie jest aktualizowany za pomocą aktualizacji systemu Windows, wersja programu PowerShell jest 5.0.

## <a name="need-azure-powershell"></a>Wymagają programu Azure PowerShell

Jeśli szukasz **programu Azure PowerShell**, można uruchomić z [Omówienie programu Azure PowerShell](https://docs.microsoft.com/powershell/azure).

W przeciwnym razie może być konieczne jest [Instalowanie i konfigurowanie programu Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Zobacz też

- [Wymagania systemowe programu PowerShell systemu Windows](Windows-PowerShell-System-Requirements.md)
- [Uruchamianie środowiska Windows PowerShell](Starting-Windows-PowerShell.md)