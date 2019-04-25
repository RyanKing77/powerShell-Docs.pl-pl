---
title: Element TypeName dla SelectionCondition dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083947"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="c05cb-102">TypeName, element — SelectionCondition, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="c05cb-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c05cb-103">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="c05cb-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="c05cb-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="c05cb-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c05cb-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do kontrolki Element CustomEntry konfiguracji (w formacie) dla formant niestandardowy dla formantów EntrySelectedBy elementu konfiguracji (Format) CustomEntry dla formantów SelectionCondition elementu konfiguracji (Format) EntrySelectedBy dla CustomEntry dla Element TypeName konfiguracji (w formacie) dla SelectionCondition dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c05cb-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c05cb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c05cb-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c05cb-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c05cb-107">Attributes and Elements</span></span>

<span data-ttu-id="c05cb-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="c05cb-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c05cb-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c05cb-109">Attributes</span></span>

<span data-ttu-id="c05cb-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="c05cb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c05cb-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c05cb-111">Child Elements</span></span>

<span data-ttu-id="c05cb-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="c05cb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c05cb-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c05cb-113">Parent Elements</span></span>

|<span data-ttu-id="c05cb-114">Element</span><span class="sxs-lookup"><span data-stu-id="c05cb-114">Element</span></span>|<span data-ttu-id="c05cb-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c05cb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c05cb-116">Element SelectionCondition EntrySelectedBy dla CustomEntry konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c05cb-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="c05cb-117">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="c05cb-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c05cb-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="c05cb-118">Text Value</span></span>

<span data-ttu-id="c05cb-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="c05cb-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c05cb-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c05cb-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c05cb-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c05cb-121">See Also</span></span>

[<span data-ttu-id="c05cb-122">Element SelectionCondition EntrySelectedBy dla CustomEntry konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c05cb-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="c05cb-123">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="c05cb-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
