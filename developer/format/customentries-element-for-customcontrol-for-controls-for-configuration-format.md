---
title: Element CustomEntries formant niestandardowy dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847026"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="bef9d-102">CustomEntries, element — CustomControl, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bef9d-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bef9d-103">Zawiera definicje wspólnej kontroli.</span><span class="sxs-lookup"><span data-stu-id="bef9d-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="bef9d-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="bef9d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bef9d-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format)</span><span class="sxs-lookup"><span data-stu-id="bef9d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bef9d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bef9d-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bef9d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bef9d-107">Attributes and Elements</span></span>

<span data-ttu-id="bef9d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomEntries` elementu.</span><span class="sxs-lookup"><span data-stu-id="bef9d-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="bef9d-109">Należy określić jeden lub więcej elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="bef9d-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bef9d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bef9d-110">Attributes</span></span>

<span data-ttu-id="bef9d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="bef9d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bef9d-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bef9d-112">Child Elements</span></span>

|<span data-ttu-id="bef9d-113">Element</span><span class="sxs-lookup"><span data-stu-id="bef9d-113">Element</span></span>|<span data-ttu-id="bef9d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="bef9d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bef9d-115">Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="bef9d-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="bef9d-116">Zawiera definicję wspólnej kontroli.</span><span class="sxs-lookup"><span data-stu-id="bef9d-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bef9d-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bef9d-117">Parent Elements</span></span>

|<span data-ttu-id="bef9d-118">Element</span><span class="sxs-lookup"><span data-stu-id="bef9d-118">Element</span></span>|<span data-ttu-id="bef9d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="bef9d-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bef9d-120">Element formant niestandardowy do sterowania do konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="bef9d-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="bef9d-121">Określa wspólną kontrolą.</span><span class="sxs-lookup"><span data-stu-id="bef9d-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bef9d-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bef9d-122">Remarks</span></span>

<span data-ttu-id="bef9d-123">W większości przypadków formant ma tylko jedną definicję, która jest zdefiniowana w ramach pojedynczej `CustomEntry` elementu.</span><span class="sxs-lookup"><span data-stu-id="bef9d-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="bef9d-124">Jednak użytkownik może mieć wielu definicji, jeśli chcesz używać tej samej kontrolki do wyświetlania różnych obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="bef9d-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="bef9d-125">W takich przypadkach można zdefiniować `CustomEntry` elementu dla każdego obiektu lub grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="bef9d-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="bef9d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bef9d-126">See Also</span></span>

[<span data-ttu-id="bef9d-127">Element formant niestandardowy do sterowania do konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="bef9d-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="bef9d-128">Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="bef9d-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="bef9d-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="bef9d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
