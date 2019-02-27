---
title: Element CustomEntry CustomEntries dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850883"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="5e027-102">CustomEntry, element — CustomEntries, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="5e027-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="5e027-103">Zawiera definicję widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="5e027-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="5e027-104">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (w formacie) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="5e027-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5e027-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e027-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e027-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5e027-106">Attributes and Elements</span></span>

<span data-ttu-id="5e027-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="5e027-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="5e027-108">Należy określić elementów wyświetlanych przez definicję.</span><span class="sxs-lookup"><span data-stu-id="5e027-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e027-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5e027-109">Attributes</span></span>

<span data-ttu-id="5e027-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="5e027-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e027-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5e027-111">Child Elements</span></span>

|<span data-ttu-id="5e027-112">Element</span><span class="sxs-lookup"><span data-stu-id="5e027-112">Element</span></span>|<span data-ttu-id="5e027-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5e027-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e027-114">Element EntrySelectedBy CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="5e027-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e027-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5e027-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5e027-116">Definiuje typy .NET, korzystających z definicji widoku kontrolkę niestandardową lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="5e027-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="5e027-117">Element CustomItem CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="5e027-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e027-118">Definiuje formant do zdefiniowania kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="5e027-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5e027-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5e027-119">Parent Elements</span></span>

|<span data-ttu-id="5e027-120">Element</span><span class="sxs-lookup"><span data-stu-id="5e027-120">Element</span></span>|<span data-ttu-id="5e027-121">Opis</span><span class="sxs-lookup"><span data-stu-id="5e027-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e027-122">Element CustomEntries formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="5e027-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e027-123">Zawiera definicje widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="5e027-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="5e027-124">Wyświetl formant niestandardowy, należy określić co najmniej jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="5e027-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e027-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e027-125">Remarks</span></span>

<span data-ttu-id="5e027-126">W większości przypadków tylko jedną definicję, jest wymagana dla każdego widoku formant niestandardowy, ale użytkownik może mieć wielu definicji, jeśli chcesz wyświetlić różne obiekty platformy .NET przy użyciu tego samego widoku.</span><span class="sxs-lookup"><span data-stu-id="5e027-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="5e027-127">W takich przypadkach możesz podać definicję osobne dla każdego obiektu lub grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="5e027-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e027-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e027-128">See Also</span></span>

[<span data-ttu-id="5e027-129">Formant niestandardowy Element widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="5e027-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="5e027-130">Element CustomItem CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="5e027-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e027-131">Element EntrySelectedBy CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="5e027-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e027-132">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="5e027-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
