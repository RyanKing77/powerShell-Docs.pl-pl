---
title: Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849476"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="dddd3-102">CustomEntry, element — CustomControl, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="dddd3-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="dddd3-103">Zawiera definicję wspólnej kontroli.</span><span class="sxs-lookup"><span data-stu-id="dddd3-103">Provides a definition of the common control.</span></span> <span data-ttu-id="dddd3-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="dddd3-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="dddd3-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="dddd3-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dddd3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="dddd3-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="dddd3-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dddd3-107">Attributes and Elements</span></span>

<span data-ttu-id="dddd3-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="dddd3-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="dddd3-109">Należy określić elementów wyświetlanych przez definicję.</span><span class="sxs-lookup"><span data-stu-id="dddd3-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="dddd3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dddd3-110">Attributes</span></span>

<span data-ttu-id="dddd3-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="dddd3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dddd3-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dddd3-112">Child Elements</span></span>

|<span data-ttu-id="dddd3-113">Element</span><span class="sxs-lookup"><span data-stu-id="dddd3-113">Element</span></span>|<span data-ttu-id="dddd3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="dddd3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dddd3-115">Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="dddd3-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="dddd3-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="dddd3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="dddd3-117">Definiuje typy .NET, korzystających z definicji formantu typowego lub warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="dddd3-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="dddd3-118">Element CustomItem CustomEntry dla formantów dla konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dddd3-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="dddd3-119">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="dddd3-119">Required element.</span></span><br /><br /> <span data-ttu-id="dddd3-120">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="dddd3-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dddd3-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dddd3-121">Parent Elements</span></span>

|<span data-ttu-id="dddd3-122">Element</span><span class="sxs-lookup"><span data-stu-id="dddd3-122">Element</span></span>|<span data-ttu-id="dddd3-123">Opis</span><span class="sxs-lookup"><span data-stu-id="dddd3-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dddd3-124">Element CustomEntries formant niestandardowy do konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="dddd3-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="dddd3-125">Zawiera definicje wspólnej kontroli.</span><span class="sxs-lookup"><span data-stu-id="dddd3-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dddd3-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dddd3-126">Remarks</span></span>

<span data-ttu-id="dddd3-127">W większości przypadków tylko jedną definicję, jest wymagana dla poszczególnych typowych kontrolek niestandardowych, ale użytkownik może mieć wielu definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="dddd3-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="dddd3-128">W takich przypadkach możesz podać definicję osobne dla każdego obiektu lub grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="dddd3-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="dddd3-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dddd3-129">See Also</span></span>

[<span data-ttu-id="dddd3-130">Element CustomEntries formant niestandardowy do konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="dddd3-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="dddd3-131">Element CustomItem CustomEntry dla formantów dla konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dddd3-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="dddd3-132">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="dddd3-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
