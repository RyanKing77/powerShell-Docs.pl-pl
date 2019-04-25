---
title: Określa Element konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066876"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="306ba-102">Controls, element — Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="306ba-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="306ba-103">Definiuje typowe formanty, które mogą być używane przez wszystkie widoki formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="306ba-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="306ba-104">Element kontrolki elementu (w formacie) konfiguracji konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="306ba-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="306ba-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="306ba-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="306ba-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="306ba-106">Attributes and Elements</span></span>

<span data-ttu-id="306ba-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Controls` elementu.</span><span class="sxs-lookup"><span data-stu-id="306ba-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="306ba-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="306ba-108">Attributes</span></span>

<span data-ttu-id="306ba-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="306ba-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="306ba-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="306ba-110">Child Elements</span></span>

|<span data-ttu-id="306ba-111">Element</span><span class="sxs-lookup"><span data-stu-id="306ba-111">Element</span></span>|<span data-ttu-id="306ba-112">Opis</span><span class="sxs-lookup"><span data-stu-id="306ba-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="306ba-113">Elementu formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="306ba-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="306ba-114">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="306ba-114">Required element.</span></span><br /><br /> <span data-ttu-id="306ba-115">Definiuje typowe formant, który może być używany przez wszystkie widoki formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="306ba-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="306ba-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="306ba-116">Parent Elements</span></span>

|<span data-ttu-id="306ba-117">Element</span><span class="sxs-lookup"><span data-stu-id="306ba-117">Element</span></span>|<span data-ttu-id="306ba-118">Opis</span><span class="sxs-lookup"><span data-stu-id="306ba-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="306ba-119">Element konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="306ba-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="306ba-120">Reprezentuje element najwyższego poziomu w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="306ba-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="306ba-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="306ba-121">Remarks</span></span>

<span data-ttu-id="306ba-122">Można utworzyć dowolną liczbę wspólnych formantów.</span><span class="sxs-lookup"><span data-stu-id="306ba-122">You can create any number of common controls.</span></span> <span data-ttu-id="306ba-123">Dla każdego formantu należy określić nazwę, która jest używana do odwoływania się kontrolki i składniki formantu.</span><span class="sxs-lookup"><span data-stu-id="306ba-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="306ba-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="306ba-124">See Also</span></span>

[<span data-ttu-id="306ba-125">Element konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="306ba-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="306ba-126">Elementu formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="306ba-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="306ba-127">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="306ba-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
