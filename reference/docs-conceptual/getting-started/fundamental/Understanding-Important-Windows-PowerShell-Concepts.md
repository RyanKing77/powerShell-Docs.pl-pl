---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Opis ważnych pojęć związanych z programem Windows PowerShell
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: 07ceaa2f3e6a192c6281cb4c99aed4c3f66afc7e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="understanding-important-windows-powershell-concepts"></a>Opis ważnych pojęć związanych z programem Windows PowerShell
Projekt programu Windows PowerShell integruje pojęcia z wielu różnych środowiskach. Niektóre z nich są znane osoby z doświadczeniem w środowiskach programowania i powłoki określonego, ale tylko kilka osób będzie wiedzieć o wszystkich z nich. Niektóre z tych pojęć patrzeć Przegląd przydatne powłoki.

### <a name="commands-are-not-text-based"></a>Polecenia nie są oparte na tekst
W przeciwieństwie do tradycyjnych interfejs wiersza polecenia poleceń programu Windows PowerShell polecenia cmdlet jest zaprojektowana do obsługi obiektów - struktury informacje, które jest więcej niż tylko ciąg znaków wyświetlany na ekranie. Zawsze dane wyjściowe polecenia niesie wzdłuż informacji dodatkowych, których można użyć, jeśli zajdzie taka potrzeba. Omówimy w tym temacie szczegółowo w tym dokumencie.

Jeśli użyto narzędzia przetwarzania tekstu do przetwarzania danych wiersza polecenia w przeszłości, będą dostępne, czy zachowują się inaczej w przypadku próby użycia ich w programie Windows PowerShell. W większości przypadków nie trzeba narzędzia przetwarzania tekstu do wyodrębnienia określone informacje. Można uzyskać dostępu do części danych bezpośrednio za pomocą standardowych poleceń manipulowania obiektów programu Windows PowerShell.

### <a name="the-command-family-is-extensible"></a>Rodzina polecenia jest rozszerzalny
Interfejsy, takich jak Cmd.exe nie umożliwiają zwiększenie bezpośrednio zestawu wbudowanego polecenia. Zewnętrzne narzędzia wiersza polecenia uruchamiane w Cmd.exe, można utworzyć, ale te narzędzia zewnętrznego nie mają usług, takich jak integracji Pomocy i Cmd.exe nie może automatycznie określić czy są one prawidłowych poleceń.

Natywnych danych binarnych poleceń programu Windows PowerShell, znany jako *poleceń cmdlet* (wyraźnym komand Let), może zostać rozszerzony o polecenia cmdlet tworzenia i dodany do programu Windows PowerShell za pomocą przystawki. Środowisko Windows PowerShell *przystawek* są kompilowane, podobnie jak narzędzia binarne w inny interfejs. Aby dodać dostawców środowiska Windows PowerShell do powłoki, jak również nowe polecenia cmdlet można używać ich.

Ze względu na specyfikę wewnętrzny poleceń programu Windows PowerShell, odnoszą się do nich jako *poleceń cmdlet*.

> [!NOTE]
> Środowiska Windows PowerShell można uruchamiać polecenia innych niż polecenia cmdlet. Firma Microsoft będzie nie w niniejszym dokumencie je szczegółowo w podręczniku użytkownika programu Windows PowerShell, ale są one warto wiedzieć o jako kategorie typów poleceń. Program Windows PowerShell obsługuje skrypty, które są podobne do skryptów powłoki systemu UNIX i pliki wsadowe Cmd.exe, ale mają rozszerzenie nazwy pliku .ps1. Windows PowerShell umożliwia również tworzenie funkcji wewnętrznych, które mogą być używane bezpośrednio w interfejsie lub w skryptach.

### <a name="windows-powershell-handles-console-input-and-display"></a>Windows PowerShell uchwytów — dane wejściowe konsoli i wyświetlanie
Po wpisaniu polecenia programu Windows PowerShell zawsze przetwarzania danych wejściowych wiersza polecenia bezpośrednio. Środowisko Windows PowerShell również formatuje dane wyjściowe, wyświetlany na ekranie. Jest to istotne, ponieważ zmniejsza pracy wymaganej każde polecenie cmdlet i zapewnia, że zawsze należy rzeczy taki sam sposób, niezależnie od tego, które polecenia cmdlet używane są. Przykład sposobu upraszcza życia dla narzędzia deweloperzy i użytkownicy jest pomoc wiersza polecenia.

Tradycyjne narzędzia wiersza polecenia mają własne systemy dla żądania i wyświetlanie pomocy. Niektóre narzędzia wiersza polecenia użyj **/?** Aby wyzwolić Wyświetlanie pomocy; Użyj innych **-?**, **/H**, a nawet **//**. Niektóre wyświetli pomocy w oknie graficznego interfejsu użytkownika, a nie w oknie konsoli. Niektóre narzędzia złożonych, takie jak metod aktualizowania aplikacji, Rozpakuj pliki wewnętrzne przed wyświetleniem ich pomocy. Jeśli używasz zły parametr, narzędzie może zignorować co wpisany i Rozpocznij wykonywanie zadań automatycznie.

Po wprowadzeniu polecenia programu Windows PowerShell, wszystko, czego możesz wprowadzić jest automatycznie przeanalizować i wstępnie przetworzonych przez program Windows PowerShell. Jeśli używasz **-?** Parametr za pomocą polecenia cmdlet programu Windows PowerShell, zawsze oznacza "Pokaż Pomoc dla tego polecenia". Polecenia cmdlet programiści nie muszą przeanalizować polecenie. potrzebna jest tylko podać tekst pomocy.

Należy zrozumieć funkcje pomocy programu Windows PowerShell są dostępne, nawet jeśli tradycyjne narzędzia wiersza polecenia zostanie uruchomiony w programie Windows PowerShell. Środowisko Windows PowerShell przetwarza parametry i przekazuje wyniki do zewnętrznego narzędzia.

> [!NOTE]
> Po uruchomieniu aplikacji grafiki w programie Windows PowerShell zostanie otwarte okno aplikacji. Środowisko Windows PowerShell uczestniczyło tylko podczas przetwarzania w wierszu polecenia wprowadź możesz dostaw lub dane wyjściowe aplikacji powrót do okna konsoli; nie dotyczy wewnętrznie działanie aplikacji.

### <a name="windows-powershell-uses-some-c-syntax"></a>Windows PowerShell korzysta z części składni języka C#
Środowisko Windows PowerShell jest składnia funkcji i słów kluczowych, które są bardzo podobne do tych używanych w języku C# język programowania, ponieważ środowisko Windows PowerShell jest oparta na programie .NET Framework. Poznawanie środowiska Windows PowerShell ułatwi łatwiej Naucz się C#, jeśli interesuje Cię w języku.

Jeśli nie masz programisty C#, to podobieństwa nie jest ważna. Jednak jeśli znasz już C#, podobieństwa wprowadzić Poznawanie środowiska Windows PowerShell znacznie łatwiejsze.