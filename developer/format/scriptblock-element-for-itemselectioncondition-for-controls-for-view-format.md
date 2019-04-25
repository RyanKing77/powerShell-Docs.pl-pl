---
title: Element ScriptBlock ItemSelectionCondition dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064717"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="c1dc2-102">ScriptBlock, element — ItemSelectionCondition, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="c1dc2-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="c1dc2-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="c1dc2-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="c1dc2-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i formant jest używany.</span><span class="sxs-lookup"><span data-stu-id="c1dc2-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="c1dc2-105">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="c1dc2-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c1dc2-106">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla formantów widoku (Format) Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format) elementu ScriptBlock ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="c1dc2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1dc2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1dc2-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1dc2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c1dc2-108">Attributes and Elements</span></span>

<span data-ttu-id="c1dc2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="c1dc2-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1dc2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c1dc2-110">Attributes</span></span>

<span data-ttu-id="c1dc2-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="c1dc2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1dc2-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c1dc2-112">Child Elements</span></span>

<span data-ttu-id="c1dc2-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="c1dc2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1dc2-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c1dc2-114">Parent Elements</span></span>

|<span data-ttu-id="c1dc2-115">Element</span><span class="sxs-lookup"><span data-stu-id="c1dc2-115">Element</span></span>|<span data-ttu-id="c1dc2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c1dc2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1dc2-117">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="c1dc2-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c1dc2-118">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="c1dc2-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c1dc2-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="c1dc2-119">Text Value</span></span>

<span data-ttu-id="c1dc2-120">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="c1dc2-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1dc2-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1dc2-121">Remarks</span></span>

<span data-ttu-id="c1dc2-122">Jeśli ten element jest używany, nie można określić [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) elementu podczas definiowania warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="c1dc2-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1dc2-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1dc2-123">See Also</span></span>

[<span data-ttu-id="c1dc2-124">Element PropertyName ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="c1dc2-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="c1dc2-125">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="c1dc2-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c1dc2-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="c1dc2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
