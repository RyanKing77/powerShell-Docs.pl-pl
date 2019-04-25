---
title: Element SelectionSetName EntrySelectedBy dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075651"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="67e0c-102">SelectionSetName, element — EntrySelectedBy, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="67e0c-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="67e0c-103">Określa zestaw typów .NET, korzystających z tej definicji formantu.</span><span class="sxs-lookup"><span data-stu-id="67e0c-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="67e0c-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="67e0c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="67e0c-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy dla formantów widoku (Format) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu EntrySelectedBy CustomEntry dla formantów widoku (Format) elementu SelectionSetName EntrySelectedBy dla kontrolki (Widok Format)</span><span class="sxs-lookup"><span data-stu-id="67e0c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67e0c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="67e0c-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="67e0c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="67e0c-107">Attributes and Elements</span></span>

<span data-ttu-id="67e0c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="67e0c-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67e0c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="67e0c-109">Attributes</span></span>

<span data-ttu-id="67e0c-110">Brak</span><span class="sxs-lookup"><span data-stu-id="67e0c-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="67e0c-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="67e0c-111">Child Elements</span></span>

<span data-ttu-id="67e0c-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="67e0c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67e0c-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="67e0c-113">Parent Elements</span></span>

|<span data-ttu-id="67e0c-114">Element</span><span class="sxs-lookup"><span data-stu-id="67e0c-114">Element</span></span>|<span data-ttu-id="67e0c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="67e0c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67e0c-116">Element EntrySelectedBy CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="67e0c-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="67e0c-117">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="67e0c-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67e0c-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="67e0c-118">Text Value</span></span>

<span data-ttu-id="67e0c-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="67e0c-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="67e0c-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67e0c-120">Remarks</span></span>

<span data-ttu-id="67e0c-121">Każda definicja kontrolka musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="67e0c-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="67e0c-122">Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="67e0c-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="67e0c-123">Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia wybór](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="67e0c-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67e0c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67e0c-124">See Also</span></span>

[<span data-ttu-id="67e0c-125">Element EntrySelectedBy CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="67e0c-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="67e0c-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="67e0c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
