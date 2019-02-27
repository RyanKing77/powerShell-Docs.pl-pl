---
title: Element SelectionCondition EntrySelectedBy dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848223"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="8908f-102">SelectionCondition, element — EntrySelectedBy, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="8908f-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="8908f-103">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="8908f-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="8908f-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="8908f-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8908f-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu EntrySelectedBy CustomEntry dla formantów widoku (Format) elementu SelectionCondition EntrySelectedBy dla kontrolki (Widok Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8908f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8908f-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8908f-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8908f-107">Attributes and Elements</span></span>

<span data-ttu-id="8908f-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="8908f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8908f-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8908f-109">Attributes</span></span>

<span data-ttu-id="8908f-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="8908f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8908f-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8908f-111">Child Elements</span></span>

|<span data-ttu-id="8908f-112">Element</span><span class="sxs-lookup"><span data-stu-id="8908f-112">Element</span></span>|<span data-ttu-id="8908f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8908f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8908f-114">Element PropertyName SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8908f-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8908f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8908f-116">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="8908f-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8908f-117">Element ScriptBlock SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8908f-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8908f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8908f-119">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="8908f-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="8908f-120">Element SelectionSetName SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8908f-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8908f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8908f-122">Określa zestaw typów .NET wyzwalającego warunku.</span><span class="sxs-lookup"><span data-stu-id="8908f-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="8908f-123">Element TypeName dla SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8908f-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8908f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8908f-125">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="8908f-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8908f-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8908f-126">Parent Elements</span></span>

|<span data-ttu-id="8908f-127">Element</span><span class="sxs-lookup"><span data-stu-id="8908f-127">Element</span></span>|<span data-ttu-id="8908f-128">Opis</span><span class="sxs-lookup"><span data-stu-id="8908f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8908f-129">Element EntrySelectedBy CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="8908f-130">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="8908f-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8908f-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8908f-131">Remarks</span></span>

<span data-ttu-id="8908f-132">Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="8908f-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="8908f-133">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="8908f-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8908f-134">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="8908f-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8908f-135">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8908f-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8908f-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8908f-136">See Also</span></span>

[<span data-ttu-id="8908f-137">Element PropertyName SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8908f-138">Element ScriptBlock SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8908f-139">Element SelectionSetName SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8908f-140">Element TypeName dla SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8908f-141">Element EntrySelectedBy CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="8908f-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="8908f-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="8908f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
