---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie rozszerzenia karty
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686201"
---
# <a name="using-tab-expansion"></a>Używanie rozszerzenia karty

Wiersza polecenia powłoki często umożliwiają automatyczne, ukończenie nazwy plików długi lub polecenia przyspieszanie wprowadzania polecenia, a także. Program Windows PowerShell umożliwia Wypełnij nazw plików i polecenia cmdlet, naciskając klawisz **kartę** klucza.

> [!NOTE]
> Rozszerzenia karty jest kontrolowana przez funkcji wewnętrznej TabExpansion lub TabExpansion2. Ponieważ ta funkcja mogą być zmodyfikowane lub zastąpione, tej dyskusji jest Przewodnik z zachowaniem domyślnej konfiguracji programu PowerShell.

Automatyczne wypełnianie nazwę pliku lub ścieżki z listy dostępnych opcji, wpisz część nazwy i naciśnij klawisz **kartę** klucza. PowerShell będzie automatycznie rozwiń nazwę pierwsze dopasowanie, które znajdzie. Naciśnięcie klawisza **kartę** klucz będzie wielokrotnie przechodzić przez wszystkie dostępne opcje.

Karta rozszerzenia nazwy poleceń cmdlet jest nieco inne. Aby użyć rozszerzenia karty na nazwę polecenia cmdlet, wpisz całą pierwszej części nazwy (zlecenie) i łącznik, który po nim następuje. Można wypełnić więcej nazwy częściowe dopasowanie. Na przykład, jeśli wpiszesz **get-co** , a następnie naciśnij klawisz **kartę** klucza, programu PowerShell automatycznie rozwinie to **Get-Command** polecenia cmdlet (Zwróć uwagę, również zmienia wielkość liter z listy do postaci standard). Jeśli użytkownik naciśnie klawisz **kartę** klucza ponownie, programu PowerShell zastępuje to tylko innych zgodnych nazwa polecenia cmdlet, **pobrania zawartości**.

Rozszerzenia karty można użyć wielokrotnie, w tym samym wierszu. Na przykład, można użyć rozszerzenia karty nazwę **pobrania zawartości** polecenia cmdlet, wpisując:

```
PS> Get-Con<Tab>
```

Po naciśnięciu klawisza **kartę** klucza, polecenie jest rozszerzany, aby:

```
PS> Get-Content
```

Można następnie częściowo Określ ścieżkę do pliku dziennika Instalatora Active i użyć ponownie rozszerzenia karty:

```
PS> Get-Content c:\windows\acts<Tab>
```

Po naciśnięciu klawisza **kartę** klucza, polecenie jest rozszerzany, aby:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Jednym z ograniczeń kartę proces rozszerzenia jest karty są zawsze interpretowane jako próby Dokończ wyraz. Jeśli skopiujesz i wkleisz przykłady poleceń w konsoli programu PowerShell, upewnij się, plik nie zawiera karty; Jeśli tak jest, wyniki będą nieprzewidywalne i prawie na pewno nie będzie zamierzonym.