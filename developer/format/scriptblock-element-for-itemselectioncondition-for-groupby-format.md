---
title: Element ScriptBlock ItemSelectionCondition dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064547"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="7541d-102">ScriptBlock, element — ItemSelectionCondition, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7541d-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="7541d-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="7541d-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="7541d-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i formant jest używany.</span><span class="sxs-lookup"><span data-stu-id="7541d-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="7541d-105">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="7541d-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7541d-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem GroupBy (Format) elementu ItemSelectionCondition ExpressionBinding elementu ScriptBlock GroupBy (Format) ItemSelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7541d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7541d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7541d-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7541d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7541d-108">Attributes and Elements</span></span>

<span data-ttu-id="7541d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="7541d-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7541d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7541d-110">Attributes</span></span>

<span data-ttu-id="7541d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="7541d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7541d-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7541d-112">Child Elements</span></span>

<span data-ttu-id="7541d-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="7541d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7541d-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7541d-114">Parent Elements</span></span>

|<span data-ttu-id="7541d-115">Element</span><span class="sxs-lookup"><span data-stu-id="7541d-115">Element</span></span>|<span data-ttu-id="7541d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="7541d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7541d-117">Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7541d-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7541d-118">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="7541d-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7541d-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="7541d-119">Text Value</span></span>

<span data-ttu-id="7541d-120">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="7541d-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7541d-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7541d-121">Remarks</span></span>

<span data-ttu-id="7541d-122">Jeśli ten element jest używany, nie można określić [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) elementu podczas definiowania warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="7541d-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="7541d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7541d-123">See Also</span></span>

[<span data-ttu-id="7541d-124">Element ItemSelectionCondition ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7541d-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7541d-125">Element PropertyName ItemSelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7541d-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="7541d-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="7541d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
