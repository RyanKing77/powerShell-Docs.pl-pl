---
title: Pisanie modułu programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082060"
---
# <a name="writing-a-windows-powershell-module"></a>Pisanie modułu programu Windows PowerShell

Ten dokument jest przeznaczony dla administratorów, deweloperzy skryptu i polecenia cmdlet deweloperzy, którzy potrzebują pakować i rozpowszechniać ich poleceń cmdlet programu Windows PowerShell. Za pomocą modułów programu Windows PowerShell, można pakietu i dystrybuować rozwiązania programu Windows PowerShell bez przy użyciu języka skompilowany.

Moduły programu Windows PowerShell umożliwiają partycji, organizowanie i abstrakcyjnej kodu programu Windows PowerShell na jednostki samodzielnych, wielokrotnego użytku. W tych jednostkach wielokrotnego użytku mogą łatwo udostępniać moduły bezpośrednio z innymi osobami. Jeśli jesteś deweloperem skryptu, można również Przeprowadź ponowne pakowanie modułów innych firm do tworzenia niestandardowych aplikacji opartych na skryptach. Moduły, podobnie jak modułów w innych językach skryptów, takich jak Perl i Python, Włącz gotowe do produkcji rozwiązania skryptów, które składniki wielokrotnego użytku, do dystrybucji, za pomocą jednocześnie ma dodatkową zaletę umożliwiając Przeprowadź ponowne pakowanie i streszczenie kilka składników Twórz niestandardowe rozwiązania.

W swoich najbardziej podstawowym programu Windows PowerShell będą traktować prawidłowy kod skryptu programu Windows PowerShell zapisywane w pliku psm1 jako moduł. PowerShell automatycznie traktują każdy zespół binarne polecenia cmdlet jako moduł. Jednak również służy modułem (lub dokładniej, manifestu modułu) powiązać razem całego rozwiązania. W poniższych scenariuszach opisano typowe zastosowania dla modułów programu Windows PowerShell.

### <a name="libraries"></a>Biblioteki

Moduły można pakować i rozpowszechniać spójnych biblioteki funkcji służących do wykonywania typowych zadań. Zazwyczaj nazwy tych funkcji udostępnić co najmniej jeden rzeczowniki odzwierciedlające typowe zadania, które są używane dla. Te funkcje można także podobny do klasy .NET Framework, w tym mają publicznych i prywatnych elementów członkowskich. Na przykład biblioteka może zawierać zbiór funkcji do transferu plików. W tym przypadku rzeczownik odzwierciedlające typowe zadania może być "plik".

### <a name="configuration"></a>Konfiguracja

Moduły może służyć do dostosowywania środowiska, dodając konkretne polecenia cmdlet, dostawców, funkcje i zmienne.

### <a name="compiled-code-development-and-distribution"></a>Skompilowany kod tworzenia i dystrybucji

Polecenia cmdlet i dostawcy deweloperzy mogą używać modułów, testowanie i rozpowszechniania ich skompilowany kod bez konieczności tworzenia przystawek. Będą mogli zaimportować zestaw, który zawiera kod skompilowany jako moduł (moduł binarny) bez konieczności tworzenia i rejestrowania przystawki.

## <a name="see-also"></a>Zobacz też

[Opis modułu programu Windows PowerShell](./understanding-a-windows-powershell-module.md)

[Jak napisać modul Skriptu Powershellu](./how-to-write-a-powershell-script-module.md)

[Jak napisać modułu plik binarny programu PowerShell](./how-to-write-a-powershell-binary-module.md)

[Jak napisać Manifest modułu programu PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[Modyfikowanie PSModulePath ścieżki instalacji](./modifying-the-psmodulepath-installation-path.md)

[Importowanie modułu programu PowerShell](./importing-a-powershell-module.md)

[Instalowanie modułu programu PowerShell](./installing-a-powershell-module.md)
