---
title: Element SelectionCondition EntrySelectedBy dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845493"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="6e4c5-102">SelectionCondition, element — EntrySelectedBy, WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="6e4c5-103">Określa warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="6e4c5-104">Nie ma żadnego limitu, liczbę warunków wyboru, które można określić dla definicji szerokiego wpisu.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="6e4c5-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition WideEntry (Format) EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e4c5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e4c5-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e4c5-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6e4c5-107">Attributes and Elements</span></span>

<span data-ttu-id="6e4c5-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="6e4c5-109">Należy określić pojedynczy `PropertyName` lub `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="6e4c5-110">`SelectionSetName` i `TypeName` elementy są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="6e4c5-111">Można określić jedną z dowolnego elementu.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e4c5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6e4c5-112">Attributes</span></span>

<span data-ttu-id="6e4c5-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e4c5-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6e4c5-114">Child Elements</span></span>

|<span data-ttu-id="6e4c5-115">Element</span><span class="sxs-lookup"><span data-stu-id="6e4c5-115">Element</span></span>|<span data-ttu-id="6e4c5-116">Opis</span><span class="sxs-lookup"><span data-stu-id="6e4c5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e4c5-117">Element PropertyName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="6e4c5-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6e4c5-119">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="6e4c5-120">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="6e4c5-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-121">Optional element.</span></span><br /><br /> <span data-ttu-id="6e4c5-122">Określa blok skryptu, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="6e4c5-123">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="6e4c5-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-124">Optional element.</span></span><br /><br /> <span data-ttu-id="6e4c5-125">Określa zestaw typów .NET wyzwalającego warunku.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="6e4c5-126">Element TypeName dla SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="6e4c5-127">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-127">Optional element.</span></span><br /><br /> <span data-ttu-id="6e4c5-128">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6e4c5-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6e4c5-129">Parent Elements</span></span>

|<span data-ttu-id="6e4c5-130">Element</span><span class="sxs-lookup"><span data-stu-id="6e4c5-130">Element</span></span>|<span data-ttu-id="6e4c5-131">Opis</span><span class="sxs-lookup"><span data-stu-id="6e4c5-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e4c5-132">Element EntrySelectedBy WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="6e4c5-133">Definiuje typy .NET, korzystające z tego wpisu szeroki lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6e4c5-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e4c5-134">Remarks</span></span>

<span data-ttu-id="6e4c5-135">Każdy wpis szerokiego musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="6e4c5-136">Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="6e4c5-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="6e4c5-137">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="6e4c5-138">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="6e4c5-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="6e4c5-139">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6e4c5-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6e4c5-140">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6e4c5-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e4c5-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e4c5-141">See Also</span></span>

[<span data-ttu-id="6e4c5-142">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="6e4c5-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6e4c5-143">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="6e4c5-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6e4c5-144">Element EntrySelectedBy WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="6e4c5-145">Element PropertyName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="6e4c5-146">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="6e4c5-147">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="6e4c5-148">Element TypeName dla SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6e4c5-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="6e4c5-149">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="6e4c5-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
