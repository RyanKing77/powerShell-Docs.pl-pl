---
title: Element SelectionSetName EntrySelectedBy dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850246"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="4e43e-102">SelectionSetName, element — EntrySelectedBy, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="4e43e-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4e43e-103">Określa zestaw typów .NET, korzystających z tej definicji formantu.</span><span class="sxs-lookup"><span data-stu-id="4e43e-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="4e43e-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="4e43e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4e43e-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów EntrySelectedBy elementu konfiguracji (Format) CustomEntry dla formantów SelectionSetName elementu konfiguracji (Format) EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="4e43e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e43e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e43e-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e43e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e43e-107">Attributes and Elements</span></span>

<span data-ttu-id="4e43e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="4e43e-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e43e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e43e-109">Attributes</span></span>

<span data-ttu-id="4e43e-110">Brak</span><span class="sxs-lookup"><span data-stu-id="4e43e-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e43e-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e43e-111">Child Elements</span></span>

<span data-ttu-id="4e43e-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="4e43e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4e43e-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e43e-113">Parent Elements</span></span>

|<span data-ttu-id="4e43e-114">Element</span><span class="sxs-lookup"><span data-stu-id="4e43e-114">Element</span></span>|<span data-ttu-id="4e43e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4e43e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e43e-116">Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="4e43e-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="4e43e-117">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="4e43e-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4e43e-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="4e43e-118">Text Value</span></span>

<span data-ttu-id="4e43e-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="4e43e-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4e43e-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e43e-120">Remarks</span></span>

<span data-ttu-id="4e43e-121">Każda definicja kontrolka musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="4e43e-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4e43e-122">Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="4e43e-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="4e43e-123">Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia wybór](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="4e43e-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e43e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e43e-124">See Also</span></span>

[<span data-ttu-id="4e43e-125">Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="4e43e-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="4e43e-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="4e43e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
