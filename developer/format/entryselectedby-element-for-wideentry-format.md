---
title: Element EntrySelectedBy WideEntry (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066179"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="26f3c-102">EntrySelectedBy, element — WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="26f3c-103">Definiuje typy .NET używających tej definicji szerokie lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="26f3c-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="26f3c-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu WideControl (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26f3c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="26f3c-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26f3c-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="26f3c-106">Attributes and Elements</span></span>

<span data-ttu-id="26f3c-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="26f3c-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26f3c-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="26f3c-108">Attributes</span></span>

<span data-ttu-id="26f3c-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="26f3c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26f3c-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="26f3c-110">Child Elements</span></span>

|<span data-ttu-id="26f3c-111">Element</span><span class="sxs-lookup"><span data-stu-id="26f3c-111">Element</span></span>|<span data-ttu-id="26f3c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="26f3c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26f3c-113">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="26f3c-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="26f3c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="26f3c-115">Określa warunek, który musi istnieć dla tej definicji szerokie ma być używany.</span><span class="sxs-lookup"><span data-stu-id="26f3c-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="26f3c-116">Element SelectionSetName EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="26f3c-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="26f3c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="26f3c-118">Określa zestaw typów .NET, które używają tej definicji szerokie.</span><span class="sxs-lookup"><span data-stu-id="26f3c-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="26f3c-119">Element TypeName dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="26f3c-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="26f3c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="26f3c-121">Określa typ architektury .NET, która używa tej definicji szerokie.</span><span class="sxs-lookup"><span data-stu-id="26f3c-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="26f3c-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="26f3c-122">Parent Elements</span></span>

|<span data-ttu-id="26f3c-123">Element</span><span class="sxs-lookup"><span data-stu-id="26f3c-123">Element</span></span>|<span data-ttu-id="26f3c-124">Opis</span><span class="sxs-lookup"><span data-stu-id="26f3c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26f3c-125">Element WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="26f3c-126">Zawiera definicję szerokie.</span><span class="sxs-lookup"><span data-stu-id="26f3c-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="26f3c-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26f3c-127">Remarks</span></span>

<span data-ttu-id="26f3c-128">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru dla definicji szerokie.</span><span class="sxs-lookup"><span data-stu-id="26f3c-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="26f3c-129">Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="26f3c-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="26f3c-130">Wybór warunki są używane do definiowania warunek, który musi istnieć dla definicji, który ma być używany, na przykład jeśli obiekt ma określoną właściwość lub wartość określoną właściwość lub wartość skryptu daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="26f3c-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="26f3c-131">Aby uzyskać więcej informacji o warunkach wyboru, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="26f3c-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="26f3c-132">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="26f3c-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26f3c-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26f3c-133">See Also</span></span>

[<span data-ttu-id="26f3c-134">Element WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="26f3c-135">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="26f3c-136">Element SelectionSetName EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="26f3c-137">Element TypeName dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26f3c-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="26f3c-138">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="26f3c-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="26f3c-139">Definiowanie warunków do wyświetlania danych</span><span class="sxs-lookup"><span data-stu-id="26f3c-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="26f3c-140">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="26f3c-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
