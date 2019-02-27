---
title: Element ExpressionBinding CustomItem dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848419"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="efa78-102">ExpressionBinding, element — CustomItem, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="efa78-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="efa78-103">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="efa78-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="efa78-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="efa78-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="efa78-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="efa78-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="efa78-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="efa78-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="efa78-107">Attributes and Elements</span></span>

<span data-ttu-id="efa78-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ExpressionBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="efa78-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="efa78-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="efa78-109">Attributes</span></span>

<span data-ttu-id="efa78-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="efa78-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="efa78-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="efa78-111">Child Elements</span></span>

|<span data-ttu-id="efa78-112">Element</span><span class="sxs-lookup"><span data-stu-id="efa78-112">Element</span></span>|<span data-ttu-id="efa78-113">Opis</span><span class="sxs-lookup"><span data-stu-id="efa78-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="efa78-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="efa78-114">Optional element.</span></span><br /><br /> <span data-ttu-id="efa78-115">Definiuje formant, który jest używany przez tę kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="efa78-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="efa78-116">Element CustomControlName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="efa78-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="efa78-117">Optional element.</span></span><br /><br /> <span data-ttu-id="efa78-118">Określa nazwę wspólne kontrolki lub kontrolki widoku.</span><span class="sxs-lookup"><span data-stu-id="efa78-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="efa78-119">Element EnumerateCollection ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="efa78-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="efa78-120">Optional element.</span></span><br /><br /> <span data-ttu-id="efa78-121">Określa, czy elementy kolekcji są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="efa78-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="efa78-122">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="efa78-123">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="efa78-123">Optional element.</span></span><br /><br /> <span data-ttu-id="efa78-124">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="efa78-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="efa78-125">Element PropertyName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="efa78-126">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="efa78-126">Optional element.</span></span><br /><br /> <span data-ttu-id="efa78-127">Określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="efa78-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="efa78-128">Element ScriptBlock ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="efa78-129">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="efa78-129">Optional element.</span></span><br /><br /> <span data-ttu-id="efa78-130">Określa skrypt, którego wartość jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="efa78-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="efa78-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="efa78-131">Parent Elements</span></span>

|<span data-ttu-id="efa78-132">Element</span><span class="sxs-lookup"><span data-stu-id="efa78-132">Element</span></span>|<span data-ttu-id="efa78-133">Opis</span><span class="sxs-lookup"><span data-stu-id="efa78-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="efa78-134">Element CustomItem CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="efa78-135">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="efa78-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="efa78-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efa78-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="efa78-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efa78-137">See Also</span></span>

[<span data-ttu-id="efa78-138">Element CustomItem CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="efa78-139">Element CustomControlName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="efa78-140">Element EnumerateCollection ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="efa78-141">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="efa78-142">Element PropertyName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="efa78-143">Element ScriptBlock ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="efa78-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="efa78-144">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="efa78-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
