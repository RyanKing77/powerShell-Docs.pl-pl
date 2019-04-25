---
title: Kontrolowanie elementu dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066774"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="070c1-102">Control, element — Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="070c1-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="070c1-103">Definiuje formant, który może służyć przez widok i nazwę, która jest używana do odwołania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="070c1-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="070c1-104">Element widoku elementu ViewDefinitions (Format) — Element (w formacie) konfiguracji (Format) kontrolki elementu formantu elementu (w formacie) dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="070c1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="070c1-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="070c1-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="070c1-106">Attributes and Elements</span></span>

<span data-ttu-id="070c1-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Control` elementu.</span><span class="sxs-lookup"><span data-stu-id="070c1-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="070c1-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="070c1-108">Attributes</span></span>

<span data-ttu-id="070c1-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="070c1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="070c1-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="070c1-110">Child Elements</span></span>

|<span data-ttu-id="070c1-111">Element</span><span class="sxs-lookup"><span data-stu-id="070c1-111">Element</span></span>|<span data-ttu-id="070c1-112">Opis</span><span class="sxs-lookup"><span data-stu-id="070c1-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="070c1-113">Name — Element dla kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="070c1-114">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="070c1-114">Required element.</span></span><br /><br /> <span data-ttu-id="070c1-115">Określa nazwę formantu.</span><span class="sxs-lookup"><span data-stu-id="070c1-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="070c1-116">Formant niestandardowy Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="070c1-117">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="070c1-117">Required element.</span></span><br /><br /> <span data-ttu-id="070c1-118">Definiuje kontrolki, używany przez ten widok.</span><span class="sxs-lookup"><span data-stu-id="070c1-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="070c1-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="070c1-119">Parent Elements</span></span>

|<span data-ttu-id="070c1-120">Element</span><span class="sxs-lookup"><span data-stu-id="070c1-120">Element</span></span>|<span data-ttu-id="070c1-121">Opis</span><span class="sxs-lookup"><span data-stu-id="070c1-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="070c1-122">Element kontrolki (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="070c1-123">Definiuje kontrolki widoku, które mogą być używane przez określonego widoku.</span><span class="sxs-lookup"><span data-stu-id="070c1-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="070c1-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="070c1-124">Remarks</span></span>

<span data-ttu-id="070c1-125">Ten formant, można określić następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="070c1-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="070c1-126">Element CustomControlName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="070c1-127">Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="070c1-128">Element CustomControlName ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="070c1-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="070c1-129">Element CustomControlName GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="070c1-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="070c1-130">See Also</span></span>

[<span data-ttu-id="070c1-131">Formant niestandardowy Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="070c1-132">Element CustomControlName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="070c1-133">Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="070c1-134">Element CustomControlName ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="070c1-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="070c1-135">Element CustomControlName ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="070c1-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="070c1-136">Element kontrolki (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="070c1-137">Name — Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="070c1-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="070c1-138">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="070c1-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
