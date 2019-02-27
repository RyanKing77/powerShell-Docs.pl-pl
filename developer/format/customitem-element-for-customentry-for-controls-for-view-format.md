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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846536"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="f9a8d-102">CustomItem, element — CustomEntry, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="f9a8d-103">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="f9a8d-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f9a8d-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9a8d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9a8d-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9a8d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f9a8d-107">Attributes and Elements</span></span>

<span data-ttu-id="f9a8d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="f9a8d-109">Aby uzyskać więcej informacji zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9a8d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9a8d-110">Attributes</span></span>

<span data-ttu-id="f9a8d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9a8d-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f9a8d-112">Child Elements</span></span>

|<span data-ttu-id="f9a8d-113">Element</span><span class="sxs-lookup"><span data-stu-id="f9a8d-113">Element</span></span>|<span data-ttu-id="f9a8d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f9a8d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9a8d-115">Element ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="f9a8d-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f9a8d-117">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="f9a8d-118">Element ramki dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="f9a8d-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f9a8d-120">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="f9a8d-121">Element nowego wiersza dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="f9a8d-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f9a8d-123">Dodaje pusty wiersz do wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="f9a8d-124">Tekst elementu CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="f9a8d-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f9a8d-126">Dodaje tekstu, na przykład nawiasów zwykłych lub nawiasy kwadratowe, do wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f9a8d-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f9a8d-127">Parent Elements</span></span>

|<span data-ttu-id="f9a8d-128">Element</span><span class="sxs-lookup"><span data-stu-id="f9a8d-128">Element</span></span>|<span data-ttu-id="f9a8d-129">Opis</span><span class="sxs-lookup"><span data-stu-id="f9a8d-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9a8d-130">Element CustomEntry CustomEntries dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="f9a8d-131">Zawiera definicję formantu.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f9a8d-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9a8d-132">Remarks</span></span>

<span data-ttu-id="f9a8d-133">Podczas określania elementów podrzędnych `CustomItem` elementu pamiętać o następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f9a8d-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="f9a8d-134">Elementy podrzędne muszą zostać dodane w następującej kolejności: `ExpressionBinding`, `NewLine`, `Text`, i `Frame`.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="f9a8d-135">Nie ma żadnych maksymalnego limitu numer sekwencji, które można określić.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="f9a8d-136">W każdej sekwencji nie ma limitu maksymalnej liczby `ExpressionBinding` elementy, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="f9a8d-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9a8d-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9a8d-137">See Also</span></span>

[<span data-ttu-id="f9a8d-138">Element ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="f9a8d-139">Element ramki dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="f9a8d-140">Element nowego wiersza dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="f9a8d-141">Tekst elementu CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f9a8d-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="f9a8d-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="f9a8d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
