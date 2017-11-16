---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 3413672e73705252225300a853c10a514500baa2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="ae624-102">Wyodrębnij i analizować Structured obiektów poza ciągu</span><span class="sxs-lookup"><span data-stu-id="ae624-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="ae624-103">Wprowadza to również kilka dodatkowych funkcji ConvertFrom parametry polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="ae624-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="ae624-104">Usuwa właściwość text zakresie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ae624-104">Removes the extent text property by default.</span></span> <span data-ttu-id="ae624-105">Można dołączyć ją za pomocą parametru - IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="ae624-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="ae624-106">Wiele uczenia algorytm poprawki z opinii MVP oraz społeczność użytkowników.</span><span class="sxs-lookup"><span data-stu-id="ae624-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="ae624-107">Nowy parametr - UpdateTemplate, aby zapisać wyniki algorytmie uczenia w komentarz w pliku szablonu.</span><span class="sxs-lookup"><span data-stu-id="ae624-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="ae624-108">Dzięki temu learning przetworzyć jednorazowe koszt (etap najwolniejsze).</span><span class="sxs-lookup"><span data-stu-id="ae624-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="ae624-109">Niemal natychmiastowe jest teraz uruchomiona przekonwertować ciągu z szablonu, który zawiera Algorytm uczenia zakodowany.</span><span class="sxs-lookup"><span data-stu-id="ae624-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="ae624-110">Wyodrębnij i analizować strukturalnych obiektów poza zawartości ciągu</span><span class="sxs-lookup"><span data-stu-id="ae624-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="ae624-111">We współpracy z [Microsoft Research](http://research.microsoft.com/), nowy **ConvertFrom ciąg** dodano polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae624-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="ae624-112">To polecenie cmdlet obsługuje dwa tryby: basic rozdzielany analizowania i automatycznie generowane oparte na przykład podczas analizowania.</span><span class="sxs-lookup"><span data-stu-id="ae624-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="ae624-113">Rozdzielany analizy, domyślnie dzieli dane wejściowe na biały znak i przypisuje nazw właściwości do uzyskane grupy.</span><span class="sxs-lookup"><span data-stu-id="ae624-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="ae624-114">Ogranicznik, który można dostosować:</span><span class="sxs-lookup"><span data-stu-id="ae624-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="ae624-115">1 \[C:\\temp\] &gt; &gt; "Hello World" | Ciąg ConvertFrom | Format-Table-Auto</span><span class="sxs-lookup"><span data-stu-id="ae624-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="ae624-116">P1 P2</span><span class="sxs-lookup"><span data-stu-id="ae624-116">P1    P2</span></span>
--    --

<span data-ttu-id="ae624-117">Polecenie cmdlet obsługuje również automatycznie generowanej oparte na przykład analizy na podstawie [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) badania pracy w [Microsoft Research](http://research.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="ae624-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="ae624-118">Aby rozpocząć pracę, należy wziąć pod uwagę książki adresowej tekstowych:</span><span class="sxs-lookup"><span data-stu-id="ae624-118">To get started, consider a text-based address book:</span></span>

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

<span data-ttu-id="ae624-119">Do pliku, który będzie używany jako szablon, należy skopiować kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="ae624-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

   

<span data-ttu-id="ae624-120">Umieść nawiasy klamrowe wokół dane, które mają zostać wyodrębnione, nadanie mu nazwy, jak możesz to zrobić.</span><span class="sxs-lookup"><span data-stu-id="ae624-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="ae624-121">Ponieważ **nazwa** właściwości (i jego skojarzony inne właściwości) może pojawić się wiele razy, należy użyć gwiazdki (\*) wskazująca, że spowoduje to wiele rekordów (zamiast wyodrębniania zbiór właściwości do jednego rekord):</span><span class="sxs-lookup"><span data-stu-id="ae624-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="ae624-122">Z tego zestawu przykłady **ConvertFrom ciąg** może teraz automatycznie wyodrębnić oparty na dane wyjściowe z plików wejściowych z podobną strukturę.</span><span class="sxs-lookup"><span data-stu-id="ae624-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="ae624-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="ae624-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="ae624-124">&gt;&gt;Get zawartość. \\addresses.output.txt | Ciąg ConvertFrom - TemplateFile. \\addresses.template.txt | &gt; &gt; &gt; Format-Table-Auto</span><span class="sxs-lookup"><span data-stu-id="ae624-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="ae624-125">ExtentText nazwę miejscowości stanu</span><span class="sxs-lookup"><span data-stu-id="ae624-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="ae624-126">Ana Trujillo...                Ana Trujillo Redmond, WA Antonio Moreno...              Antonio Moreno Renton WA blogu Thomasa Hardy...                Kowalski Aneta Seattle WA Hardy blogu Thomasa...          Hanna WA Redmond Kowalski Krystyna Moos...                  Hanna Moos Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="ae624-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="ae624-127">Do manipulowania dodatkowe dane na wyodrębnionego tekstu, **ExtentText** właściwości przechwytuje nieprzetworzony tekst, z którego został wyodrębniony rekordu.</span><span class="sxs-lookup"><span data-stu-id="ae624-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="ae624-128">Aby wyrazić swoją opinię na temat tej funkcji lub udostępnić zawartość, dla którego masz problemy zapisywania przykłady, Wyślij wiadomość e-mail < psdmfb@microsoft.com >.</span><span class="sxs-lookup"><span data-stu-id="ae624-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>

