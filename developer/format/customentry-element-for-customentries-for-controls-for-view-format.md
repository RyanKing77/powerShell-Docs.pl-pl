---
title: Element CustomEntry CustomEntries dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066502"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="6356c-102">CustomEntry, element — CustomEntries, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="6356c-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="6356c-103">Zawiera definicję formantu.</span><span class="sxs-lookup"><span data-stu-id="6356c-103">Provides a definition of the control.</span></span> <span data-ttu-id="6356c-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="6356c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6356c-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="6356c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6356c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6356c-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6356c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6356c-107">Attributes and Elements</span></span>

<span data-ttu-id="6356c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `CustomEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="6356c-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6356c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6356c-109">Attributes</span></span>

<span data-ttu-id="6356c-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="6356c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6356c-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6356c-111">Child Elements</span></span>

|<span data-ttu-id="6356c-112">Element</span><span class="sxs-lookup"><span data-stu-id="6356c-112">Element</span></span>|<span data-ttu-id="6356c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6356c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6356c-114">Element EntrySelectedBy CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="6356c-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="6356c-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6356c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6356c-116">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="6356c-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="6356c-117">Element CustomItem CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="6356c-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="6356c-118">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="6356c-118">Required element.</span></span><br /><br /> <span data-ttu-id="6356c-119">Definiuje, jak kontrolka ma wyświetlać dane.</span><span class="sxs-lookup"><span data-stu-id="6356c-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6356c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6356c-120">Parent Elements</span></span>

|<span data-ttu-id="6356c-121">Element</span><span class="sxs-lookup"><span data-stu-id="6356c-121">Element</span></span>|<span data-ttu-id="6356c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="6356c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6356c-123">Element CustomEntries formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="6356c-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="6356c-124">Zawiera definicje dla formantu.</span><span class="sxs-lookup"><span data-stu-id="6356c-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6356c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6356c-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="6356c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6356c-126">See Also</span></span>

[<span data-ttu-id="6356c-127">Element CustomEntries formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="6356c-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6356c-128">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="6356c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
