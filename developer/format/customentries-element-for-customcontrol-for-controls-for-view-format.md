---
title: Element CustomEntries formant niestandardowy dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850876"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="2e77c-102">CustomEntries, element — CustomControl, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="2e77c-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="2e77c-103">Zawiera definicje dla formantu.</span><span class="sxs-lookup"><span data-stu-id="2e77c-103">Provides the definitions for the control.</span></span> <span data-ttu-id="2e77c-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="2e77c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="2e77c-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2e77c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e77c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e77c-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e77c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2e77c-107">Attributes and Elements</span></span>

<span data-ttu-id="2e77c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `CustomEntries` elementu.</span><span class="sxs-lookup"><span data-stu-id="2e77c-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="2e77c-109">Nie ma żadnego limitu maksymalną liczbę elementów podrzędnych, które można określić.</span><span class="sxs-lookup"><span data-stu-id="2e77c-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e77c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2e77c-110">Attributes</span></span>

<span data-ttu-id="2e77c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="2e77c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e77c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2e77c-112">Child Elements</span></span>

|<span data-ttu-id="2e77c-113">Element</span><span class="sxs-lookup"><span data-stu-id="2e77c-113">Element</span></span>|<span data-ttu-id="2e77c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2e77c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e77c-115">Element CustomEntry CustomEntries dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2e77c-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="2e77c-116">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="2e77c-116">Required element.</span></span><br /><br /> <span data-ttu-id="2e77c-117">Zawiera definicję formantu.</span><span class="sxs-lookup"><span data-stu-id="2e77c-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e77c-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2e77c-118">Parent Elements</span></span>

|<span data-ttu-id="2e77c-119">Element</span><span class="sxs-lookup"><span data-stu-id="2e77c-119">Element</span></span>|<span data-ttu-id="2e77c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2e77c-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e77c-121">Formant niestandardowy Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2e77c-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="2e77c-122">Definiuje kontrolki użytej w widoku.</span><span class="sxs-lookup"><span data-stu-id="2e77c-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e77c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e77c-123">Remarks</span></span>

<span data-ttu-id="2e77c-124">W większości przypadków formant ma tylko jedną definicję, która jest określona w jednym `CustomEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="2e77c-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="2e77c-125">Jednak jest możliwe podanie wiele definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2e77c-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="2e77c-126">W takich przypadkach można zdefiniować `CustomEntry` elementu dla każdego obiektu lub grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="2e77c-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e77c-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e77c-127">See Also</span></span>

[<span data-ttu-id="2e77c-128">Element CustomEntry CustomEntries dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2e77c-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="2e77c-129">Formant niestandardowy Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="2e77c-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="2e77c-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="2e77c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
