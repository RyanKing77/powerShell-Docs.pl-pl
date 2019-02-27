---
title: Formant niestandardowy Element widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850491"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="c3706-102">CustomControl, element — View (format)</span><span class="sxs-lookup"><span data-stu-id="c3706-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="c3706-103">Definiuje format formantu niestandardowego dla widoku.</span><span class="sxs-lookup"><span data-stu-id="c3706-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="c3706-104">Konfiguracji elementu (w formacie) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) formant niestandardowy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c3706-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3706-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3706-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3706-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c3706-106">Attributes and Elements</span></span>

<span data-ttu-id="c3706-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomControl` elementu.</span><span class="sxs-lookup"><span data-stu-id="c3706-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="c3706-108">Należy określić jeden element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="c3706-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3706-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3706-109">Attributes</span></span>

<span data-ttu-id="c3706-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="c3706-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3706-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c3706-111">Child Elements</span></span>

|<span data-ttu-id="c3706-112">Element</span><span class="sxs-lookup"><span data-stu-id="c3706-112">Element</span></span>|<span data-ttu-id="c3706-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c3706-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3706-114">Element CustomEntries formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="c3706-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="c3706-115">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="c3706-115">Required element.</span></span><br /><br /> <span data-ttu-id="c3706-116">Zawiera definicje widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="c3706-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c3706-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3706-117">Parent Elements</span></span>

|<span data-ttu-id="c3706-118">Element</span><span class="sxs-lookup"><span data-stu-id="c3706-118">Element</span></span>|<span data-ttu-id="c3706-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c3706-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3706-120">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="c3706-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c3706-121">Określa widok, który służy do wyświetlania jeden lub więcej obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c3706-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c3706-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3706-122">Remarks</span></span>

<span data-ttu-id="c3706-123">W większości przypadków tylko jedną definicję, jest wymagana dla każdego widoku kontroli, ale istnieje możliwość określenia wiele definicji, jeśli chcesz wyświetlić różne obiekty platformy .NET przy użyciu tego samego widoku.</span><span class="sxs-lookup"><span data-stu-id="c3706-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="c3706-124">W takich przypadkach możesz podać definicję osobne dla każdego obiektu lub grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="c3706-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3706-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3706-125">See Also</span></span>

[<span data-ttu-id="c3706-126">Element CustomEntries formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="c3706-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c3706-127">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="c3706-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c3706-128">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="c3706-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
