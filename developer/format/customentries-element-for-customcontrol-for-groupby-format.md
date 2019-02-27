---
title: Element CustomEntries formant niestandardowy do grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845185"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="f3ba5-102">CustomEntries, element — CustomControl, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f3ba5-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="f3ba5-103">Zawiera definicje dla formantu.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-103">Provides the definitions for the control.</span></span> <span data-ttu-id="f3ba5-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f3ba5-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f3ba5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f3ba5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3ba5-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f3ba5-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f3ba5-107">Attributes and Elements</span></span>

<span data-ttu-id="f3ba5-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `CustomEntries` elementu.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="f3ba5-109">Nie ma żadnego limitu maksymalną liczbę elementów podrzędnych, które można określić.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="f3ba5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f3ba5-110">Attributes</span></span>

<span data-ttu-id="f3ba5-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f3ba5-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f3ba5-112">Child Elements</span></span>

|<span data-ttu-id="f3ba5-113">Element</span><span class="sxs-lookup"><span data-stu-id="f3ba5-113">Element</span></span>|<span data-ttu-id="f3ba5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f3ba5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3ba5-115">Element CustomEntry formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f3ba5-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="f3ba5-116">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-116">Required element.</span></span><br /><br /> <span data-ttu-id="f3ba5-117">Zawiera definicję formantu.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f3ba5-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f3ba5-118">Parent Elements</span></span>

|<span data-ttu-id="f3ba5-119">Element</span><span class="sxs-lookup"><span data-stu-id="f3ba5-119">Element</span></span>|<span data-ttu-id="f3ba5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="f3ba5-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3ba5-121">Element formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f3ba5-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="f3ba5-122">Definiuje kontrolki niestandardowej, która przedstawia nową grupę.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f3ba5-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3ba5-123">Remarks</span></span>

<span data-ttu-id="f3ba5-124">W większości przypadków formant ma tylko jedną definicję, która jest określona w jednym `CustomEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="f3ba5-125">Jednak jest możliwe podanie wiele definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych grup.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="f3ba5-126">W takich przypadkach można zdefiniować `CustomEntry` elementu dla grupy.</span><span class="sxs-lookup"><span data-stu-id="f3ba5-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3ba5-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3ba5-127">See Also</span></span>

[<span data-ttu-id="f3ba5-128">Element CustomEntry CustomEntries dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="f3ba5-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="f3ba5-129">Element formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f3ba5-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="f3ba5-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="f3ba5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
