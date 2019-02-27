---
title: Element TypeName dla EntrySelectedBy dla CustomEntry widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848797"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="0750d-102">TypeName, element — EntrySelectedBy, CustomEntry, View (format)</span><span class="sxs-lookup"><span data-stu-id="0750d-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="0750d-103">Określa typ architektury .NET, który używa tej definicji widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="0750d-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="0750d-104">Nie ma żadnego limitu liczby typów, które można określić dla definicji.</span><span class="sxs-lookup"><span data-stu-id="0750d-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="0750d-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla EntrySelectedBy widoku (Format) Element CustomEntry widoku (Format) elementu TypeName EntrySelectedBy dla CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="0750d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0750d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0750d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0750d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0750d-107">Attributes and Elements</span></span>

<span data-ttu-id="0750d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="0750d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0750d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0750d-109">Attributes</span></span>

<span data-ttu-id="0750d-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="0750d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0750d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0750d-111">Child Elements</span></span>

<span data-ttu-id="0750d-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="0750d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0750d-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0750d-113">Parent Elements</span></span>

|<span data-ttu-id="0750d-114">Element</span><span class="sxs-lookup"><span data-stu-id="0750d-114">Element</span></span>|<span data-ttu-id="0750d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="0750d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0750d-116">Element EntrySelectedBy CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="0750d-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="0750d-117">Definiuje typy .NET, używające tej kontrolki niestandardowej definicji widoku lub warunek, który musi istnieć, aby ta definicja ma być używany.</span><span class="sxs-lookup"><span data-stu-id="0750d-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0750d-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="0750d-118">Text Value</span></span>

<span data-ttu-id="0750d-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="0750d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0750d-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0750d-120">Remarks</span></span>

<span data-ttu-id="0750d-121">Każda definicja widoku formantu niestandardowego musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="0750d-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0750d-122">Aby uzyskać więcej informacji o składnikach widoku kontrolki niestandardowej, zobacz [Tworzenie niestandardowych formantów](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0750d-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0750d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0750d-123">See Also</span></span>

[<span data-ttu-id="0750d-124">Tworzenie niestandardowych formantów</span><span class="sxs-lookup"><span data-stu-id="0750d-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="0750d-125">Element EntrySelectedBy CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="0750d-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0750d-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="0750d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
