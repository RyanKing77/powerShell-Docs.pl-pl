---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Składnia wyszukiwania w galerii
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004077"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="42c2d-103">Składnia wyszukiwania w galerii</span><span class="sxs-lookup"><span data-stu-id="42c2d-103">Gallery Search Syntax</span></span>

<span data-ttu-id="42c2d-104">Galeria programu PowerShell oferuje searchbox tekstu, których można użyć słów i fraz wyrażeń — słowo kluczowe, aby zawęzić wyniki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="42c2d-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="42c2d-105">Wyszukiwanie według słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="42c2d-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="42c2d-106">Wyszukiwanie wykonaj jego wszelkich starań, aby znaleźć odpowiednie dokumenty zawierające wszystkie 3 słowa kluczowe i zwracać pasujących dokumentów.</span><span class="sxs-lookup"><span data-stu-id="42c2d-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="42c2d-107">Wyszukaj przy użyciu słów kluczowych i fraz</span><span class="sxs-lookup"><span data-stu-id="42c2d-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="42c2d-108">Wprowadź frazę między znakami cudzysłowu ("") zmodyfikuj wyszukiwanie, aby wyszukać określoną frazę zamiast oddzielnych słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="42c2d-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="42c2d-109">Pasujących dokumentów zazwyczaj powinna zawierać dokładnej frazy "azure sql", np. w tym odmiany wielkość liter "Usługa azure SQL", a także zwykle zawierają wyraz "wdrożenie".</span><span class="sxs-lookup"><span data-stu-id="42c2d-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="42c2d-110">Filtrowanie według pól</span><span class="sxs-lookup"><span data-stu-id="42c2d-110">Filtering on fields</span></span>

<span data-ttu-id="42c2d-111">Wyszukaj identyfikator określony pakiet (lub "Id" lub "id") lub niektóre inne pola przez dodanie przedrostka wyszukiwanego terminu z polem o nazwie.</span><span class="sxs-lookup"><span data-stu-id="42c2d-111">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="42c2d-112">Obecnie pola z możliwością wyszukiwania są "Id", "Version", "Autor", "DscResources", "Właściciel", "Poleceń cmdlet", "Tagów", "Funkcji" i "PowerShellVersion".</span><span class="sxs-lookup"><span data-stu-id="42c2d-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="42c2d-113">[Co to jest różnicą między identyfikator i tytuł?</span><span class="sxs-lookup"><span data-stu-id="42c2d-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="42c2d-114">Identyfikator jest nazwą, używane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="42c2d-114">ID is the name you use in the console.</span></span> <span data-ttu-id="42c2d-115">Tytuł jest przedstawionego w górnej części strony pakietu w wynikach wyszukiwania.]</span><span class="sxs-lookup"><span data-stu-id="42c2d-115">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="42c2d-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="42c2d-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="42c2d-117">Umożliwia znalezienie pakietów o "PSReadline" lub "AzureRM.Profile" w polu Identyfikatora odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="42c2d-117">finds packages with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="42c2d-118">to kolejny sposób, aby znaleźć pakiety z "AzureRM.Profile" w polu Identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="42c2d-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="42c2d-119">Filtr 'Id' jest podciąg być zgodne, dlatego w przypadku wyszukiwania dla następujących:</span><span class="sxs-lookup"><span data-stu-id="42c2d-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="42c2d-120">Otrzymasz wyników, takich jak "AzureRM.Profile" i "Azure.Storage".</span><span class="sxs-lookup"><span data-stu-id="42c2d-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="42c2d-121">Możesz również wyszukać wiele słów kluczowych w jednym polu.</span><span class="sxs-lookup"><span data-stu-id="42c2d-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="42c2d-122">Lub mieszanie i Dopasowywanie pól.</span><span class="sxs-lookup"><span data-stu-id="42c2d-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="42c2d-123">I wyszukiwanie frazy:</span><span class="sxs-lookup"><span data-stu-id="42c2d-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="42c2d-124">Aby wyszukać wszystkie pakiety z tagiem DSC.</span><span class="sxs-lookup"><span data-stu-id="42c2d-124">To search all packages with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="42c2d-125">Aby wyszukać wszystkie pakiety przy użyciu określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="42c2d-125">To search all packages with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="42c2d-126">Aby wyszukać wszystkie pakiety za pomocą określonego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42c2d-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="42c2d-127">Aby wyszukać wszystkie pakiety z określoną nazwą zasobu DSC.</span><span class="sxs-lookup"><span data-stu-id="42c2d-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="42c2d-128">Aby wyszukać wszystkie pakiety za pomocą określonego PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="42c2d-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="42c2d-129">Ponadto jeśli używasz pola, które nie są obsługiwane, takich jak "poleceń", utworzymy po prostu go zignorować i wszystkie pola wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="42c2d-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="42c2d-130">Rozważmy następujące zapytanie</span><span class="sxs-lookup"><span data-stu-id="42c2d-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="42c2d-131">Jest interpretowane tak samo jak to zapytanie:</span><span class="sxs-lookup"><span data-stu-id="42c2d-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
