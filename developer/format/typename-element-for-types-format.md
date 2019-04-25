---
title: Element TypeName dla typów (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083794"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="04dbd-102">TypeName, element — Types (format)</span><span class="sxs-lookup"><span data-stu-id="04dbd-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="04dbd-103">Określa typ architektury .NET, obiektu, który należy do zestawu zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="04dbd-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="04dbd-104">Element SelectionSet SelectionSets — Element (w formacie) — Element (w formacie) konfiguracji (Format) typy elementu TypeName elementu (w formacie) typy (Format)</span><span class="sxs-lookup"><span data-stu-id="04dbd-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04dbd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="04dbd-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04dbd-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="04dbd-106">Attributes and Elements</span></span>

<span data-ttu-id="04dbd-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="04dbd-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="04dbd-108">Co najmniej jeden `TypeName` element musi być uwzględniony w zestawie zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="04dbd-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="04dbd-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="04dbd-109">Attributes</span></span>

<span data-ttu-id="04dbd-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="04dbd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04dbd-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="04dbd-111">Child Elements</span></span>

<span data-ttu-id="04dbd-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="04dbd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="04dbd-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="04dbd-113">Parent Elements</span></span>

|<span data-ttu-id="04dbd-114">Element</span><span class="sxs-lookup"><span data-stu-id="04dbd-114">Element</span></span>|<span data-ttu-id="04dbd-115">Opis</span><span class="sxs-lookup"><span data-stu-id="04dbd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04dbd-116">Typy elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="04dbd-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="04dbd-117">Definiuje obiekty .NET, ustawionych w zaznaczeniu.</span><span class="sxs-lookup"><span data-stu-id="04dbd-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="04dbd-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="04dbd-118">Text Value</span></span>

<span data-ttu-id="04dbd-119">Określ w pełni kwalifikowana nazwa typ architektury .NET.</span><span class="sxs-lookup"><span data-stu-id="04dbd-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="04dbd-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04dbd-120">Remarks</span></span>

<span data-ttu-id="04dbd-121">Można użyć zestawów zaznaczenie, gdy masz zestaw powiązanych obiektów, które odwołują się za pomocą jednej nazwy, takiego jak zestaw obiektów, które są powiązane z dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="04dbd-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="04dbd-122">Podczas definiowania widoków, można określić zestaw obiektów przy użyciu nazwy wybór zestawu, zamiast wymieniać wszystkich obiektów w ramach każdego widoku.</span><span class="sxs-lookup"><span data-stu-id="04dbd-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="04dbd-123">Wspólne wybór zestawy są określane przez ich nazwy, podczas definiowania widoków formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="04dbd-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="04dbd-124">W takich przypadkach `SelectionSetName` element podrzędny elementu `ViewSelectedBy` elementu widoku określa zestaw.</span><span class="sxs-lookup"><span data-stu-id="04dbd-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="04dbd-125">Jednakże wpisy widoku można również określić zestaw zaznaczenia dotyczy tylko ten wpis z widoku.</span><span class="sxs-lookup"><span data-stu-id="04dbd-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="04dbd-126">Aby uzyskać więcej informacji na temat zestawów wybór zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="04dbd-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="04dbd-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="04dbd-127">Example</span></span>

<span data-ttu-id="04dbd-128">W poniższym przykładzie przedstawiono `SelectionSet` element, który definiuje cztery typy .NET.</span><span class="sxs-lookup"><span data-stu-id="04dbd-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="04dbd-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04dbd-129">See Also</span></span>

[<span data-ttu-id="04dbd-130">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="04dbd-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="04dbd-131">Element SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="04dbd-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="04dbd-132">Element SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="04dbd-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="04dbd-133">Typy elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="04dbd-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="04dbd-134">Pisanie programu Windows PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="04dbd-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
