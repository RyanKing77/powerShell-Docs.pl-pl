---
title: Element TypeName dla SelectionCondition dla EntrySelectedBy dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083845"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="b39f6-102">TypeName, element — SelectionCondition, EntrySelectedBy, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b39f6-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="b39f6-103">Określa typ architektury .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="b39f6-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="b39f6-104">W przypadku tego typu jest obecny, warunek jest spełniony, i służy wiersza tabeli.</span><span class="sxs-lookup"><span data-stu-id="b39f6-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="b39f6-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) EntrySelectedBy Element konfiguracji dla TableRowEntry (Format) Element SelectionCondition EntrySelectedBy TableRowEntry (Format) elementu TypeName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b39f6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b39f6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b39f6-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b39f6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b39f6-107">Attributes and Elements</span></span>

<span data-ttu-id="b39f6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="b39f6-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b39f6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b39f6-109">Attributes</span></span>

<span data-ttu-id="b39f6-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="b39f6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b39f6-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b39f6-111">Child Elements</span></span>

<span data-ttu-id="b39f6-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="b39f6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b39f6-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b39f6-113">Parent Elements</span></span>

|<span data-ttu-id="b39f6-114">Element</span><span class="sxs-lookup"><span data-stu-id="b39f6-114">Element</span></span>|<span data-ttu-id="b39f6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b39f6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b39f6-116">Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b39f6-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b39f6-117">Określa warunek, który musi istnieć dla tego wiersza tabeli ma być używany.</span><span class="sxs-lookup"><span data-stu-id="b39f6-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b39f6-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="b39f6-118">Text Value</span></span>

<span data-ttu-id="b39f6-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="b39f6-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b39f6-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b39f6-120">Remarks</span></span>

<span data-ttu-id="b39f6-121">Warunek wyboru można określić dowolną liczbę typów .NET lub zaznaczenie Ustawia, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="b39f6-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="b39f6-122">Aby uzyskać więcej informacji o sposobie używania warunków wyboru, zobacz [definiujący warunki dla, gdy wpis widoku lub służy element](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b39f6-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b39f6-123">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b39f6-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b39f6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b39f6-124">See Also</span></span>

[<span data-ttu-id="b39f6-125">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="b39f6-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b39f6-126">Definiowanie warunków, gdy dane są wyświetlane</span><span class="sxs-lookup"><span data-stu-id="b39f6-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b39f6-127">Element SelectionCondition EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b39f6-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b39f6-128">Element SelectionSetName SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b39f6-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b39f6-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="b39f6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
