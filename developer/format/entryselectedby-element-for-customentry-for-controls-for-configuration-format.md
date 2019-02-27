---
title: Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: e930e4422afd203feda6a389655ff8a355e3bec0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848678"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="d42fd-102">EntrySelectedBy, element — CustomEntry, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d42fd-103">Definiuje typy .NET, korzystających z definicji formantu typowego lub warunek, który musi istnieć dla tej kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="d42fd-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="d42fd-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="d42fd-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d42fd-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów EntrySelectedBy elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d42fd-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d42fd-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d42fd-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d42fd-107">Attributes and Elements</span></span>

<span data-ttu-id="d42fd-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EntrySelectedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="d42fd-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d42fd-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d42fd-109">Attributes</span></span>

<span data-ttu-id="d42fd-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="d42fd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d42fd-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d42fd-111">Child Elements</span></span>

|<span data-ttu-id="d42fd-112">Element</span><span class="sxs-lookup"><span data-stu-id="d42fd-112">Element</span></span>|<span data-ttu-id="d42fd-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d42fd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d42fd-114">Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d42fd-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d42fd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d42fd-116">Określa warunek, który musi istnieć przez wspólnej definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="d42fd-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="d42fd-117">Element SelectionSetName EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="d42fd-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d42fd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d42fd-119">Określa zestaw typów .NET, korzystających z tej definicji wspólnej kontroli.</span><span class="sxs-lookup"><span data-stu-id="d42fd-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="d42fd-120">Element TypeName dla EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d42fd-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d42fd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d42fd-122">Określa typ architektury .NET, który używa tej definicji wspólnej kontroli.</span><span class="sxs-lookup"><span data-stu-id="d42fd-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d42fd-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d42fd-123">Parent Elements</span></span>

|<span data-ttu-id="d42fd-124">Element</span><span class="sxs-lookup"><span data-stu-id="d42fd-124">Element</span></span>|<span data-ttu-id="d42fd-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d42fd-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d42fd-126">Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="d42fd-127">Zawiera definicję wspólnej kontroli.</span><span class="sxs-lookup"><span data-stu-id="d42fd-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d42fd-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d42fd-128">Remarks</span></span>

<span data-ttu-id="d42fd-129">Jako minimum Każda definicja musi mieć co najmniej jeden typ .NET, zestawu wyboru lub wyboru warunek określony.</span><span class="sxs-lookup"><span data-stu-id="d42fd-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="d42fd-130">Nie ma żadnych maksymalny limit liczby typów, ustawia zaznaczenie lub zaznaczenie warunki, które można określić.</span><span class="sxs-lookup"><span data-stu-id="d42fd-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="d42fd-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d42fd-131">See Also</span></span>

[<span data-ttu-id="d42fd-132">Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="d42fd-133">Element SelectionSetName EntrySelectedBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="d42fd-134">Element CustomEntry formant niestandardowy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="d42fd-135">Element TypeName dla EntrySelectdBy dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="d42fd-135">TypeName Element for EntrySelectdBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="d42fd-136">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="d42fd-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
