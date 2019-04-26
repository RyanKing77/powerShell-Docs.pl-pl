---
title: Element ItemSelectionCondition ExpressionBinding dla formant niestandardowy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065828"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="811e2-102">ItemSelectionCondition, element — ExpressionBinding, CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="811e2-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="811e2-103">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="811e2-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="811e2-104">Nie ma żadnego limitu, liczbę warunków wyboru, które mogą być określone dla elementu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="811e2-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="811e2-105">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="811e2-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="811e2-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry widoku (Format) elementu ExpressionBinding CustomItem dla formant niestandardowy dla elementu ItemSelectionCondition widoku (w formacie) dla wyrażenia wiązania dla formant niestandardowy, widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="811e2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="811e2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="811e2-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="811e2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="811e2-108">Attributes and Elements</span></span>

<span data-ttu-id="811e2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ItemSelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="811e2-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="811e2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="811e2-110">Attributes</span></span>

<span data-ttu-id="811e2-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="811e2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="811e2-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="811e2-112">Child Elements</span></span>

|<span data-ttu-id="811e2-113">Element</span><span class="sxs-lookup"><span data-stu-id="811e2-113">Element</span></span>|<span data-ttu-id="811e2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="811e2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="811e2-115">Element PropertyName ItemSelectionCondition dla formant niestandardowy dla widoku (w formacie</span><span class="sxs-lookup"><span data-stu-id="811e2-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="811e2-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="811e2-116">Optional element.</span></span><br /><br /> <span data-ttu-id="811e2-117">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="811e2-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="811e2-118">Element ScriptBlock ItemSelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="811e2-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="811e2-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="811e2-119">Optional element.</span></span><br /><br /> <span data-ttu-id="811e2-120">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="811e2-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="811e2-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="811e2-121">Parent Elements</span></span>

|<span data-ttu-id="811e2-122">Element</span><span class="sxs-lookup"><span data-stu-id="811e2-122">Element</span></span>|<span data-ttu-id="811e2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="811e2-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="811e2-124">Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="811e2-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="811e2-125">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="811e2-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="811e2-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="811e2-126">Remarks</span></span>

<span data-ttu-id="811e2-127">Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="811e2-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="811e2-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="811e2-128">See Also</span></span>

[<span data-ttu-id="811e2-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="811e2-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="811e2-130">Element ExpressionBinding CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="811e2-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
