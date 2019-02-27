---
title: Element TypeName dla EntrySelectedBy dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846620"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="32058-102">TypeName, element — EntrySelectedBy, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="32058-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="32058-103">Określa typ architektury .NET, który używa tego wpisu w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="32058-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="32058-104">Nie ma żadnego limitu liczby typów, które można określić dla wpisu tabeli.</span><span class="sxs-lookup"><span data-stu-id="32058-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="32058-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) EntrySelectedBy — Element (Format) TypeName Element konfiguracji dla EntrySelectedBy Aby uzyskać TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="32058-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="32058-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="32058-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="32058-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="32058-107">Attributes and Elements</span></span>

<span data-ttu-id="32058-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="32058-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="32058-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="32058-109">Attributes</span></span>

<span data-ttu-id="32058-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="32058-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="32058-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="32058-111">Child Elements</span></span>

<span data-ttu-id="32058-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="32058-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="32058-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="32058-113">Parent Elements</span></span>

|<span data-ttu-id="32058-114">Element</span><span class="sxs-lookup"><span data-stu-id="32058-114">Element</span></span>|<span data-ttu-id="32058-115">Opis</span><span class="sxs-lookup"><span data-stu-id="32058-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32058-116">Element EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="32058-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="32058-117">Definiuje typy .NET, korzystające z tego wpisu lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="32058-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="32058-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="32058-118">Text Value</span></span>

<span data-ttu-id="32058-119">Określ nazwę typu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="32058-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="32058-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32058-120">Remarks</span></span>

<span data-ttu-id="32058-121">Każdy wpis na liście musi mieć co najmniej jedną nazwę typu, wybór zestawu lub warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="32058-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="32058-122">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="32058-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32058-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32058-123">See Also</span></span>

[<span data-ttu-id="32058-124">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="32058-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="32058-125">Element EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="32058-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="32058-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="32058-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
