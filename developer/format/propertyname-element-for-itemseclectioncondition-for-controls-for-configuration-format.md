---
title: Element PropertyName ItemSeclectionCondition dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064908"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="8865c-102">PropertyName, element — ItemSelectionCondition, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8865c-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8865c-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="8865c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8865c-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany.</span><span class="sxs-lookup"><span data-stu-id="8865c-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="8865c-105">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="8865c-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8865c-106">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ExpressionBinding CustomItem dla formantów dla konfiguracji (Format) Element ItemSelectionCondition ExpressionBinding dla formantów PropertyName elementu konfiguracji (Format) ItemSeclectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="8865c-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8865c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8865c-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8865c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8865c-108">Attributes and Elements</span></span>

<span data-ttu-id="8865c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="8865c-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8865c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8865c-110">Attributes</span></span>

<span data-ttu-id="8865c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="8865c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8865c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8865c-112">Child Elements</span></span>

<span data-ttu-id="8865c-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="8865c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8865c-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8865c-114">Parent Elements</span></span>

|<span data-ttu-id="8865c-115">Element</span><span class="sxs-lookup"><span data-stu-id="8865c-115">Element</span></span>|<span data-ttu-id="8865c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8865c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8865c-117">Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="8865c-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8865c-118">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="8865c-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8865c-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="8865c-119">Text Value</span></span>

<span data-ttu-id="8865c-120">Określ nazwę właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="8865c-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="8865c-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8865c-121">Remarks</span></span>

<span data-ttu-id="8865c-122">Jeśli ten element jest używany, nie można określić [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elementu podczas definiowania warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="8865c-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="8865c-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8865c-123">See Also</span></span>

[<span data-ttu-id="8865c-124">Element ScriptBlock ItemSeclectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="8865c-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="8865c-125">Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="8865c-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="8865c-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="8865c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
