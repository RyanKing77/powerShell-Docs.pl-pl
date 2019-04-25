---
title: Element TableRowEntries tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075498"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="f2725-102">TableRowEntries, element — TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="f2725-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="f2725-103">Definiuje wiersze w tabeli.</span><span class="sxs-lookup"><span data-stu-id="f2725-103">Defines the rows of the table.</span></span>

<span data-ttu-id="f2725-104">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (w formacie) TableRowEntries Element konfiguracji dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2725-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2725-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2725-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2725-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f2725-106">Attributes and Elements</span></span>

<span data-ttu-id="f2725-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableRowEntries` elementu.</span><span class="sxs-lookup"><span data-stu-id="f2725-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2725-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f2725-108">Attributes</span></span>

<span data-ttu-id="f2725-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="f2725-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2725-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f2725-110">Child Elements</span></span>

|<span data-ttu-id="f2725-111">Element</span><span class="sxs-lookup"><span data-stu-id="f2725-111">Element</span></span>|<span data-ttu-id="f2725-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f2725-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2725-113">Element TableRowEntry TableRowEntries dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2725-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="f2725-114">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="f2725-114">Required element.</span></span><br /><br /> <span data-ttu-id="f2725-115">Definiuje dane, które są wyświetlane w wierszu tabeli.</span><span class="sxs-lookup"><span data-stu-id="f2725-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f2725-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f2725-116">Parent Elements</span></span>

|<span data-ttu-id="f2725-117">Element</span><span class="sxs-lookup"><span data-stu-id="f2725-117">Element</span></span>|<span data-ttu-id="f2725-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f2725-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2725-119">Tablecontrol — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f2725-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="f2725-120">Definiuje format tabeli w celu wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="f2725-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f2725-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2725-121">Remarks</span></span>

<span data-ttu-id="f2725-122">Należy określić co najmniej jedną `TableRowEntry` elementów do widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="f2725-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="f2725-123">Nie ma żadnego limitu maksymalnej liczby `TableRowEntry` elementy, które można dodać ani nie jest ważna ich kolejność.</span><span class="sxs-lookup"><span data-stu-id="f2725-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="f2725-124">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f2725-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f2725-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2725-125">Example</span></span>

<span data-ttu-id="f2725-126">W poniższym przykładzie przedstawiono `TableRowEntries` element, który definiuje wiersza, który wyświetla wartości właściwości dwóch [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="f2725-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="f2725-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2725-127">See Also</span></span>

[<span data-ttu-id="f2725-128">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="f2725-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f2725-129">Tablecontrol — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f2725-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="f2725-130">Element TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f2725-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="f2725-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="f2725-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
