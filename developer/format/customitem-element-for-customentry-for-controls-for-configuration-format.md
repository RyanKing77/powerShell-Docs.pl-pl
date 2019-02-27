---
title: Element CustomItem CustomEntry dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851667"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="e6491-102">CustomItem, element — CustomEntry, Controls, Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e6491-103">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="e6491-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="e6491-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="e6491-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e6491-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e6491-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="e6491-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6491-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6491-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e6491-107">Attributes and Elements</span></span>

<span data-ttu-id="e6491-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="e6491-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="e6491-109">Aby uzyskać więcej informacji zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="e6491-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6491-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6491-110">Attributes</span></span>

<span data-ttu-id="e6491-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="e6491-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6491-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6491-112">Child Elements</span></span>

|<span data-ttu-id="e6491-113">Element</span><span class="sxs-lookup"><span data-stu-id="e6491-113">Element</span></span>|<span data-ttu-id="e6491-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e6491-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6491-115">Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e6491-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e6491-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e6491-117">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="e6491-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="e6491-118">Element ramki dla CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e6491-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e6491-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e6491-120">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="e6491-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="e6491-121">Element nowego wiersza dla CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e6491-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e6491-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e6491-123">Dodaje pusty wiersz do wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e6491-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="e6491-124">Tekst elementu CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="e6491-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e6491-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e6491-126">Dodaje tekstu, na przykład nawiasów zwykłych lub nawiasy kwadratowe, do wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e6491-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e6491-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e6491-127">Parent Elements</span></span>

|<span data-ttu-id="e6491-128">Element</span><span class="sxs-lookup"><span data-stu-id="e6491-128">Element</span></span>|<span data-ttu-id="e6491-129">Opis</span><span class="sxs-lookup"><span data-stu-id="e6491-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6491-130">Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="e6491-131">Zawiera definicję formantu.</span><span class="sxs-lookup"><span data-stu-id="e6491-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e6491-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6491-132">Remarks</span></span>

<span data-ttu-id="e6491-133">Podczas określania elementów podrzędnych `CustomItem` elementu pamiętać o następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e6491-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="e6491-134">Elementy podrzędne muszą zostać dodane w następującej kolejności: `ExpressionBinding`, `NewLine`, `Text`, i `Frame`.</span><span class="sxs-lookup"><span data-stu-id="e6491-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="e6491-135">Nie ma żadnych maksymalnego limitu numer sekwencji, które można określić.</span><span class="sxs-lookup"><span data-stu-id="e6491-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="e6491-136">W każdej sekwencji nie ma limitu maksymalnej liczby `ExpressionBinding` elementy, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="e6491-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6491-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6491-137">See Also</span></span>

[<span data-ttu-id="e6491-138">Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e6491-139">Element ramki dla CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e6491-140">Element nowego wiersza dla CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e6491-141">Tekst elementu CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e6491-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e6491-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="e6491-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
