---
title: Element SelectionSetName EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075566"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c4a87-102">SelectionSetName, element — EntrySelectedBy, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="c4a87-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c4a87-103">Określa zestaw obiektów platformy .NET dla wpisu listy.</span><span class="sxs-lookup"><span data-stu-id="c4a87-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="c4a87-104">Nie ma żadnego limitu liczby zestawów wybór, które można określić dla wpisu.</span><span class="sxs-lookup"><span data-stu-id="c4a87-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="c4a87-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionSetName ListEntry (Format) EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c4a87-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4a87-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4a87-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4a87-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c4a87-107">Attributes and Elements</span></span>

<span data-ttu-id="c4a87-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="c4a87-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4a87-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c4a87-109">Attributes</span></span>

<span data-ttu-id="c4a87-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="c4a87-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4a87-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c4a87-111">Child Elements</span></span>

<span data-ttu-id="c4a87-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="c4a87-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c4a87-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c4a87-113">Parent Elements</span></span>

|<span data-ttu-id="c4a87-114">Element</span><span class="sxs-lookup"><span data-stu-id="c4a87-114">Element</span></span>|<span data-ttu-id="c4a87-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c4a87-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4a87-116">Element EntrySelectedBy ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c4a87-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c4a87-117">Definiuje typy .NET, korzystające z tego wpisu listy lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="c4a87-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c4a87-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="c4a87-118">Text Value</span></span>

<span data-ttu-id="c4a87-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="c4a87-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4a87-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4a87-120">Remarks</span></span>

<span data-ttu-id="c4a87-121">Każdy wpis na liście musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="c4a87-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c4a87-122">Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="c4a87-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="c4a87-123">Na przykład można utworzyć widoku tabeli i widok listy, aby uzyskać ten sam zestaw obiektów.</span><span class="sxs-lookup"><span data-stu-id="c4a87-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="c4a87-124">Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia obiektów w celu wyświetlenia](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c4a87-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c4a87-125">Aby uzyskać więcej informacji o składnikach w widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c4a87-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c4a87-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4a87-126">Example</span></span>

<span data-ttu-id="c4a87-127">Poniższy przykład pokazuje, jak określić wejścia widok listy wyboru.</span><span class="sxs-lookup"><span data-stu-id="c4a87-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="c4a87-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4a87-128">See Also</span></span>

[<span data-ttu-id="c4a87-129">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="c4a87-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c4a87-130">Element EntrySelectedBy ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c4a87-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c4a87-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="c4a87-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
