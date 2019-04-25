---
title: Element ScriptBlock SelectionCondition dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064394"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="822da-102">ScriptBlock, element — SelectionCondition, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="822da-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="822da-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="822da-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="822da-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="822da-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="822da-105">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="822da-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="822da-106">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu EntrySelectedBy CustomEntry dla formantów widoku (Format) elementu SelectionCondition EntrySelectedBy dla kontrolki (Widok Format) elementu ScriptBlock SelectionCondition dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="822da-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="822da-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="822da-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="822da-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="822da-108">Attributes and Elements</span></span>

<span data-ttu-id="822da-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="822da-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="822da-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="822da-110">Attributes</span></span>

<span data-ttu-id="822da-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="822da-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="822da-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="822da-112">Child Elements</span></span>

<span data-ttu-id="822da-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="822da-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="822da-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="822da-114">Parent Elements</span></span>

|<span data-ttu-id="822da-115">Element</span><span class="sxs-lookup"><span data-stu-id="822da-115">Element</span></span>|<span data-ttu-id="822da-116">Opis</span><span class="sxs-lookup"><span data-stu-id="822da-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="822da-117">Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="822da-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="822da-118">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="822da-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="822da-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="822da-119">Text Value</span></span>

<span data-ttu-id="822da-120">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="822da-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="822da-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="822da-121">Remarks</span></span>

<span data-ttu-id="822da-122">Warunek wyboru należy określić co najmniej jedną nazwę skryptu lub właściwości do oceny, ale nie można podać obydwie wartości.</span><span class="sxs-lookup"><span data-stu-id="822da-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="822da-123">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="822da-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="822da-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="822da-124">See Also</span></span>

[<span data-ttu-id="822da-125">Element SelectionCondition EntrySelectedBy dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="822da-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="822da-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="822da-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
