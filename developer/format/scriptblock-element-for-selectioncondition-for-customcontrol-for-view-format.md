---
title: Element ScriptBlock SelectionCondition dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847803"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="02403-102">ScriptBlock, element — SelectionCondition, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="02403-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="02403-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="02403-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="02403-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="02403-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="02403-105">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="02403-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="02403-106">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy Element konfiguracji elementu CustomEntries widoku (Format), formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formant niestandardowy do widoku ( Format) elementu CustomItem CustomEntry dla formant niestandardowy widok (w formacie) elementu SelectionCondition EntrySelectedBy dla formant niestandardowy widok (w formacie) elementu ScriptBlock SelectionCondition dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="02403-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="02403-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="02403-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="02403-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="02403-108">Attributes and Elements</span></span>

<span data-ttu-id="02403-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="02403-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="02403-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="02403-110">Attributes</span></span>

<span data-ttu-id="02403-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="02403-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="02403-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="02403-112">Child Elements</span></span>

<span data-ttu-id="02403-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="02403-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="02403-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="02403-114">Parent Elements</span></span>

|<span data-ttu-id="02403-115">Element</span><span class="sxs-lookup"><span data-stu-id="02403-115">Element</span></span>|<span data-ttu-id="02403-116">Opis</span><span class="sxs-lookup"><span data-stu-id="02403-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="02403-117">Element SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="02403-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="02403-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="02403-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="02403-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="02403-119">Text Value</span></span>

<span data-ttu-id="02403-120">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="02403-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="02403-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02403-121">Remarks</span></span>

<span data-ttu-id="02403-122">Warunek wyboru należy określić co najmniej jedną nazwę skryptu lub właściwości do oceny, ale nie można podać obydwie wartości.</span><span class="sxs-lookup"><span data-stu-id="02403-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="02403-123">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="02403-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02403-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02403-124">See Also</span></span>

[<span data-ttu-id="02403-125">Element SelectionCondition EntrySelectedBy dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="02403-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="02403-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="02403-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
