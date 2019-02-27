---
title: Element SelectionSetName EntrySelectedBy dla EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851534"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="da5ca-102">SelectionSetName, element — EntrySelectedBy, EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="da5ca-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="da5ca-103">Określa zestaw typów .NET, które są rozszerzane przez tę definicję.</span><span class="sxs-lookup"><span data-stu-id="da5ca-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="da5ca-104">— Element (w formacie) DefaultSettings — Element (Format) EnumerableExpansions — Element (Format) EnumerableExpansion — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionSetName EnumerableExpansion (Format) EntrySelectedBy dla EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="da5ca-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="da5ca-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="da5ca-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="da5ca-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="da5ca-106">Attributes and Elements</span></span>

<span data-ttu-id="da5ca-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="da5ca-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="da5ca-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="da5ca-108">Attributes</span></span>

<span data-ttu-id="da5ca-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="da5ca-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="da5ca-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="da5ca-110">Child Elements</span></span>

<span data-ttu-id="da5ca-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="da5ca-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="da5ca-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="da5ca-112">Parent Elements</span></span>

|<span data-ttu-id="da5ca-113">Element</span><span class="sxs-lookup"><span data-stu-id="da5ca-113">Element</span></span>|<span data-ttu-id="da5ca-114">Opis</span><span class="sxs-lookup"><span data-stu-id="da5ca-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="da5ca-115">Element EntrySelectedBy EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="da5ca-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="da5ca-116">Definiuje obiekty kolekcji .NET, które są rozszerzane przez tę definicję.</span><span class="sxs-lookup"><span data-stu-id="da5ca-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="da5ca-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="da5ca-117">Text Value</span></span>

<span data-ttu-id="da5ca-118">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="da5ca-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="da5ca-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da5ca-119">Remarks</span></span>

<span data-ttu-id="da5ca-120">Każda definicja należy określić co najmniej jedną nazwę typu, zestaw zaznaczenia lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="da5ca-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="da5ca-121">Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="da5ca-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="da5ca-122">Na przykład można utworzyć widoku tabeli i widok listy, aby uzyskać ten sam zestaw obiektów.</span><span class="sxs-lookup"><span data-stu-id="da5ca-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="da5ca-123">Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia z obiektów w celu wyświetlenia](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="da5ca-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="da5ca-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da5ca-124">See Also</span></span>

[<span data-ttu-id="da5ca-125">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="da5ca-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="da5ca-126">Element EntrySelectedBy EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="da5ca-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="da5ca-127">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="da5ca-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
