---
title: Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065950"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="961f1-102">ExpressionBinding, element — CustomItem, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="961f1-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="961f1-103">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="961f1-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="961f1-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="961f1-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="961f1-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="961f1-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="961f1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="961f1-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="961f1-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="961f1-107">Attributes and Elements</span></span>

<span data-ttu-id="961f1-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ExpressionBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="961f1-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="961f1-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="961f1-109">Attributes</span></span>

<span data-ttu-id="961f1-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="961f1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="961f1-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="961f1-111">Child Elements</span></span>

|<span data-ttu-id="961f1-112">Element</span><span class="sxs-lookup"><span data-stu-id="961f1-112">Element</span></span>|<span data-ttu-id="961f1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="961f1-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="961f1-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="961f1-114">Optional element.</span></span><br /><br /> <span data-ttu-id="961f1-115">Definiuje formant, który jest używany przez tę kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="961f1-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="961f1-116">Element CustomControlName ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="961f1-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="961f1-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="961f1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="961f1-118">Określa nazwę wspólne kontrolki lub kontrolki widoku.</span><span class="sxs-lookup"><span data-stu-id="961f1-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="961f1-119">Element EnumerateCollection ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="961f1-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="961f1-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="961f1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="961f1-121">Określono, że elementy kolekcji są wyświetlane przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="961f1-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="961f1-122">Element ItemSelectionCondition ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="961f1-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="961f1-123">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="961f1-123">Optional element.</span></span><br /><br /> <span data-ttu-id="961f1-124">Określa warunek, który musi istnieć dla tego wspólnego formantu ma być używany.</span><span class="sxs-lookup"><span data-stu-id="961f1-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="961f1-125">Element PropertyName ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="961f1-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="961f1-126">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="961f1-126">Optional element.</span></span><br /><br /> <span data-ttu-id="961f1-127">Określa właściwości platformy .NET, którego wartość jest wyświetlana za pomocą wspólnej kontroli.</span><span class="sxs-lookup"><span data-stu-id="961f1-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="961f1-128">Element ScriptBlock ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="961f1-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="961f1-129">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="961f1-129">Optional element.</span></span><br /><br /> <span data-ttu-id="961f1-130">Określa skrypt, którego wartość jest wyświetlana za pomocą wspólnej kontroli.</span><span class="sxs-lookup"><span data-stu-id="961f1-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="961f1-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="961f1-131">Parent Elements</span></span>

|<span data-ttu-id="961f1-132">Element</span><span class="sxs-lookup"><span data-stu-id="961f1-132">Element</span></span>|<span data-ttu-id="961f1-133">Opis</span><span class="sxs-lookup"><span data-stu-id="961f1-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="961f1-134">Element CustomItem CustomEntry dla formantów dla konfiguracji</span><span class="sxs-lookup"><span data-stu-id="961f1-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="961f1-135">Definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="961f1-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="961f1-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="961f1-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="961f1-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="961f1-137">See Also</span></span>

[<span data-ttu-id="961f1-138">Element CustomItem CustomEntry dla formantów dla konfiguracji</span><span class="sxs-lookup"><span data-stu-id="961f1-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="961f1-139">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="961f1-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
