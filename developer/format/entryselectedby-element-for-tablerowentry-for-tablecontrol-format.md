---
title: Element EntrySelectedBy TableRowEntry dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066162"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="e0355-102">EntrySelectedBy, element — TableRowEntry, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="e0355-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="e0355-103">Definiuje typy .NET używających tej definicji widoku tabeli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="e0355-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="e0355-104">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries — Element (Format) TableRowEntry — Element (Format) EntrySelectedBy Element konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e0355-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0355-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0355-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0355-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e0355-106">Attributes and Elements</span></span>

<span data-ttu-id="e0355-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="e0355-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0355-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e0355-108">Attributes</span></span>

<span data-ttu-id="e0355-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="e0355-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0355-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e0355-110">Child Elements</span></span>

|<span data-ttu-id="e0355-111">Element</span><span class="sxs-lookup"><span data-stu-id="e0355-111">Element</span></span>|<span data-ttu-id="e0355-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e0355-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0355-113">Element SelectionCondition EntrySelectedBy dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e0355-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e0355-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e0355-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e0355-115">Określa warunek, który musi istnieć dla tej definicji widoku tabeli ma być używany.</span><span class="sxs-lookup"><span data-stu-id="e0355-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="e0355-116">Element SelectionSetName EntrySelectedBy dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e0355-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e0355-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e0355-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e0355-118">Określa zestaw typów .NET, korzystających z tej definicji widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="e0355-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="e0355-119">Element TypeName dla EntrySelectedBy dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e0355-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e0355-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e0355-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e0355-121">Określa typ architektury .NET, która używa tej definicji widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="e0355-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0355-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e0355-122">Parent Elements</span></span>

|<span data-ttu-id="e0355-123">Element</span><span class="sxs-lookup"><span data-stu-id="e0355-123">Element</span></span>|<span data-ttu-id="e0355-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e0355-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0355-125">Element TableRowEntry tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e0355-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="e0355-126">Definiuje dane, które są wyświetlane w wierszu tabeli.</span><span class="sxs-lookup"><span data-stu-id="e0355-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0355-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0355-127">Remarks</span></span>

<span data-ttu-id="e0355-128">Należy określić co najmniej jeden typ, wybór zestawu lub warunek wyboru definicji widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="e0355-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="e0355-129">Jest nieograniczona maksymalną liczbę elementów podrzędnych, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="e0355-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="e0355-130">Wybór warunki są używane do definiowania warunek, który musi istnieć dla definicji, który ma być używany, na przykład jeśli obiekt ma określoną właściwość lub wartość określoną właściwość lub skrypt daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="e0355-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e0355-131">Aby uzyskać więcej informacji o warunkach wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e0355-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e0355-132">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e0355-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e0355-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0355-133">Example</span></span>

<span data-ttu-id="e0355-134">W poniższym przykładzie przedstawiono `TableRowEntry` element, który służy do wyświetlania właściwości [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="e0355-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="e0355-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0355-135">See Also</span></span>

[<span data-ttu-id="e0355-136">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="e0355-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e0355-137">Element SelectionCondition EntrySelectedBy dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e0355-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e0355-138">Element SelectionSetName EntrySelectedBy dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e0355-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e0355-139">Element TableRowEntry tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e0355-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="e0355-140">Element TypeName dla EntrySelectedBy dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="e0355-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e0355-141">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="e0355-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
