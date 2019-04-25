---
title: Element ViewSelectedBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083828"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="7b6e3-102">ViewSelectedBy, element (format)</span><span class="sxs-lookup"><span data-stu-id="7b6e3-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="7b6e3-103">Definiuje obiekty .NET, które są wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="7b6e3-104">Każdy widok należy określić co najmniej jednego obiektu .NET.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="7b6e3-105">Element ViewDefinitions (Format) widok elementów (w formacie) ViewSelectedBy elemencie (Format)</span><span class="sxs-lookup"><span data-stu-id="7b6e3-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b6e3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b6e3-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b6e3-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7b6e3-107">Attributes and Elements</span></span>

<span data-ttu-id="7b6e3-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ViewSelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="7b6e3-109">Ten element musi zawierać co najmniej jeden `TypeName` lub `SelectionSetName` elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="7b6e3-110">Nie ma żadnego limitu liczby elementów podrzędnych, które można określić ani nie jest ważna ich kolejność.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b6e3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7b6e3-111">Attributes</span></span>

<span data-ttu-id="7b6e3-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b6e3-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7b6e3-113">Child Elements</span></span>

|<span data-ttu-id="7b6e3-114">Element</span><span class="sxs-lookup"><span data-stu-id="7b6e3-114">Element</span></span>|<span data-ttu-id="7b6e3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7b6e3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b6e3-116">Element TypeName dla ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b6e3-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="7b6e3-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7b6e3-118">Określa obiekt .NET, który jest wyświetlany w widoku.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="7b6e3-119">Element SelectionSetName ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b6e3-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="7b6e3-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7b6e3-121">Określa zestaw obiektów platformy .NET, które są wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7b6e3-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7b6e3-122">Parent Elements</span></span>

|<span data-ttu-id="7b6e3-123">Element</span><span class="sxs-lookup"><span data-stu-id="7b6e3-123">Element</span></span>|<span data-ttu-id="7b6e3-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7b6e3-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b6e3-125">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7b6e3-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="7b6e3-126">Określa widok, który zawiera jeden lub więcej obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7b6e3-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b6e3-127">Remarks</span></span>

<span data-ttu-id="7b6e3-128">Aby uzyskać więcej informacji o sposobie korzystania z tego elementu w różnych widokach, zobacz [składników widok tabeli](./creating-a-table-view.md), [składniki widok listy](./creating-a-list-view.md), [szeroki składniki widoków](./creating-a-wide-view.md)i [Kontrolek niestandardowych składników](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7b6e3-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="7b6e3-129">`SelectionSetName` Element jest używany podczas formatowania plik definiuje zestaw obiektów, które są wyświetlane przez wiele widoków.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="7b6e3-130">Aby uzyskać więcej informacji o wybór zestawów są zdefiniowane i odwołania, zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7b6e3-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="7b6e3-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b6e3-131">Example</span></span>

<span data-ttu-id="7b6e3-132">Poniższy przykład pokazuje, jak określić [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiekt widoku listy.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="7b6e3-133">Ten sam schemat jest używany dla tabeli, szeroką i niestandardowe widoki.</span><span class="sxs-lookup"><span data-stu-id="7b6e3-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="7b6e3-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b6e3-134">See Also</span></span>

[<span data-ttu-id="7b6e3-135">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="7b6e3-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7b6e3-136">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="7b6e3-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7b6e3-137">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="7b6e3-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7b6e3-138">Tworzenie niestandardowych formantów</span><span class="sxs-lookup"><span data-stu-id="7b6e3-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="7b6e3-139">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="7b6e3-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7b6e3-140">Element SelectionSetName ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b6e3-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="7b6e3-141">Element TypeName (Format)</span><span class="sxs-lookup"><span data-stu-id="7b6e3-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="7b6e3-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="7b6e3-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
