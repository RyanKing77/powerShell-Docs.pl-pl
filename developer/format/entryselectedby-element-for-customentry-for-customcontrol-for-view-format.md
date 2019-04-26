---
title: Element EntrySelectedBy CustomEntry dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066281"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="a6abc-102">EntrySelectedBy, element — CustomEntry, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="a6abc-103">Definiuje typy .NET, korzystające z tego wpisu niestandardowych lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="a6abc-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="a6abc-104">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla EntrySelectedBy widoku (Format) Element CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6abc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6abc-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6abc-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a6abc-106">Attributes and Elements</span></span>

<span data-ttu-id="a6abc-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="a6abc-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6abc-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a6abc-108">Attributes</span></span>

<span data-ttu-id="a6abc-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="a6abc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6abc-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a6abc-110">Child Elements</span></span>

|<span data-ttu-id="a6abc-111">Element</span><span class="sxs-lookup"><span data-stu-id="a6abc-111">Element</span></span>|<span data-ttu-id="a6abc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a6abc-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6abc-113">Element SelectionCondition EntrySelectedBy dla CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="a6abc-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a6abc-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a6abc-115">Określa warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="a6abc-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a6abc-116">Element SelectionSetName EntrySelectedBy dla CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="a6abc-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a6abc-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a6abc-118">Określa zestaw typów .NET, korzystających z tej definicji widoku kontrolnym.</span><span class="sxs-lookup"><span data-stu-id="a6abc-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="a6abc-119">Element TypeName dla EntrySelectedBy dla CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="a6abc-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a6abc-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a6abc-121">Określa typ architektury .NET, który używa tej definicji widoku kontrolnym.</span><span class="sxs-lookup"><span data-stu-id="a6abc-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a6abc-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a6abc-122">Parent Elements</span></span>

|<span data-ttu-id="a6abc-123">Element</span><span class="sxs-lookup"><span data-stu-id="a6abc-123">Element</span></span>|<span data-ttu-id="a6abc-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a6abc-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6abc-125">Element CustomEntry CustomEntries widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="a6abc-126">Definiuje kontrolki, używany przez konkretne obiekty platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="a6abc-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a6abc-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6abc-127">Remarks</span></span>

<span data-ttu-id="a6abc-128">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru dla wpisu.</span><span class="sxs-lookup"><span data-stu-id="a6abc-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="a6abc-129">Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="a6abc-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="a6abc-130">Wybór warunki są używane do definiowania warunek, który musi istnieć wpis, który ma być używany, np. Jeśli obiekt ma określoną właściwość lub gdy wartość określoną właściwość lub skryptu, które daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="a6abc-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a6abc-131">Aby uzyskać więcej informacji o warunkach wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a6abc-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a6abc-132">Aby uzyskać więcej informacji o składnikach widoku kontrolki niestandardowej, zobacz [widok niestandardowy formant](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a6abc-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6abc-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6abc-133">See Also</span></span>

[<span data-ttu-id="a6abc-134">Element SelectionCondition EntrySelectedBy dla CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="a6abc-135">Element SelectionSetName EntrySelectedBy dla CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a6abc-136">Element TypeName dla EntrySelectedBy dla CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a6abc-137">Element CustomEntry CustomEntries widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="a6abc-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a6abc-138">Wyświetl formant niestandardowy</span><span class="sxs-lookup"><span data-stu-id="a6abc-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="a6abc-139">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="a6abc-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
