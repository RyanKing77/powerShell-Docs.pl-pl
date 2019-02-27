---
title: Typy elementu SelectionSet (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851275"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="06f6d-102">Types, element — SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="06f6d-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="06f6d-103">Definiuje obiekty .NET, ustawionych w zaznaczeniu.</span><span class="sxs-lookup"><span data-stu-id="06f6d-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="06f6d-104">Element SelectionSet SelectionSets — Element (w formacie) — Element (w formacie) konfiguracji (Format) typy elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="06f6d-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06f6d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="06f6d-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="06f6d-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06f6d-106">Attributes and Elements</span></span>

<span data-ttu-id="06f6d-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Types` elementu.</span><span class="sxs-lookup"><span data-stu-id="06f6d-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="06f6d-108">Musi istnieć co najmniej jeden element podrzędny, ale nie ma żadnego limitu maksymalnej liczby elementów podrzędnych, które mogą zostać dodane.</span><span class="sxs-lookup"><span data-stu-id="06f6d-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="06f6d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06f6d-109">Attributes</span></span>

<span data-ttu-id="06f6d-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="06f6d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06f6d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06f6d-111">Child Elements</span></span>

|<span data-ttu-id="06f6d-112">Element</span><span class="sxs-lookup"><span data-stu-id="06f6d-112">Element</span></span>|<span data-ttu-id="06f6d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="06f6d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06f6d-114">Element TypeName typów (Format)</span><span class="sxs-lookup"><span data-stu-id="06f6d-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="06f6d-115">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="06f6d-115">Required element.</span></span><br /><br /> <span data-ttu-id="06f6d-116">Określa obiekt .NET, który należy do zestawu zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="06f6d-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06f6d-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06f6d-117">Parent Elements</span></span>

|<span data-ttu-id="06f6d-118">Element</span><span class="sxs-lookup"><span data-stu-id="06f6d-118">Element</span></span>|<span data-ttu-id="06f6d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="06f6d-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06f6d-120">Element SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="06f6d-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="06f6d-121">Definiuje zestaw obiektów platformy .NET, które mogą być przywoływane przez nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="06f6d-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06f6d-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06f6d-122">Remarks</span></span>

<span data-ttu-id="06f6d-123">Obiekty zdefiniowane przez ten element tworzą zbiór, który może służyć przez widok, zgodnie z definicją widoku (widoki mogą mieć wiele definicji), lub podczas określania warunku zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="06f6d-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="06f6d-124">Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="06f6d-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="06f6d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="06f6d-125">Example</span></span>

<span data-ttu-id="06f6d-126">W tym przykładzie `SelectionSet` element, który definiuje cztery typy .NET.</span><span class="sxs-lookup"><span data-stu-id="06f6d-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="06f6d-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06f6d-127">See Also</span></span>

[<span data-ttu-id="06f6d-128">Definiowanie zestawów obiektów</span><span class="sxs-lookup"><span data-stu-id="06f6d-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="06f6d-129">Element SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="06f6d-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="06f6d-130">Element TypeName typów (Format)</span><span class="sxs-lookup"><span data-stu-id="06f6d-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="06f6d-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="06f6d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
