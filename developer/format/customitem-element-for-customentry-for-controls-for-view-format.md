---
title: Element CustomItem CustomEntry dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066384"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="faa5f-102">CustomItem, element — CustomEntry, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="faa5f-103">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="faa5f-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="faa5f-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="faa5f-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="faa5f-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="faa5f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="faa5f-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="faa5f-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="faa5f-107">Attributes and Elements</span></span>

<span data-ttu-id="faa5f-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="faa5f-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="faa5f-109">Aby uzyskać więcej informacji zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="faa5f-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="faa5f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="faa5f-110">Attributes</span></span>

<span data-ttu-id="faa5f-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="faa5f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="faa5f-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="faa5f-112">Child Elements</span></span>

|<span data-ttu-id="faa5f-113">Element</span><span class="sxs-lookup"><span data-stu-id="faa5f-113">Element</span></span>|<span data-ttu-id="faa5f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="faa5f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="faa5f-115">Element ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="faa5f-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="faa5f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="faa5f-117">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="faa5f-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="faa5f-118">Element ramki dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="faa5f-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="faa5f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="faa5f-120">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="faa5f-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="faa5f-121">Element nowego wiersza dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="faa5f-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="faa5f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="faa5f-123">Dodaje pusty wiersz do wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="faa5f-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="faa5f-124">Tekst elementu CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="faa5f-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="faa5f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="faa5f-126">Dodaje tekstu, na przykład nawiasów zwykłych lub nawiasy kwadratowe, do wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="faa5f-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="faa5f-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="faa5f-127">Parent Elements</span></span>

|<span data-ttu-id="faa5f-128">Element</span><span class="sxs-lookup"><span data-stu-id="faa5f-128">Element</span></span>|<span data-ttu-id="faa5f-129">Opis</span><span class="sxs-lookup"><span data-stu-id="faa5f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="faa5f-130">Element CustomEntry CustomEntries dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="faa5f-131">Zawiera definicję formantu.</span><span class="sxs-lookup"><span data-stu-id="faa5f-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="faa5f-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="faa5f-132">Remarks</span></span>

<span data-ttu-id="faa5f-133">Podczas określania elementów podrzędnych `CustomItem` elementu pamiętać o następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="faa5f-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="faa5f-134">Elementy podrzędne muszą zostać dodane w następującej kolejności: `ExpressionBinding`, `NewLine`, `Text`, i `Frame`.</span><span class="sxs-lookup"><span data-stu-id="faa5f-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="faa5f-135">Nie ma żadnych maksymalnego limitu numer sekwencji, które można określić.</span><span class="sxs-lookup"><span data-stu-id="faa5f-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="faa5f-136">W każdej sekwencji nie ma limitu maksymalnej liczby `ExpressionBinding` elementy, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="faa5f-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="faa5f-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="faa5f-137">See Also</span></span>

[<span data-ttu-id="faa5f-138">Element ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="faa5f-139">Element ramki dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="faa5f-140">Element nowego wiersza dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="faa5f-141">Tekst elementu CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="faa5f-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="faa5f-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="faa5f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
