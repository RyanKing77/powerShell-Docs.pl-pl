---
title: Element PropertyName dla elementu listy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846627"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="b6ff7-102">PropertyName, element — ListItem, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="b6ff7-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="b6ff7-103">Określa właściwości platformy .NET, którego wartość jest wyświetlana na liście.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="b6ff7-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) ListItems — Element (Format) Element ListItem (Format) PropertyName Element konfiguracji dla ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="b6ff7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b6ff7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6ff7-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6ff7-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b6ff7-106">Attributes and Elements</span></span>

<span data-ttu-id="b6ff7-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6ff7-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6ff7-108">Attributes</span></span>

<span data-ttu-id="b6ff7-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6ff7-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b6ff7-110">Child Elements</span></span>

<span data-ttu-id="b6ff7-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b6ff7-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b6ff7-112">Parent Elements</span></span>

|<span data-ttu-id="b6ff7-113">Element</span><span class="sxs-lookup"><span data-stu-id="b6ff7-113">Element</span></span>|<span data-ttu-id="b6ff7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b6ff7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b6ff7-115">ListItem — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b6ff7-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="b6ff7-116">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b6ff7-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="b6ff7-117">Text Value</span></span>

<span data-ttu-id="b6ff7-118">Określ nazwę właściwości, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6ff7-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6ff7-119">Remarks</span></span>

<span data-ttu-id="b6ff7-120">Gdy ten element jest określony, nie można określić [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="b6ff7-121">Oprócz wyświetlania wartości właściwości, można również określić etykietę dla wartość lub ciąg formatu, który może służyć do zmienić sposób wyświetlania wartości.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="b6ff7-122">Aby uzyskać więcej informacji na temat określania danych w widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b6ff7-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b6ff7-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6ff7-123">Example</span></span>

<span data-ttu-id="b6ff7-124">Poniższy przykład pokazuje, jak określić etykietę i właściwości, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="b6ff7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6ff7-125">See Also</span></span>

[<span data-ttu-id="b6ff7-126">Element ScriptBlock dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b6ff7-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b6ff7-127">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="b6ff7-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b6ff7-128">ListItem Element ListControl(Format)</span><span class="sxs-lookup"><span data-stu-id="b6ff7-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="b6ff7-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="b6ff7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
