---
title: Element TypeName dla EntrySelectedBy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084032"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="afe8f-102">TypeName, element — EntrySelectedBy, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="afe8f-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="afe8f-103">Określa typ architektury .NET, która używa tego wpisu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="afe8f-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="afe8f-104">Nie ma żadnego limitu liczby typów, które mogą być określone dla wpisu listy.</span><span class="sxs-lookup"><span data-stu-id="afe8f-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="afe8f-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu TypeName ListEntry (Format) EntrySelectedBy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="afe8f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="afe8f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="afe8f-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="afe8f-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="afe8f-107">Attributes and Elements</span></span>

<span data-ttu-id="afe8f-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="afe8f-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="afe8f-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="afe8f-109">Attributes</span></span>

<span data-ttu-id="afe8f-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="afe8f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="afe8f-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="afe8f-111">Child Elements</span></span>

<span data-ttu-id="afe8f-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="afe8f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="afe8f-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="afe8f-113">Parent Elements</span></span>

|<span data-ttu-id="afe8f-114">Element</span><span class="sxs-lookup"><span data-stu-id="afe8f-114">Element</span></span>|<span data-ttu-id="afe8f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="afe8f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="afe8f-116">Element EntrySelectedBy ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="afe8f-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="afe8f-117">Definiuje typy .NET, korzystające z tego wpisu listy lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="afe8f-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="afe8f-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="afe8f-118">Text Value</span></span>

<span data-ttu-id="afe8f-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="afe8f-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="afe8f-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afe8f-120">Remarks</span></span>

<span data-ttu-id="afe8f-121">Każdy wpis na liście musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="afe8f-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="afe8f-122">Aby uzyskać więcej informacji o sposobie korzystania z tego elementu w widoku listy, zobacz [widok listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="afe8f-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="afe8f-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="afe8f-123">Example</span></span>

<span data-ttu-id="afe8f-124">Poniższy przykład pokazuje, jak określić wejścia widok listy wyboru.</span><span class="sxs-lookup"><span data-stu-id="afe8f-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="afe8f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afe8f-125">See Also</span></span>

[<span data-ttu-id="afe8f-126">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="afe8f-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="afe8f-127">Element EntrySelectedBy ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="afe8f-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="afe8f-128">Element SelectionSetName EntrySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="afe8f-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="afe8f-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="afe8f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
