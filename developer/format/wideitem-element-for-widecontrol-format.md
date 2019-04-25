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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083641"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="73481-102">WideItem, element — WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="73481-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="73481-103">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="73481-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="73481-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) WideControl — Element (Format) elementu WideEntries (Format) WideEntry — Element (Format) WideItem Element konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="73481-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73481-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="73481-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73481-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="73481-106">Attributes and Elements</span></span>

<span data-ttu-id="73481-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `WideItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="73481-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="73481-108">`FormatString` Element jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="73481-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="73481-109">Jednakże, należy określić `PropertyName` lub `ScriptBlock` element, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="73481-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="73481-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="73481-110">Attributes</span></span>

<span data-ttu-id="73481-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="73481-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73481-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="73481-112">Child Elements</span></span>

|<span data-ttu-id="73481-113">Element</span><span class="sxs-lookup"><span data-stu-id="73481-113">Element</span></span>|<span data-ttu-id="73481-114">Opis</span><span class="sxs-lookup"><span data-stu-id="73481-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73481-115">Element FormatString dla WideItem dla WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73481-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="73481-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="73481-116">Optional element.</span></span><br /><br /> <span data-ttu-id="73481-117">Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku.</span><span class="sxs-lookup"><span data-stu-id="73481-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="73481-118">Element PropertyName WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="73481-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="73481-119">Określa właściwość obiektu, którego wartość jest wyświetlana w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="73481-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="73481-120">Element ScriptBlock WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="73481-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="73481-121">Określa skrypt, którego wartość jest wyświetlana w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="73481-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73481-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="73481-122">Parent Elements</span></span>

|<span data-ttu-id="73481-123">Element</span><span class="sxs-lookup"><span data-stu-id="73481-123">Element</span></span>|<span data-ttu-id="73481-124">Opis</span><span class="sxs-lookup"><span data-stu-id="73481-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73481-125">Element WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="73481-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="73481-126">Zawiera definicję szerokie.</span><span class="sxs-lookup"><span data-stu-id="73481-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73481-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73481-127">Remarks</span></span>

<span data-ttu-id="73481-128">Aby uzyskać więcej informacji na temat składników szerokie, zobacz [szerokie](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="73481-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="73481-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="73481-129">Example</span></span>

<span data-ttu-id="73481-130">W poniższym przykładzie przedstawiono `WideEntry` element, który definiuje pojedynczy `WideItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="73481-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="73481-131">`WideItem` Element definiuje właściwość lub skryptu, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="73481-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="73481-132">Aby uzyskać pełny przykład szerokie, zobacz [szerokie (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="73481-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73481-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73481-133">See Also</span></span>

[<span data-ttu-id="73481-134">Element FormatString dla WideItem dla WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73481-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="73481-135">Element PropertyName WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="73481-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="73481-136">Element ScriptBlock WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="73481-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="73481-137">Element WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="73481-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="73481-138">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="73481-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
