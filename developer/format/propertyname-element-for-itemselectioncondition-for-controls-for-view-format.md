---
title: Element PropertyName ItemSelectionCondition dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075855"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="cec8c-102">PropertyName, element — ItemSelectionCondition, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="cec8c-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="cec8c-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="cec8c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="cec8c-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany.</span><span class="sxs-lookup"><span data-stu-id="cec8c-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="cec8c-105">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="cec8c-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="cec8c-106">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla formantów widoku (Format) Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format) elementu PropertyName ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="cec8c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cec8c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="cec8c-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cec8c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cec8c-108">Attributes and Elements</span></span>

<span data-ttu-id="cec8c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="cec8c-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cec8c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cec8c-110">Attributes</span></span>

<span data-ttu-id="cec8c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="cec8c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cec8c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cec8c-112">Child Elements</span></span>

<span data-ttu-id="cec8c-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="cec8c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cec8c-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cec8c-114">Parent Elements</span></span>

|<span data-ttu-id="cec8c-115">Element</span><span class="sxs-lookup"><span data-stu-id="cec8c-115">Element</span></span>|<span data-ttu-id="cec8c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="cec8c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cec8c-117">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="cec8c-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="cec8c-118">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="cec8c-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cec8c-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="cec8c-119">Text Value</span></span>

<span data-ttu-id="cec8c-120">Określ nazwę właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="cec8c-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="cec8c-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cec8c-121">Remarks</span></span>

<span data-ttu-id="cec8c-122">Jeśli ten element jest używany, nie można określić [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) elementu podczas definiowania warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="cec8c-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="cec8c-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cec8c-123">See Also</span></span>

[<span data-ttu-id="cec8c-124">Element ScriptBlock ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="cec8c-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="cec8c-125">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="cec8c-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cec8c-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="cec8c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
