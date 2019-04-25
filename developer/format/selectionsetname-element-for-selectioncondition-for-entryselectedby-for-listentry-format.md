---
title: Element SelectionSetName SelectionCondition dla EntrySelectedBy dla ListEntry (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075515"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="9c687-102">SelectionSetName, element — SelectionCondition, EntrySelectedBy, ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9c687-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="9c687-103">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="9c687-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="9c687-104">Jeśli typy w tym zestawie, warunek jest spełniony, a obiekt jest wyświetlana przy użyciu tej definicji widoku listy.</span><span class="sxs-lookup"><span data-stu-id="9c687-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="9c687-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition ListEntry (Format) EntrySelectedBy ListEntry (Format) elementu SelectionSetName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9c687-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c687-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c687-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c687-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9c687-107">Attributes and Elements</span></span>

<span data-ttu-id="9c687-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="9c687-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c687-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c687-109">Attributes</span></span>

<span data-ttu-id="9c687-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="9c687-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c687-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9c687-111">Child Elements</span></span>

<span data-ttu-id="9c687-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="9c687-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c687-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9c687-113">Parent Elements</span></span>

|<span data-ttu-id="9c687-114">Element</span><span class="sxs-lookup"><span data-stu-id="9c687-114">Element</span></span>|<span data-ttu-id="9c687-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9c687-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c687-116">Element SelectionCondition EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9c687-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="9c687-117">Określa warunek, którego można użyć tej definicji widoku listy, musi istnieć.</span><span class="sxs-lookup"><span data-stu-id="9c687-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9c687-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="9c687-118">Text Value</span></span>

<span data-ttu-id="9c687-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="9c687-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c687-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c687-120">Remarks</span></span>

<span data-ttu-id="9c687-121">Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="9c687-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="9c687-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9c687-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9c687-123">Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="9c687-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="9c687-124">Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9c687-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="9c687-125">Aby uzyskać więcej informacji o innych składnikach widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="9c687-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9c687-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c687-126">See Also</span></span>

[<span data-ttu-id="9c687-127">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="9c687-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9c687-128">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="9c687-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9c687-129">Element SelectionCondition EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9c687-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="9c687-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9c687-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
