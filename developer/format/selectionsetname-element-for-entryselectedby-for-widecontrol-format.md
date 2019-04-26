---
title: Element SelectionSetName EntrySelectedBy dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064034"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="4322b-102">SelectionSetName, element — EntrySelectedBy, WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="4322b-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="4322b-103">Określa zestaw obiektów platformy .NET dla definicji.</span><span class="sxs-lookup"><span data-stu-id="4322b-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="4322b-104">Definicja jest używana zawsze, gdy wyświetlony zostanie jeden z tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="4322b-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="4322b-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionSetName WideEntry (Format) EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4322b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4322b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4322b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4322b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4322b-107">Attributes and Elements</span></span>

<span data-ttu-id="4322b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="4322b-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4322b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4322b-109">Attributes</span></span>

<span data-ttu-id="4322b-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="4322b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4322b-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4322b-111">Child Elements</span></span>

<span data-ttu-id="4322b-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="4322b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4322b-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4322b-113">Parent Elements</span></span>

|<span data-ttu-id="4322b-114">Element</span><span class="sxs-lookup"><span data-stu-id="4322b-114">Element</span></span>|<span data-ttu-id="4322b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4322b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4322b-116">Element EntrySelectedBy WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4322b-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="4322b-117">Definiuje typy .NET, korzystające z tego wpisu szeroki lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="4322b-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4322b-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="4322b-118">Text Value</span></span>

<span data-ttu-id="4322b-119">Określ nazwę zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="4322b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4322b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4322b-120">Remarks</span></span>

<span data-ttu-id="4322b-121">Każda definicja należy określić jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="4322b-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="4322b-122">Wybór zestawy są zwykle używane zdefiniować grupy obiektów, które są używane w wielu widoków.</span><span class="sxs-lookup"><span data-stu-id="4322b-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="4322b-123">Na przykład można utworzyć widoku tabeli i widok listy, aby uzyskać ten sam zestaw obiektów.</span><span class="sxs-lookup"><span data-stu-id="4322b-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="4322b-124">Aby uzyskać więcej informacji na temat definiowania zestawów wybór zobacz [Definiowanie ustawia z obiektów w celu wyświetlenia](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="4322b-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="4322b-125">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4322b-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4322b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4322b-126">See Also</span></span>

[<span data-ttu-id="4322b-127">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="4322b-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4322b-128">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="4322b-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="4322b-129">Element EntrySelectedBy WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4322b-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="4322b-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="4322b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
