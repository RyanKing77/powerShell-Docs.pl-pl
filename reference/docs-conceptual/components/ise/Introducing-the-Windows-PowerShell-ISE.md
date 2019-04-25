---
ms.date: 08/14/2018
keywords: polecenia cmdlet programu PowerShell
title: Wprowadzenie do środowiska Windows PowerShell ISE
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057427"
---
# <a name="the-windows-powershell-ise"></a>W środowisku Windows PowerShell ISE

Windows PowerShell zintegrowane Scripting Environment (ISE) jest aplikacją hosta dla środowiska Windows PowerShell. W środowisku ISE Uruchom polecenia i zapisu, testowanie i debugowanie skryptów w pojedynczy oparte na Windows graficzny interfejs użytkownika. Środowiska ISE zapewnia wielowierszowe edytowanie, uzupełniania po naciśnięciu tabulatora, kolorowanie składni, selektywnego wykonywania, Pomoc kontekstowa i obsługę języków od prawej do lewej. Elementy menu i skróty klawiaturowe są mapowane na wiele tych samych zadań, które należy w konsoli programu Windows PowerShell. Na przykład podczas debugowania skryptu w środowisku ISE, możesz kliknąć prawym przyciskiem myszy na linii kodu, w okienku edytowania, aby ustawić punkt przerwania.

## <a name="support"></a>Pomoc techniczna

Środowiska ISE została najpierw wprowadzona w systemach Windows PowerShell w wersji 2 i ponownie został zaprojektowany przy użyciu programu PowerShell w wersji 3. Środowiska ISE jest obsługiwana we wszystkich obsługiwanych wersjach programu Windows PowerShell do i łącznie Windows PowerShell V5.1. ISE, jednak jest w trybie konserwacji, a żadne nowe funkcje są prawdopodobnie ma zostać dodana.
Ponadto nie jest obsługiwane w środowisku ISE przy użyciu programu PowerShell w wersji 6 i nie tylko. Użytkowników, którzy chcą mieć graficznego narzędzia, z których chcesz zarządzać, skrypty programu PowerShell, itd., należy wziąć pod uwagę [programu Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Najważniejsze funkcje

Kluczowe funkcje w środowisku Windows PowerShell ISE:

- Wielowierszowe edytowanie: Aby wstawić pusty wiersz poniżej bieżącego wiersza w okienku poleceń, naciśnij klawisze SHIFT + ENTER.
- Uruchamianie selektywne: Aby uruchomić część skryptu, zaznacz tekst, aby uruchomić, a następnie kliknij **uruchamianie skryptu** przycisku. Lub naciśnij klawisz F5.
- Pomoc kontekstowa: Typ **Invoke-Item**, a następnie naciśnij klawisz F1. Plik pomocy otwiera artykuł dotyczący **Invoke-Item** polecenia cmdlet.

W środowisku Windows PowerShell ISE pozwala dostosować niektóre aspekty ich wyglądu. Ma również swój własny skrypt profil programu Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Aby uruchomić program Windows PowerShell ISE

Kliknij przycisk **Start**, wybierz opcję **programu Windows PowerShell**, a następnie kliknij przycisk **środowiska Windows PowerShell ISE**.
Alternatywnie możesz wpisać `powershell_ise.exe` w dowolnej powłoki poleceń lub wykonywania.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Aby uzyskać pomoc w środowisku Windows PowerShell ISE

Na **pomocy** menu, kliknij przycisk **pomocy programu Windows PowerShell**. Naciśnięcie klawisza F1. Plik który zostanie otwarty w tym artykule opisano środowiska Windows PowerShell ISE i programu PowerShell Windows, w tym wszystkie dostępne polecenia cmdlet Get-Help pomocy.
