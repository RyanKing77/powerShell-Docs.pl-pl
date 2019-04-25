---
title: Element SelectionCondition EntrySelectedBy dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075719"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="ecee8-102">SelectionCondition, element — EntrySelectedBy, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ecee8-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="ecee8-103">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ecee8-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="ecee8-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="ecee8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ecee8-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu EntrySelectedBy CustomEntry GroupBy (Format) elementu SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="ecee8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ecee8-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecee8-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ecee8-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ecee8-107">Attributes and Elements</span></span>

<span data-ttu-id="ecee8-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="ecee8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ecee8-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ecee8-109">Attributes</span></span>

<span data-ttu-id="ecee8-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="ecee8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ecee8-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ecee8-111">Child Elements</span></span>

|<span data-ttu-id="ecee8-112">Element</span><span class="sxs-lookup"><span data-stu-id="ecee8-112">Element</span></span>|<span data-ttu-id="ecee8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ecee8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ecee8-114">Element PropertyName SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="ecee8-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="ecee8-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ecee8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ecee8-116">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="ecee8-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ecee8-117">Element ScriptBlock SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="ecee8-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="ecee8-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ecee8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ecee8-119">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="ecee8-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="ecee8-120">Element SelectionSetName SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="ecee8-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="ecee8-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ecee8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ecee8-122">Określa zestaw typów .NET wyzwalającego warunku.</span><span class="sxs-lookup"><span data-stu-id="ecee8-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="ecee8-123">Element TypeName dla SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="ecee8-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="ecee8-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ecee8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ecee8-125">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="ecee8-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ecee8-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ecee8-126">Parent Elements</span></span>

|<span data-ttu-id="ecee8-127">Element</span><span class="sxs-lookup"><span data-stu-id="ecee8-127">Element</span></span>|<span data-ttu-id="ecee8-128">Opis</span><span class="sxs-lookup"><span data-stu-id="ecee8-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ecee8-129">Element EntrySelectedBy CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="ecee8-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="ecee8-130">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ecee8-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ecee8-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecee8-131">Remarks</span></span>

<span data-ttu-id="ecee8-132">Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="ecee8-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="ecee8-133">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="ecee8-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="ecee8-134">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="ecee8-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="ecee8-135">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ecee8-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ecee8-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecee8-136">See Also</span></span>

[<span data-ttu-id="ecee8-137">Element PropertyName SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ecee8-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ecee8-138">Element ScriptBlock SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ecee8-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ecee8-139">Element SelectionSetName SelectionCondition dla formantu niestandardowego dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ecee8-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ecee8-140">Element TypeName dla SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="ecee8-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="ecee8-141">Element EntrySelectedBy CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="ecee8-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="ecee8-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="ecee8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
