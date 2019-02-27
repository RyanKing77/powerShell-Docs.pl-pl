---
title: Element TableHeaders (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847425"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="9a793-102">TableHeaders, element (format)</span><span class="sxs-lookup"><span data-stu-id="9a793-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="9a793-103">Określa nagłówki kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="9a793-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="9a793-104">Element ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (w formacie) TableHeaders elementu tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9a793-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a793-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a793-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a793-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9a793-106">Attributes and Elements</span></span>

<span data-ttu-id="9a793-107">W następujących sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `TableHeaders` elementu.</span><span class="sxs-lookup"><span data-stu-id="9a793-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="9a793-108">Musi to być element podrzędny dla każdej właściwości obiektu, który ma być wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="9a793-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="9a793-109">Informacje nagłówka kolumny są wyświetlane w kolejności, że elementy podrzędne są określone.</span><span class="sxs-lookup"><span data-stu-id="9a793-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a793-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9a793-110">Attributes</span></span>

<span data-ttu-id="9a793-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="9a793-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a793-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9a793-112">Child Elements</span></span>

|<span data-ttu-id="9a793-113">Element</span><span class="sxs-lookup"><span data-stu-id="9a793-113">Element</span></span>|<span data-ttu-id="9a793-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9a793-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a793-115">Element TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="9a793-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="9a793-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9a793-116">Optional element.</span></span><br /><br /> <span data-ttu-id="9a793-117">Definiuje etykietę, szerokości i wyrównania danych dla kolumny widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="9a793-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9a793-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9a793-118">Parent Elements</span></span>

|<span data-ttu-id="9a793-119">Element</span><span class="sxs-lookup"><span data-stu-id="9a793-119">Element</span></span>|<span data-ttu-id="9a793-120">Opis</span><span class="sxs-lookup"><span data-stu-id="9a793-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a793-121">Tablecontrol — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9a793-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="9a793-122">Definiuje format tabeli w celu wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="9a793-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9a793-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a793-123">Remarks</span></span>

<span data-ttu-id="9a793-124">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9a793-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9a793-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a793-125">Example</span></span>

<span data-ttu-id="9a793-126">W tym przykładzie `TableHeaders` element, który definiuje dwa nagłówki kolumn.</span><span class="sxs-lookup"><span data-stu-id="9a793-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="9a793-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a793-127">See Also</span></span>

[<span data-ttu-id="9a793-128">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="9a793-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9a793-129">Element TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="9a793-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="9a793-130">Tablecontrol — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9a793-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="9a793-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9a793-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
