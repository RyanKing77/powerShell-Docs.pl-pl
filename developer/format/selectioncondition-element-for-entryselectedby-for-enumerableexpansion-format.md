---
title: Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064139"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="a5b13-102">SelectionCondition, element — EntrySelectedBy, EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="a5b13-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="a5b13-103">Określa warunek, który musi istnieć, aby rozwinąć kolekcji obiektów tej definicji.</span><span class="sxs-lookup"><span data-stu-id="a5b13-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="a5b13-104">— Element (w formacie) DefaultSettings — Element (Format) EnumerableExpansions — Element (Format) EnumerableExpansion — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition EnumerableExpansion (Format) EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="a5b13-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5b13-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5b13-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5b13-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5b13-106">Attributes and Elements</span></span>

<span data-ttu-id="a5b13-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="a5b13-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="a5b13-108">Należy określić pojedynczy `PropertyName` lub `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="a5b13-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="a5b13-109">`SelectionSetName` i `TypeName` elementy są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a5b13-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="a5b13-110">Można określić jedną z dowolnego elementu.</span><span class="sxs-lookup"><span data-stu-id="a5b13-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5b13-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5b13-111">Attributes</span></span>

<span data-ttu-id="a5b13-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="a5b13-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5b13-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5b13-113">Child Elements</span></span>

|<span data-ttu-id="a5b13-114">Element</span><span class="sxs-lookup"><span data-stu-id="a5b13-114">Element</span></span>|<span data-ttu-id="a5b13-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a5b13-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5b13-116">Element PropertyName SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="a5b13-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a5b13-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5b13-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a5b13-118">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="a5b13-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a5b13-119">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="a5b13-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a5b13-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5b13-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a5b13-121">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="a5b13-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a5b13-122">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="a5b13-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a5b13-123">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5b13-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a5b13-124">Określa zestaw typów .NET wyzwalającego warunku.</span><span class="sxs-lookup"><span data-stu-id="a5b13-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="a5b13-125">Element TypeName dla SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="a5b13-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a5b13-126">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a5b13-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a5b13-127">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="a5b13-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a5b13-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5b13-128">Parent Elements</span></span>

|<span data-ttu-id="a5b13-129">Element</span><span class="sxs-lookup"><span data-stu-id="a5b13-129">Element</span></span>|<span data-ttu-id="a5b13-130">Opis</span><span class="sxs-lookup"><span data-stu-id="a5b13-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5b13-131">Element EntrySelectedBy EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="a5b13-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="a5b13-132">Definiuje, które obiekty kolekcji .NET są rozszerzane przez tę definicję.</span><span class="sxs-lookup"><span data-stu-id="a5b13-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5b13-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5b13-133">Remarks</span></span>

<span data-ttu-id="a5b13-134">Każda definicja musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="a5b13-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a5b13-135">Podczas definiowania warunek wyboru mają zastosowanie następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="a5b13-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a5b13-136">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a5b13-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a5b13-137">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a5b13-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a5b13-138">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [Definiowanie warunków danych Diplaying](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a5b13-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a5b13-139">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [szerokie](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a5b13-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5b13-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5b13-140">See Also</span></span>

[<span data-ttu-id="a5b13-141">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="a5b13-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a5b13-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="a5b13-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
