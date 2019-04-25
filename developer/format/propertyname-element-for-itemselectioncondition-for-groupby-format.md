---
title: Element PropertyName ItemSelectionCondition dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064768"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="54412-102">PropertyName, element — ItemSelectionCondition, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="54412-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="54412-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="54412-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="54412-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany.</span><span class="sxs-lookup"><span data-stu-id="54412-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="54412-105">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="54412-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="54412-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem GroupBy (Format) elementu ItemSelectionCondition ExpressionBinding elementu PropertyName GroupBy (Format) ItemSelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="54412-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54412-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="54412-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54412-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="54412-108">Attributes and Elements</span></span>

<span data-ttu-id="54412-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="54412-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="54412-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="54412-110">Attributes</span></span>

<span data-ttu-id="54412-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="54412-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54412-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="54412-112">Child Elements</span></span>

<span data-ttu-id="54412-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="54412-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="54412-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="54412-114">Parent Elements</span></span>

|<span data-ttu-id="54412-115">Element</span><span class="sxs-lookup"><span data-stu-id="54412-115">Element</span></span>|<span data-ttu-id="54412-116">Opis</span><span class="sxs-lookup"><span data-stu-id="54412-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54412-117">Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="54412-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="54412-118">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="54412-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="54412-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="54412-119">Text Value</span></span>

<span data-ttu-id="54412-120">Określ nazwę właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="54412-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="54412-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54412-121">Remarks</span></span>

<span data-ttu-id="54412-122">Jeśli ten element jest używany, nie można określić [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) elementu podczas definiowania warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="54412-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="54412-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54412-123">See Also</span></span>

[<span data-ttu-id="54412-124">Element ScriptBlock ItemSelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="54412-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="54412-125">Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="54412-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="54412-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="54412-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
