---
title: Element SelectionSet (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076314"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="2ce58-102">SelectionSet, element (format)</span><span class="sxs-lookup"><span data-stu-id="2ce58-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="2ce58-103">Definiuje zestaw obiektów platformy .NET, które mogą być przywoływane przez nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="2ce58-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="2ce58-104">Element SelectionSet SelectionSets — Element (w formacie) — Element (w formacie) konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="2ce58-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ce58-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ce58-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ce58-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2ce58-106">Attributes and Elements</span></span>

<span data-ttu-id="2ce58-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSet` elementu.</span><span class="sxs-lookup"><span data-stu-id="2ce58-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="2ce58-108">Każdy zestaw wybór musi mieć nazwę i musi on również określać obiektów platformy .NET, zestawu.</span><span class="sxs-lookup"><span data-stu-id="2ce58-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ce58-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2ce58-109">Attributes</span></span>

<span data-ttu-id="2ce58-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="2ce58-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ce58-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2ce58-111">Child Elements</span></span>

|<span data-ttu-id="2ce58-112">Element</span><span class="sxs-lookup"><span data-stu-id="2ce58-112">Element</span></span>|<span data-ttu-id="2ce58-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2ce58-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ce58-114">Name — Element dla SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="2ce58-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="2ce58-115">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="2ce58-115">Required element.</span></span><br /><br /> <span data-ttu-id="2ce58-116">Określa nazwę używaną do odwoływać się do zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="2ce58-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="2ce58-117">Typy elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2ce58-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="2ce58-118">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="2ce58-118">Required element.</span></span><br /><br /> <span data-ttu-id="2ce58-119">Definiuje obiekty .NET, ustawionych w zaznaczeniu.</span><span class="sxs-lookup"><span data-stu-id="2ce58-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2ce58-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2ce58-120">Parent Elements</span></span>

|<span data-ttu-id="2ce58-121">Element</span><span class="sxs-lookup"><span data-stu-id="2ce58-121">Element</span></span>|<span data-ttu-id="2ce58-122">Opis</span><span class="sxs-lookup"><span data-stu-id="2ce58-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ce58-123">Format elementu SelectionSets</span><span class="sxs-lookup"><span data-stu-id="2ce58-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="2ce58-124">Definiuje typowe rodzaje obiektów platformy .NET, które mogą być używane przez wszystkie widoki formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="2ce58-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2ce58-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ce58-125">Remarks</span></span>

<span data-ttu-id="2ce58-126">Można użyć zestawów zaznaczenie, gdy masz zestaw powiązanych obiektów, które odwołują się za pomocą jednej nazwy, takiego jak zestaw obiektów, które są powiązane z dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="2ce58-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="2ce58-127">Podczas definiowania widoków, można określić zestaw obiektów przy użyciu nazwy wybór zestawu, zamiast wymieniać wszystkich obiektów w ramach każdego widoku.</span><span class="sxs-lookup"><span data-stu-id="2ce58-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="2ce58-128">Wspólne wybór zestawy są określane przez ich nazwy, podczas definiowania widoków formatowania pliku lub w definicjach widoków.</span><span class="sxs-lookup"><span data-stu-id="2ce58-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="2ce58-129">W takich przypadkach `SelectionSetName` element podrzędny elementu `ViewSelectedBy` i `EntrySelectedBy` elementy określa zestaw, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="2ce58-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="2ce58-130">Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2ce58-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="2ce58-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ce58-131">Example</span></span>

<span data-ttu-id="2ce58-132">W poniższym przykładzie przedstawiono `SelectionSet` element, który definiuje cztery typy .NET.</span><span class="sxs-lookup"><span data-stu-id="2ce58-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="2ce58-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ce58-133">See Also</span></span>

[<span data-ttu-id="2ce58-134">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="2ce58-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2ce58-135">Nazwa elementu SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="2ce58-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="2ce58-136">Element SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="2ce58-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="2ce58-137">Typy elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="2ce58-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="2ce58-138">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="2ce58-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
