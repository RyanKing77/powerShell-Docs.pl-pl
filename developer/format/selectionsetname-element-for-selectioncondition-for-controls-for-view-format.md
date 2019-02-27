---
title: Element SelectionSetName SelectionCondition dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846193"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="fa1dc-102">SelectionSetName, element — SelectionCondition, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="fa1dc-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="fa1dc-103">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="fa1dc-104">Gdy dowolnego typu, w tym zestawie, warunek jest spełniony, i jest wyświetlany obiekt, za pomocą tego formantu.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="fa1dc-105">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="fa1dc-106">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu EntrySelectedBy CustomEntry dla formantów widoku (Format) elementu SelectionCondition EntrySelectedBy dla kontrolki (Widok Format) elementu SelectionSetName SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="fa1dc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa1dc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa1dc-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa1dc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fa1dc-108">Attributes and Elements</span></span>

<span data-ttu-id="fa1dc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa1dc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fa1dc-110">Attributes</span></span>

<span data-ttu-id="fa1dc-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa1dc-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fa1dc-112">Child Elements</span></span>

<span data-ttu-id="fa1dc-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fa1dc-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fa1dc-114">Parent Elements</span></span>

|<span data-ttu-id="fa1dc-115">Element</span><span class="sxs-lookup"><span data-stu-id="fa1dc-115">Element</span></span>|<span data-ttu-id="fa1dc-116">Opis</span><span class="sxs-lookup"><span data-stu-id="fa1dc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa1dc-117">Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="fa1dc-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="fa1dc-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fa1dc-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="fa1dc-119">Text Value</span></span>

<span data-ttu-id="fa1dc-120">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa1dc-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa1dc-121">Remarks</span></span>

<span data-ttu-id="fa1dc-122">Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="fa1dc-123">Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia wybór](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="fa1dc-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="fa1dc-124">Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="fa1dc-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="fa1dc-125">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fa1dc-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa1dc-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa1dc-126">See Also</span></span>

[<span data-ttu-id="fa1dc-127">Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="fa1dc-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="fa1dc-128">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="fa1dc-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fa1dc-129">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="fa1dc-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="fa1dc-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="fa1dc-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
