---
title: Element ScriptBlock ItemSelectionCondition dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851177"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="27a19-102">ScriptBlock, element — ItemSelectionCondition, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="27a19-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="27a19-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="27a19-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="27a19-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i formant jest używany.</span><span class="sxs-lookup"><span data-stu-id="27a19-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="27a19-105">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="27a19-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="27a19-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry widoku (Format) elementu ExpressionBinding CustomItem dla formant niestandardowy dla elementu ItemSelectionCondition widoku (w formacie) dla wiązania wyrażenia dla formant niestandardowy widok (w formacie) elementu ScriptBlock ItemSelectionCondition dla Formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="27a19-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27a19-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="27a19-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27a19-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="27a19-108">Attributes and Elements</span></span>

<span data-ttu-id="27a19-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="27a19-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="27a19-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="27a19-110">Attributes</span></span>

<span data-ttu-id="27a19-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="27a19-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27a19-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="27a19-112">Child Elements</span></span>

<span data-ttu-id="27a19-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="27a19-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="27a19-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="27a19-114">Parent Elements</span></span>

|<span data-ttu-id="27a19-115">Element</span><span class="sxs-lookup"><span data-stu-id="27a19-115">Element</span></span>|<span data-ttu-id="27a19-116">Opis</span><span class="sxs-lookup"><span data-stu-id="27a19-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27a19-117">Element ItemSelectionCondition dla wyrażenia wiązania dla formant niestandardowy, widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="27a19-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="27a19-118">Określa warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="27a19-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="27a19-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="27a19-119">Text Value</span></span>

<span data-ttu-id="27a19-120">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="27a19-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="27a19-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27a19-121">Remarks</span></span>

<span data-ttu-id="27a19-122">Jeśli ten element jest używany, nie można określić [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elementu podczas definiowania warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="27a19-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="27a19-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27a19-123">See Also</span></span>

[<span data-ttu-id="27a19-124">Element PropertyName ItemSelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="27a19-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27a19-125">Element ItemSelectionCondition dla wyrażenia wiązania dla formant niestandardowy, widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="27a19-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="27a19-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="27a19-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
