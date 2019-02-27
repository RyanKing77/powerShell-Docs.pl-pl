---
title: Element TypeName dla EntrySelectedBy dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850778"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="aefcf-102">TypeName, element — EntrySelectedBy, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="aefcf-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="aefcf-103">Określa typ architektury .NET, która używa tej definicji kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="aefcf-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="aefcf-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="aefcf-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="aefcf-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu EntrySelectedBy CustomEntry GroupBy (Format) elementu TypeName EntrySelectedBy dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="aefcf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aefcf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="aefcf-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aefcf-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aefcf-107">Attributes and Elements</span></span>

<span data-ttu-id="aefcf-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="aefcf-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aefcf-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aefcf-109">Attributes</span></span>

<span data-ttu-id="aefcf-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="aefcf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aefcf-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aefcf-111">Child Elements</span></span>

<span data-ttu-id="aefcf-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="aefcf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aefcf-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aefcf-113">Parent Elements</span></span>

|<span data-ttu-id="aefcf-114">Element</span><span class="sxs-lookup"><span data-stu-id="aefcf-114">Element</span></span>|<span data-ttu-id="aefcf-115">Opis</span><span class="sxs-lookup"><span data-stu-id="aefcf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aefcf-116">Element EntrySelectedBy CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="aefcf-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="aefcf-117">Definiuje typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="aefcf-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aefcf-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="aefcf-118">Text Value</span></span>

<span data-ttu-id="aefcf-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="aefcf-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="aefcf-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aefcf-120">Remarks</span></span>

<span data-ttu-id="aefcf-121">Każda definicja kontrolka musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="aefcf-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="aefcf-122">Aby uzyskać więcej informacji o składnikach widoku kontrolki niestandardowej, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="aefcf-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aefcf-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aefcf-123">See Also</span></span>

[<span data-ttu-id="aefcf-124">Tworzenie niestandardowych formantów</span><span class="sxs-lookup"><span data-stu-id="aefcf-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="aefcf-125">Element EntrySelectedBy CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="aefcf-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="aefcf-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="aefcf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
