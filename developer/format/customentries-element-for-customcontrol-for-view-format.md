---
title: Element CustomEntries formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066519"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="eaffe-102">CustomEntries, element — CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="eaffe-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="eaffe-103">Zawiera definicje widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="eaffe-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="eaffe-104">Wyświetl formant niestandardowy, należy określić co najmniej jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="eaffe-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="eaffe-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (w formacie) CustomEntries Element konfiguracji dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="eaffe-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eaffe-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="eaffe-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eaffe-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eaffe-107">Attributes and Elements</span></span>

<span data-ttu-id="eaffe-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomControlEntries` elementu.</span><span class="sxs-lookup"><span data-stu-id="eaffe-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="eaffe-109">Należy określić jeden lub więcej elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="eaffe-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="eaffe-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eaffe-110">Attributes</span></span>

<span data-ttu-id="eaffe-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="eaffe-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eaffe-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eaffe-112">Child Elements</span></span>

|<span data-ttu-id="eaffe-113">Element</span><span class="sxs-lookup"><span data-stu-id="eaffe-113">Element</span></span>|<span data-ttu-id="eaffe-114">Opis</span><span class="sxs-lookup"><span data-stu-id="eaffe-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eaffe-115">Element CustomEntry CustomEntries widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="eaffe-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="eaffe-116">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="eaffe-116">Required element.</span></span><br /><br /> <span data-ttu-id="eaffe-117">Zawiera definicję widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="eaffe-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eaffe-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eaffe-118">Parent Elements</span></span>

|<span data-ttu-id="eaffe-119">Element</span><span class="sxs-lookup"><span data-stu-id="eaffe-119">Element</span></span>|<span data-ttu-id="eaffe-120">Opis</span><span class="sxs-lookup"><span data-stu-id="eaffe-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eaffe-121">Formant niestandardowy Element widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="eaffe-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="eaffe-122">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="eaffe-122">Required element.</span></span><br /><br /> <span data-ttu-id="eaffe-123">Definiuje format formantu niestandardowego dla widoku.</span><span class="sxs-lookup"><span data-stu-id="eaffe-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eaffe-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eaffe-124">Remarks</span></span>

<span data-ttu-id="eaffe-125">W większości przypadków formant ma tylko jedną definicję, która jest zdefiniowana w ramach pojedynczej `CustomEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="eaffe-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="eaffe-126">Jednak użytkownik może mieć wielu definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="eaffe-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="eaffe-127">W takich przypadkach można zdefiniować `CustomEntry` elementu dla każdego obiektu lub grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="eaffe-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="eaffe-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eaffe-128">See Also</span></span>

[<span data-ttu-id="eaffe-129">Formant niestandardowy Element widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="eaffe-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="eaffe-130">Element CustomEntry CustomEntries widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="eaffe-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="eaffe-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="eaffe-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
