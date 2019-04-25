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
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075396"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="16fb4-102">TableColumnItems, element — TableRowEntry, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="16fb4-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="16fb4-103">Definiuje właściwości lub skryptów, których wartości są wyświetlane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="16fb4-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="16fb4-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries Element konfiguracji elementu TableRowEntry tablecontrol — (w formacie) TableRowEntries dla tablecontrol — (w formacie) Element TableColumnItems TableControlEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="16fb4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="16fb4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="16fb4-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16fb4-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="16fb4-106">Attributes and Elements</span></span>

<span data-ttu-id="16fb4-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableColumnItems` elementu.</span><span class="sxs-lookup"><span data-stu-id="16fb4-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="16fb4-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="16fb4-108">Attributes</span></span>

<span data-ttu-id="16fb4-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="16fb4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="16fb4-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="16fb4-110">Child Elements</span></span>

|<span data-ttu-id="16fb4-111">Element</span><span class="sxs-lookup"><span data-stu-id="16fb4-111">Element</span></span>|<span data-ttu-id="16fb4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="16fb4-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16fb4-113">Element TableColumnItem TableColumnItems dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="16fb4-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="16fb4-114">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="16fb4-114">Required element.</span></span><br /><br /> <span data-ttu-id="16fb4-115">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="16fb4-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="16fb4-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="16fb4-116">Parent Elements</span></span>

|<span data-ttu-id="16fb4-117">Element</span><span class="sxs-lookup"><span data-stu-id="16fb4-117">Element</span></span>|<span data-ttu-id="16fb4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="16fb4-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16fb4-119">Element TableRowEntry TableRowEntries dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="16fb4-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="16fb4-120">Definiuje dane, które są wyświetlane w wierszu tabeli.</span><span class="sxs-lookup"><span data-stu-id="16fb4-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="16fb4-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16fb4-121">Remarks</span></span>

<span data-ttu-id="16fb4-122">A `TableColumnItem` element jest wymagany dla każdej kolumny wiersza.</span><span class="sxs-lookup"><span data-stu-id="16fb4-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="16fb4-123">Pierwszy wpis jest wyświetlany w pierwszej kolumnie, drugi wpis w drugiej kolumnie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="16fb4-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="16fb4-124">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="16fb4-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="16fb4-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="16fb4-125">Example</span></span>

<span data-ttu-id="16fb4-126">W poniższym przykładzie przedstawiono `TableColumnItems` element, który definiuje trzy właściwości [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="16fb4-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="16fb4-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16fb4-127">See Also</span></span>

[<span data-ttu-id="16fb4-128">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="16fb4-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="16fb4-129">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="16fb4-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="16fb4-130">Element TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="16fb4-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="16fb4-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="16fb4-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
