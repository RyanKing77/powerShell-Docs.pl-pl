---
title: Element ScriptBlock SelectionCondition dla EntrySelectedBy dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851674"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="db784-102">ScriptBlock, element — SelectionCondition, EntrySelectedBy, WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="db784-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="db784-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="db784-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="db784-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i definicja szerokiego wpis jest używana.</span><span class="sxs-lookup"><span data-stu-id="db784-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="db784-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition WideEntry (Format) EntrySelectedBy WideEntry (Format) elementu ScriptBlock SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="db784-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db784-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="db784-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db784-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="db784-107">Attributes and Elements</span></span>

<span data-ttu-id="db784-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="db784-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db784-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="db784-109">Attributes</span></span>

<span data-ttu-id="db784-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="db784-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db784-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="db784-111">Child Elements</span></span>

<span data-ttu-id="db784-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="db784-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="db784-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="db784-113">Parent Elements</span></span>

|<span data-ttu-id="db784-114">Element</span><span class="sxs-lookup"><span data-stu-id="db784-114">Element</span></span>|<span data-ttu-id="db784-115">Opis</span><span class="sxs-lookup"><span data-stu-id="db784-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db784-116">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="db784-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="db784-117">Określa warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="db784-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="db784-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="db784-118">Text Value</span></span>

<span data-ttu-id="db784-119">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="db784-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="db784-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db784-120">Remarks</span></span>

<span data-ttu-id="db784-121">Warunek wyboru należy określić co najmniej jedną nazwę skryptu lub właściwości do oceny, ale nie można podać obydwie wartości.</span><span class="sxs-lookup"><span data-stu-id="db784-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="db784-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="db784-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="db784-123">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [szerokie](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="db784-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db784-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db784-124">See Also</span></span>

[<span data-ttu-id="db784-125">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="db784-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="db784-126">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="db784-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="db784-127">Element PropertyName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="db784-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="db784-128">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="db784-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="db784-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="db784-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
