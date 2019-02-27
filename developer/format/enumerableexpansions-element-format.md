---
title: Element EnumerableExpansions (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849791"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="4f202-102">EnumerableExpansions, element (format)</span><span class="sxs-lookup"><span data-stu-id="4f202-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="4f202-103">Definiuje, jak rozszerzyć obiekty kolekcji .NET, gdy są one wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="4f202-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="4f202-104">Element EnumerableExpansions DefaultSettings — Element (w formacie) — Element (w formacie) konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="4f202-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f202-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f202-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f202-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4f202-106">Attributes and Elements</span></span>

<span data-ttu-id="4f202-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `EnumerableExpansions` elementu.</span><span class="sxs-lookup"><span data-stu-id="4f202-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="4f202-108">Nie ma żadnego limitu liczby elementów podrzędnych, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="4f202-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f202-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4f202-109">Attributes</span></span>

<span data-ttu-id="4f202-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="4f202-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f202-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4f202-111">Child Elements</span></span>

|<span data-ttu-id="4f202-112">Element</span><span class="sxs-lookup"><span data-stu-id="4f202-112">Element</span></span>|<span data-ttu-id="4f202-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4f202-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f202-114">Element EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="4f202-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="4f202-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4f202-115">Optional element.</span></span><br /><br /> <span data-ttu-id="4f202-116">Definiuje określone obiekty kolekcji .NET, które są rozszerzane, gdy są one wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="4f202-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4f202-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4f202-117">Parent Elements</span></span>

|<span data-ttu-id="4f202-118">Element</span><span class="sxs-lookup"><span data-stu-id="4f202-118">Element</span></span>|<span data-ttu-id="4f202-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4f202-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f202-120">Element DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="4f202-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="4f202-121">Definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="4f202-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4f202-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f202-122">Remarks</span></span>

<span data-ttu-id="4f202-123">Ten element jest używany do definiowania sposobu wyświetlania obiektów kolekcji i obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f202-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="4f202-124">W tym przypadku obiekt kolekcji odnosi się do dowolnego obiektu, który obsługuje **System.Collections.ICollection** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4f202-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f202-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f202-125">See Also</span></span>

[<span data-ttu-id="4f202-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="4f202-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
