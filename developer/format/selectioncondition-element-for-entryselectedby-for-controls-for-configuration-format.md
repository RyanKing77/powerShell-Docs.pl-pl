---
title: Element SelectionCondition EntrySelectedBy dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845514"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="0bb5f-102">SelectionCondition, element — EntrySelectedBy, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0bb5f-103">Określa warunek, który musi istnieć do wspólnej definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="0bb5f-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0bb5f-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do kontrolki Element CustomEntry konfiguracji (w formacie) dla formant niestandardowy dla formantów EntrySelectedBy elementu konfiguracji (Format) CustomEntry dla formantów SelectionCondition elementu konfiguracji (Format) EntrySelectedBy dla CustomEntry dla Konfiguracja (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0bb5f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bb5f-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0bb5f-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0bb5f-107">Attributes and Elements</span></span>

<span data-ttu-id="0bb5f-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0bb5f-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0bb5f-109">Attributes</span></span>

<span data-ttu-id="0bb5f-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0bb5f-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0bb5f-111">Child Elements</span></span>

|<span data-ttu-id="0bb5f-112">Element</span><span class="sxs-lookup"><span data-stu-id="0bb5f-112">Element</span></span>|<span data-ttu-id="0bb5f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0bb5f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bb5f-114">Element PropertyName SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0bb5f-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0bb5f-116">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0bb5f-117">Element ScriptBlock SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0bb5f-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0bb5f-119">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="0bb5f-120">Element SelectionSetName SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0bb5f-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0bb5f-122">Określa zestaw typów .NET wyzwalającego warunku.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="0bb5f-123">Element TypeName dla SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0bb5f-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0bb5f-125">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0bb5f-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0bb5f-126">Parent Elements</span></span>

|<span data-ttu-id="0bb5f-127">Element</span><span class="sxs-lookup"><span data-stu-id="0bb5f-127">Element</span></span>|<span data-ttu-id="0bb5f-128">Opis</span><span class="sxs-lookup"><span data-stu-id="0bb5f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bb5f-129">Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0bb5f-130">Definiuje typy .NET, korzystających z tego wpisu wspólnej definicji kontroli.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0bb5f-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0bb5f-131">Remarks</span></span>

<span data-ttu-id="0bb5f-132">Podczas definiowania warunek wyboru należy przestrzegać następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="0bb5f-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="0bb5f-133">Warunek wyboru należy określić co najmniej jednej nazwy właściwości lub blok skryptu, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0bb5f-134">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="0bb5f-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0bb5f-135">Aby uzyskać więcej informacji o używaniu wybór warunków, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0bb5f-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bb5f-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bb5f-136">See Also</span></span>

[<span data-ttu-id="0bb5f-137">Element PropertyName SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0bb5f-138">Element ScriptBlock SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0bb5f-139">Element SelectionSetName SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0bb5f-140">Element TypeName dla SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0bb5f-141">Element EntrySelectedBy CustomEntry dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="0bb5f-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="0bb5f-142">Pisanie programu Windows PowerShell, formatowania i typy plików</span><span class="sxs-lookup"><span data-stu-id="0bb5f-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
