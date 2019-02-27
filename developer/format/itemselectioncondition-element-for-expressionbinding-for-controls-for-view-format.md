---
title: Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850904"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="93ab6-102">ItemSelectionCondition, element — ExpressionBinding, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="93ab6-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="93ab6-103">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="93ab6-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="93ab6-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="93ab6-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="93ab6-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla formantów widoku (Format) Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="93ab6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93ab6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="93ab6-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93ab6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="93ab6-107">Attributes and Elements</span></span>

<span data-ttu-id="93ab6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ItemSelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="93ab6-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="93ab6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="93ab6-109">Attributes</span></span>

<span data-ttu-id="93ab6-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="93ab6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93ab6-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="93ab6-111">Child Elements</span></span>

|<span data-ttu-id="93ab6-112">Element</span><span class="sxs-lookup"><span data-stu-id="93ab6-112">Element</span></span>|<span data-ttu-id="93ab6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="93ab6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93ab6-114">Element PropertyName ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="93ab6-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="93ab6-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="93ab6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="93ab6-116">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="93ab6-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="93ab6-117">Element ScriptBlock ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="93ab6-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="93ab6-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="93ab6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="93ab6-119">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="93ab6-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="93ab6-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="93ab6-120">Parent Elements</span></span>

|<span data-ttu-id="93ab6-121">Element</span><span class="sxs-lookup"><span data-stu-id="93ab6-121">Element</span></span>|<span data-ttu-id="93ab6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="93ab6-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93ab6-123">Element ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="93ab6-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="93ab6-124">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="93ab6-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="93ab6-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93ab6-125">Remarks</span></span>

<span data-ttu-id="93ab6-126">Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="93ab6-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="93ab6-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93ab6-127">See Also</span></span>

[<span data-ttu-id="93ab6-128">Element PropertyName ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="93ab6-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="93ab6-129">Element ScriptBlock ItemSelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="93ab6-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="93ab6-130">Element ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="93ab6-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="93ab6-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="93ab6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
