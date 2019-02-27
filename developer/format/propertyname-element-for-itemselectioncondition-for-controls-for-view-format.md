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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847950"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="ccff1-102">PropertyName, element — ItemSelectionCondition, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="ccff1-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="ccff1-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="ccff1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ccff1-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany.</span><span class="sxs-lookup"><span data-stu-id="ccff1-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ccff1-105">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="ccff1-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ccff1-106">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla formantów widoku (Format) Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format) elementu PropertyName ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ccff1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ccff1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccff1-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ccff1-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ccff1-108">Attributes and Elements</span></span>

<span data-ttu-id="ccff1-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="ccff1-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ccff1-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ccff1-110">Attributes</span></span>

<span data-ttu-id="ccff1-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="ccff1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ccff1-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ccff1-112">Child Elements</span></span>

<span data-ttu-id="ccff1-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="ccff1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ccff1-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ccff1-114">Parent Elements</span></span>

|<span data-ttu-id="ccff1-115">Element</span><span class="sxs-lookup"><span data-stu-id="ccff1-115">Element</span></span>|<span data-ttu-id="ccff1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ccff1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccff1-117">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ccff1-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="ccff1-118">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ccff1-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ccff1-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="ccff1-119">Text Value</span></span>

<span data-ttu-id="ccff1-120">Określ nazwę właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="ccff1-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccff1-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ccff1-121">Remarks</span></span>

<span data-ttu-id="ccff1-122">Jeśli ten element jest używany, nie można określić [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) elementu podczas definiowania warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="ccff1-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccff1-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccff1-123">See Also</span></span>

[<span data-ttu-id="ccff1-124">Element ScriptBlock ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ccff1-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ccff1-125">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="ccff1-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="ccff1-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="ccff1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
