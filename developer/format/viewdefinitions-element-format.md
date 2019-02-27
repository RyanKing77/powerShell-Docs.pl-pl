---
title: Element ViewDefinitions (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851072"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="80490-102">ViewDefinitions, element (format)</span><span class="sxs-lookup"><span data-stu-id="80490-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="80490-103">Zawiera definicje widoków, używany do wyświetlania obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="80490-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="80490-104">Widoki te można wyświetlić właściwości i wartości obiektu w skrypcie w formacie tabeli, format listy, formacie szerokim i format formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="80490-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="80490-105">Element ViewDefinitions (Format XML) (w formacie) elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="80490-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="80490-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="80490-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80490-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80490-107">Attributes and Elements</span></span>

<span data-ttu-id="80490-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ViewDefinitions` elementu.</span><span class="sxs-lookup"><span data-stu-id="80490-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="80490-109">Nie ma żadnego limitu liczby widoków, które mogą być definiowane w pliku formatowania i mogą być dodawane w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="80490-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="80490-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80490-110">Attributes</span></span>

<span data-ttu-id="80490-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="80490-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80490-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80490-112">Child Elements</span></span>

|<span data-ttu-id="80490-113">Element</span><span class="sxs-lookup"><span data-stu-id="80490-113">Element</span></span>|<span data-ttu-id="80490-114">Opis</span><span class="sxs-lookup"><span data-stu-id="80490-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80490-115">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="80490-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="80490-116">Określa widok, który służy do wyświetlania jeden lub więcej obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="80490-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80490-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80490-117">Parent Elements</span></span>

|<span data-ttu-id="80490-118">Element</span><span class="sxs-lookup"><span data-stu-id="80490-118">Element</span></span>|<span data-ttu-id="80490-119">Opis</span><span class="sxs-lookup"><span data-stu-id="80490-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80490-120">Element konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="80490-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="80490-121">Reprezentuje element najwyższego poziomu w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="80490-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80490-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80490-122">Remarks</span></span>

<span data-ttu-id="80490-123">Aby uzyskać więcej informacji na temat składników różne typy widoków zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="80490-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="80490-124">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="80490-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="80490-125">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="80490-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="80490-126">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="80490-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="80490-127">Formanty niestandardowe</span><span class="sxs-lookup"><span data-stu-id="80490-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="80490-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="80490-128">Example</span></span>

<span data-ttu-id="80490-129">W tym przykładzie `ViewDefinitions` element, który zawiera elementy nadrzędne w widoku tabeli i widok listy.</span><span class="sxs-lookup"><span data-stu-id="80490-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="80490-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80490-130">See Also</span></span>

[<span data-ttu-id="80490-131">Element konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="80490-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="80490-132">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="80490-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="80490-133">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="80490-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="80490-134">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="80490-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="80490-135">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="80490-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="80490-136">Formanty niestandardowe</span><span class="sxs-lookup"><span data-stu-id="80490-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="80490-137">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="80490-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
