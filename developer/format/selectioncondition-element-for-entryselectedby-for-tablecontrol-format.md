---
title: Element SelectionCondition EntrySelectedBy dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850477"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="e0b38-102">SelectionCondition, element — EntrySelectedBy, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="e0b38-103">Określa warunek, który musi istnieć na potrzeby tej definicji widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="e0b38-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="e0b38-104">Nie ma żadnego limitu liczby warunki wyboru, które można określić definicję tabeli.</span><span class="sxs-lookup"><span data-stu-id="e0b38-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="e0b38-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) EntrySelectedBy Element konfiguracji dla TableRowEntry (Format) Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0b38-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0b38-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0b38-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e0b38-107">Attributes and Elements</span></span>

<span data-ttu-id="e0b38-108">Poniżej opisano atrybuty, elementy podrzędne i element nadrzędny elementu SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="e0b38-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0b38-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e0b38-109">Attributes</span></span>

<span data-ttu-id="e0b38-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="e0b38-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0b38-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e0b38-111">Child Elements</span></span>

|<span data-ttu-id="e0b38-112">Element</span><span class="sxs-lookup"><span data-stu-id="e0b38-112">Element</span></span>|<span data-ttu-id="e0b38-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e0b38-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0b38-114">Element PropertyName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="e0b38-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e0b38-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e0b38-116">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="e0b38-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e0b38-117">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e0b38-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e0b38-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e0b38-119">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="e0b38-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="e0b38-120">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e0b38-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e0b38-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e0b38-122">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="e0b38-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="e0b38-123">Element TypeName dla SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e0b38-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e0b38-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e0b38-125">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="e0b38-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0b38-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e0b38-126">Parent Elements</span></span>

|<span data-ttu-id="e0b38-127">Element</span><span class="sxs-lookup"><span data-stu-id="e0b38-127">Element</span></span>|<span data-ttu-id="e0b38-128">Opis</span><span class="sxs-lookup"><span data-stu-id="e0b38-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0b38-129">Element EntrySelectedBy TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="e0b38-130">Definiuje typy .NET, korzystające z tego wpisu w tabeli lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="e0b38-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0b38-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0b38-131">Remarks</span></span>

<span data-ttu-id="e0b38-132">Każdy wpis na liście musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="e0b38-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e0b38-133">Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="e0b38-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="e0b38-134">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e0b38-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="e0b38-135">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e0b38-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="e0b38-136">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e0b38-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e0b38-137">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e0b38-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0b38-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0b38-138">See Also</span></span>

[<span data-ttu-id="e0b38-139">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="e0b38-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e0b38-140">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="e0b38-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e0b38-141">Element EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="e0b38-142">Element PropertyName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="e0b38-143">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e0b38-144">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e0b38-145">Element TypeName dla SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e0b38-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e0b38-146">Pisanie programu Windows PowerShell, formatowania i typy plików</span><span class="sxs-lookup"><span data-stu-id="e0b38-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
