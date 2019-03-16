---
title: Element TypeName dla SelectionCondition dla EntrySelectedBy dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056011"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="8905b-102">TypeName, element — SelectionCondition, EntrySelectedBy, WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="8905b-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="8905b-103">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="8905b-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="8905b-104">Jeśli występuje ten typ definicji jest używany.</span><span class="sxs-lookup"><span data-stu-id="8905b-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="8905b-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu SelectionCondition WideEntry (Format) EntrySelectedBy WideEntry (Format) elementu TypeName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8905b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8905b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8905b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8905b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8905b-107">Attributes and Elements</span></span>

<span data-ttu-id="8905b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="8905b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8905b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8905b-109">Attributes</span></span>

<span data-ttu-id="8905b-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="8905b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8905b-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8905b-111">Child Elements</span></span>

<span data-ttu-id="8905b-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="8905b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8905b-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8905b-113">Parent Elements</span></span>

|<span data-ttu-id="8905b-114">Element</span><span class="sxs-lookup"><span data-stu-id="8905b-114">Element</span></span>|<span data-ttu-id="8905b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8905b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8905b-116">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8905b-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="8905b-117">Określa warunek, który musi istnieć dla tego wpisu szerokiego ma być używany.</span><span class="sxs-lookup"><span data-stu-id="8905b-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8905b-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="8905b-118">Text Value</span></span>

<span data-ttu-id="8905b-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="8905b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8905b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8905b-120">Remarks</span></span>

<span data-ttu-id="8905b-121">Warunek wyboru można określić typ architektury .NET lub zaznaczenie ustawiona, ale nie można podać obydwie wartości.</span><span class="sxs-lookup"><span data-stu-id="8905b-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="8905b-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8905b-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8905b-123">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="8905b-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8905b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8905b-124">See Also</span></span>

[<span data-ttu-id="8905b-125">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="8905b-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8905b-126">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="8905b-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8905b-127">Element SelectionCondition EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8905b-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="8905b-128">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8905b-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="8905b-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="8905b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
