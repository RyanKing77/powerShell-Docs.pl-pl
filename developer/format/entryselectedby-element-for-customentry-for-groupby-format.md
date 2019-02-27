---
title: Element EntrySelectedBy CustomEntry dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851583"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="f63c5-102">EntrySelectedBy, element — CustomEntry, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f63c5-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="f63c5-103">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="f63c5-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="f63c5-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="f63c5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f63c5-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu EntrySelectedBy CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f63c5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f63c5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f63c5-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f63c5-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f63c5-107">Attributes and Elements</span></span>

<span data-ttu-id="f63c5-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="f63c5-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="f63c5-109">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru dla definicji.</span><span class="sxs-lookup"><span data-stu-id="f63c5-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="f63c5-110">Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="f63c5-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="f63c5-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f63c5-111">Attributes</span></span>

<span data-ttu-id="f63c5-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="f63c5-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f63c5-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f63c5-113">Child Elements</span></span>

|<span data-ttu-id="f63c5-114">Element</span><span class="sxs-lookup"><span data-stu-id="f63c5-114">Element</span></span>|<span data-ttu-id="f63c5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f63c5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f63c5-116">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f63c5-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="f63c5-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f63c5-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f63c5-118">Określa warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="f63c5-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="f63c5-119">Element SelectionSetName EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f63c5-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="f63c5-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f63c5-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f63c5-121">Określa zestaw typów .NET, korzystających z tej definicji formantu.</span><span class="sxs-lookup"><span data-stu-id="f63c5-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="f63c5-122">Element TypeName dla EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f63c5-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="f63c5-123">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f63c5-123">Optional element.</span></span><br /><br /> <span data-ttu-id="f63c5-124">Określa typ architektury .NET, która używa tej definicji kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f63c5-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f63c5-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f63c5-125">Parent Elements</span></span>

|<span data-ttu-id="f63c5-126">Element</span><span class="sxs-lookup"><span data-stu-id="f63c5-126">Element</span></span>|<span data-ttu-id="f63c5-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f63c5-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f63c5-128">Element CustomEntry formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f63c5-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="f63c5-129">Zawiera definicję formantu.</span><span class="sxs-lookup"><span data-stu-id="f63c5-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f63c5-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f63c5-130">Remarks</span></span>

<span data-ttu-id="f63c5-131">Wybór warunki są używane do definiowania warunek, który musi istnieć definicja ma być używany, np. Jeśli obiekt ma określoną właściwość lub gdy wartość określoną właściwość lub skryptu, które daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="f63c5-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="f63c5-132">Aby uzyskać więcej informacji o warunkach wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f63c5-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f63c5-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f63c5-133">See Also</span></span>

[<span data-ttu-id="f63c5-134">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f63c5-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="f63c5-135">Element SelectionSetName EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f63c5-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="f63c5-136">Element TypeName dla EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f63c5-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="f63c5-137">Element CustomEntry CustomEntries dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f63c5-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="f63c5-138">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="f63c5-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
