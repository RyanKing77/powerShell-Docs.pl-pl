---
title: Element TableRowEntry TableRowEntries dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075328"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="7852d-102">TableRowEntry, element — TableRowEntries, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="7852d-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="7852d-103">Definiuje dane, które są wyświetlane w wierszu tabeli.</span><span class="sxs-lookup"><span data-stu-id="7852d-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="7852d-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries Element konfiguracji elementu TableRowEntry tablecontrol — (w formacie) TableRowEntries dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7852d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7852d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7852d-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7852d-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7852d-106">Attributes and Elements</span></span>

<span data-ttu-id="7852d-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableRowEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="7852d-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7852d-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7852d-108">Attributes</span></span>

<span data-ttu-id="7852d-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="7852d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7852d-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7852d-110">Child Elements</span></span>

|<span data-ttu-id="7852d-111">Element</span><span class="sxs-lookup"><span data-stu-id="7852d-111">Element</span></span>|<span data-ttu-id="7852d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7852d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7852d-113">Element EntrySelectedBy TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7852d-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="7852d-114">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="7852d-114">Required element.</span></span><br /><br /> <span data-ttu-id="7852d-115">Definiuje obiekty, których wartości właściwości są wyświetlane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="7852d-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="7852d-116">Element TableColumnItems TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7852d-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="7852d-117">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="7852d-117">Required element.</span></span><br /><br /> <span data-ttu-id="7852d-118">Definiuje właściwości lub skryptów, których wartości są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="7852d-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="7852d-119">OPAKOWYWANIE Element do TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7852d-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="7852d-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7852d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7852d-121">Określa, czy tekst przekraczający szerokość kolumny jest wyświetlane w następnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="7852d-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7852d-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7852d-122">Parent Elements</span></span>

|<span data-ttu-id="7852d-123">Element</span><span class="sxs-lookup"><span data-stu-id="7852d-123">Element</span></span>|<span data-ttu-id="7852d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7852d-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7852d-125">Element TableRowEntries tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7852d-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="7852d-126">Definiuje wiersze w tabeli.</span><span class="sxs-lookup"><span data-stu-id="7852d-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7852d-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7852d-127">Remarks</span></span>

<span data-ttu-id="7852d-128">Jeden `TableColumnItems` elementu i jeden `EntrySelectedBy` element musi być określona.</span><span class="sxs-lookup"><span data-stu-id="7852d-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="7852d-129">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7852d-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7852d-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="7852d-130">Example</span></span>

<span data-ttu-id="7852d-131">W poniższym przykładzie przedstawiono `TableRowEntry` element, który definiuje wiersza, który wyświetla wartości właściwości dwóch [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="7852d-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="7852d-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7852d-132">See Also</span></span>

[<span data-ttu-id="7852d-133">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="7852d-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7852d-134">Element EntrySelectedBy TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7852d-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="7852d-135">Element TableColumnItems TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7852d-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="7852d-136">Element TableRowEntries tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7852d-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="7852d-137">OPAKOWYWANIE Element do TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7852d-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="7852d-138">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="7852d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
