---
title: Element PropertyName SelectionCondition dla EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064895"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="710ea-102">PropertyName, element — SelectionCondition, EntrySelectedBy, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="710ea-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="710ea-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="710ea-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="710ea-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i wpis na liście jest używany.</span><span class="sxs-lookup"><span data-stu-id="710ea-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="710ea-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition ListEntry (Format) EntrySelectedBy ListEntry (Format) elementu PropertyName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="710ea-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="710ea-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="710ea-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="710ea-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="710ea-107">Attributes and Elements</span></span>

<span data-ttu-id="710ea-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="710ea-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="710ea-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="710ea-109">Attributes</span></span>

<span data-ttu-id="710ea-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="710ea-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="710ea-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="710ea-111">Child Elements</span></span>

<span data-ttu-id="710ea-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="710ea-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="710ea-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="710ea-113">Parent Elements</span></span>

|<span data-ttu-id="710ea-114">Element</span><span class="sxs-lookup"><span data-stu-id="710ea-114">Element</span></span>|<span data-ttu-id="710ea-115">Opis</span><span class="sxs-lookup"><span data-stu-id="710ea-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="710ea-116">Element SelectionCondition EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="710ea-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="710ea-117">Określa warunek, który musi istnieć dla tego wpisu listy ma być używany.</span><span class="sxs-lookup"><span data-stu-id="710ea-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="710ea-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="710ea-118">Text Value</span></span>

<span data-ttu-id="710ea-119">Określ nazwę właściwości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="710ea-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="710ea-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="710ea-120">Remarks</span></span>

<span data-ttu-id="710ea-121">Warunek wyboru należy określić co najmniej jedną właściwość name lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="710ea-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="710ea-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="710ea-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="710ea-123">Aby uzyskać więcej informacji o innych składnikach widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="710ea-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="710ea-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="710ea-124">See Also</span></span>

[<span data-ttu-id="710ea-125">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="710ea-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="710ea-126">Definiowanie warunków podczas danych jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="710ea-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="710ea-127">Element ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="710ea-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="710ea-128">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="710ea-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="710ea-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="710ea-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
