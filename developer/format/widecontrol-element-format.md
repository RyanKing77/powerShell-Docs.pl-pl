---
title: Element WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849490"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="63000-102">WideControl, element (format)</span><span class="sxs-lookup"><span data-stu-id="63000-102">WideControl Element (Format)</span></span>

<span data-ttu-id="63000-103">Definiuje całej (pojedyncza wartość) format listy dla widoku.</span><span class="sxs-lookup"><span data-stu-id="63000-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="63000-104">Ten widok przedstawia jedną właściwość wartość lub wartość skryptu dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="63000-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="63000-105">Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) WideControl elemencie (Format)</span><span class="sxs-lookup"><span data-stu-id="63000-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63000-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="63000-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63000-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="63000-107">Attributes and Elements</span></span>

<span data-ttu-id="63000-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `WideControl` elementu.</span><span class="sxs-lookup"><span data-stu-id="63000-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="63000-109">Nie można określić `AutoSize` i `ColumnNumber` elementy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="63000-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="63000-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="63000-110">Attributes</span></span>

<span data-ttu-id="63000-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="63000-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63000-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="63000-112">Child Elements</span></span>

|<span data-ttu-id="63000-113">Element</span><span class="sxs-lookup"><span data-stu-id="63000-113">Element</span></span>|<span data-ttu-id="63000-114">Opis</span><span class="sxs-lookup"><span data-stu-id="63000-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63000-115">Element AutoSize WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="63000-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="63000-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="63000-116">Optional element.</span></span><br /><br /> <span data-ttu-id="63000-117">Określa, czy rozmiar kolumny i liczba kolumn są dostosowywane na podstawie rozmiaru danych.</span><span class="sxs-lookup"><span data-stu-id="63000-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="63000-118">Element ColumnNumber WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="63000-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="63000-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="63000-119">Optional element.</span></span><br /><br /> <span data-ttu-id="63000-120">Określa liczbę kolumn wyświetlanych w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="63000-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="63000-121">Element WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="63000-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="63000-122">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="63000-122">Required element.</span></span><br /><br /> <span data-ttu-id="63000-123">Zawiera definicje szerokie.</span><span class="sxs-lookup"><span data-stu-id="63000-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="63000-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="63000-124">Parent Elements</span></span>

|<span data-ttu-id="63000-125">Element</span><span class="sxs-lookup"><span data-stu-id="63000-125">Element</span></span>|<span data-ttu-id="63000-126">Opis</span><span class="sxs-lookup"><span data-stu-id="63000-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63000-127">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="63000-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="63000-128">Określa widok, który służy do wyświetlania jeden lub więcej obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="63000-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63000-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63000-129">Remarks</span></span>

<span data-ttu-id="63000-130">Podczas definiowania szerokie, możesz dodać `AutoSize` element lub `ColumnNumber` , ale nie można dodać oba.</span><span class="sxs-lookup"><span data-stu-id="63000-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="63000-131">W większości przypadków tylko jedną definicję, jest wymagana dla każdego szerokie, ale użytkownik może mieć wielu definicji, jeśli chcesz wyświetlić różne obiekty platformy .NET przy użyciu tego samego widoku.</span><span class="sxs-lookup"><span data-stu-id="63000-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="63000-132">W takich przypadkach możesz podać definicję osobne dla każdego obiektu lub grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="63000-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="63000-133">Aby uzyskać więcej informacji na temat składników szerokie, zobacz [szeroki składniki widoków](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="63000-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="63000-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="63000-134">Example</span></span>

<span data-ttu-id="63000-135">W poniższym przykładzie przedstawiono `WideControl` element, który służy do wyświetlania właściwości [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="63000-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="63000-136">Aby uzyskać pełny przykład szerokie, zobacz [szerokie (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="63000-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63000-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63000-137">See Also</span></span>

[<span data-ttu-id="63000-138">Element AutoSize WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="63000-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="63000-139">Element ColumnNumber WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="63000-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="63000-140">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="63000-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="63000-141">Element WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="63000-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="63000-142">Szerokie (Basic)</span><span class="sxs-lookup"><span data-stu-id="63000-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="63000-143">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="63000-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="63000-144">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="63000-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
