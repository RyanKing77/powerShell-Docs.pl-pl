---
title: Element SelectionCondition EntrySelectedBy dla formant niestandardowy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075753"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="331d4-102">SelectionCondition, element — EntrySelectedBy, CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="331d4-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="331d4-103">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="331d4-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="331d4-104">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="331d4-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="331d4-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy Element konfiguracji elementu CustomEntries widoku (Format), formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formant niestandardowy do widoku ( Format) elementu CustomItem CustomEntry dla formant niestandardowy widok (w formacie) elementu EntrySelectedBy CustomEntry dla formant niestandardowy widok (w formacie) elementu SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="331d4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="331d4-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="331d4-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="331d4-107">Attributes and Elements</span></span>

<span data-ttu-id="331d4-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="331d4-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="331d4-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="331d4-109">Attributes</span></span>

<span data-ttu-id="331d4-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="331d4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="331d4-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="331d4-111">Child Elements</span></span>

|<span data-ttu-id="331d4-112">Element</span><span class="sxs-lookup"><span data-stu-id="331d4-112">Element</span></span>|<span data-ttu-id="331d4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="331d4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="331d4-114">Element PropertyName SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="331d4-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="331d4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="331d4-116">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="331d4-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="331d4-117">Element ScriptBlock SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="331d4-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="331d4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="331d4-119">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="331d4-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="331d4-120">Element SelectionSetName SelectionCondition dla formantu niestandardowego dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="331d4-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="331d4-121">Optional element.</span></span><br /><br /> <span data-ttu-id="331d4-122">Określa zestaw typów .NET wyzwalającego warunku.</span><span class="sxs-lookup"><span data-stu-id="331d4-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="331d4-123">Element TypeName dla SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="331d4-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="331d4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="331d4-125">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="331d4-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="331d4-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="331d4-126">Parent Elements</span></span>

|<span data-ttu-id="331d4-127">Element</span><span class="sxs-lookup"><span data-stu-id="331d4-127">Element</span></span>|<span data-ttu-id="331d4-128">Opis</span><span class="sxs-lookup"><span data-stu-id="331d4-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="331d4-129">Element EntrySelectedBy CustomEntry dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="331d4-130">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="331d4-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="331d4-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="331d4-131">Remarks</span></span>

<span data-ttu-id="331d4-132">Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="331d4-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="331d4-133">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="331d4-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="331d4-134">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="331d4-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="331d4-135">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="331d4-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="331d4-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="331d4-136">See Also</span></span>

[<span data-ttu-id="331d4-137">Element PropertyName SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="331d4-138">Element ScriptBlock SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="331d4-139">Element SelectionSetName SelectionCondition dla formantu niestandardowego dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="331d4-140">Element TypeName dla SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="331d4-141">Element EntrySelectedBy CustomEntry dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="331d4-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="331d4-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="331d4-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
