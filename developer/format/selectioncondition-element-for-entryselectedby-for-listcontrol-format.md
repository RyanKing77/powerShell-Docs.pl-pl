---
title: Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735088"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="8e6cf-102">SelectionCondition, element — EntrySelectedBy, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="8e6cf-103">Określa warunek, którego można użyć tej definicji widoku listy, musi istnieć.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="8e6cf-104">Nie ma żadnego limitu liczby warunki wyboru, które mogą być określone dla definicji listy.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="8e6cf-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition ListEntry (Format) EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e6cf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e6cf-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e6cf-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8e6cf-107">Attributes and Elements</span></span>

<span data-ttu-id="8e6cf-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e6cf-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8e6cf-109">Attributes</span></span>

<span data-ttu-id="8e6cf-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e6cf-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8e6cf-111">Child Elements</span></span>

|<span data-ttu-id="8e6cf-112">Element</span><span class="sxs-lookup"><span data-stu-id="8e6cf-112">Element</span></span>|<span data-ttu-id="8e6cf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8e6cf-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e6cf-114">Element PropertyName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8e6cf-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8e6cf-116">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8e6cf-117">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8e6cf-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8e6cf-119">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="8e6cf-120">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="8e6cf-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8e6cf-122">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="8e6cf-123">Element TypeName dla SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8e6cf-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8e6cf-125">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8e6cf-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8e6cf-126">Parent Elements</span></span>

|<span data-ttu-id="8e6cf-127">Element</span><span class="sxs-lookup"><span data-stu-id="8e6cf-127">Element</span></span>|<span data-ttu-id="8e6cf-128">Opis</span><span class="sxs-lookup"><span data-stu-id="8e6cf-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e6cf-129">Element EntrySelectedBy TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="8e6cf-130">Definiuje typy .NET, korzystające z tego wpisu w tabeli lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e6cf-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e6cf-131">Remarks</span></span>

<span data-ttu-id="8e6cf-132">określasz warunek wyboru lWhen, obowiązują następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="8e6cf-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="8e6cf-133">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8e6cf-134">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="8e6cf-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8e6cf-135">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8e6cf-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8e6cf-136">Aby uzyskać więcej informacji o innych składnikach widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e6cf-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e6cf-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e6cf-137">See Also</span></span>

[<span data-ttu-id="8e6cf-138">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="8e6cf-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8e6cf-139">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="8e6cf-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8e6cf-140">Element ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="8e6cf-141">Element SelectionSetName EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8e6cf-142">Element TypeName dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8e6cf-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="8e6cf-143">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="8e6cf-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
