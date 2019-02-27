---
title: Element PropertyName ItemSelectionCondition dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846487"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="b4027-102">PropertyName, element — ItemSelectionCondition, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="b4027-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="b4027-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="b4027-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b4027-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, a widok jest używany.</span><span class="sxs-lookup"><span data-stu-id="b4027-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="b4027-105">Ten element jest używany podczas definiowania widoku listy.</span><span class="sxs-lookup"><span data-stu-id="b4027-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="b4027-106">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries — Element (Format) ListEntry Element konfiguracji elementu ListControl (Format) elementu ListItems ListEntry dla ListItem elementu ListControl (Format) Element ListItems elementu ListControl (Format) ItemSelectionCondition elementu ListItem elementu PropertyName ListControls ItemSelectionCondition dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b4027-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4027-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4027-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4027-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b4027-108">Attributes and Elements</span></span>

<span data-ttu-id="b4027-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="b4027-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4027-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b4027-110">Attributes</span></span>

<span data-ttu-id="b4027-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="b4027-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4027-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b4027-112">Child Elements</span></span>

<span data-ttu-id="b4027-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="b4027-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b4027-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b4027-114">Parent Elements</span></span>

|<span data-ttu-id="b4027-115">Element</span><span class="sxs-lookup"><span data-stu-id="b4027-115">Element</span></span>|<span data-ttu-id="b4027-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b4027-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4027-117">Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b4027-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="b4027-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="b4027-118">Text Value</span></span>

<span data-ttu-id="b4027-119">Określ nazwę właściwości, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="b4027-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4027-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4027-120">Remarks</span></span>

<span data-ttu-id="b4027-121">Jeśli ten element jest używany, nie można określić [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) elementu podczas definiowania warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="b4027-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4027-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4027-122">See Also</span></span>

[<span data-ttu-id="b4027-123">Element ScriptBlock ItemSelectionCondition dla ListIControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b4027-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="b4027-124">Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b4027-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b4027-125">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="b4027-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
