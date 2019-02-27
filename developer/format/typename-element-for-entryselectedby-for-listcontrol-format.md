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
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846886"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="11763-102">TypeName, element — EntrySelectedBy, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="11763-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="11763-103">Określa typ architektury .NET, która używa tego wpisu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="11763-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="11763-104">Nie ma żadnego limitu liczby typów, które mogą być określone dla wpisu listy.</span><span class="sxs-lookup"><span data-stu-id="11763-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="11763-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) elementu ListEntries (Format) ListEntry — Element (Format) EntrySelectedBy Element konfiguracji elementu TypeName ListEntry (Format) EntrySelectedBy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="11763-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11763-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="11763-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11763-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="11763-107">Attributes and Elements</span></span>

<span data-ttu-id="11763-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="11763-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11763-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="11763-109">Attributes</span></span>

<span data-ttu-id="11763-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="11763-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11763-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="11763-111">Child Elements</span></span>

<span data-ttu-id="11763-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="11763-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11763-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="11763-113">Parent Elements</span></span>

|<span data-ttu-id="11763-114">Element</span><span class="sxs-lookup"><span data-stu-id="11763-114">Element</span></span>|<span data-ttu-id="11763-115">Opis</span><span class="sxs-lookup"><span data-stu-id="11763-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11763-116">Element EntrySelectedBy ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11763-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="11763-117">Definiuje typy .NET, korzystające z tego wpisu listy lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="11763-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="11763-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="11763-118">Text Value</span></span>

<span data-ttu-id="11763-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="11763-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="11763-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11763-120">Remarks</span></span>

<span data-ttu-id="11763-121">Każdy wpis na liście musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="11763-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="11763-122">Aby uzyskać więcej informacji o sposobie korzystania z tego elementu w widoku listy, zobacz [widok listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="11763-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="11763-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="11763-123">Example</span></span>

<span data-ttu-id="11763-124">Poniższy przykład pokazuje, jak określić wejścia widok listy wyboru.</span><span class="sxs-lookup"><span data-stu-id="11763-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="11763-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11763-125">See Also</span></span>

[<span data-ttu-id="11763-126">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="11763-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="11763-127">Element EntrySelectedBy ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11763-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="11763-128">Element SelectionSetName EnrtySelectedBy dla ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11763-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="11763-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="11763-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
