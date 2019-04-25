---
title: Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065924"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="d15ca-102">ExpressionBinding, element — CustomItem, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="d15ca-103">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="d15ca-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="d15ca-104">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="d15ca-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d15ca-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy Element konfiguracji elementu CustomEntries widoku (Format), formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formant niestandardowy do widoku ( Format) elementu CustomItem CustomEntry dla formant niestandardowy widok (w formacie) elementu ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d15ca-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d15ca-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="d15ca-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d15ca-107">Attributes and Elements</span></span>

<span data-ttu-id="d15ca-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ExpressionBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="d15ca-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d15ca-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d15ca-109">Attributes</span></span>

<span data-ttu-id="d15ca-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="d15ca-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d15ca-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d15ca-111">Child Elements</span></span>

|<span data-ttu-id="d15ca-112">Element</span><span class="sxs-lookup"><span data-stu-id="d15ca-112">Element</span></span>|<span data-ttu-id="d15ca-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d15ca-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="d15ca-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d15ca-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d15ca-115">Definiuje formant, który jest używany przez tę kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="d15ca-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="d15ca-116">Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d15ca-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d15ca-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d15ca-118">Określa nazwę wspólne kontrolki lub kontrolki widoku.</span><span class="sxs-lookup"><span data-stu-id="d15ca-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="d15ca-119">Element EnumerateCollection ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d15ca-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d15ca-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d15ca-121">Określono, że elementy kolekcji są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d15ca-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="d15ca-122">Element ItemSelectionCondition ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="d15ca-123">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d15ca-123">Optional element.</span></span><br /><br /> <span data-ttu-id="d15ca-124">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="d15ca-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="d15ca-125">Element PropertyName ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d15ca-126">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d15ca-126">Optional element.</span></span><br /><br /> <span data-ttu-id="d15ca-127">Określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="d15ca-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="d15ca-128">Element ScriptBlock ExpressionBinding dla CustomCustomControl widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d15ca-129">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d15ca-129">Optional element.</span></span><br /><br /> <span data-ttu-id="d15ca-130">Określa skrypt, którego wartość jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="d15ca-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d15ca-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d15ca-131">Parent Elements</span></span>

|<span data-ttu-id="d15ca-132">Element</span><span class="sxs-lookup"><span data-stu-id="d15ca-132">Element</span></span>|<span data-ttu-id="d15ca-133">Opis</span><span class="sxs-lookup"><span data-stu-id="d15ca-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d15ca-134">Element CustomItem CustomEntry dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="d15ca-135">Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="d15ca-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d15ca-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d15ca-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d15ca-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d15ca-137">See Also</span></span>

[<span data-ttu-id="d15ca-138">Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d15ca-139">Element EnumerateCollection ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d15ca-140">Element ItemSelectionCondition ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="d15ca-141">Element PropertyName ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d15ca-142">Element ScriptBlock ExpressionBinding dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d15ca-143">Element CustomItem CustomEntry dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="d15ca-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d15ca-144">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="d15ca-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
