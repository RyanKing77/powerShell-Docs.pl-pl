---
title: Element TypeName dla SelectionCondition dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848776"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="16fab-102">TypeName, element — SelectionCondition, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="16fab-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="16fab-103">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="16fab-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="16fab-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="16fab-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="16fab-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu EntrySelectedBy CustomEntry GroupBy (Format) elementu SelectionCondition EntrySelectedBy GroupBy (Format) elementu TypeName SelectionCondition dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="16fab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="16fab-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="16fab-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="16fab-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="16fab-107">Attributes and Elements</span></span>

<span data-ttu-id="16fab-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="16fab-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="16fab-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="16fab-109">Attributes</span></span>

<span data-ttu-id="16fab-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="16fab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="16fab-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="16fab-111">Child Elements</span></span>

<span data-ttu-id="16fab-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="16fab-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="16fab-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="16fab-113">Parent Elements</span></span>

|<span data-ttu-id="16fab-114">Element</span><span class="sxs-lookup"><span data-stu-id="16fab-114">Element</span></span>|<span data-ttu-id="16fab-115">Opis</span><span class="sxs-lookup"><span data-stu-id="16fab-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16fab-116">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="16fab-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="16fab-117">Określa warunek, który musi istnieć dla definicji kontrolki ma być używany.</span><span class="sxs-lookup"><span data-stu-id="16fab-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="16fab-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="16fab-118">Text Value</span></span>

<span data-ttu-id="16fab-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="16fab-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="16fab-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16fab-120">Remarks</span></span>

<span data-ttu-id="16fab-121">Gdy ten element jest określony, nie można określić `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="16fab-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="16fab-122">Aby uzyskać więcej informacji na temat definiowania warunków wybór zobacz [Definiowanie warunków wyświetlania danych](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="16fab-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16fab-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16fab-123">See Also</span></span>

[<span data-ttu-id="16fab-124">Element SelectionCondition EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="16fab-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="16fab-125">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="16fab-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
