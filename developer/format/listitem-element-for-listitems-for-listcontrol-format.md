---
title: Element ListItem ListItems dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846221"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="fc9e5-102">ListItem, element — ListItems, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="fc9e5-103">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="fc9e5-104">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji dla elementu ListEntry elementu ListControl (w formacie) dla elementu ListItems elementu ListControl (w formacie) dla elementu ListControl (Format) ListItem dla elementu elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc9e5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc9e5-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc9e5-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fc9e5-106">Attributes and Elements</span></span>

<span data-ttu-id="fc9e5-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ListItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="fc9e5-108">Można określić tylko jedną właściwość lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc9e5-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fc9e5-109">Attributes</span></span>

<span data-ttu-id="fc9e5-110">Brak</span><span class="sxs-lookup"><span data-stu-id="fc9e5-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc9e5-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fc9e5-111">Child Elements</span></span>

|<span data-ttu-id="fc9e5-112">Element</span><span class="sxs-lookup"><span data-stu-id="fc9e5-112">Element</span></span>|<span data-ttu-id="fc9e5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fc9e5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc9e5-114">Element FormatString dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="fc9e5-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fc9e5-116">Określa ciąg formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="fc9e5-117">Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="fc9e5-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-118">Optional element.</span></span><br /><br /> <span data-ttu-id="fc9e5-119">Określa warunek, który musi istnieć przez ten element listy do użycia.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="fc9e5-120">Element LABEL dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="fc9e5-121">Opcjonalny element</span><span class="sxs-lookup"><span data-stu-id="fc9e5-121">Optional element</span></span><br /><br /> <span data-ttu-id="fc9e5-122">Określa etykietę, który jest wyświetlany po lewej stronie wartości właściwości lub skryptu w wierszu.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="fc9e5-123">Element PropertyName dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="fc9e5-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-124">Optional element.</span></span><br /><br /> <span data-ttu-id="fc9e5-125">Określa właściwości platformy .NET, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="fc9e5-126">Element ScriptBlock dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="fc9e5-127">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-127">Optional element.</span></span><br /><br /> <span data-ttu-id="fc9e5-128">Określa skrypt, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fc9e5-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fc9e5-129">Parent Elements</span></span>

|<span data-ttu-id="fc9e5-130">Element</span><span class="sxs-lookup"><span data-stu-id="fc9e5-130">Element</span></span>|<span data-ttu-id="fc9e5-131">Opis</span><span class="sxs-lookup"><span data-stu-id="fc9e5-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc9e5-132">Element ListItems dla kontrolki listy (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="fc9e5-133">Definiuje właściwości i skrypty, których wartości są wyświetlane w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fc9e5-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc9e5-134">Remarks</span></span>

<span data-ttu-id="fc9e5-135">Aby uzyskać więcej informacji o składnikach w widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="fc9e5-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fc9e5-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc9e5-136">Example</span></span>

<span data-ttu-id="fc9e5-137">Ten przykład pokazuje elementy XML, które określają trzy wiersze w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="fc9e5-138">Pierwsze dwa wiersze wyświetlić wartość właściwości platformy .NET, a ostatni wiersz wyświetla wartość wygenerowaną przez skrypt.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="fc9e5-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc9e5-139">See Also</span></span>

[<span data-ttu-id="fc9e5-140">Element ListItems (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="fc9e5-141">Element FormatString dla elementu listy (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="fc9e5-142">Etykieta elementu ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="fc9e5-143">PropertyName Element ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="fc9e5-144">Blok skryptu Element ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="fc9e5-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="fc9e5-145">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="fc9e5-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fc9e5-146">Pisanie programu Windows PowerShell, formatowania i typy plików</span><span class="sxs-lookup"><span data-stu-id="fc9e5-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
