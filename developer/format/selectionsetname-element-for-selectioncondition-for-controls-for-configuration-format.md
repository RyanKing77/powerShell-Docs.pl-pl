---
title: Element SelectionSetName SelectionCondition dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848307"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="92c89-102">SelectionSetName, element — SelectionCondition, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="92c89-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="92c89-103">Określa zestaw typów .NET, które mogą powodować warunku.</span><span class="sxs-lookup"><span data-stu-id="92c89-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="92c89-104">Gdy dowolnego typu, w tym zestawie, warunek jest spełniony, i jest wyświetlany obiekt, za pomocą tego formantu.</span><span class="sxs-lookup"><span data-stu-id="92c89-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="92c89-105">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="92c89-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="92c89-106">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do kontrolki Element CustomEntry konfiguracji (w formacie) dla formant niestandardowy dla formantów EntrySelectedBy elementu konfiguracji (Format) CustomEntry dla formantów SelectionCondition elementu konfiguracji (Format) EntrySelectedBy dla kontrolki Element SelectionSetName konfiguracji (w formacie) dla SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="92c89-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92c89-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="92c89-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92c89-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="92c89-108">Attributes and Elements</span></span>

<span data-ttu-id="92c89-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="92c89-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92c89-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="92c89-110">Attributes</span></span>

<span data-ttu-id="92c89-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="92c89-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92c89-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="92c89-112">Child Elements</span></span>

<span data-ttu-id="92c89-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="92c89-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92c89-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92c89-114">Parent Elements</span></span>

|<span data-ttu-id="92c89-115">Element</span><span class="sxs-lookup"><span data-stu-id="92c89-115">Element</span></span>|<span data-ttu-id="92c89-116">Opis</span><span class="sxs-lookup"><span data-stu-id="92c89-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92c89-117">Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="92c89-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="92c89-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="92c89-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="92c89-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="92c89-119">Text Value</span></span>

<span data-ttu-id="92c89-120">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="92c89-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="92c89-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92c89-121">Remarks</span></span>

<span data-ttu-id="92c89-122">Wybór zestawy są wspólne grupy obiektów platformy .NET, które mogą być używane przez dowolny widok, który definiuje formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="92c89-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="92c89-123">Aby uzyskać więcej informacji na temat tworzenia i odwołania do zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="92c89-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="92c89-124">Warunek wyboru można określić zbiór lub typ architektury .NET, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="92c89-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="92c89-125">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="92c89-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92c89-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92c89-126">See Also</span></span>

[<span data-ttu-id="92c89-127">Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="92c89-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="92c89-128">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="92c89-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="92c89-129">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="92c89-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="92c89-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="92c89-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
