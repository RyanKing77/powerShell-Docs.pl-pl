---
title: Nazwa elementu dla SelectionSet (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065159"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="34771-102">Name, element — SelectionSet (format)</span><span class="sxs-lookup"><span data-stu-id="34771-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="34771-103">Określa nazwę używaną do odwoływać się do zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="34771-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="34771-104">Konfiguracji elementu (w formacie) elementu SelectionSets (Format) elementu SelectionSet (Format) nazwa elementu SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="34771-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34771-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="34771-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34771-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34771-106">Attributes and Elements</span></span>

<span data-ttu-id="34771-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Name` elementu.</span><span class="sxs-lookup"><span data-stu-id="34771-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34771-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34771-108">Attributes</span></span>

<span data-ttu-id="34771-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="34771-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34771-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34771-110">Child Elements</span></span>

<span data-ttu-id="34771-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="34771-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34771-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34771-112">Parent Elements</span></span>

|<span data-ttu-id="34771-113">Element</span><span class="sxs-lookup"><span data-stu-id="34771-113">Element</span></span>|<span data-ttu-id="34771-114">Opis</span><span class="sxs-lookup"><span data-stu-id="34771-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34771-115">Element SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="34771-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="34771-116">Definiuje pojedynczy zestaw obiektów platformy .NET, które mogą być przywoływane przez nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="34771-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34771-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="34771-117">Text Value</span></span>

<span data-ttu-id="34771-118">Określ nazwę aby odwoływać się do zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="34771-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="34771-119">Istnieją żadne ograniczenia dotyczące znaków, które można użyć.</span><span class="sxs-lookup"><span data-stu-id="34771-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="34771-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34771-120">Remarks</span></span>

<span data-ttu-id="34771-121">Nazwa określona w tym miejscu jest używana w `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="34771-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="34771-122">Zbiór, który może służyć przez widok, zgodnie z definicją widoku (widoki mogą mieć wiele definicji), lub podczas określania warunku zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="34771-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="34771-123">Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="34771-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="34771-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="34771-124">Example</span></span>

<span data-ttu-id="34771-125">W tym przykładzie `SelectionSet` element, który definiuje cztery typy .NET.</span><span class="sxs-lookup"><span data-stu-id="34771-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="34771-126">Nazwa zestawu wyboru jest "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="34771-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34771-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34771-127">See Also</span></span>

[<span data-ttu-id="34771-128">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="34771-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="34771-129">Element SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="34771-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="34771-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="34771-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
