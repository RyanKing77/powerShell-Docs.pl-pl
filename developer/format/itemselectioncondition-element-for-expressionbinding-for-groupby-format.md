---
title: Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844807"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="0ac51-102">ItemSelectionCondition, element — ExpressionBinding, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0ac51-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="0ac51-103">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="0ac51-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="0ac51-104">Nie ma żadnego limitu, liczbę warunków wyboru, które mogą być określone dla elementu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0ac51-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="0ac51-105">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="0ac51-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0ac51-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem GroupBy (Format) elementu ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="0ac51-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ac51-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ac51-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ac51-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0ac51-108">Attributes and Elements</span></span>

<span data-ttu-id="0ac51-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ItemSelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="0ac51-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ac51-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0ac51-110">Attributes</span></span>

<span data-ttu-id="0ac51-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="0ac51-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ac51-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0ac51-112">Child Elements</span></span>

|<span data-ttu-id="0ac51-113">Element</span><span class="sxs-lookup"><span data-stu-id="0ac51-113">Element</span></span>|<span data-ttu-id="0ac51-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0ac51-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ac51-115">Element PropertyName ItemSelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="0ac51-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="0ac51-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0ac51-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0ac51-117">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="0ac51-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0ac51-118">Element ScriptBlock ItemSelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="0ac51-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="0ac51-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0ac51-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0ac51-120">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="0ac51-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0ac51-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0ac51-121">Parent Elements</span></span>

|<span data-ttu-id="0ac51-122">Element</span><span class="sxs-lookup"><span data-stu-id="0ac51-122">Element</span></span>|<span data-ttu-id="0ac51-123">Opis</span><span class="sxs-lookup"><span data-stu-id="0ac51-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ac51-124">Element ExpressionBinding CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="0ac51-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="0ac51-125">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="0ac51-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ac51-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ac51-126">Remarks</span></span>

<span data-ttu-id="0ac51-127">Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="0ac51-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ac51-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ac51-128">See Also</span></span>

[<span data-ttu-id="0ac51-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="0ac51-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="0ac51-130">Element ExpressionBinding CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="0ac51-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
