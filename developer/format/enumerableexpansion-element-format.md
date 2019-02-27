---
title: Element EnumerableExpansion (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847397"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="06939-102">EnumerableExpansion, element (format)</span><span class="sxs-lookup"><span data-stu-id="06939-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="06939-103">Definiuje sposób określonej kolekcji .NET, które obiekty są rozszerzane, gdy są one wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="06939-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="06939-104">Konfiguracji elementu (w formacie) elementu DefaultSettings (Format) EnumerableExpansions — Element (Format) EnumerableExpansion elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="06939-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06939-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="06939-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06939-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06939-106">Attributes and Elements</span></span>

<span data-ttu-id="06939-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EnumerableExpansion` elementu.</span><span class="sxs-lookup"><span data-stu-id="06939-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06939-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06939-108">Attributes</span></span>

<span data-ttu-id="06939-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="06939-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06939-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06939-110">Child Elements</span></span>

|<span data-ttu-id="06939-111">Element</span><span class="sxs-lookup"><span data-stu-id="06939-111">Element</span></span>|<span data-ttu-id="06939-112">Opis</span><span class="sxs-lookup"><span data-stu-id="06939-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06939-113">Element EntrySelectedBy EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="06939-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="06939-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="06939-114">Optional element.</span></span><br /><br /> <span data-ttu-id="06939-115">Definiuje, które obiekty kolekcji .NET są rozszerzane przez tę definicję.</span><span class="sxs-lookup"><span data-stu-id="06939-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="06939-116">Rozwiń Element (Format)</span><span class="sxs-lookup"><span data-stu-id="06939-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="06939-117">Określa, jak obiekt kolekcji jest rozwinięta, dla tej definicji.</span><span class="sxs-lookup"><span data-stu-id="06939-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06939-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06939-118">Parent Elements</span></span>

|<span data-ttu-id="06939-119">Element</span><span class="sxs-lookup"><span data-stu-id="06939-119">Element</span></span>|<span data-ttu-id="06939-120">Opis</span><span class="sxs-lookup"><span data-stu-id="06939-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06939-121">Element EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="06939-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="06939-122">Definiuje różne sposoby tej kolekcji .NET, które obiekty są rozszerzane, gdy są one wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="06939-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06939-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06939-123">Remarks</span></span>

<span data-ttu-id="06939-124">Ten element jest używany do definiowania sposobu wyświetlania obiektów kolekcji i obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="06939-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="06939-125">W tym przypadku obiekt kolekcji odnosi się do dowolnego obiektu, który obsługuje **System.Collections.ICollection** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="06939-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="06939-126">Zachowanie domyślne jest do wyświetlenia tylko właściwości obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="06939-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="06939-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06939-127">See Also</span></span>

[<span data-ttu-id="06939-128">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="06939-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
