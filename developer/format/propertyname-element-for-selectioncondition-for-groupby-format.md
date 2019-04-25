---
title: Element PropertyName SelectionCondition dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064819"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="34ba1-102">PropertyName, element — SelectionCondition, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="34ba1-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="34ba1-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="34ba1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="34ba1-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="34ba1-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="34ba1-105">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="34ba1-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="34ba1-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu EntrySelectedBy CustomEntry GroupBy (Format) elementu SelectionCondition EntrySelectedBy GroupBy (Format) elementu PropertyName SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="34ba1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34ba1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="34ba1-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34ba1-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34ba1-108">Attributes and Elements</span></span>

<span data-ttu-id="34ba1-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="34ba1-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34ba1-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34ba1-110">Attributes</span></span>

<span data-ttu-id="34ba1-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="34ba1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34ba1-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34ba1-112">Child Elements</span></span>

<span data-ttu-id="34ba1-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="34ba1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34ba1-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34ba1-114">Parent Elements</span></span>

|<span data-ttu-id="34ba1-115">Element</span><span class="sxs-lookup"><span data-stu-id="34ba1-115">Element</span></span>|<span data-ttu-id="34ba1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="34ba1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34ba1-117">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="34ba1-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="34ba1-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="34ba1-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34ba1-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="34ba1-119">Text Value</span></span>

<span data-ttu-id="34ba1-120">Określ nazwę właściwości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="34ba1-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="34ba1-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34ba1-121">Remarks</span></span>

<span data-ttu-id="34ba1-122">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="34ba1-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="34ba1-123">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="34ba1-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34ba1-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34ba1-124">See Also</span></span>

[<span data-ttu-id="34ba1-125">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="34ba1-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="34ba1-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="34ba1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
