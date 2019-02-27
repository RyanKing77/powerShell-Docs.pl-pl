---
title: Element ScriptBlock SelectionCondition dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844863"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="a9f12-102">ScriptBlock, element — SelectionCondition, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a9f12-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a9f12-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="a9f12-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a9f12-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany przez definicję.</span><span class="sxs-lookup"><span data-stu-id="a9f12-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="a9f12-105">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="a9f12-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a9f12-106">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów EntrySelectedBy elementu konfiguracji (Format) CustomEntry dla formantów SelectionCondition elementu konfiguracji (Format) EntrySelectedBy dla formantów dla konfiguracji (Format) Element ScriptBlock SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="a9f12-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a9f12-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9f12-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9f12-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a9f12-108">Attributes and Elements</span></span>

<span data-ttu-id="a9f12-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="a9f12-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9f12-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a9f12-110">Attributes</span></span>

<span data-ttu-id="a9f12-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="a9f12-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a9f12-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a9f12-112">Child Elements</span></span>

<span data-ttu-id="a9f12-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="a9f12-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a9f12-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a9f12-114">Parent Elements</span></span>

|<span data-ttu-id="a9f12-115">Element</span><span class="sxs-lookup"><span data-stu-id="a9f12-115">Element</span></span>|<span data-ttu-id="a9f12-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a9f12-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9f12-117">Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="a9f12-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="a9f12-118">Określa warunek, który musi istnieć przez wspólnej definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="a9f12-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a9f12-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="a9f12-119">Text Value</span></span>

<span data-ttu-id="a9f12-120">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="a9f12-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9f12-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9f12-121">Remarks</span></span>

<span data-ttu-id="a9f12-122">Warunek wyboru należy określić co najmniej jedną nazwę skryptu lub właściwości do oceny, ale nie można podać obydwie wartości.</span><span class="sxs-lookup"><span data-stu-id="a9f12-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="a9f12-123">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a9f12-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9f12-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9f12-124">See Also</span></span>

[<span data-ttu-id="a9f12-125">Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="a9f12-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="a9f12-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="a9f12-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
