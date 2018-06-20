---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak używać funkcji uzupełniania po naciśnięciu klawisza TAB w okienku skryptów i okienku konsoli
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: e1f8146b6113a82fd3d857c98550ec2e459715a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954929"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Jak używać funkcji uzupełniania po naciśnięciu klawisza TAB w okienku skryptów i okienku konsoli

Uzupełnianie po naciśnięciu tabulatora zapewnia automatyczne pomocy podczas wpisywania, w okienku skryptów lub w okienku polecenia. Aby móc korzystać z tej funkcji, wykonaj następujące kroki:

## <a name="to-automatically-complete-a-command-entry"></a>Aby automatycznie wypełnić polecenie wpisu

W okienku polecenia lub skryptu w okienku wpisz polecenie kilku znaków, a następnie naciśnij klawisz TAB, aby wybrać żądaną uzupełniania tekstu. Jeśli wiele elementów zaczyna się od tekstu, który został początkowo wpisany, Kontynuuj, naciskając klawisz Tab, aż zostanie wyświetlony element, który ma. Uzupełnianie po naciśnięciu tabulatora może pomóc w trakcie pisania nazwa polecenia cmdlet, nazwa parametru, nazwa zmiennej, nazwa właściwości obiektu lub ścieżkę do pliku.

> [!NOTE]
> W okienku skryptów naciskając klawisz TAB automatycznie ukończy polecenie tylko podczas edytowania .ps1, psd1 lub plikach .psm1. Uzupełnianie po naciśnięciu tabulatora działa w dowolnym momencie podczas wpisywania w okienku polecenia.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Aby automatycznie wypełnić zapis parametru polecenia cmdlet

W okienku Okienko polecenia lub skryptu wpisz polecenie cmdlet następuje myślnik, a następnie naciśnij klawisz TAB.

Na przykład wpisz `Get-Process -` , a następnie naciśnij kilkakrotnie klawisz TAB do wyświetlania każdego z parametrów polecenia cmdlet z kolei.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Jak utworzyć kartę programu PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)