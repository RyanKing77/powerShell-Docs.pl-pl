---
title: Element PropertyName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850302"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="66459-102">PropertyName, element — SelectionCondition, EntrySelectedBy, TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="66459-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="66459-103">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="66459-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="66459-104">Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i służy wpisu tabeli.</span><span class="sxs-lookup"><span data-stu-id="66459-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="66459-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) EntrySelectedBy Element konfiguracji dla TableRowEntry (Format) Element SelectionCondition EntrySelectedBy TableRowEntry (Format) elementu PropertyName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="66459-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="66459-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="66459-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="66459-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="66459-107">Attributes and Elements</span></span>

<span data-ttu-id="66459-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="66459-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="66459-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="66459-109">Attributes</span></span>

<span data-ttu-id="66459-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="66459-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="66459-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="66459-111">Child Elements</span></span>

<span data-ttu-id="66459-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="66459-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="66459-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="66459-113">Parent Elements</span></span>

|<span data-ttu-id="66459-114">Element</span><span class="sxs-lookup"><span data-stu-id="66459-114">Element</span></span>|<span data-ttu-id="66459-115">Opis</span><span class="sxs-lookup"><span data-stu-id="66459-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66459-116">Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="66459-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="66459-117">Określa warunek, który musi istnieć dla tego wpisu w tabeli ma być używany.</span><span class="sxs-lookup"><span data-stu-id="66459-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="66459-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="66459-118">Text Value</span></span>

<span data-ttu-id="66459-119">Określ nazwę właściwości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="66459-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="66459-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66459-120">Remarks</span></span>

<span data-ttu-id="66459-121">Warunek wyboru należy określić co najmniej jedną właściwość name lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="66459-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="66459-122">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="66459-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="66459-123">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="66459-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66459-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66459-124">See Also</span></span>

[<span data-ttu-id="66459-125">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="66459-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="66459-126">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="66459-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="66459-127">Element ScriptBlock SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="66459-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="66459-128">Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="66459-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="66459-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="66459-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
