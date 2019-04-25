---
title: Element SelectionSetName SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063864"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="2b83d-102">SelectionSetName, element — SelectionCondition, EntrySelectedBy, EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="2b83d-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="2b83d-103">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="2b83d-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="2b83d-104">Jeśli jeden z typów, w tym zestawie, warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="2b83d-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="2b83d-105">Element DefaultSettings — Element (Format) EnumerableExpansions — Element (w formacie) EnumerableExpansions — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition EnumerableExpansion (Format) EntrySelectedBy dla Element SelectionSetName EnumerableExpansion (w formacie) dla SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="2b83d-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b83d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b83d-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b83d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2b83d-107">Attributes and Elements</span></span>

<span data-ttu-id="2b83d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="2b83d-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b83d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2b83d-109">Attributes</span></span>

<span data-ttu-id="2b83d-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b83d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b83d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2b83d-111">Child Elements</span></span>

<span data-ttu-id="2b83d-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b83d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b83d-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2b83d-113">Parent Elements</span></span>

|<span data-ttu-id="2b83d-114">Element</span><span class="sxs-lookup"><span data-stu-id="2b83d-114">Element</span></span>|<span data-ttu-id="2b83d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="2b83d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b83d-116">Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="2b83d-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="2b83d-117">Określa warunek, który musi istnieć, aby rozwinąć kolekcji obiektów tej definicji.</span><span class="sxs-lookup"><span data-stu-id="2b83d-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2b83d-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="2b83d-118">Text Value</span></span>

<span data-ttu-id="2b83d-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="2b83d-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b83d-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b83d-120">Remarks</span></span>

<span data-ttu-id="2b83d-121">Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="2b83d-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="2b83d-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2b83d-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2b83d-123">Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="2b83d-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="2b83d-124">Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia wybór](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2b83d-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b83d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b83d-125">See Also</span></span>

[<span data-ttu-id="2b83d-126">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="2b83d-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2b83d-127">Element SelectionCondition EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="2b83d-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="2b83d-128">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="2b83d-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
