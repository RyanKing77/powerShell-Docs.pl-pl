---
title: Element PropertyName SelectionCondition dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845080"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="6a99c-102">PropertyName, element — SelectionCondition, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="6a99c-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="6a99c-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="6a99c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="6a99c-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, a ten wpis jest używany.</span><span class="sxs-lookup"><span data-stu-id="6a99c-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="6a99c-105">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="6a99c-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6a99c-106">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu EntrySelectedBy CustomEntry dla formantów widoku (Format) elementu SelectionCondition EntrySelectedBy dla kontrolki (Widok Format) elementu PropertyName SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="6a99c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a99c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a99c-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a99c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a99c-108">Attributes and Elements</span></span>

<span data-ttu-id="6a99c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="6a99c-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a99c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a99c-110">Attributes</span></span>

<span data-ttu-id="6a99c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a99c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a99c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a99c-112">Child Elements</span></span>

<span data-ttu-id="6a99c-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a99c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6a99c-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a99c-114">Parent Elements</span></span>

|<span data-ttu-id="6a99c-115">Element</span><span class="sxs-lookup"><span data-stu-id="6a99c-115">Element</span></span>|<span data-ttu-id="6a99c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="6a99c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a99c-117">Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="6a99c-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6a99c-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="6a99c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6a99c-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="6a99c-119">Text Value</span></span>

<span data-ttu-id="6a99c-120">Określ nazwę właściwości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="6a99c-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a99c-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a99c-121">Remarks</span></span>

<span data-ttu-id="6a99c-122">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="6a99c-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="6a99c-123">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6a99c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a99c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a99c-124">See Also</span></span>

[<span data-ttu-id="6a99c-125">Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="6a99c-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="6a99c-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="6a99c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
