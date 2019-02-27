---
title: Element WideItem WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851450"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="e98d3-102">WideItem, element — WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="e98d3-103">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="e98d3-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="e98d3-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) WideControl — Element (Format) elementu WideEntries (Format) WideEntry — Element (Format) WideItem Element konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e98d3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e98d3-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e98d3-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e98d3-106">Attributes and Elements</span></span>

<span data-ttu-id="e98d3-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `WideItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="e98d3-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="e98d3-108">`FormatString` Element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e98d3-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="e98d3-109">Jednakże, należy określić `PropertyName` lub `ScriptBlock` element, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e98d3-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="e98d3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e98d3-110">Attributes</span></span>

<span data-ttu-id="e98d3-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="e98d3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e98d3-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e98d3-112">Child Elements</span></span>

|<span data-ttu-id="e98d3-113">Element</span><span class="sxs-lookup"><span data-stu-id="e98d3-113">Element</span></span>|<span data-ttu-id="e98d3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e98d3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e98d3-115">Element FormatString dla WideItem dla WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e98d3-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e98d3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e98d3-117">Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku.</span><span class="sxs-lookup"><span data-stu-id="e98d3-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="e98d3-118">Element PropertyName WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e98d3-119">Określa właściwość obiektu, którego wartość jest wyświetlana w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="e98d3-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="e98d3-120">Element ScriptBlock WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="e98d3-121">Określa skrypt, którego wartość jest wyświetlana w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="e98d3-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e98d3-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e98d3-122">Parent Elements</span></span>

|<span data-ttu-id="e98d3-123">Element</span><span class="sxs-lookup"><span data-stu-id="e98d3-123">Element</span></span>|<span data-ttu-id="e98d3-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e98d3-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e98d3-125">Element WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="e98d3-126">Zawiera definicję szerokie.</span><span class="sxs-lookup"><span data-stu-id="e98d3-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e98d3-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e98d3-127">Remarks</span></span>

<span data-ttu-id="e98d3-128">Aby uzyskać więcej informacji na temat składników szerokie, zobacz [szerokie](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e98d3-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e98d3-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="e98d3-129">Example</span></span>

<span data-ttu-id="e98d3-130">W poniższym przykładzie przedstawiono `WideEntry` element, który definiuje pojedynczy `WideItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="e98d3-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="e98d3-131">`WideItem` Element definiuje właściwość lub skryptu, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="e98d3-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="e98d3-132">Aby uzyskać pełny przykład szerokie, zobacz [szerokie (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e98d3-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e98d3-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e98d3-133">See Also</span></span>

[<span data-ttu-id="e98d3-134">Element FormatString dla WideItem dla WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e98d3-135">Element PropertyName WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e98d3-136">Element ScriptBlock WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="e98d3-137">Element WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e98d3-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="e98d3-138">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="e98d3-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
