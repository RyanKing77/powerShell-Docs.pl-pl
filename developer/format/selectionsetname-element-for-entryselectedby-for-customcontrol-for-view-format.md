---
title: Element SelectionSetName EntrySelectedBy dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846130"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="15240-102">SelectionSetName, element — EntrySelectedBy, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="15240-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="15240-103">Określa zestaw obiektów platformy .NET dla wpisu listy.</span><span class="sxs-lookup"><span data-stu-id="15240-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="15240-104">Nie ma żadnego limitu liczby zestawów wybór, które można określić dla wpisu.</span><span class="sxs-lookup"><span data-stu-id="15240-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="15240-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla EntrySelectedBy widoku (Format) Element CustomEntry widoku (Format) elementu SelectionSetName EntrySelectedBy dla CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15240-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15240-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="15240-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15240-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="15240-107">Attributes and Elements</span></span>

<span data-ttu-id="15240-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="15240-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15240-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="15240-109">Attributes</span></span>

<span data-ttu-id="15240-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="15240-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15240-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="15240-111">Child Elements</span></span>

<span data-ttu-id="15240-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="15240-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15240-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="15240-113">Parent Elements</span></span>

|<span data-ttu-id="15240-114">Element</span><span class="sxs-lookup"><span data-stu-id="15240-114">Element</span></span>|<span data-ttu-id="15240-115">Opis</span><span class="sxs-lookup"><span data-stu-id="15240-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15240-116">Element EntrySelectedBy CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="15240-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="15240-117">Definiuje typy .NET, korzystające z tego wpisu niestandardowych lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="15240-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="15240-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="15240-118">Text Value</span></span>

<span data-ttu-id="15240-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="15240-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="15240-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15240-120">Remarks</span></span>

<span data-ttu-id="15240-121">Każdy wpis formant niestandardowy musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="15240-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="15240-122">Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="15240-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="15240-123">Na przykład można utworzyć widoku tabeli i widok listy, aby uzyskać ten sam zestaw obiektów.</span><span class="sxs-lookup"><span data-stu-id="15240-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="15240-124">Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia wybór](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="15240-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="15240-125">Aby uzyskać więcej informacji o składnikach widoku kontrolki niestandardowej, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="15240-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15240-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15240-126">See Also</span></span>

[<span data-ttu-id="15240-127">Element EntrySelectedBy CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="15240-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="15240-128">Wyświetl formant niestandardowy</span><span class="sxs-lookup"><span data-stu-id="15240-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="15240-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="15240-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
