---
title: Element EntrySelectedBy CustomEntry dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066247"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="ec38e-102">EntrySelectedBy, element — CustomEntry, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="ec38e-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="ec38e-103">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ec38e-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ec38e-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="ec38e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ec38e-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu EntrySelectedBy CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ec38e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec38e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec38e-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec38e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ec38e-107">Attributes and Elements</span></span>

<span data-ttu-id="ec38e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="ec38e-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="ec38e-109">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru dla definicji.</span><span class="sxs-lookup"><span data-stu-id="ec38e-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="ec38e-110">Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="ec38e-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec38e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ec38e-111">Attributes</span></span>

<span data-ttu-id="ec38e-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="ec38e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec38e-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ec38e-113">Child Elements</span></span>

|<span data-ttu-id="ec38e-114">Element</span><span class="sxs-lookup"><span data-stu-id="ec38e-114">Element</span></span>|<span data-ttu-id="ec38e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ec38e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec38e-116">Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ec38e-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="ec38e-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ec38e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ec38e-118">Określa warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ec38e-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="ec38e-119">Element SelectionSetName EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ec38e-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="ec38e-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ec38e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ec38e-121">Określa zestaw typów .NET, korzystających z tej definicji formantu.</span><span class="sxs-lookup"><span data-stu-id="ec38e-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="ec38e-122">Element TypeName dla EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ec38e-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="ec38e-123">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ec38e-123">Optional element.</span></span><br /><br /> <span data-ttu-id="ec38e-124">Określa typ architektury .NET, która używa tej definicji kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ec38e-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ec38e-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ec38e-125">Parent Elements</span></span>

|<span data-ttu-id="ec38e-126">Element</span><span class="sxs-lookup"><span data-stu-id="ec38e-126">Element</span></span>|<span data-ttu-id="ec38e-127">Opis</span><span class="sxs-lookup"><span data-stu-id="ec38e-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec38e-128">Element CustomEntry CustomEntries dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ec38e-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="ec38e-129">Zawiera definicję formantu.</span><span class="sxs-lookup"><span data-stu-id="ec38e-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ec38e-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec38e-130">Remarks</span></span>

<span data-ttu-id="ec38e-131">Wybór warunki są używane do definiowania warunek, który musi istnieć definicja ma być używany, np. Jeśli obiekt ma określoną właściwość lub gdy wartość określoną właściwość lub skryptu, które daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="ec38e-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="ec38e-132">Aby uzyskać więcej informacji o warunkach wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ec38e-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec38e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec38e-133">See Also</span></span>

[<span data-ttu-id="ec38e-134">Element CustomEntry CustomEntries dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ec38e-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="ec38e-135">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="ec38e-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
