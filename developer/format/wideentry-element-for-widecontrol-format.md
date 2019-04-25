---
title: Element WideEntry WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083675"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="a40dd-102">WideEntry, element — WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="a40dd-103">Zawiera definicję szerokie.</span><span class="sxs-lookup"><span data-stu-id="a40dd-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="a40dd-104">Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) elementu WideEntries (Format) WideEntry elemencie (Format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a40dd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a40dd-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a40dd-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a40dd-106">Attributes and Elements</span></span>

<span data-ttu-id="a40dd-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `WideEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="a40dd-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="a40dd-108">Należy określić pojedynczy `WideItem` elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a40dd-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a40dd-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a40dd-109">Attributes</span></span>

<span data-ttu-id="a40dd-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="a40dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a40dd-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a40dd-111">Child Elements</span></span>

|<span data-ttu-id="a40dd-112">Element</span><span class="sxs-lookup"><span data-stu-id="a40dd-112">Element</span></span>|<span data-ttu-id="a40dd-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a40dd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a40dd-114">Element EntrySelectedBy WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="a40dd-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a40dd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a40dd-116">Definiuje typy .NET, które używają tej definicji szerokiego wpisu lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="a40dd-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a40dd-117">Element WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="a40dd-118">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="a40dd-118">Required element.</span></span><br /><br /> <span data-ttu-id="a40dd-119">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="a40dd-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a40dd-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a40dd-120">Parent Elements</span></span>

|<span data-ttu-id="a40dd-121">Element</span><span class="sxs-lookup"><span data-stu-id="a40dd-121">Element</span></span>|<span data-ttu-id="a40dd-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a40dd-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a40dd-123">Element WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="a40dd-124">Zawiera definicje szerokie.</span><span class="sxs-lookup"><span data-stu-id="a40dd-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a40dd-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a40dd-125">Remarks</span></span>

<span data-ttu-id="a40dd-126">Szerokie jest format listy, który wyświetla wartość właściwości jednego lub wartość skryptu dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a40dd-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="a40dd-127">W odróżnieniu od innych rodzajów widoków można określić tylko jeden element elementu dla każdego definicji widoku.</span><span class="sxs-lookup"><span data-stu-id="a40dd-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="a40dd-128">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a40dd-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a40dd-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="a40dd-129">Example</span></span>

<span data-ttu-id="a40dd-130">W poniższym przykładzie przedstawiono `WideEntry` element, który definiuje pojedynczy `WideItem` elementu.</span><span class="sxs-lookup"><span data-stu-id="a40dd-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="a40dd-131">`WideItem` Element definiuje właściwość, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="a40dd-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="a40dd-132">Aby uzyskać pełny przykład szerokie, zobacz [szerokie (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="a40dd-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a40dd-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a40dd-133">See Also</span></span>

[<span data-ttu-id="a40dd-134">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="a40dd-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a40dd-135">Element SelectionCondition WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="a40dd-136">Element SelectionSetName WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="a40dd-137">Element TypeName dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="a40dd-138">Element WideEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="a40dd-139">Element WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="a40dd-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="a40dd-140">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="a40dd-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
