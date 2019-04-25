---
title: Element PropertyName SelectionCondition dla EntrySelectedBy dla WideEntry (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064683"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="ce5c6-102">PropertyName, element — SelectionCondition, EntrySelectedBy, WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ce5c6-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="ce5c6-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="ce5c6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ce5c6-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="ce5c6-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="ce5c6-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition WideEntry (Format) EntrySelectedBy WideEntry (Format) elementu PropertyName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="ce5c6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ce5c6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce5c6-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ce5c6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ce5c6-107">Attributes and Elements</span></span>

<span data-ttu-id="ce5c6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="ce5c6-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ce5c6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ce5c6-109">Attributes</span></span>

<span data-ttu-id="ce5c6-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="ce5c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ce5c6-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ce5c6-111">Child Elements</span></span>

<span data-ttu-id="ce5c6-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="ce5c6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ce5c6-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ce5c6-113">Parent Elements</span></span>

|<span data-ttu-id="ce5c6-114">Element</span><span class="sxs-lookup"><span data-stu-id="ce5c6-114">Element</span></span>|<span data-ttu-id="ce5c6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ce5c6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ce5c6-116">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="ce5c6-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ce5c6-117">Określa warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ce5c6-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ce5c6-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="ce5c6-118">Text Value</span></span>

<span data-ttu-id="ce5c6-119">Określ nazwę właściwości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ce5c6-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="ce5c6-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce5c6-120">Remarks</span></span>

<span data-ttu-id="ce5c6-121">Warunek wyboru należy określić co najmniej jedną właściwość name lub skryptu w celu oceny, ale nie można podać obydwie wartości.</span><span class="sxs-lookup"><span data-stu-id="ce5c6-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ce5c6-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ce5c6-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ce5c6-123">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [szerokie](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ce5c6-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ce5c6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce5c6-124">See Also</span></span>

[<span data-ttu-id="ce5c6-125">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="ce5c6-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ce5c6-126">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="ce5c6-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ce5c6-127">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="ce5c6-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ce5c6-128">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="ce5c6-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ce5c6-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="ce5c6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
