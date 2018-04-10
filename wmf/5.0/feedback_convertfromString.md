---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: cedda61241df4965fe5db723f03e3497f046fa44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Wyodrębnianie i analizowanie obiektów ze strukturą poza ciągiem
Wprowadza to również kilka dodatkowych funkcji ConvertFrom parametry polecenia cmdlet:

-   Usuwa właściwość text zakresie domyślnie. Można dołączyć ją za pomocą parametru - IncludeExtent.

-   Wiele uczenia algorytm poprawki z opinii MVP oraz społeczność użytkowników.

-   Nowy parametr - UpdateTemplate, aby zapisać wyniki algorytmie uczenia w komentarz w pliku szablonu. Dzięki temu learning przetworzyć jednorazowe koszt (etap najwolniejsze). Niemal natychmiastowe jest teraz uruchomiona przekonwertować ciągu z szablonu, który zawiera Algorytm uczenia zakodowany.


<a name="extract-and-parse-structured-objects-out-of-string-content"></a>Wyodrębnij i analizować strukturalnych obiektów poza zawartości ciągu
----------------------------------------------------------

We współpracy z [Microsoft Research](http://research.microsoft.com/), nowy **ConvertFrom ciąg** dodano polecenia cmdlet.

To polecenie cmdlet obsługuje dwa tryby: basic rozdzielany analizowania i automatycznie generowane oparte na przykład podczas analizowania.

Rozdzielany analizy, domyślnie dzieli dane wejściowe na biały znak i przypisuje nazw właściwości do uzyskane grupy. Ogranicznik, który można dostosować:

> 1 \[C:\\temp\] &gt; &gt; "Hello World" | Ciąg ConvertFrom | Format-Table-Auto

P1    P2
--    --

Polecenie cmdlet obsługuje również automatycznie generowanej oparte na przykład analizy na podstawie [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) badania pracy w [Microsoft Research](http://research.microsoft.com).

Aby rozpocząć pracę, należy wziąć pod uwagę książki adresowej tekstowych:

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

Do pliku, który będzie używany jako szablon, należy skopiować kilka przykładów:

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



Umieść nawiasy klamrowe wokół dane, które mają zostać wyodrębnione, nadanie mu nazwy, jak możesz to zrobić. Ponieważ **nazwa** właściwości (i jego skojarzony inne właściwości) może pojawić się wiele razy, należy użyć gwiazdki (\*) wskazująca, że spowoduje to wiele rekordów (zamiast wyodrębniania zbiór właściwości do jednego rekord):

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

Z tego zestawu przykłady **ConvertFrom ciąg** może teraz automatycznie wyodrębnić oparty na dane wyjściowe z plików wejściowych z podobną strukturę.

> 2 \[C:\\temp\]
>
> &gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto
>
> ExtentText nazwę miejscowości stanu
> ----------                     ----               ----     -----
> Ana Trujillo...                Ana Trujillo Redmond, WA Antonio Moreno...              Antonio Moreno Renton WA blogu Thomasa Hardy...                Kowalski Aneta Seattle WA Hardy blogu Thomasa...          Hanna WA Redmond Kowalski Krystyna Moos...                  Hanna Moos Puyallup WA

Do manipulowania dodatkowe dane na wyodrębnionego tekstu, **ExtentText** właściwości przechwytuje nieprzetworzony tekst, z którego został wyodrębniony rekordu. Aby wyrazić swoją opinię na temat tej funkcji lub udostępnić zawartość, dla którego masz problemy zapisywania przykłady, Wyślij wiadomość e-mail <psdmfb@microsoft.com>.