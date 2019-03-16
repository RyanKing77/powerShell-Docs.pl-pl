---
title: Element ScriptBlock SelectionCondition dla EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057777"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="30094-102">ScriptBlock, element — SelectionCondition, EntrySelectedBy, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="30094-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="30094-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="30094-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="30094-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i wpis na liście jest używany.</span><span class="sxs-lookup"><span data-stu-id="30094-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="30094-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition ListEntry (Format) EntrySelectedBy ListEntry (Format) elementu ScriptBlock SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="30094-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="30094-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="30094-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="30094-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="30094-107">Attributes and Elements</span></span>

<span data-ttu-id="30094-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="30094-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="30094-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="30094-109">Attributes</span></span>

<span data-ttu-id="30094-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="30094-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="30094-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="30094-111">Child Elements</span></span>

<span data-ttu-id="30094-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="30094-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="30094-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="30094-113">Parent Elements</span></span>

|<span data-ttu-id="30094-114">Element</span><span class="sxs-lookup"><span data-stu-id="30094-114">Element</span></span>|<span data-ttu-id="30094-115">Opis</span><span class="sxs-lookup"><span data-stu-id="30094-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="30094-116">Element SelectionCondition EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="30094-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="30094-117">Określa warunek, który musi istnieć dla tego wpisu listy ma być używany.</span><span class="sxs-lookup"><span data-stu-id="30094-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="30094-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="30094-118">Text Value</span></span>

<span data-ttu-id="30094-119">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="30094-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="30094-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30094-120">Remarks</span></span>

<span data-ttu-id="30094-121">Warunek wyboru należy określić co najmniej jedną nazwę skryptu lub właściwości do oceny, ale nie można podać obydwie wartości.</span><span class="sxs-lookup"><span data-stu-id="30094-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="30094-122">(Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="30094-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="30094-123">Aby uzyskać więcej informacji o innych składnikach widoku listy, zobacz [widok listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="30094-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30094-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30094-124">See Also</span></span>

[<span data-ttu-id="30094-125">Element ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="30094-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="30094-126">Element PropertyName SelectionCondition dla EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="30094-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="30094-127">Element SelectionCondition EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="30094-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="30094-128">Widok listy</span><span class="sxs-lookup"><span data-stu-id="30094-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="30094-129">Definiowanie warunki, gdy jest używany widok wpisu lub elementu</span><span class="sxs-lookup"><span data-stu-id="30094-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="30094-130">Pisanie programu Windows PowerShell, formatowania i typy plików</span><span class="sxs-lookup"><span data-stu-id="30094-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
