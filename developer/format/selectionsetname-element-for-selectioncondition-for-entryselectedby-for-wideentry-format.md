---
title: Element SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845500"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="09032-102">SelectionSetName, element — SelectionCondition, EntrySelectedBy, WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="09032-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="09032-103">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="09032-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="09032-104">Jeśli typy w tym zestawie, warunek jest spełniony, a obiekt jest wyświetlana przy użyciu tej definicji szerokie.</span><span class="sxs-lookup"><span data-stu-id="09032-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="09032-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition WideEntry (Format) EntrySelectedBy WideEntry (Format) elementu SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="09032-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09032-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="09032-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09032-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="09032-107">Attributes and Elements</span></span>

<span data-ttu-id="09032-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="09032-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09032-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="09032-109">Attributes</span></span>

<span data-ttu-id="09032-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="09032-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09032-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="09032-111">Child Elements</span></span>

<span data-ttu-id="09032-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="09032-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="09032-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="09032-113">Parent Elements</span></span>

|<span data-ttu-id="09032-114">Element</span><span class="sxs-lookup"><span data-stu-id="09032-114">Element</span></span>|<span data-ttu-id="09032-115">Opis</span><span class="sxs-lookup"><span data-stu-id="09032-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09032-116">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="09032-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="09032-117">Określa warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="09032-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="09032-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="09032-118">Text Value</span></span>

<span data-ttu-id="09032-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="09032-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="09032-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09032-120">Remarks</span></span>

<span data-ttu-id="09032-121">Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="09032-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="09032-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="09032-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="09032-123">Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="09032-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="09032-124">Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="09032-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="09032-125">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="09032-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09032-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09032-126">See Also</span></span>

[<span data-ttu-id="09032-127">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="09032-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="09032-128">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="09032-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="09032-129">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="09032-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="09032-130">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="09032-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="09032-131">Element TypeName dla SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="09032-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="09032-132">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="09032-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
