---
title: Element PropertyName SelectionCondition dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064700"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="822a1-102">PropertyName, element — SelectionCondition, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="822a1-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="822a1-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="822a1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="822a1-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="822a1-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="822a1-105">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="822a1-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="822a1-106">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy Element konfiguracji elementu CustomEntries widoku (Format), formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formant niestandardowy do widoku ( Format) elementu CustomItem CustomEntry dla formant niestandardowy widok (w formacie) elementu EntrySelectedBy CustomEntry dla formant niestandardowy widok (w formacie) elementu SelectionCondition EntrySelectedBy dla formant niestandardowy do PropertyName widoku (Format) Element SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="822a1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="822a1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="822a1-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="822a1-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="822a1-108">Attributes and Elements</span></span>

<span data-ttu-id="822a1-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="822a1-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="822a1-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="822a1-110">Attributes</span></span>

<span data-ttu-id="822a1-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="822a1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="822a1-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="822a1-112">Child Elements</span></span>

<span data-ttu-id="822a1-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="822a1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="822a1-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="822a1-114">Parent Elements</span></span>

|<span data-ttu-id="822a1-115">Element</span><span class="sxs-lookup"><span data-stu-id="822a1-115">Element</span></span>|<span data-ttu-id="822a1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="822a1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="822a1-117">Element SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="822a1-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="822a1-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="822a1-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="822a1-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="822a1-119">Text Value</span></span>

<span data-ttu-id="822a1-120">Określ nazwę właściwości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="822a1-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="822a1-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="822a1-121">Remarks</span></span>

<span data-ttu-id="822a1-122">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="822a1-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="822a1-123">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="822a1-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="822a1-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="822a1-124">See Also</span></span>

[<span data-ttu-id="822a1-125">Element SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="822a1-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="822a1-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="822a1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
