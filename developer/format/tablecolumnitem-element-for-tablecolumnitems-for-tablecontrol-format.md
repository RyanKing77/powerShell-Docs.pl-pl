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
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851303"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="f2720-102">TableColumnItem, element — TableColumnItems, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="f2720-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="f2720-103">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="f2720-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="f2720-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableRowEntries Element konfiguracji elementu TableRowEntry tablecontrol — (w formacie) TableRowEntries dla tablecontrol — (w formacie) Element TableColumnItems TableControlEntry tablecontrol — (w formacie) elementu TableColumnItem TableColumnItems dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2720-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2720-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2720-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f2720-106">Attributes and Elements</span></span>

<span data-ttu-id="f2720-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableColumnItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="f2720-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2720-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f2720-108">Attributes</span></span>

<span data-ttu-id="f2720-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="f2720-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2720-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f2720-110">Child Elements</span></span>

|<span data-ttu-id="f2720-111">Element</span><span class="sxs-lookup"><span data-stu-id="f2720-111">Element</span></span>|<span data-ttu-id="f2720-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f2720-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2720-113">Wyrównanie elementu TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="f2720-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f2720-114">Optional element.</span></span><br /><br /> <span data-ttu-id="f2720-115">Definiuje sposób wyświetlania danych w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="f2720-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="f2720-116">Element FormatString dla TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="f2720-117">Określa wzorzec formatu, który jest używany do formatowania danych w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="f2720-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="f2720-118">Element PropertyName TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="f2720-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f2720-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f2720-120">Określa nazwę właściwości, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="f2720-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="f2720-121">Element ScriptBlock TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="f2720-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f2720-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f2720-123">Określa skrypt, którego wartość jest wyświetlana w kolumnie wiersz.</span><span class="sxs-lookup"><span data-stu-id="f2720-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f2720-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f2720-124">Parent Elements</span></span>

|<span data-ttu-id="f2720-125">Element</span><span class="sxs-lookup"><span data-stu-id="f2720-125">Element</span></span>|<span data-ttu-id="f2720-126">Opis</span><span class="sxs-lookup"><span data-stu-id="f2720-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2720-127">Element TableColumnItems TableControlEntry dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f2720-128">Definiuje właściwości lub skryptów, których wartości są wyświetlane w wierszu.</span><span class="sxs-lookup"><span data-stu-id="f2720-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f2720-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2720-129">Remarks</span></span>

<span data-ttu-id="f2720-130">Można określić właściwości obiektu lub skryptu w każdej kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="f2720-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="f2720-131">Jeśli nie określono żadnych elementów podrzędnych, element jest symbolem zastępczym, a nie zostaną wyświetlone dane.</span><span class="sxs-lookup"><span data-stu-id="f2720-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="f2720-132">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f2720-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f2720-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2720-133">Example</span></span>

<span data-ttu-id="f2720-134">W tym przykładzie `TableColumnItem` element, który wyświetla wartość `Status` właściwość [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="f2720-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="f2720-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2720-135">See Also</span></span>

[<span data-ttu-id="f2720-136">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="f2720-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f2720-137">Wyrównanie elementu TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="f2720-138">Element TableColumnItems (Format)</span><span class="sxs-lookup"><span data-stu-id="f2720-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="f2720-139">Element FormatString dla TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="f2720-140">Element PropertyName TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="f2720-141">Element ScriptBlock TableColumnItem dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f2720-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="f2720-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="f2720-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
