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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065465"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="9babc-102">ItemSelectionCondition, element — ExpressionBinding, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="9babc-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="9babc-103">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9babc-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="9babc-104">Nie ma żadnego limitu, liczbę warunków wyboru, które mogą być określone dla elementu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9babc-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="9babc-105">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="9babc-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9babc-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem GroupBy (Format) elementu ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9babc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9babc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9babc-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9babc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9babc-108">Attributes and Elements</span></span>

<span data-ttu-id="9babc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ItemSelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="9babc-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9babc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9babc-110">Attributes</span></span>

<span data-ttu-id="9babc-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="9babc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9babc-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9babc-112">Child Elements</span></span>

|<span data-ttu-id="9babc-113">Element</span><span class="sxs-lookup"><span data-stu-id="9babc-113">Element</span></span>|<span data-ttu-id="9babc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9babc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9babc-115">Element PropertyName ItemSelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9babc-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="9babc-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9babc-116">Optional element.</span></span><br /><br /> <span data-ttu-id="9babc-117">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="9babc-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="9babc-118">Element ScriptBlock ItemSelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9babc-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="9babc-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9babc-119">Optional element.</span></span><br /><br /> <span data-ttu-id="9babc-120">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="9babc-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9babc-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9babc-121">Parent Elements</span></span>

|<span data-ttu-id="9babc-122">Element</span><span class="sxs-lookup"><span data-stu-id="9babc-122">Element</span></span>|<span data-ttu-id="9babc-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9babc-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9babc-124">Element ExpressionBinding CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9babc-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="9babc-125">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="9babc-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9babc-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9babc-126">Remarks</span></span>

<span data-ttu-id="9babc-127">Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="9babc-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="9babc-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9babc-128">See Also</span></span>

[<span data-ttu-id="9babc-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9babc-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="9babc-130">Element ExpressionBinding CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9babc-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
