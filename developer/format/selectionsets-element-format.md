---
title: Element SelectionSets (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063781"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="a761f-102">SelectionSets, element (format)</span><span class="sxs-lookup"><span data-stu-id="a761f-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="a761f-103">Definiuje typowe rodzaje obiektów platformy .NET, które mogą być używane przez wszystkie widoki formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="a761f-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="a761f-104">Widoki i kontrolki formatowania pliku odwoływać kompletny zestaw obiektów za pomocą tylko nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="a761f-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="a761f-105">Format elementu SelectionSets elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a761f-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="a761f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a761f-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a761f-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a761f-107">Attributes and Elements</span></span>

<span data-ttu-id="a761f-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSets` elementu.</span><span class="sxs-lookup"><span data-stu-id="a761f-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="a761f-109">Każdy element podrzędny definiuje zestaw obiektów, które mogą być przywoływane przez nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="a761f-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="a761f-110">Kolejność elementów podrzędnych nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="a761f-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="a761f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a761f-111">Attributes</span></span>

<span data-ttu-id="a761f-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="a761f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a761f-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a761f-113">Child Elements</span></span>

|<span data-ttu-id="a761f-114">Element</span><span class="sxs-lookup"><span data-stu-id="a761f-114">Element</span></span>|<span data-ttu-id="a761f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a761f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a761f-116">Element SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="a761f-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="a761f-117">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="a761f-117">Required element.</span></span><br /><br /> <span data-ttu-id="a761f-118">Definiuje pojedynczy zestaw obiektów platformy .NET, które mogą być przywoływane przez nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="a761f-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a761f-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a761f-119">Parent Elements</span></span>

|<span data-ttu-id="a761f-120">Element</span><span class="sxs-lookup"><span data-stu-id="a761f-120">Element</span></span>|<span data-ttu-id="a761f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="a761f-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a761f-122">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a761f-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="a761f-123">Reprezentuje element najwyższego poziomu w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="a761f-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a761f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a761f-124">Remarks</span></span>

<span data-ttu-id="a761f-125">Można użyć zestawów zaznaczenie, gdy masz zestaw powiązanych obiektów, które odwołują się za pomocą jednej nazwy, takiego jak zestaw obiektów, które są powiązane z dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="a761f-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="a761f-126">Podczas definiowania widoków, można określić zestaw obiektów przy użyciu nazwy wybór zestawu, zamiast wymieniać wszystkich obiektów w ramach każdego widoku.</span><span class="sxs-lookup"><span data-stu-id="a761f-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="a761f-127">Wspólne wybór zestawy są określane przez ich nazwy, podczas definiowania widoków formatowania pliku lub w definicjach widoków.</span><span class="sxs-lookup"><span data-stu-id="a761f-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="a761f-128">W takich przypadkach `SelectionSetName` element podrzędny elementu `ViewSelectedBy` i `EntrySelectedBy` elementy określa zestaw, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="a761f-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="a761f-129">Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a761f-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a761f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a761f-130">See Also</span></span>

[<span data-ttu-id="a761f-131">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a761f-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="a761f-132">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="a761f-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a761f-133">Element SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="a761f-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="a761f-134">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="a761f-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
