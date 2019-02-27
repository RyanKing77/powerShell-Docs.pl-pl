---
title: Element ScriptBlock dla elementu listy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846501"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="e58a2-102">ScriptBlock, element — ListItem, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e58a2-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="e58a2-103">Określa skrypt, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="e58a2-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="e58a2-104">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListEntries elementu ListControl (Format) elementu ListItems ListEntry dla elementu ListControl (Format) elementu ListItem ListItems elementu ListControl (Format) ScriptBlock elementu ListItem dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e58a2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e58a2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e58a2-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e58a2-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e58a2-106">Attributes and Elements</span></span>

<span data-ttu-id="e58a2-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="e58a2-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e58a2-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e58a2-108">Attributes</span></span>

<span data-ttu-id="e58a2-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="e58a2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e58a2-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e58a2-110">Child Elements</span></span>

<span data-ttu-id="e58a2-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="e58a2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e58a2-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e58a2-112">Parent Elements</span></span>

|<span data-ttu-id="e58a2-113">Element</span><span class="sxs-lookup"><span data-stu-id="e58a2-113">Element</span></span>|<span data-ttu-id="e58a2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e58a2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e58a2-115">ListItem — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e58a2-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="e58a2-116">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="e58a2-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e58a2-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="e58a2-117">Text Value</span></span>

<span data-ttu-id="e58a2-118">Określ skrypt, którego wartość jest wyświetlana w wierszu.</span><span class="sxs-lookup"><span data-stu-id="e58a2-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="e58a2-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e58a2-119">Remarks</span></span>

<span data-ttu-id="e58a2-120">Gdy ten element jest określony, nie można określić [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e58a2-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="e58a2-121">Aby uzyskać więcej informacji na temat określania skryptów w widoku listy, zobacz [widok listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e58a2-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e58a2-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e58a2-122">Example</span></span>

<span data-ttu-id="e58a2-123">Poniższy przykład pokazuje sposób określania właściwości, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="e58a2-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="e58a2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e58a2-124">See Also</span></span>

[<span data-ttu-id="e58a2-125">Element PropertyName dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e58a2-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="e58a2-126">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="e58a2-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e58a2-127">Element ListItem ListItems dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e58a2-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="e58a2-128">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="e58a2-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
