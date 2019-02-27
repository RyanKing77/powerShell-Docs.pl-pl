---
title: Element PropertyName SelectionCondition dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850330"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="2b2dc-102">PropertyName, element — SelectionCondition, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="2b2dc-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2b2dc-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="2b2dc-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="2b2dc-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, a ten wpis jest używany.</span><span class="sxs-lookup"><span data-stu-id="2b2dc-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="2b2dc-105">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="2b2dc-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2b2dc-106">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów EntrySelectedBy elementu konfiguracji (Format) CustomEntry dla formantów SelectionCondition elementu konfiguracji (Format) EntrySelectedBy dla CustomEntry dla konfiguracji ( Format) elementu PropertyName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b2dc-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b2dc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b2dc-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b2dc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2b2dc-108">Attributes and Elements</span></span>

<span data-ttu-id="2b2dc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="2b2dc-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b2dc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2b2dc-110">Attributes</span></span>

<span data-ttu-id="2b2dc-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b2dc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b2dc-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2b2dc-112">Child Elements</span></span>

<span data-ttu-id="2b2dc-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b2dc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b2dc-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2b2dc-114">Parent Elements</span></span>

|<span data-ttu-id="2b2dc-115">Element</span><span class="sxs-lookup"><span data-stu-id="2b2dc-115">Element</span></span>|<span data-ttu-id="2b2dc-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2b2dc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b2dc-117">Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="2b2dc-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="2b2dc-118">Określa warunek, który musi istnieć do wspólnej definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="2b2dc-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2b2dc-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="2b2dc-119">Text Value</span></span>

<span data-ttu-id="2b2dc-120">Określ nazwę właściwości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2b2dc-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b2dc-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b2dc-121">Remarks</span></span>

<span data-ttu-id="2b2dc-122">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="2b2dc-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="2b2dc-123">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2b2dc-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b2dc-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b2dc-124">See Also</span></span>

[<span data-ttu-id="2b2dc-125">Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="2b2dc-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="2b2dc-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="2b2dc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
