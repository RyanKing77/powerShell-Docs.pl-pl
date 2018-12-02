---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Składnia wyszukiwania w galerii
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742860"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="7d7c6-103">Składnia wyszukiwania w galerii</span><span class="sxs-lookup"><span data-stu-id="7d7c6-103">Gallery Search Syntax</span></span>

<span data-ttu-id="7d7c6-104">Można wyszukiwać za pomocą galerii programu PowerShell [witryny sieci web galerii programu PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="7d7c6-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="7d7c6-105">Witryny sieci web galerii programu PowerShell oferuje searchbox tekstu, których można użyć słów i fraz wyrażeń — słowo kluczowe, aby zawęzić wyniki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="7d7c6-106">Wyszukiwanie według słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="7d7c6-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="7d7c6-107">Wyszukiwanie próbuje znaleźć odpowiednie dokumenty zawierające wszystkie 3 słowa kluczowe i zwracać pasujących dokumentów.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="7d7c6-108">Wyszukaj przy użyciu słów kluczowych i fraz</span><span class="sxs-lookup"><span data-stu-id="7d7c6-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="7d7c6-109">Wprowadź frazę między znakami cudzysłowu ("") zmodyfikuj wyszukiwanie, aby wyszukać określoną frazę zamiast oddzielnych słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="7d7c6-110">Pasujących dokumentów zazwyczaj powinna zawierać dokładnej frazy "azure sql", np. w tym odmiany wielkość liter "Usługa azure SQL", a także zwykle zawierają wyraz "wdrożenie".</span><span class="sxs-lookup"><span data-stu-id="7d7c6-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="7d7c6-111">Filtrowanie według pól</span><span class="sxs-lookup"><span data-stu-id="7d7c6-111">Filtering on fields</span></span>

<span data-ttu-id="7d7c6-112">Wyszukaj identyfikator określony pakiet (lub "Id" lub "id") lub niektóre inne pola przez dodanie przedrostka wyszukiwanego terminu z polem o nazwie.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="7d7c6-113">Obecnie pola z możliwością wyszukiwania są "Id", "Version", "Autor", "DscResources", "Właściciel", "Poleceń cmdlet", "Tagów", "Funkcji" i "PowerShellVersion".</span><span class="sxs-lookup"><span data-stu-id="7d7c6-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="7d7c6-114">[Co to jest różnicą między identyfikator i tytuł?</span><span class="sxs-lookup"><span data-stu-id="7d7c6-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="7d7c6-115">Identyfikator jest nazwą, używane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-115">ID is the name you use in the console.</span></span> <span data-ttu-id="7d7c6-116">Tytuł jest przedstawionego w górnej części strony pakietu w wynikach wyszukiwania.]</span><span class="sxs-lookup"><span data-stu-id="7d7c6-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="7d7c6-117">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7d7c6-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="7d7c6-118">Umożliwia znalezienie pakietów o identyfikatorze zawierające "PSReadline".</span><span class="sxs-lookup"><span data-stu-id="7d7c6-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="7d7c6-119">to kolejny sposób, aby znaleźć pakiety z "AzureRM.Profile" w polu Identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="7d7c6-120">Filtr 'Id' jest podciąg być zgodne, dlatego w przypadku wyszukiwania dla następujących:</span><span class="sxs-lookup"><span data-stu-id="7d7c6-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="7d7c6-121">Dzięki temu wyniki, które obejmują AzureRM.Profile "i"Azure.Storage".</span><span class="sxs-lookup"><span data-stu-id="7d7c6-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="7d7c6-122">Możesz również wyszukać wiele słów kluczowych w jednym polu.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="7d7c6-123">I wyszukiwanie frazy przy użyciu podwójnych cudzysłowów:</span><span class="sxs-lookup"><span data-stu-id="7d7c6-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="7d7c6-124">Aby wyszukać wszystkie pakiety z tagiem DSC.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="7d7c6-125">Aby wyszukać wszystkie pakiety przy użyciu określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="7d7c6-126">Aby wyszukać wszystkie pakiety za pomocą określonego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="7d7c6-127">Aby wyszukać wszystkie pakiety z określoną nazwą zasobu DSC.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="7d7c6-128">Aby wyszukać wszystkie pakiety za pomocą określonego PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="7d7c6-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="7d7c6-129">Ponadto jeśli używasz pola, które nie są obsługiwane, takich jak "poleceń", utworzymy po prostu go zignorować i wszystkie pola wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="7d7c6-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="7d7c6-130">Rozważmy następujące zapytanie</span><span class="sxs-lookup"><span data-stu-id="7d7c6-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="7d7c6-131">Jest interpretowane tak samo jak to zapytanie:</span><span class="sxs-lookup"><span data-stu-id="7d7c6-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
