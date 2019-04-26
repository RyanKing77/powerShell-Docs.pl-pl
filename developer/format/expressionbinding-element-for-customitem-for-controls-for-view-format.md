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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065955"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="512ad-102">ExpressionBinding, element — CustomItem, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="512ad-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="512ad-103">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="512ad-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="512ad-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="512ad-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="512ad-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="512ad-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="512ad-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="512ad-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="512ad-107">Attributes and Elements</span></span>

<span data-ttu-id="512ad-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ExpressionBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="512ad-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="512ad-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="512ad-109">Attributes</span></span>

<span data-ttu-id="512ad-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="512ad-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="512ad-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="512ad-111">Child Elements</span></span>

|<span data-ttu-id="512ad-112">Element</span><span class="sxs-lookup"><span data-stu-id="512ad-112">Element</span></span>|<span data-ttu-id="512ad-113">Opis</span><span class="sxs-lookup"><span data-stu-id="512ad-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="512ad-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="512ad-114">Optional element.</span></span><br /><br /> <span data-ttu-id="512ad-115">Definiuje formant, który jest używany przez tę kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="512ad-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="512ad-116">Element CustomControlName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="512ad-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="512ad-117">Optional element.</span></span><br /><br /> <span data-ttu-id="512ad-118">Określa nazwę wspólne kontrolki lub kontrolki widoku.</span><span class="sxs-lookup"><span data-stu-id="512ad-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="512ad-119">Element EnumerateCollection ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="512ad-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="512ad-120">Optional element.</span></span><br /><br /> <span data-ttu-id="512ad-121">Określa, czy elementy kolekcji są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="512ad-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="512ad-122">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="512ad-123">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="512ad-123">Optional element.</span></span><br /><br /> <span data-ttu-id="512ad-124">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="512ad-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="512ad-125">Element PropertyName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="512ad-126">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="512ad-126">Optional element.</span></span><br /><br /> <span data-ttu-id="512ad-127">Określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="512ad-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="512ad-128">Element ScriptBlock ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="512ad-129">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="512ad-129">Optional element.</span></span><br /><br /> <span data-ttu-id="512ad-130">Określa skrypt, którego wartość jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="512ad-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="512ad-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="512ad-131">Parent Elements</span></span>

|<span data-ttu-id="512ad-132">Element</span><span class="sxs-lookup"><span data-stu-id="512ad-132">Element</span></span>|<span data-ttu-id="512ad-133">Opis</span><span class="sxs-lookup"><span data-stu-id="512ad-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="512ad-134">Element CustomItem CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="512ad-135">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="512ad-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="512ad-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="512ad-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="512ad-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="512ad-137">See Also</span></span>

[<span data-ttu-id="512ad-138">Element CustomItem CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="512ad-139">Element CustomControlName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="512ad-140">Element EnumerateCollection ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="512ad-141">Element ItemSelectionCondition ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="512ad-142">Element PropertyName ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="512ad-143">Element ScriptBlock ExpressionBinding dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="512ad-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="512ad-144">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="512ad-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
