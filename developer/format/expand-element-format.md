---
title: Rozwiń Element (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066009"
---
# <a name="expand-element-format"></a><span data-ttu-id="2240d-102">Expand, element (format)</span><span class="sxs-lookup"><span data-stu-id="2240d-102">Expand Element (Format)</span></span>

<span data-ttu-id="2240d-103">Określa, jak obiekt kolekcji jest rozwinięta, dla tej definicji.</span><span class="sxs-lookup"><span data-stu-id="2240d-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="2240d-104">Konfiguracji elementu (w formacie) elementu DefaultSettings (Format) EnumerableExpansions — Element (Format) EnumerableExpansion elementu (w formacie), rozwiń Element (Format)</span><span class="sxs-lookup"><span data-stu-id="2240d-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2240d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2240d-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2240d-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2240d-106">Attributes and Elements</span></span>

<span data-ttu-id="2240d-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Expand` elementu.</span><span class="sxs-lookup"><span data-stu-id="2240d-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2240d-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2240d-108">Attributes</span></span>

<span data-ttu-id="2240d-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="2240d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2240d-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2240d-110">Child Elements</span></span>

<span data-ttu-id="2240d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="2240d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2240d-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2240d-112">Parent Elements</span></span>

|<span data-ttu-id="2240d-113">Element</span><span class="sxs-lookup"><span data-stu-id="2240d-113">Element</span></span>|<span data-ttu-id="2240d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2240d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2240d-115">Element EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="2240d-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="2240d-116">Definiuje sposób określonej kolekcji .NET, które obiekty są rozszerzane, gdy są one wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="2240d-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2240d-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="2240d-117">Text Value</span></span>

<span data-ttu-id="2240d-118">Określ jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="2240d-118">Specify one of the following values:</span></span>

- <span data-ttu-id="2240d-119">EnumOnly: Wyświetla tylko właściwości obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2240d-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="2240d-120">CoreOnly: Wyświetla tylko właściwości obiektu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2240d-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="2240d-121">Zarówno: Wyświetla właściwości obiektów w kolekcji i właściwości obiektu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2240d-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="2240d-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2240d-122">Remarks</span></span>

<span data-ttu-id="2240d-123">Ten element jest używany do definiowania sposobu wyświetlania obiektów kolekcji i obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2240d-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="2240d-124">W tym przypadku obiekt kolekcji odnosi się do dowolnego obiektu, który obsługuje **System.Collections.ICollection** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2240d-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="2240d-125">Zachowanie domyślne jest do wyświetlenia tylko właściwości obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2240d-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="2240d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2240d-126">See Also</span></span>

[<span data-ttu-id="2240d-127">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="2240d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
