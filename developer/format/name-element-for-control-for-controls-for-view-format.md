---
title: Nazwa elementu dla formantu dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065108"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="ea4a5-102">Name, element — Control, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="ea4a5-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="ea4a5-103">Określa nazwę formantu.</span><span class="sxs-lookup"><span data-stu-id="ea4a5-103">Specifies the name of the control.</span></span>

<span data-ttu-id="ea4a5-104">Konfiguracji elementu (w formacie) ViewDefinitions — Element (Format) widok Element (Format) kontroluje elementu formantu elementu (w formacie) dla formantów dla elementu nazwa widoku (Format) dla kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ea4a5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea4a5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea4a5-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea4a5-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ea4a5-106">Attributes and Elements</span></span>

<span data-ttu-id="ea4a5-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Name` elementu.</span><span class="sxs-lookup"><span data-stu-id="ea4a5-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea4a5-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ea4a5-108">Attributes</span></span>

<span data-ttu-id="ea4a5-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="ea4a5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea4a5-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ea4a5-110">Child Elements</span></span>

<span data-ttu-id="ea4a5-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="ea4a5-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ea4a5-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ea4a5-112">Parent Elements</span></span>

|<span data-ttu-id="ea4a5-113">Element</span><span class="sxs-lookup"><span data-stu-id="ea4a5-113">Element</span></span>|<span data-ttu-id="ea4a5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ea4a5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea4a5-115">Elementu formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ea4a5-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="ea4a5-116">Definiuje formant, który może służyć przez widok i nazwę, która jest używana do odwołania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ea4a5-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ea4a5-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="ea4a5-117">Text Value</span></span>

<span data-ttu-id="ea4a5-118">Określ nazwę, która jest używana do odwołania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ea4a5-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea4a5-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea4a5-119">Remarks</span></span>

<span data-ttu-id="ea4a5-120">Nazwa określona w tym miejscu może służyć w następujących elementów można odwoływać się do tego formantu.</span><span class="sxs-lookup"><span data-stu-id="ea4a5-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="ea4a5-121">Podczas tworzenia tabeli, lista, szeroki lub niestandardowe kontrolki widoku, można określić formantu przez następujący element: [GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="ea4a5-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="ea4a5-122">Podczas tworzenia inny formant, który może służyć przez widok, można określić tego formantu przez następujący element: [Element ExpressionBinding CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="ea4a5-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="ea4a5-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea4a5-123">See Also</span></span>

[<span data-ttu-id="ea4a5-124">GroupBy — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ea4a5-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="ea4a5-125">Element ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ea4a5-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="ea4a5-126">Elementu formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ea4a5-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="ea4a5-127">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="ea4a5-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
