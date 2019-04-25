---
title: Kontrolowanie elementu dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066797"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="80c0a-102">Control, element — Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="80c0a-103">Definiuje typowe formant, który może być używany przez wszystkie widoki formatowania pliku i nazwę, która jest używana do odwołania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="80c0a-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="80c0a-104">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80c0a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="80c0a-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80c0a-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80c0a-106">Attributes and Elements</span></span>

<span data-ttu-id="80c0a-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny dla `Control` elementu.</span><span class="sxs-lookup"><span data-stu-id="80c0a-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="80c0a-108">Należy określić tylko jeden z każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="80c0a-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80c0a-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80c0a-109">Attributes</span></span>

<span data-ttu-id="80c0a-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="80c0a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80c0a-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80c0a-111">Child Elements</span></span>

|<span data-ttu-id="80c0a-112">Element</span><span class="sxs-lookup"><span data-stu-id="80c0a-112">Element</span></span>|<span data-ttu-id="80c0a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="80c0a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80c0a-114">Formant niestandardowy Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="80c0a-115">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="80c0a-115">Required element.</span></span><br /><br /> <span data-ttu-id="80c0a-116">Definiuje kontrolki.</span><span class="sxs-lookup"><span data-stu-id="80c0a-116">Defines the control.</span></span>|
|[<span data-ttu-id="80c0a-117">Name — Element dla formantu konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="80c0a-118">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="80c0a-118">Required element.</span></span><br /><br /> <span data-ttu-id="80c0a-119">Określa nazwę używaną do odwoływać się do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="80c0a-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80c0a-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80c0a-120">Parent Elements</span></span>

|<span data-ttu-id="80c0a-121">Element</span><span class="sxs-lookup"><span data-stu-id="80c0a-121">Element</span></span>|<span data-ttu-id="80c0a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="80c0a-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80c0a-123">Kontrolki elementu konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="80c0a-124">Definiuje typowe formanty, które mogą być używane przez wszystkie widoki formatowania pliku lub przez inne kontrolki.</span><span class="sxs-lookup"><span data-stu-id="80c0a-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80c0a-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80c0a-125">Remarks</span></span>

<span data-ttu-id="80c0a-126">Nazwa nadana tej kontrolki może znajdować się w następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="80c0a-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="80c0a-127">Element ExpressionBinding CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="80c0a-128">GroupBy Element View(Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="80c0a-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80c0a-129">See Also</span></span>

[<span data-ttu-id="80c0a-130">Kontrolki elementu konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="80c0a-131">Element formant niestandardowy do sterowania do konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="80c0a-132">Element ExpressionBinding CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="80c0a-133">GroupBy Element View(Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="80c0a-134">Name — Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="80c0a-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="80c0a-135">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="80c0a-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
