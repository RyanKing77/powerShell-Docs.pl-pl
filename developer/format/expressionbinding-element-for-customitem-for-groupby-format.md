---
title: Element ExpressionBinding CustomItem dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065907"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="73b51-102">ExpressionBinding, element — CustomItem, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="73b51-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="73b51-103">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="73b51-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="73b51-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="73b51-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="73b51-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73b51-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="73b51-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="73b51-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="73b51-107">Attributes and Elements</span></span>

<span data-ttu-id="73b51-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ExpressionBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="73b51-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="73b51-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="73b51-109">Attributes</span></span>

<span data-ttu-id="73b51-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="73b51-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73b51-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="73b51-111">Child Elements</span></span>

|<span data-ttu-id="73b51-112">Element</span><span class="sxs-lookup"><span data-stu-id="73b51-112">Element</span></span>|<span data-ttu-id="73b51-113">Opis</span><span class="sxs-lookup"><span data-stu-id="73b51-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="73b51-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="73b51-114">Optional element.</span></span><br /><br /> <span data-ttu-id="73b51-115">Definiuje formant, który jest używany przez tę kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="73b51-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="73b51-116">Element CustomControlName ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="73b51-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="73b51-117">Optional element.</span></span><br /><br /> <span data-ttu-id="73b51-118">Określa nazwę wspólne kontrolki lub kontrolki widoku.</span><span class="sxs-lookup"><span data-stu-id="73b51-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="73b51-119">[Element EnumerateCollection ExpressionBinding dla grupowania (w formacie)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection elementu ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="73b51-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="73b51-120">Optional element.</span></span><br /><br /> <span data-ttu-id="73b51-121">Określono, że elementy kolekcji są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="73b51-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="73b51-122">Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="73b51-123">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="73b51-123">Optional element.</span></span><br /><br /> <span data-ttu-id="73b51-124">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="73b51-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="73b51-125">Element PropertyName ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="73b51-126">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="73b51-126">Optional element.</span></span><br /><br /> <span data-ttu-id="73b51-127">Określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="73b51-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="73b51-128">Element ScriptBlock ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="73b51-129">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="73b51-129">Optional element.</span></span><br /><br /> <span data-ttu-id="73b51-130">Określa skrypt, którego wartość jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="73b51-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73b51-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="73b51-131">Parent Elements</span></span>

|<span data-ttu-id="73b51-132">Element</span><span class="sxs-lookup"><span data-stu-id="73b51-132">Element</span></span>|<span data-ttu-id="73b51-133">Opis</span><span class="sxs-lookup"><span data-stu-id="73b51-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73b51-134">Element CustomItem CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="73b51-135">Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="73b51-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="73b51-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73b51-136">See Also</span></span>

[<span data-ttu-id="73b51-137">Element CustomControlName ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="73b51-138">Element EnumerateCollection ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="73b51-139">Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="73b51-140">Element PropertyName ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="73b51-141">Element ScriptBlock ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="73b51-142">Element CustomItem CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="73b51-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="73b51-143">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="73b51-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
