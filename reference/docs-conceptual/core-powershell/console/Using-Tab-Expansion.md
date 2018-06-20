---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie rozszerzenia karty
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949234"
---
# <a name="using-tab-expansion"></a>Używanie rozszerzenia karty

Wiersza polecenia powłoki często umożliwiają przeprowadzenie automatycznie, nazwy plików długa lub polecenia przyspieszenia polecenie wpisu i dostarczanie. Windows PowerShell umożliwia podanie nazw plików i polecenia cmdlet przez naciśnięcie przycisku **kartę** klucza.

> [!NOTE]
> Karta rozszerzenia jest kontrolowana przez funkcji wewnętrznej TabExpansion lub TabExpansion2. Od tej funkcji można zmodyfikowane lub zastąpione, rozważania jest przewodnik dotyczący zachowanie domyślnej konfiguracji programu PowerShell.

Aby automatycznie wypełnić nazwę pliku lub ścieżki z dostępnych wyborów, wpisz część nazwy i naciśnij klawisz **kartę** klucza. PowerShell zostanie automatycznie rozwiń nazwę do pierwszego znalezionego dopasowania. Naciśnięcie przycisku **kartę** klucza wielokrotnie może mieć wszystkich dostępnych opcji.

Karta rozszerzenia nazw polecenia cmdlet są nieco inne. Aby użyć karta rozszerzeń na nazwę polecenia cmdlet, wpisz cały pierwszej części nazwy (zlecenie) i następującym łącznik. Możesz wpisać bardziej nazwy częściowe dopasowanie. Na przykład jeśli wpiszesz **get co** , a następnie naciśnij klawisz **kartę** klucza, programu PowerShell zostanie automatycznie Rozwiń do **Get-Command** polecenia cmdlet (Uwaga on również zmienia wielkość liter z listy do postaci standard). Jeśli naciśniesz **kartę** klucza ponownie, programu PowerShell zastępuje to tylko innych pasującego nazwa polecenia cmdlet, **pobrania zawartości**.

Karta rozszerzeń można użyć wielokrotnie w tym samym wierszu. Na przykład można użyć karty rozszerzeń na nazwę **pobrania zawartości** polecenia cmdlet, wpisując:

```
PS> Get-Con<Tab>
```

Po naciśnięciu **kartę** klucza, polecenie rozwijany do:

```
PS> Get-Content
```

Można częściowo określić ścieżkę do pliku dziennika Instalatora Active i użyć ponownie kartę rozszerzenia:

```
PS> Get-Content c:\windows\acts<Tab>
```

Po naciśnięciu **kartę** klucza, polecenie rozwijany do:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Jednym z ograniczeń procesu rozszerzenia karta jest czy karty są zawsze interpretowane jako próby wykonania programu word. Jeśli skopiuj i Wklej przykładach poleceń w konsoli programu PowerShell, upewnij się, próbki nie zawiera karty; Jeśli tak, wyniki będą nieprzewidywalne i prawie na pewno nie będzie zgodny z zamierzonym.