---
title: Element TableColumnItems TableRowEntry dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849224"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="5cb03-102">TableColumnItems, element — TableRowEntry, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="5cb03-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="5cb03-103">Definiuje właściwości lub skryptów, których wartości są wyświetlane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="5cb03-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="5cb03-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries Element konfiguracji elementu TableRowEntry tablecontrol — (w formacie) TableRowEntries dla tablecontrol — (w formacie) Element TableColumnItems TableControlEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="5cb03-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5cb03-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cb03-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5cb03-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5cb03-106">Attributes and Elements</span></span>

<span data-ttu-id="5cb03-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableColumnItems` elementu.</span><span class="sxs-lookup"><span data-stu-id="5cb03-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5cb03-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5cb03-108">Attributes</span></span>

<span data-ttu-id="5cb03-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="5cb03-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5cb03-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5cb03-110">Child Elements</span></span>

|<span data-ttu-id="5cb03-111">Element</span><span class="sxs-lookup"><span data-stu-id="5cb03-111">Element</span></span>|<span data-ttu-id="5cb03-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5cb03-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5cb03-113">Element TableColumnItem TableColumnItems dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="5cb03-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="5cb03-114">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="5cb03-114">Required element.</span></span><br /><br /> <span data-ttu-id="5cb03-115">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="5cb03-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5cb03-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5cb03-116">Parent Elements</span></span>

|<span data-ttu-id="5cb03-117">Element</span><span class="sxs-lookup"><span data-stu-id="5cb03-117">Element</span></span>|<span data-ttu-id="5cb03-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5cb03-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5cb03-119">Element TableRowEntry TableRowEntries dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="5cb03-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="5cb03-120">Definiuje dane, które są wyświetlane w wierszu tabeli.</span><span class="sxs-lookup"><span data-stu-id="5cb03-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5cb03-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5cb03-121">Remarks</span></span>

<span data-ttu-id="5cb03-122">A `TableColumnItem` element jest wymagany dla każdej kolumny wiersza.</span><span class="sxs-lookup"><span data-stu-id="5cb03-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="5cb03-123">Pierwszy wpis jest wyświetlany w pierwszej kolumnie, drugi wpis w drugiej kolumnie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="5cb03-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="5cb03-124">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="5cb03-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5cb03-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cb03-125">Example</span></span>

<span data-ttu-id="5cb03-126">W poniższym przykładzie przedstawiono `TableColumnItems` element, który definiuje trzy właściwości [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="5cb03-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="5cb03-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cb03-127">See Also</span></span>

[<span data-ttu-id="5cb03-128">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="5cb03-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5cb03-129">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="5cb03-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="5cb03-130">Element TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5cb03-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="5cb03-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="5cb03-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
