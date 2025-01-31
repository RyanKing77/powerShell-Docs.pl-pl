---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie rozszerzenia karty
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031007"
---
# <a name="using-tab-expansion"></a>Używanie rozszerzenia karty

Wiersza polecenia powłoki często umożliwiają automatyczne, ukończenie nazwy plików długi lub polecenia przyspieszanie wprowadzania polecenia, a także wskazówki. Program PowerShell umożliwia Wypełnij nazw plików i polecenia cmdlet, naciskając klawisz <kbd>kartę</kbd> klucza.

> [!NOTE]
> Rozszerzenia karty jest kontrolowana przez funkcji wewnętrznej TabExpansion lub TabExpansion2. Ponieważ ta funkcja mogą być zmodyfikowane lub zastąpione, tej dyskusji jest Przewodnik z zachowaniem domyślnej konfiguracji programu PowerShell.

Automatyczne wypełnianie nazwę pliku lub ścieżki z listy dostępnych opcji, wpisz część nazwy i naciśnij klawisz <kbd>kartę</kbd> klucza. PowerShell będzie automatycznie rozwiń nazwę pierwsze dopasowanie, które znajdzie. Naciśnięcie klawisza <kbd>kartę</kbd> klucz będzie wielokrotnie przechodzić przez wszystkie dostępne opcje.

Karta rozszerzenia nazwy poleceń cmdlet jest nieco inne. Aby użyć rozszerzenia karty na nazwę polecenia cmdlet, wpisz całą pierwszej części nazwy (zlecenie) i łącznik, który po nim następuje. Można wypełnić więcej nazwy częściowe dopasowanie. Na przykład, jeśli wpiszesz `get-co` , a następnie naciśnij klawisz <kbd>kartę</kbd> klucza, programu PowerShell automatycznie rozwinie to `Get-Command` polecenia cmdlet (Uwaga on również zmiany wielkości liter do postaci standard). Jeśli użytkownik naciśnie klawisz <kbd>kartę</kbd> klucza ponownie, programu PowerShell zastępuje to tylko innych zgodnych nazwa polecenia cmdlet, `Get-Content`.

Rozszerzenia karty można użyć wielokrotnie, w tym samym wierszu. Na przykład, można użyć rozszerzenia karty nazwę `Get-Content` polecenia cmdlet, wpisując:

```
PS> Get-Con<Tab>
```

Po naciśnięciu klawisza <kbd>kartę</kbd> klucza, polecenie jest rozszerzany, aby:

```
PS> Get-Content
```

Można następnie częściowo Określ ścieżkę do pliku dziennika Instalatora Active i użyć ponownie rozszerzenia karty:

```
PS> Get-Content c:\windows\acts<Tab>
```

Po naciśnięciu klawisza <kbd>kartę</kbd> klucza, polecenie jest rozszerzany, aby:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Jednym z ograniczeń kartę proces rozszerzenia jest karty są zawsze interpretowane jako próby Dokończ wyraz. Jeśli skopiujesz i wkleisz przykłady poleceń w konsoli programu PowerShell, upewnij się, plik nie zawiera karty; Jeśli tak jest, wyniki będą nieprzewidywalne i prawie na pewno nie będzie zamierzonym.
