---
title: Element SelectionSetName SelectionCondition dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075583"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="0a440-102">SelectionSetName, element — SelectionCondition, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="0a440-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="0a440-103">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="0a440-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="0a440-104">Gdy dowolnego typu, w tym zestawie, warunek jest spełniony, i jest wyświetlany obiekt, za pomocą tego formantu.</span><span class="sxs-lookup"><span data-stu-id="0a440-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="0a440-105">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="0a440-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0a440-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla EntrySelectedBy widoku (Format) Element CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="0a440-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a440-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a440-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a440-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0a440-108">Attributes and Elements</span></span>

<span data-ttu-id="0a440-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="0a440-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a440-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0a440-110">Attributes</span></span>

<span data-ttu-id="0a440-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="0a440-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a440-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0a440-112">Child Elements</span></span>

<span data-ttu-id="0a440-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="0a440-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0a440-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0a440-114">Parent Elements</span></span>

|<span data-ttu-id="0a440-115">Element</span><span class="sxs-lookup"><span data-stu-id="0a440-115">Element</span></span>|<span data-ttu-id="0a440-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0a440-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a440-117">Element SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="0a440-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="0a440-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="0a440-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0a440-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="0a440-119">Text Value</span></span>

<span data-ttu-id="0a440-120">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="0a440-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a440-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a440-121">Remarks</span></span>

<span data-ttu-id="0a440-122">Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="0a440-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="0a440-123">Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0a440-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="0a440-124">Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="0a440-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="0a440-125">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0a440-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0a440-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a440-126">See Also</span></span>

[<span data-ttu-id="0a440-127">Element SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="0a440-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="0a440-128">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="0a440-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0a440-129">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="0a440-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0a440-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="0a440-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
