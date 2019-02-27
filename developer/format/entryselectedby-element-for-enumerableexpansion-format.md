---
title: Element EntrySelectedBy EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846522"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="7f2a4-102">EntrySelectedBy, element — EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="7f2a4-103">Definiuje typy .NET, które używają tej definicji lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="7f2a4-104">— Element (Format) DefaultSettings — Element (Format) elementu EnumerableExpansions (Format) elementu EnumerableExpansion (Format) EntrySelectedBy Element konfiguracji dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7f2a4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f2a4-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7f2a4-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f2a4-106">Attributes and Elements</span></span>

<span data-ttu-id="7f2a4-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7f2a4-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f2a4-108">Attributes</span></span>

<span data-ttu-id="7f2a4-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7f2a4-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f2a4-110">Child Elements</span></span>

|<span data-ttu-id="7f2a4-111">Element</span><span class="sxs-lookup"><span data-stu-id="7f2a4-111">Element</span></span>|<span data-ttu-id="7f2a4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7f2a4-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f2a4-113">Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7f2a4-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7f2a4-115">Określa warunek, który musi istnieć, aby rozwinąć kolekcji obiektów tej definicji.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="7f2a4-116">Element SelectionSetName EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7f2a4-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7f2a4-118">Określa zestaw typów .NET, korzystających z tej definicji jak obiekty kolekcji zostaną rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="7f2a4-119">Element TypeName dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7f2a4-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7f2a4-121">Określa typ architektury .NET, który używa tej definicji jak obiekty kolekcji zostaną rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7f2a4-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f2a4-122">Parent Elements</span></span>

|<span data-ttu-id="7f2a4-123">Element</span><span class="sxs-lookup"><span data-stu-id="7f2a4-123">Element</span></span>|<span data-ttu-id="7f2a4-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7f2a4-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f2a4-125">Element EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="7f2a4-126">Definiuje sposób określonej kolekcji .NET, które obiekty są rozszerzane, gdy są one wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7f2a4-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f2a4-127">Remarks</span></span>

<span data-ttu-id="7f2a4-128">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru dla wpisu definicji.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="7f2a4-129">Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="7f2a4-130">Wybór warunki są używane do definiowania warunek, który musi istnieć dla definicji, który ma być używany, na przykład jeśli obiekt ma określoną właściwość lub wartość określoną właściwość lub skrypt daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="7f2a4-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="7f2a4-131">Aby uzyskać więcej informacji o warunkach wyboru, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7f2a4-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f2a4-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f2a4-132">See Also</span></span>

[<span data-ttu-id="7f2a4-133">Definiowanie warunków do wyświetlania danych</span><span class="sxs-lookup"><span data-stu-id="7f2a4-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7f2a4-134">Element EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="7f2a4-135">Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7f2a4-136">Element SelectionSetName EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7f2a4-137">Element TypeName dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="7f2a4-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7f2a4-138">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="7f2a4-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
