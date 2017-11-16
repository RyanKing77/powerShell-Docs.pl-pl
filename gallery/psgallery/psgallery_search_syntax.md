---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_search_syntax
ms.openlocfilehash: 409ae607557af760f9cec4e3c54f39e51b5fac18
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="5b389-103">Składnia poleceń wyszukiwania galerii</span><span class="sxs-lookup"><span data-stu-id="5b389-103">Gallery Search Syntax</span></span>

<span data-ttu-id="5b389-104">Galerii programu PowerShell oferuje searchbox tekst, gdzie można użyć słowa, wyrażenia i wyrażeń — słowo kluczowe, aby zawęzić wyniki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5b389-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="5b389-105">Wyszukiwanie według słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="5b389-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="5b389-106">Wyszukiwanie wykonaj jego starań, aby znaleźć odpowiednie dokumenty zawierające wszystkie 3 słowa kluczowe i zwracać pasujących dokumentów.</span><span class="sxs-lookup"><span data-stu-id="5b389-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="5b389-107">Wyszukiwanie przy użyciu wyrażeń i słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="5b389-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="5b389-108">Wprowadzanie frazę w cudzysłów ("") zmodyfikuj wyszukiwanie, aby wyszukać określonego frazy zamiast osobne słowa kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5b389-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="5b389-109">Dopasowywanie dokumentów zwykle powinna zawierać dokładną frazę "azure sql", np. w tym odmiany wielkość liter "Azure SQL", a także zwykle zawiera słowo "wdrożenie".</span><span class="sxs-lookup"><span data-stu-id="5b389-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="5b389-110">Filtrowanie według pól</span><span class="sxs-lookup"><span data-stu-id="5b389-110">Filtering on fields</span></span>

<span data-ttu-id="5b389-111">Wyszukiwanie identyfikator określonego elementu (lub "Id" lub "id") lub niektóre inne pola, dodając terminy nazwą pola wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5b389-111">You can search for a specific item ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="5b389-112">Obecnie pól z możliwością wyszukiwania są "Id", "Version", "Tagi", "Autor", "Właściciel", "Funkcji", "Poleceń cmdlet", "DscResources" i "PowerShellVersion".</span><span class="sxs-lookup"><span data-stu-id="5b389-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="5b389-113">[Jaka jest różnica między identyfikator i tytuł?</span><span class="sxs-lookup"><span data-stu-id="5b389-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="5b389-114">Identyfikator jest nazwą używanego w konsoli.</span><span class="sxs-lookup"><span data-stu-id="5b389-114">ID is the name you use in the console.</span></span> <span data-ttu-id="5b389-115">Tytuł jest to, co jest wyświetlany w górnej części strony elementu w wynikach wyszukiwania.]</span><span class="sxs-lookup"><span data-stu-id="5b389-115">Title is what is shown at the top of the item page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="5b389-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5b389-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="5b389-117">odpowiednio znajduje "PSReadline" lub "AzureRM.Profile" w polu Identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5b389-117">finds items with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="5b389-118">jest inny sposób, aby znaleźć elementy z "AzureRM.Profile" w polu Identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5b389-118">is another way to find items with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="5b389-119">Filtr 'Id' jest podciągu są zgodne, to w przypadku następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5b389-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"
    
<span data-ttu-id="5b389-120">Można uzyskać wyników, takich jak "AzureRM.Profile" i "Azure.Storage".</span><span class="sxs-lookup"><span data-stu-id="5b389-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="5b389-121">Możesz również wyszukać wiele słów kluczowych w jednym polu.</span><span class="sxs-lookup"><span data-stu-id="5b389-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="5b389-122">Lub mieszać i dopasować pola.</span><span class="sxs-lookup"><span data-stu-id="5b389-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="5b389-123">I mogą wykonywać wyszukiwania fraz:</span><span class="sxs-lookup"><span data-stu-id="5b389-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="5b389-124">Aby wyszukać wszystkie elementy z tagiem DSC.</span><span class="sxs-lookup"><span data-stu-id="5b389-124">To search all items with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="5b389-125">Aby wyszukać wszystkie elementy o określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="5b389-125">To search all items with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="5b389-126">Aby wyszukać wszystkie elementy z określone polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5b389-126">To search all items with the specified cmdlet.</span></span>
    
    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="5b389-127">Aby wyszukać wszystkie elementy o określonej nazwie zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="5b389-127">To search all items with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="5b389-128">Aby wyszukać wszystkie elementy z określonej PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="5b389-128">To search all items with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="5b389-129">Ponadto użycie pola, które nie są obsługiwane, takie jak "polecenia", firma Microsoft będzie tylko ją zignorować i wyszukiwanie wszystkich pól.</span><span class="sxs-lookup"><span data-stu-id="5b389-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="5b389-130">Dlatego po zapytania</span><span class="sxs-lookup"><span data-stu-id="5b389-130">So the following query</span></span>

    commands:blobs storage
    
<span data-ttu-id="5b389-131">Jest interpretowany tak samo jak to zapytanie:</span><span class="sxs-lookup"><span data-stu-id="5b389-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage

