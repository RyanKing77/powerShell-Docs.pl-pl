---
title: Element TableRowEntry TableRowEntroes dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 001d46debde61f928c338b2f68112fb201f96216
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845122"
---
# <a name="tablerowentry-element-for-tablerowentroes-for-tablecontrol-format"></a><span data-ttu-id="cc451-102">TableRowEntry, element — TableRowEntroes, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="cc451-102">TableRowEntry Element for TableRowEntroes for TableControl (Format)</span></span>

<span data-ttu-id="cc451-103">Definiuje dane, które są wyświetlane w wierszu tabeli.</span><span class="sxs-lookup"><span data-stu-id="cc451-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="cc451-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries Element konfiguracji elementu TableRowEntry tablecontrol — (w formacie) TableRowEntries dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="cc451-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc451-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc451-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc451-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cc451-106">Attributes and Elements</span></span>

<span data-ttu-id="cc451-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableRowEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="cc451-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc451-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cc451-108">Attributes</span></span>

<span data-ttu-id="cc451-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="cc451-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc451-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cc451-110">Child Elements</span></span>

|<span data-ttu-id="cc451-111">Element</span><span class="sxs-lookup"><span data-stu-id="cc451-111">Element</span></span>|<span data-ttu-id="cc451-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cc451-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc451-113">Element EntrySelectedBy TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="cc451-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="cc451-114">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="cc451-114">Required element.</span></span><br /><br /> <span data-ttu-id="cc451-115">Definiuje obiekty, których wartości właściwości są wyświetlane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="cc451-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="cc451-116">Element TableColumnItems TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="cc451-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="cc451-117">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="cc451-117">Required element.</span></span><br /><br /> <span data-ttu-id="cc451-118">Definiuje właściwości lub skryptów, których wartości są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="cc451-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="cc451-119">OPAKOWYWANIE Element do TableRowEntry dla TableCntrol (Format)</span><span class="sxs-lookup"><span data-stu-id="cc451-119">Wrap Element for TableRowEntry for TableCntrol (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)|<span data-ttu-id="cc451-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cc451-120">Optional element.</span></span><br /><br /> <span data-ttu-id="cc451-121">Określa, czy tekst przekraczający szerokość kolumny jest wyświetlane w następnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="cc451-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc451-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cc451-122">Parent Elements</span></span>

|<span data-ttu-id="cc451-123">Element</span><span class="sxs-lookup"><span data-stu-id="cc451-123">Element</span></span>|<span data-ttu-id="cc451-124">Opis</span><span class="sxs-lookup"><span data-stu-id="cc451-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc451-125">Element TableRowEntries tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="cc451-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="cc451-126">Definiuje wiersze w tabeli.</span><span class="sxs-lookup"><span data-stu-id="cc451-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc451-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc451-127">Remarks</span></span>

<span data-ttu-id="cc451-128">Jeden `TableColumnItems` elementu i jeden `EntrySelectedBy` element musi być określona.</span><span class="sxs-lookup"><span data-stu-id="cc451-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="cc451-129">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="cc451-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cc451-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc451-130">Example</span></span>

<span data-ttu-id="cc451-131">W poniższym przykładzie przedstawiono `TableRowEntry` element, który definiuje wiersza, który wyświetla wartości właściwości dwóch [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc451-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cc451-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc451-132">See Also</span></span>

[<span data-ttu-id="cc451-133">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="cc451-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cc451-134">Element EntrySelectedBy TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="cc451-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="cc451-135">Element TableColumnItems TableRowEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="cc451-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="cc451-136">Element TableRowEntries tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="cc451-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="cc451-137">Element TableRowEntry TableRowEntries dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="cc451-137">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="cc451-138">OPAKOWYWANIE Element do TableRowEntry dla TableCntrol (Format)</span><span class="sxs-lookup"><span data-stu-id="cc451-138">Wrap Element for TableRowEntry for TableCntrol (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)

[<span data-ttu-id="cc451-139">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="cc451-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
