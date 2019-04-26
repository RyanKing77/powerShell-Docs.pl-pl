---
title: Element SelectionSetName EntrySelectedBy dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063925"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a79ce-102">SelectionSetName, element — EntrySelectedBy, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="a79ce-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a79ce-103">Określa, że zestaw .NET typy użycia tego wpisu w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="a79ce-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="a79ce-104">Nie ma żadnego limitu liczby zestawów wybór, które można określić dla wpisu.</span><span class="sxs-lookup"><span data-stu-id="a79ce-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="a79ce-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) EntrySelectedBy — Element (Format) SelectionSetName Element konfiguracji dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a79ce-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a79ce-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a79ce-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a79ce-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a79ce-107">Attributes and Elements</span></span>

<span data-ttu-id="a79ce-108">Poniżej opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a79ce-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a79ce-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a79ce-109">Attributes</span></span>

<span data-ttu-id="a79ce-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="a79ce-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a79ce-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a79ce-111">Child Elements</span></span>

<span data-ttu-id="a79ce-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="a79ce-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a79ce-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a79ce-113">Parent Elements</span></span>

|<span data-ttu-id="a79ce-114">Element</span><span class="sxs-lookup"><span data-stu-id="a79ce-114">Element</span></span>|<span data-ttu-id="a79ce-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a79ce-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a79ce-116">Element EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a79ce-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="a79ce-117">Definiuje typy .NET, korzystające z tego wpisu lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="a79ce-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a79ce-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="a79ce-118">Text Value</span></span>

<span data-ttu-id="a79ce-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="a79ce-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a79ce-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a79ce-120">Remarks</span></span>

<span data-ttu-id="a79ce-121">Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="a79ce-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="a79ce-122">Na przykład można utworzyć widoku tabeli i widok listy, aby uzyskać ten sam zestaw obiektów.</span><span class="sxs-lookup"><span data-stu-id="a79ce-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="a79ce-123">Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia obiektów w celu wyświetlenia](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a79ce-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a79ce-124">Jeśli określisz zaznaczenia, ustaw dla wpisu, nie można określić nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="a79ce-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="a79ce-125">Aby uzyskać więcej informacji na temat sposobu określania typu .NET, zobacz [TypeName Element dla EntrySelectedBy dla TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="a79ce-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="a79ce-126">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a79ce-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a79ce-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a79ce-127">See Also</span></span>

[<span data-ttu-id="a79ce-128">Element EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a79ce-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="a79ce-129">Definiowanie zestawów obiektów w celu wyświetlenia</span><span class="sxs-lookup"><span data-stu-id="a79ce-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a79ce-130">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="a79ce-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a79ce-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="a79ce-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
