---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085358"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="eb1a9-102">Wyodrębnianie i analizowanie obiektów ze strukturą poza ciągiem</span><span class="sxs-lookup"><span data-stu-id="eb1a9-102">Extract and Parse Structured Objects out of String</span></span>

<span data-ttu-id="eb1a9-103">Wprowadza również nowe funkcje dla `ConvertFrom-String` polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="eb1a9-103">This also introduces some additional functionality for the `ConvertFrom-String` cmdlet:</span></span>

- <span data-ttu-id="eb1a9-104">Usuwa właściwość text zakresu, domyślnie.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-104">Removes the extent text property by default.</span></span> <span data-ttu-id="eb1a9-105">Możesz dołączyć ją za pomocą parametru - IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-105">You can include it with the -IncludeExtent parameter.</span></span>

- <span data-ttu-id="eb1a9-106">Wiele uczenie algorytmu poprawki z programu MVP i społeczności opinii.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

- <span data-ttu-id="eb1a9-107">Nowy parametr - UpdateTemplate, aby zapisać wyniki algorytmu uczenia na komentarz w pliku szablonu.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="eb1a9-108">Dzięki temu learning przetwarzania kosztu jednorazowe (etap najwolniejsze).</span><span class="sxs-lookup"><span data-stu-id="eb1a9-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="eb1a9-109">Niemal natychmiastowe jest teraz uruchomiona przekonwertować ciągu przy użyciu szablonu, który zawiera algorytmu uczenia zakodowany.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="eb1a9-110">Wyodrębnianie i analizowanie obiektów ze strukturą poza zawartość ciągu</span><span class="sxs-lookup"><span data-stu-id="eb1a9-110">Extract and parse structured objects out of string content</span></span>

<span data-ttu-id="eb1a9-111">We współpracy z [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), nowy `ConvertFrom-String` dodano polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-111">In collaboration with [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), a new `ConvertFrom-String` cmdlet has been added.</span></span>

<span data-ttu-id="eb1a9-112">To polecenie cmdlet obsługuje dwa tryby: podstawowa lista analizy i analizy opartej na przykład automatycznie generowane.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="eb1a9-113">Rozdzielany podczas analizowania, domyślnie dzieli dane wejściowe na biały znak, a następnie przypisuje nazwy właściwości do wynikowego grup.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="eb1a9-114">Można dostosować, ogranicznik:</span><span class="sxs-lookup"><span data-stu-id="eb1a9-114">You can customize the delimiter:</span></span>

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

<span data-ttu-id="eb1a9-115">Polecenie cmdlet obsługuje również generowanych automatycznie oparte na przykładzie analizy na podstawie [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) badawczych pracy w [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span><span class="sxs-lookup"><span data-stu-id="eb1a9-115">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) research work in [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span></span>

<span data-ttu-id="eb1a9-116">Aby rozpocząć pracę, należy wziąć pod uwagę książki adresowej na podstawie tekstu:</span><span class="sxs-lookup"><span data-stu-id="eb1a9-116">To get started, consider a text-based address book:</span></span>

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

<span data-ttu-id="eb1a9-117">Skopiuj z kilkoma przykładami do pliku, który będzie używany jako szablon:</span><span class="sxs-lookup"><span data-stu-id="eb1a9-117">Copy a few examples into a file, which you will use as your template:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

<span data-ttu-id="eb1a9-118">Umieść nawiasy klamrowe wokół danych, którą chcesz wyodrębnić, nadając mu nazwę, jak można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-118">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="eb1a9-119">Ponieważ **nazwa** właściwości (i jego skojarzone inne właściwości) może pojawić się wiele razy, należy użyć gwiazdki (\*) do wskazania, że powoduje to wiele rekordów (w odróżnieniu od wyodrębnienie wiele właściwości do jednego rekord):</span><span class="sxs-lookup"><span data-stu-id="eb1a9-119">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

<span data-ttu-id="eb1a9-120">Z tego zestawu przykłady `ConvertFrom-String` teraz automatycznie wyodrębniać oparte na obiekt danych wyjściowych z plików wejściowych podobną strukturę.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-120">From this set of examples, `ConvertFrom-String` can now automatically extract object-based output from input files with similar structure.</span></span>

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

<span data-ttu-id="eb1a9-121">Celu manipulowania dodatkowe dane na wyodrębniony tekst **ExtentText** właściwość przechwytuje nieprzetworzony tekst, z którego został wyodrębniony rekordu.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-121">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="eb1a9-122">Aby przekazać opinię na temat tej funkcji lub udostępniać zawartość, dla której występują trudności, zapisywanie przykłady, Wyślij wiadomość na adres <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="eb1a9-122">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>