---
title: Element TableColumnHeader (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848629"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="3561d-102">TableColumnHeader, element (format)</span><span class="sxs-lookup"><span data-stu-id="3561d-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="3561d-103">Definiuje etykietę, szerokość kolumny i wyrównanie etykiety w kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="3561d-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="3561d-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableHeaders Element konfiguracji elementu TableColumnHeader tablecontrol — (w formacie) TableHeaders dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="3561d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3561d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3561d-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3561d-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3561d-106">Attributes and Elements</span></span>

<span data-ttu-id="3561d-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableColumnHeader` elementu.</span><span class="sxs-lookup"><span data-stu-id="3561d-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3561d-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3561d-108">Attributes</span></span>

<span data-ttu-id="3561d-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="3561d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3561d-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3561d-110">Child Elements</span></span>

|<span data-ttu-id="3561d-111">Element</span><span class="sxs-lookup"><span data-stu-id="3561d-111">Element</span></span>|<span data-ttu-id="3561d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3561d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3561d-113">Element LABEL dla TableColumnHeader dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="3561d-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="3561d-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3561d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="3561d-115">Definiuje etykietę, która jest wyświetlana w górnej części kolumny.</span><span class="sxs-lookup"><span data-stu-id="3561d-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="3561d-116">Jeśli żadna etykieta nie zostanie określona, jest używana nazwa właściwości, którego wartość jest wyświetlana w wierszach.</span><span class="sxs-lookup"><span data-stu-id="3561d-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="3561d-117">Szerokość elementu TableColumnHeader dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="3561d-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="3561d-118">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="3561d-118">Required element.</span></span><br /><br /> <span data-ttu-id="3561d-119">Określa szerokość (w znakach) kolumny.</span><span class="sxs-lookup"><span data-stu-id="3561d-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="3561d-120">Wyrównanie elementu TableColumbnHeader dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="3561d-120">Alignment Element for TableColumbnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="3561d-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3561d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3561d-122">Określa, jak jest wyświetlana etykieta kolumny.</span><span class="sxs-lookup"><span data-stu-id="3561d-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="3561d-123">Jeśli określono bez wyrównania, etykieta jest wyrównany po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="3561d-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3561d-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3561d-124">Parent Elements</span></span>

|<span data-ttu-id="3561d-125">Element</span><span class="sxs-lookup"><span data-stu-id="3561d-125">Element</span></span>|<span data-ttu-id="3561d-126">Opis</span><span class="sxs-lookup"><span data-stu-id="3561d-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3561d-127">Element TableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="3561d-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="3561d-128">Definiuje kolumny widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="3561d-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3561d-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3561d-129">Remarks</span></span>

<span data-ttu-id="3561d-130">Określ nagłówek dla każdej kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="3561d-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="3561d-131">Kolumny są wyświetlane w kolejności, w którym `TableColumnHeader` elementy są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="3561d-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="3561d-132">Tabela musi mieć taką samą liczbę `TableColumnHeader` elementy jako `TableRowEntry` elementów.</span><span class="sxs-lookup"><span data-stu-id="3561d-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="3561d-133">Nagłówek kolumny definiuje sposób wyświetlania tekstu w górnej części tabeli.</span><span class="sxs-lookup"><span data-stu-id="3561d-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="3561d-134">Wpisy wiersz definiują, jakie dane są wyświetlane w wierszach tabeli.</span><span class="sxs-lookup"><span data-stu-id="3561d-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="3561d-135">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [widok tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="3561d-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3561d-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="3561d-136">Example</span></span>

<span data-ttu-id="3561d-137">W poniższym przykładzie pokazano dwa `TableColumnHeader` elementów.</span><span class="sxs-lookup"><span data-stu-id="3561d-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="3561d-138">Pierwszy element określa kolumnę, której etykietę "kolumna 1" ma szerokość o długości 16 znaków i którego etykieta jest wyrównany po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="3561d-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="3561d-139">Drugi element określa kolumnę, której etykietę "kolumna 2" ma szerokość 10 znaków i której etykietę skupia się w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="3561d-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3561d-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3561d-140">See Also</span></span>

[<span data-ttu-id="3561d-141">Wyrównanie elementu TableColumnHeader dla TableContrl (Format)</span><span class="sxs-lookup"><span data-stu-id="3561d-141">Alignment Element for TableColumnHeader for TableContrl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="3561d-142">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="3561d-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3561d-143">Element LABEL dla TableColumnHeader dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="3561d-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="3561d-144">Element TableHeaders tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="3561d-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="3561d-145">Szerokość TableColumnHeader dla tablecontrol — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3561d-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="3561d-146">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="3561d-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
