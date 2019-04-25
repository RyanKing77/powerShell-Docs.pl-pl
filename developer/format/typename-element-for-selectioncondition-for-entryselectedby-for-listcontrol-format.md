---
title: Element TypeName dla SelectionCondition dla EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083862"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="de159-102">TypeName, element — SelectionCondition, EntrySelectedBy, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="de159-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="de159-103">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="de159-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="de159-104">Jeśli występuje ten typ wpisu listy jest używane.</span><span class="sxs-lookup"><span data-stu-id="de159-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="de159-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListEntries elementu EntrySelectedBy elementu ListControl (Format) ListEntry elementu ListControl (Format) elementu SelectionCondition EntrySelectedBy elementu TypeName elementu ListControl (Format) SelectionCondition dla EntrySelectedBy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="de159-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de159-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="de159-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de159-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="de159-107">Attributes and Elements</span></span>

<span data-ttu-id="de159-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="de159-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de159-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="de159-109">Attributes</span></span>

<span data-ttu-id="de159-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="de159-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de159-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="de159-111">Child Elements</span></span>

<span data-ttu-id="de159-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="de159-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="de159-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="de159-113">Parent Elements</span></span>

|<span data-ttu-id="de159-114">Element</span><span class="sxs-lookup"><span data-stu-id="de159-114">Element</span></span>|<span data-ttu-id="de159-115">Opis</span><span class="sxs-lookup"><span data-stu-id="de159-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de159-116">Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="de159-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="de159-117">Określa warunek, który musi istnieć dla tego wpisu listy ma być używany.</span><span class="sxs-lookup"><span data-stu-id="de159-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="de159-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="de159-118">Text Value</span></span>

<span data-ttu-id="de159-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="de159-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="de159-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de159-120">Remarks</span></span>

<span data-ttu-id="de159-121">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="de159-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="de159-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [warunki określające gdy dane są wyświetlane](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="de159-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="de159-123">Aby uzyskać więcej informacji na temat innych części widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="de159-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de159-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de159-124">See Also</span></span>

[<span data-ttu-id="de159-125">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="de159-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="de159-126">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="de159-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="de159-127">Element SelectionCondition EntrySelectedBy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="de159-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="de159-128">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="de159-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
