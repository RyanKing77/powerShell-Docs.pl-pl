---
title: Element ScriptBlock SelectionCondition dla EntrySelectedBy dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064346"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="60fc2-102">ScriptBlock, element — SelectionCondition, EntrySelectedBy, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="60fc2-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="60fc2-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="60fc2-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="60fc2-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="60fc2-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="60fc2-105">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="60fc2-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="60fc2-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu EntrySelectedBy CustomEntry GroupBy (Format) elementu SelectionCondition EntrySelectedBy GroupBy (Format) elementu ScriptBlock SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="60fc2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60fc2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="60fc2-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60fc2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="60fc2-108">Attributes and Elements</span></span>

<span data-ttu-id="60fc2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="60fc2-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60fc2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="60fc2-110">Attributes</span></span>

<span data-ttu-id="60fc2-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="60fc2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60fc2-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="60fc2-112">Child Elements</span></span>

<span data-ttu-id="60fc2-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="60fc2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60fc2-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="60fc2-114">Parent Elements</span></span>

|<span data-ttu-id="60fc2-115">Element</span><span class="sxs-lookup"><span data-stu-id="60fc2-115">Element</span></span>|<span data-ttu-id="60fc2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="60fc2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60fc2-117">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="60fc2-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="60fc2-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="60fc2-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="60fc2-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="60fc2-119">Text Value</span></span>

<span data-ttu-id="60fc2-120">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="60fc2-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="60fc2-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60fc2-121">Remarks</span></span>

<span data-ttu-id="60fc2-122">Warunek wyboru należy określić co najmniej jedną nazwę skryptu lub właściwości do oceny, ale nie można podać obydwie wartości.</span><span class="sxs-lookup"><span data-stu-id="60fc2-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="60fc2-123">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="60fc2-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60fc2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60fc2-124">See Also</span></span>

[<span data-ttu-id="60fc2-125">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="60fc2-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="60fc2-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="60fc2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
