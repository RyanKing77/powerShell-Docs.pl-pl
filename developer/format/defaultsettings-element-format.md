---
title: Element DefaultSettings (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: 59cc0514087cc52438e0d1271b8b77a7799eb32c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846578"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="9177e-102">DefaultSettings, element (format)</span><span class="sxs-lookup"><span data-stu-id="9177e-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="9177e-103">Definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="9177e-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="9177e-104">Typowe ustawienia obejmują wyświetlanie błędów, zawijania tekstu w tabelach, określające, jak kolekcje są rozwinięte i więcej.</span><span class="sxs-lookup"><span data-stu-id="9177e-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="9177e-105">Element DefaultSettings (Format) — Element konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="9177e-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9177e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9177e-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9177e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9177e-107">Attributes and Elements</span></span>

<span data-ttu-id="9177e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `DefaultSettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="9177e-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9177e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9177e-109">Attributes</span></span>

<span data-ttu-id="9177e-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="9177e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9177e-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9177e-111">Child Elements</span></span>

|<span data-ttu-id="9177e-112">Element</span><span class="sxs-lookup"><span data-stu-id="9177e-112">Element</span></span>|<span data-ttu-id="9177e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9177e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9177e-114">Element DisplayError (Frmat)</span><span class="sxs-lookup"><span data-stu-id="9177e-114">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="9177e-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9177e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9177e-116">Określa, czy ciąg #ERR są wyświetlane, gdy wystąpi błąd podczas wyświetlania elementu danych.</span><span class="sxs-lookup"><span data-stu-id="9177e-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="9177e-117">Element EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="9177e-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="9177e-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9177e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9177e-119">Definiuje różne sposoby, które .NET obiekty zostaną rozwinięte, gdy są one wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="9177e-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="9177e-120">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="9177e-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="9177e-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9177e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9177e-122">Określa minimalną liczbę właściwości, które musi zawierać obiekt, aby wyświetlić obiekt w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="9177e-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="9177e-123">Element ShowError (Format)</span><span class="sxs-lookup"><span data-stu-id="9177e-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="9177e-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9177e-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9177e-125">Określa, czy rekord pełny komunikat o błędzie jest wyświetlany, gdy wystąpi błąd podczas wyświetlania elementu danych.</span><span class="sxs-lookup"><span data-stu-id="9177e-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="9177e-126">Element WrapTables (Format)</span><span class="sxs-lookup"><span data-stu-id="9177e-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="9177e-127">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9177e-127">Optional element.</span></span><br /><br /> <span data-ttu-id="9177e-128">Określa, że dane w tabeli jest przenoszony do następnego wiersza, jeśli nie mieści się na szerokość kolumny.</span><span class="sxs-lookup"><span data-stu-id="9177e-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9177e-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9177e-129">Parent Elements</span></span>

|<span data-ttu-id="9177e-130">Element</span><span class="sxs-lookup"><span data-stu-id="9177e-130">Element</span></span>|<span data-ttu-id="9177e-131">Opis</span><span class="sxs-lookup"><span data-stu-id="9177e-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9177e-132">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9177e-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="9177e-133">Reprezentuje element najwyższego poziomu w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="9177e-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9177e-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9177e-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="9177e-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9177e-135">See Also</span></span>

[<span data-ttu-id="9177e-136">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9177e-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="9177e-137">Element DisplayError (Frmat)</span><span class="sxs-lookup"><span data-stu-id="9177e-137">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="9177e-138">Element EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="9177e-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="9177e-139">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="9177e-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="9177e-140">Element ShowError (Format)</span><span class="sxs-lookup"><span data-stu-id="9177e-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="9177e-141">Element WrapTables (Format)</span><span class="sxs-lookup"><span data-stu-id="9177e-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="9177e-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9177e-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
