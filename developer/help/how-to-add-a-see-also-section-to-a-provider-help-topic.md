---
title: Jak dodać Zobacz także sekcję do tematu pomocy dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848454"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="f41fa-102">Jak dodać sekcję Zobacz także sekcję do tematu pomocy dotyczącego dostawcy</span><span class="sxs-lookup"><span data-stu-id="f41fa-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="f41fa-103">W tej sekcji wyjaśniono, jak wypełnić **Zobacz też** części tematu pomocy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="f41fa-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="f41fa-104">**Zobacz też** sekcja zawiera listę tematów, które są związane z dostawcą lub może pomóc użytkownikowi zrozumieć i używać dostawcy.</span><span class="sxs-lookup"><span data-stu-id="f41fa-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="f41fa-105">Na liście tematów mogą obejmować pomocy dotyczącej poleceń cmdlet, dostawca pomocy i pojęciach ("") Tematy Pomocy dotyczące programy w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f41fa-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="f41fa-106">Może również obejmować odwołań do książki, dokument i tematy usługi online, w tym wersji online tematu pomocy bieżącego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="f41fa-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="f41fa-107">Gdy odwołujesz się do tematów, w trybie online, podaj identyfikator URI lub wyszukiwany termin w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="f41fa-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="f41fa-108">`Get-Help` Polecenia cmdlet nie łącze lub przekierować do dowolny z tematów na liście.</span><span class="sxs-lookup"><span data-stu-id="f41fa-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="f41fa-109">Ponadto `Online` parametru `Get-Help` polecenie cmdlet nie współpracuje z dostawcą pomocy.</span><span class="sxs-lookup"><span data-stu-id="f41fa-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="f41fa-110">W sekcji Zobacz też jest tworzona na podstawie `RelatedLinks` elementu i tagi, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="f41fa-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="f41fa-111">Następujący kod XML przedstawiono sposób dodawania tagów.</span><span class="sxs-lookup"><span data-stu-id="f41fa-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="f41fa-112">Aby dodać "Zobacz też" — Tematy</span><span class="sxs-lookup"><span data-stu-id="f41fa-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="f41fa-113">W *AssemblyName*w pliku .dll help.xml `providerHelp` elementu Dodawanie `RelatedLinks` elementu.</span><span class="sxs-lookup"><span data-stu-id="f41fa-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="f41fa-114">`RelatedLinks` Element powinien być ostatnim elementem w `providerHelp` elementu.</span><span class="sxs-lookup"><span data-stu-id="f41fa-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="f41fa-115">Tylko jeden `RelatedLinks` element jest dozwolony w każdym temacie pomocy dostawcy.</span><span class="sxs-lookup"><span data-stu-id="f41fa-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="f41fa-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f41fa-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="f41fa-117">Dla każdego tematu w **Zobacz też** sekcji w ramach `RelatedLinks` elementu Dodawanie `navigationLink` elementu.</span><span class="sxs-lookup"><span data-stu-id="f41fa-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="f41fa-118">Następnie, w ramach każdej `navigationLink` elementu, dodaj je `linkText` elementu i jeden `uri` elementu.</span><span class="sxs-lookup"><span data-stu-id="f41fa-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="f41fa-119">Jeśli nie używasz `uri` elementu, można dodać go jako pusty element (\<identyfikatora uri / >).</span><span class="sxs-lookup"><span data-stu-id="f41fa-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="f41fa-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f41fa-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="f41fa-121">Wpisz nazwę tematu między `linkText` tagów.</span><span class="sxs-lookup"><span data-stu-id="f41fa-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="f41fa-122">Jeśli udostępniasz identyfikatora URI, wpisz go między `uri` tagów.</span><span class="sxs-lookup"><span data-stu-id="f41fa-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="f41fa-123">Aby wskazać wersję online bieżącego tematu pomocy dostawcy między `linkText` tagów, wpisz "wersji Online:" zamiast nazwy tematu.</span><span class="sxs-lookup"><span data-stu-id="f41fa-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="f41fa-124">Zazwyczaj "wersja Online:" link jest pierwszym temacie na liście Zobacz też temat.</span><span class="sxs-lookup"><span data-stu-id="f41fa-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="f41fa-125">Poniższy przykład zawiera trzy Zobacz też tematy.</span><span class="sxs-lookup"><span data-stu-id="f41fa-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="f41fa-126">Pierwszy odnoszą się do bieżącego tematu wersji online.</span><span class="sxs-lookup"><span data-stu-id="f41fa-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="f41fa-127">Druga dotyczy tematu pomocy polecenia cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f41fa-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="f41fa-128">Trzeci odnosi się do innego tematu w trybie online.</span><span class="sxs-lookup"><span data-stu-id="f41fa-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```