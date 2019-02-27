---
title: Element WideEntries WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844905"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="b652d-102">WideEntries, element — WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="b652d-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="b652d-103">Zawiera definicje szerokie.</span><span class="sxs-lookup"><span data-stu-id="b652d-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="b652d-104">Szerokie, należy określić co najmniej jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="b652d-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="b652d-105">Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) elementu WideControl (Format) WideEntries elemencie (Format)</span><span class="sxs-lookup"><span data-stu-id="b652d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b652d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b652d-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b652d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b652d-107">Attributes and Elements</span></span>

<span data-ttu-id="b652d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `WideEntries` elementu.</span><span class="sxs-lookup"><span data-stu-id="b652d-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="b652d-109">Należy określić co najmniej jeden element podrzędny elementu.</span><span class="sxs-lookup"><span data-stu-id="b652d-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="b652d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b652d-110">Attributes</span></span>

<span data-ttu-id="b652d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="b652d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b652d-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b652d-112">Child Elements</span></span>

|<span data-ttu-id="b652d-113">Element</span><span class="sxs-lookup"><span data-stu-id="b652d-113">Element</span></span>|<span data-ttu-id="b652d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b652d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b652d-115">Element WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b652d-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="b652d-116">Zawiera definicję szerokie.</span><span class="sxs-lookup"><span data-stu-id="b652d-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b652d-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b652d-117">Parent Elements</span></span>

|<span data-ttu-id="b652d-118">Element</span><span class="sxs-lookup"><span data-stu-id="b652d-118">Element</span></span>|<span data-ttu-id="b652d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b652d-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b652d-120">Element WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b652d-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="b652d-121">Definiuje całej (pojedyncza wartość) format listy dla widoku.</span><span class="sxs-lookup"><span data-stu-id="b652d-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b652d-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b652d-122">Remarks</span></span>

<span data-ttu-id="b652d-123">Szerokie jest format listy, który wyświetla wartość właściwości jednego lub wartość skryptu dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b652d-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="b652d-124">Aby uzyskać więcej informacji na temat składników szerokie, zobacz [szeroki składniki widoków](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b652d-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b652d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="b652d-125">Example</span></span>

<span data-ttu-id="b652d-126">W poniższym przykładzie przedstawiono `WideEntries` element, który definiuje pojedynczy `WideEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="b652d-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="b652d-127">`WideEntry` Element zawiera pojedynczy `WideItem` element, który definiuje, jakie wartości właściwości lub skryptu jest wyświetlany w widoku.</span><span class="sxs-lookup"><span data-stu-id="b652d-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="b652d-128">Aby uzyskać pełny przykład szerokie, zobacz [szerokie (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b652d-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b652d-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b652d-129">See Also</span></span>

[<span data-ttu-id="b652d-130">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="b652d-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b652d-131">Element WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b652d-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="b652d-132">Element WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b652d-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="b652d-133">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="b652d-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
