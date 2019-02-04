---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685620"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Wyodrębnianie i analizowanie obiektów ze strukturą poza ciągiem

Wprowadza również nowe funkcje dla `ConvertFrom-String` polecenia cmdlet:

- Usuwa właściwość text zakresu, domyślnie. Możesz dołączyć ją za pomocą parametru - IncludeExtent.

- Wiele uczenie algorytmu poprawki z programu MVP i społeczności opinii.

- Nowy parametr - UpdateTemplate, aby zapisać wyniki algorytmu uczenia na komentarz w pliku szablonu. Dzięki temu learning przetwarzania kosztu jednorazowe (etap najwolniejsze). Niemal natychmiastowe jest teraz uruchomiona przekonwertować ciągu przy użyciu szablonu, który zawiera algorytmu uczenia zakodowany.

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a>Wyodrębnianie i analizowanie obiektów ze strukturą poza zawartość ciągu

We współpracy z [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), nowy `ConvertFrom-String` dodano polecenia cmdlet.

To polecenie cmdlet obsługuje dwa tryby: podstawowa lista analizy i analizy opartej na przykład automatycznie generowane.

Rozdzielany podczas analizowania, domyślnie dzieli dane wejściowe na biały znak, a następnie przypisuje nazwy właściwości do wynikowego grup. Można dostosować, ogranicznik:

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

Polecenie cmdlet obsługuje również generowanych automatycznie oparte na przykładzie analizy na podstawie [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) badawczych pracy w [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).

Aby rozpocząć pracę, należy wziąć pod uwagę książki adresowej na podstawie tekstu:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA
```

Skopiuj z kilkoma przykładami do pliku, który będzie używany jako szablon:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

Umieść nawiasy klamrowe wokół danych, którą chcesz wyodrębnić, nadając mu nazwę, jak można to zrobić. Ponieważ **nazwa** właściwości (i jego skojarzone inne właściwości) może pojawić się wiele razy, należy użyć gwiazdki (\*) do wskazania, że powoduje to wiele rekordów (w odróżnieniu od wyodrębnienie wiele właściwości do jednego rekord):

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

Z tego zestawu przykłady `ConvertFrom-String` teraz automatycznie wyodrębniać oparte na obiekt danych wyjściowych z plików wejściowych podobną strukturę.

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

Celu manipulowania dodatkowe dane na wyodrębniony tekst **ExtentText** właściwość przechwytuje nieprzetworzony tekst, z którego został wyodrębniony rekordu. Aby przekazać opinię na temat tej funkcji lub udostępniać zawartość, dla której występują trudności, zapisywanie przykłady, Wyślij wiadomość na adres <psdmfb@microsoft.com>.