---
title: Element CustomItem CustomEntry dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066417"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="2b454-102">CustomItem, element — CustomEntry, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="2b454-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="2b454-103">Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="2b454-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="2b454-104">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2b454-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2b454-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b454-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b454-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b454-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2b454-107">Attributes and Elements</span></span>

<span data-ttu-id="2b454-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="2b454-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b454-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2b454-109">Attributes</span></span>

<span data-ttu-id="2b454-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b454-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b454-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2b454-111">Child Elements</span></span>

|<span data-ttu-id="2b454-112">Element</span><span class="sxs-lookup"><span data-stu-id="2b454-112">Element</span></span>|<span data-ttu-id="2b454-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2b454-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b454-114">Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b454-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b454-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2b454-116">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="2b454-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="2b454-117">Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b454-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b454-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2b454-119">Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="2b454-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="2b454-120">Element nowego wiersza dla CustomItem dla formantu niestandardowego dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b454-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b454-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2b454-122">Dodaje pusty wiersz do wyświetlania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2b454-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="2b454-123">Tekst elementu CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="2b454-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b454-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2b454-125">Określa dodatkowy tekst z danymi, wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="2b454-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2b454-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2b454-126">Parent Elements</span></span>

|<span data-ttu-id="2b454-127">Element</span><span class="sxs-lookup"><span data-stu-id="2b454-127">Element</span></span>|<span data-ttu-id="2b454-128">Opis</span><span class="sxs-lookup"><span data-stu-id="2b454-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b454-129">Element CustomEntry CustomEntries dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b454-130">Zawiera definicję widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2b454-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b454-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b454-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2b454-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b454-132">See Also</span></span>

[<span data-ttu-id="2b454-133">Element CustomEntry CustomEntries widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b454-134">Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b454-135">Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b454-136">Element nowego wiersza dla CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b454-137">Tekst elementu CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2b454-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="2b454-138">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="2b454-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
