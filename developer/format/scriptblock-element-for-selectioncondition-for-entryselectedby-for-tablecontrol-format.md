---
title: Element ScriptBlock SelectionCondition dla EntrySelectedBy dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846515"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="b6694-102">ScriptBlock, element — SelectionCondition, EntrySelectedBy, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b6694-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="b6694-103">Określa blok skryptu, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="b6694-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="b6694-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i służy wpisu tabeli.</span><span class="sxs-lookup"><span data-stu-id="b6694-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="b6694-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) EntrySelectedBy Element konfiguracji dla TableRowEntry (Format) Element SelectionCondition EntrySelectedBy TableRowEntry (Format) elementu ScriptBlock SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b6694-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b6694-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6694-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6694-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b6694-107">Attributes and Elements</span></span>

<span data-ttu-id="b6694-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="b6694-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6694-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6694-109">Attributes</span></span>

<span data-ttu-id="b6694-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="b6694-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6694-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b6694-111">Child Elements</span></span>

<span data-ttu-id="b6694-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="b6694-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b6694-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b6694-113">Parent Elements</span></span>

|<span data-ttu-id="b6694-114">Element</span><span class="sxs-lookup"><span data-stu-id="b6694-114">Element</span></span>|<span data-ttu-id="b6694-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b6694-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b6694-116">Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b6694-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b6694-117">Określa warunek, który musi istnieć dla tego wpisu w tabeli ma być używany.</span><span class="sxs-lookup"><span data-stu-id="b6694-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b6694-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="b6694-118">Text Value</span></span>

<span data-ttu-id="b6694-119">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="b6694-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6694-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6694-120">Remarks</span></span>

<span data-ttu-id="b6694-121">Warunek wyboru należy określić co najmniej jeden skrypt bloku lub nazwę właściwości, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="b6694-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="b6694-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b6694-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b6694-123">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b6694-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6694-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6694-124">See Also</span></span>

[<span data-ttu-id="b6694-125">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="b6694-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b6694-126">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="b6694-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b6694-127">Element PropertyName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b6694-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="b6694-128">Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b6694-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b6694-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="b6694-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
