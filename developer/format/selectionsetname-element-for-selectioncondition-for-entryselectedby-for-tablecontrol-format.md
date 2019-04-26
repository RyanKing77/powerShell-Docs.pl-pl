---
title: Element SelectionSetName SelectionCondition dla EntrySelectedBy dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064054"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="35e65-102">SelectionSetName, element — SelectionCondition, EntrySelectedBy, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="35e65-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="35e65-103">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="35e65-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="35e65-104">Jeśli typy w tym zestawie, warunek jest spełniony, a obiekt jest wyświetlana przy użyciu tej definicji widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="35e65-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="35e65-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) EntrySelectedBy Element konfiguracji dla TableRowEntry (Format) Element SelectionCondition EntrySelectedBy TableRowEntry (Format) elementu SelectionSetName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="35e65-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="35e65-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="35e65-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="35e65-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="35e65-107">Attributes and Elements</span></span>

<span data-ttu-id="35e65-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="35e65-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="35e65-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="35e65-109">Attributes</span></span>

<span data-ttu-id="35e65-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="35e65-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="35e65-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="35e65-111">Child Elements</span></span>

<span data-ttu-id="35e65-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="35e65-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="35e65-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35e65-113">Parent Elements</span></span>

|<span data-ttu-id="35e65-114">Element</span><span class="sxs-lookup"><span data-stu-id="35e65-114">Element</span></span>|<span data-ttu-id="35e65-115">Opis</span><span class="sxs-lookup"><span data-stu-id="35e65-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35e65-116">Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="35e65-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="35e65-117">Określa warunek, który musi istnieć na potrzeby tej definicji widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="35e65-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="35e65-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="35e65-118">Text Value</span></span>

<span data-ttu-id="35e65-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="35e65-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="35e65-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35e65-120">Remarks</span></span>

<span data-ttu-id="35e65-121">Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="35e65-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="35e65-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="35e65-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="35e65-123">Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="35e65-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="35e65-124">Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="35e65-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="35e65-125">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="35e65-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="35e65-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35e65-126">See Also</span></span>

[<span data-ttu-id="35e65-127">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="35e65-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="35e65-128">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="35e65-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="35e65-129">Element TypeName dla SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="35e65-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="35e65-130">Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="35e65-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="35e65-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="35e65-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
