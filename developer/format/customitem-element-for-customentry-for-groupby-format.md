---
title: Element CustomItem CustomEntry dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847460"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="2e898-102">CustomItem, element — CustomEntry, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2e898-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="2e898-103">Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="2e898-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="2e898-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="2e898-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2e898-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomItem GroupBy (Format) CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e898-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e898-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e898-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2e898-107">Attributes and Elements</span></span>

<span data-ttu-id="2e898-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="2e898-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e898-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2e898-109">Attributes</span></span>

<span data-ttu-id="2e898-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="2e898-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e898-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2e898-111">Child Elements</span></span>

|<span data-ttu-id="2e898-112">Element</span><span class="sxs-lookup"><span data-stu-id="2e898-112">Element</span></span>|<span data-ttu-id="2e898-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2e898-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e898-114">Element ExpressionBinding CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2e898-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2e898-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2e898-116">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="2e898-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="2e898-117">Element ramki dla CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2e898-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2e898-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2e898-119">Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="2e898-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="2e898-120">Element nowego wiersza dla CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2e898-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2e898-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2e898-122">Dodaje pusty wiersz do wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2e898-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="2e898-123">Tekst elementu CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2e898-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2e898-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2e898-125">Określa dodatkowy tekst z danymi, wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="2e898-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e898-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2e898-126">Parent Elements</span></span>

|<span data-ttu-id="2e898-127">Element</span><span class="sxs-lookup"><span data-stu-id="2e898-127">Element</span></span>|<span data-ttu-id="2e898-128">Opis</span><span class="sxs-lookup"><span data-stu-id="2e898-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e898-129">Element CustomEntry formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="2e898-130">Zawiera definicję widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2e898-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e898-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e898-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2e898-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e898-132">See Also</span></span>

[<span data-ttu-id="2e898-133">Element CustomEntry formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="2e898-134">Element ExpressionBinding CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2e898-135">Element ramki dla CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2e898-136">Element nowego wiersza dla CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2e898-137">Tekst elementu CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2e898-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2e898-138">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="2e898-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
