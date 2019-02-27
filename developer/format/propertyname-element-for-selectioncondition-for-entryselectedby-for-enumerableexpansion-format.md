---
title: Element PropertyName SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849350"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="e3167-102">PropertyName, element — SelectionCondition, EntrySelectedBy, EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e3167-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e3167-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="e3167-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e3167-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="e3167-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="e3167-105">— Element (w formacie) DefaultSettings — Element (Format) EnumerableExpansions — Element (Format) EnumerableExpansion — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition EnumerableExpansion (Format) EntrySelectedBy dla Element PropertyName EnumerableExpansion (w formacie) dla SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e3167-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3167-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3167-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3167-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e3167-107">Attributes and Elements</span></span>

<span data-ttu-id="e3167-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="e3167-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3167-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e3167-109">Attributes</span></span>

<span data-ttu-id="e3167-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="e3167-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3167-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e3167-111">Child Elements</span></span>

<span data-ttu-id="e3167-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="e3167-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3167-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e3167-113">Parent Elements</span></span>

|<span data-ttu-id="e3167-114">Element</span><span class="sxs-lookup"><span data-stu-id="e3167-114">Element</span></span>|<span data-ttu-id="e3167-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e3167-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3167-116">Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e3167-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e3167-117">Określa warunek, który musi istnieć, aby rozwinąć kolekcji obiektów tej definicji.</span><span class="sxs-lookup"><span data-stu-id="e3167-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3167-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="e3167-118">Text Value</span></span>

<span data-ttu-id="e3167-119">Określ nazwę właściwości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e3167-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3167-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3167-120">Remarks</span></span>

<span data-ttu-id="e3167-121">Warunek wyboru należy określić co najmniej jedną właściwość name lub skryptu w celu oceny, ale nie można podać obydwie wartości.</span><span class="sxs-lookup"><span data-stu-id="e3167-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e3167-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e3167-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3167-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3167-123">See Also</span></span>

[<span data-ttu-id="e3167-124">Definiowanie warunków podczas danych jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="e3167-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e3167-125">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e3167-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e3167-126">Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="e3167-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e3167-127">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="e3167-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
