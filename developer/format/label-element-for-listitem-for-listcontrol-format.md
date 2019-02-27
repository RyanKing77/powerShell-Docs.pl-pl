---
title: Etykiety elementów dla elementu listy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845955"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="f0859-102">Label, element — ListItem, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="f0859-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="f0859-103">Określa etykietę, który jest wyświetlany po lewej stronie wartości właściwości lub skryptu w wierszu.</span><span class="sxs-lookup"><span data-stu-id="f0859-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="f0859-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListItems elementu ListControl (w formacie) dla ListEntry dla elementu elementu ListControl ( Element ListItem Format) dla ListItems elementu ListControl (Format) etykiety elementu ListItem dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f0859-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f0859-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0859-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f0859-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f0859-106">Attributes and Elements</span></span>

<span data-ttu-id="f0859-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Label` elementu.</span><span class="sxs-lookup"><span data-stu-id="f0859-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f0859-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f0859-108">Attributes</span></span>

<span data-ttu-id="f0859-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="f0859-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f0859-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f0859-110">Child Elements</span></span>

<span data-ttu-id="f0859-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="f0859-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f0859-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f0859-112">Parent Elements</span></span>

|<span data-ttu-id="f0859-113">Element</span><span class="sxs-lookup"><span data-stu-id="f0859-113">Element</span></span>|<span data-ttu-id="f0859-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f0859-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f0859-115">Element ListItem ListItems dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f0859-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="f0859-116">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="f0859-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f0859-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="f0859-117">Text Value</span></span>

<span data-ttu-id="f0859-118">Określ etykietę być wyświetlana po lewej stronie wartości właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="f0859-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0859-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0859-119">Remarks</span></span>

<span data-ttu-id="f0859-120">Jeśli etykieta nie zostanie określony, jest wyświetlana nazwa właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="f0859-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="f0859-121">Aby uzyskać więcej informacji na temat używania etykiet w widoku listy zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f0859-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f0859-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0859-122">Example</span></span>

<span data-ttu-id="f0859-123">Poniższy przykład pokazuje, jak dodać etykietę do wiersza.</span><span class="sxs-lookup"><span data-stu-id="f0859-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="f0859-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0859-124">See Also</span></span>

[<span data-ttu-id="f0859-125">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="f0859-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f0859-126">ListItem — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f0859-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="f0859-127">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="f0859-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
