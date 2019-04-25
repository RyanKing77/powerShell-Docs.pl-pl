---
title: Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065516"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="c1da1-102">ItemSelectionCondition, element — ExpressionBinding, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="c1da1-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c1da1-103">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="c1da1-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="c1da1-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="c1da1-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c1da1-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ExpressionBinding CustomItem dla formantów dla konfiguracji (Format) Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c1da1-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1da1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1da1-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1da1-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c1da1-107">Attributes and Elements</span></span>

<span data-ttu-id="c1da1-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ItemSelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="c1da1-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1da1-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c1da1-109">Attributes</span></span>

<span data-ttu-id="c1da1-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="c1da1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1da1-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c1da1-111">Child Elements</span></span>

|<span data-ttu-id="c1da1-112">Element</span><span class="sxs-lookup"><span data-stu-id="c1da1-112">Element</span></span>|<span data-ttu-id="c1da1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c1da1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1da1-114">Element PropertyName ItemSelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c1da1-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="c1da1-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c1da1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c1da1-116">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="c1da1-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="c1da1-117">Element ScriptBlock ItemSelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c1da1-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="c1da1-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c1da1-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c1da1-119">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="c1da1-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c1da1-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c1da1-120">Parent Elements</span></span>

|<span data-ttu-id="c1da1-121">Element</span><span class="sxs-lookup"><span data-stu-id="c1da1-121">Element</span></span>|<span data-ttu-id="c1da1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c1da1-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1da1-123">Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c1da1-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="c1da1-124">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="c1da1-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1da1-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1da1-125">Remarks</span></span>

<span data-ttu-id="c1da1-126">Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="c1da1-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1da1-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1da1-127">See Also</span></span>

[<span data-ttu-id="c1da1-128">Element PropertyName ItemSelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c1da1-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c1da1-129">Element ScriptBlock ItemSelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c1da1-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="c1da1-130">Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c1da1-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="c1da1-131">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="c1da1-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
