---
title: Element TableColumnItem TableColumnItems dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056995"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="72819-102">TableColumnItem, element — TableColumnItems, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="72819-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="72819-103">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="72819-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="72819-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries Element konfiguracji elementu TableRowEntry tablecontrol — (w formacie) TableRowEntries dla tablecontrol — (w formacie) Element TableColumnItems TableControlEntry tablecontrol — (w formacie) elementu TableColumnItem TableColumnItems dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="72819-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="72819-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="72819-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="72819-106">Attributes and Elements</span></span>

<span data-ttu-id="72819-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableColumnItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="72819-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="72819-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="72819-108">Attributes</span></span>

<span data-ttu-id="72819-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="72819-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="72819-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="72819-110">Child Elements</span></span>

|<span data-ttu-id="72819-111">Element</span><span class="sxs-lookup"><span data-stu-id="72819-111">Element</span></span>|<span data-ttu-id="72819-112">Opis</span><span class="sxs-lookup"><span data-stu-id="72819-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72819-113">Wyrównanie elementu TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="72819-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="72819-114">Optional element.</span></span><br /><br /> <span data-ttu-id="72819-115">Definiuje sposób wyświetlania danych w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="72819-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="72819-116">Element FormatString dla TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="72819-117">Określa wzorzec formatu, który jest używany do formatowania danych w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="72819-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="72819-118">Element PropertyName TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="72819-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="72819-119">Optional element.</span></span><br /><br /> <span data-ttu-id="72819-120">Określa nazwę właściwości, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="72819-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="72819-121">Element ScriptBlock TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="72819-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="72819-122">Optional element.</span></span><br /><br /> <span data-ttu-id="72819-123">Określa skrypt, którego wartość jest wyświetlana w kolumnie wiersz.</span><span class="sxs-lookup"><span data-stu-id="72819-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="72819-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="72819-124">Parent Elements</span></span>

|<span data-ttu-id="72819-125">Element</span><span class="sxs-lookup"><span data-stu-id="72819-125">Element</span></span>|<span data-ttu-id="72819-126">Opis</span><span class="sxs-lookup"><span data-stu-id="72819-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72819-127">Element TableColumnItems TableControlEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="72819-128">Definiuje właściwości lub skryptów, których wartości są wyświetlane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="72819-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="72819-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72819-129">Remarks</span></span>

<span data-ttu-id="72819-130">Można określić właściwości obiektu lub skryptu w każdej kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="72819-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="72819-131">Jeśli nie określono żadnych elementów podrzędnych, element jest symbolem zastępczym, a nie zostaną wyświetlone dane.</span><span class="sxs-lookup"><span data-stu-id="72819-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="72819-132">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="72819-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="72819-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="72819-133">Example</span></span>

<span data-ttu-id="72819-134">W tym przykładzie `TableColumnItem` element, który wyświetla wartość `Status` właściwość [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="72819-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="72819-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72819-135">See Also</span></span>

[<span data-ttu-id="72819-136">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="72819-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="72819-137">Wyrównanie elementu TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="72819-138">Element TableColumnItems (Format)</span><span class="sxs-lookup"><span data-stu-id="72819-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="72819-139">Element FormatString dla TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="72819-140">Element PropertyName TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="72819-141">Element ScriptBlock TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="72819-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="72819-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="72819-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
