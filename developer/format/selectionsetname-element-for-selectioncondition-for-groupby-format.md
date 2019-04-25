---
title: Element SelectionSetName SelectionCondition dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063770"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="c7a3f-102">SelectionSetName, element — SelectionCondition, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="c7a3f-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="c7a3f-103">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c7a3f-104">Gdy dowolnego typu, w tym zestawie, warunek jest spełniony, i jest wyświetlany obiekt, za pomocą tego formantu.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="c7a3f-105">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c7a3f-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu EntrySelectedBy CustomEntry GroupBy (Format) elementu SelectionCondition EntrySelectedBy GroupBy (Format) elementu SelectionSetName SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="c7a3f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7a3f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7a3f-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7a3f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c7a3f-108">Attributes and Elements</span></span>

<span data-ttu-id="c7a3f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7a3f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c7a3f-110">Attributes</span></span>

<span data-ttu-id="c7a3f-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7a3f-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c7a3f-112">Child Elements</span></span>

<span data-ttu-id="c7a3f-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c7a3f-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c7a3f-114">Parent Elements</span></span>

|<span data-ttu-id="c7a3f-115">Element</span><span class="sxs-lookup"><span data-stu-id="c7a3f-115">Element</span></span>|<span data-ttu-id="c7a3f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c7a3f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7a3f-117">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="c7a3f-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="c7a3f-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c7a3f-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="c7a3f-119">Text Value</span></span>

<span data-ttu-id="c7a3f-120">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7a3f-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7a3f-121">Remarks</span></span>

<span data-ttu-id="c7a3f-122">Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c7a3f-123">Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia wybór](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c7a3f-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c7a3f-124">Gdy ten element jest określony, nie można określić [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="c7a3f-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="c7a3f-125">Aby uzyskać więcej informacji na temat definiowania warunków wybór zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c7a3f-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7a3f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7a3f-126">See Also</span></span>

[<span data-ttu-id="c7a3f-127">Element TypeName dla SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="c7a3f-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="c7a3f-128">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="c7a3f-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="c7a3f-129">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="c7a3f-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c7a3f-130">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="c7a3f-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c7a3f-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="c7a3f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
