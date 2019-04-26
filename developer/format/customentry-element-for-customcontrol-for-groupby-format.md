---
title: Element CustomEntry formant niestandardowy do grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066489"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="13e65-102">CustomEntry, element — CustomControl, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="13e65-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="13e65-103">Zawiera definicję formantu.</span><span class="sxs-lookup"><span data-stu-id="13e65-103">Provides a definition of the control.</span></span> <span data-ttu-id="13e65-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="13e65-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="13e65-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="13e65-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13e65-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="13e65-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13e65-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="13e65-107">Attributes and Elements</span></span>

<span data-ttu-id="13e65-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `CustomEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="13e65-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="13e65-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="13e65-109">Attributes</span></span>

<span data-ttu-id="13e65-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="13e65-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13e65-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="13e65-111">Child Elements</span></span>

|<span data-ttu-id="13e65-112">Element</span><span class="sxs-lookup"><span data-stu-id="13e65-112">Element</span></span>|<span data-ttu-id="13e65-113">Opis</span><span class="sxs-lookup"><span data-stu-id="13e65-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13e65-114">Element EntrySelectedBy CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="13e65-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="13e65-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="13e65-115">Optional element.</span></span><br /><br /> <span data-ttu-id="13e65-116">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="13e65-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="13e65-117">Element CustomItem CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="13e65-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="13e65-118">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="13e65-118">Required element.</span></span><br /><br /> <span data-ttu-id="13e65-119">Definiuje, jak kontrolka ma wyświetlać dane.</span><span class="sxs-lookup"><span data-stu-id="13e65-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="13e65-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="13e65-120">Parent Elements</span></span>

|<span data-ttu-id="13e65-121">Element</span><span class="sxs-lookup"><span data-stu-id="13e65-121">Element</span></span>|<span data-ttu-id="13e65-122">Opis</span><span class="sxs-lookup"><span data-stu-id="13e65-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13e65-123">Element CustomEntries formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="13e65-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="13e65-124">Zawiera definicje dla formantu.</span><span class="sxs-lookup"><span data-stu-id="13e65-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13e65-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13e65-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="13e65-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13e65-126">See Also</span></span>

[<span data-ttu-id="13e65-127">Element EntrySelectedBy CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="13e65-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="13e65-128">Element CustomItem CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="13e65-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="13e65-129">Element CustomEntries formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="13e65-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="13e65-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="13e65-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
