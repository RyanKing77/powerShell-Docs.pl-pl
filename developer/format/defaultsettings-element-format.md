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
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066349"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="bbd6c-102">DefaultSettings, element (format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="bbd6c-103">Definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="bbd6c-104">Typowe ustawienia obejmują wyświetlanie błędów, zawijania tekstu w tabelach, określające, jak kolekcje są rozwinięte i więcej.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="bbd6c-105">Element DefaultSettings (Format) — Element konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbd6c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbd6c-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbd6c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bbd6c-107">Attributes and Elements</span></span>

<span data-ttu-id="bbd6c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `DefaultSettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbd6c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bbd6c-109">Attributes</span></span>

<span data-ttu-id="bbd6c-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbd6c-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bbd6c-111">Child Elements</span></span>

|<span data-ttu-id="bbd6c-112">Element</span><span class="sxs-lookup"><span data-stu-id="bbd6c-112">Element</span></span>|<span data-ttu-id="bbd6c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bbd6c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbd6c-114">Element DisplayError (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="bbd6c-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="bbd6c-116">Określa, czy ciąg #ERR są wyświetlane, gdy wystąpi błąd podczas wyświetlania elementu danych.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="bbd6c-117">Element EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="bbd6c-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="bbd6c-119">Definiuje różne sposoby, które .NET obiekty zostaną rozwinięte, gdy są one wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="bbd6c-120">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="bbd6c-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-121">Optional element.</span></span><br /><br /> <span data-ttu-id="bbd6c-122">Określa minimalną liczbę właściwości, które musi zawierać obiekt, aby wyświetlić obiekt w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="bbd6c-123">Element ShowError (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="bbd6c-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-124">Optional element.</span></span><br /><br /> <span data-ttu-id="bbd6c-125">Określa, czy rekord pełny komunikat o błędzie jest wyświetlany, gdy wystąpi błąd podczas wyświetlania elementu danych.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="bbd6c-126">Element WrapTables (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="bbd6c-127">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-127">Optional element.</span></span><br /><br /> <span data-ttu-id="bbd6c-128">Określa, że dane w tabeli jest przenoszony do następnego wiersza, jeśli nie mieści się na szerokość kolumny.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bbd6c-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bbd6c-129">Parent Elements</span></span>

|<span data-ttu-id="bbd6c-130">Element</span><span class="sxs-lookup"><span data-stu-id="bbd6c-130">Element</span></span>|<span data-ttu-id="bbd6c-131">Opis</span><span class="sxs-lookup"><span data-stu-id="bbd6c-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbd6c-132">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bbd6c-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="bbd6c-133">Reprezentuje element najwyższego poziomu w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="bbd6c-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bbd6c-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbd6c-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="bbd6c-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbd6c-135">See Also</span></span>

[<span data-ttu-id="bbd6c-136">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bbd6c-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="bbd6c-137">Element DisplayError (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="bbd6c-138">Element EnumerableExpansions (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="bbd6c-139">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="bbd6c-140">Element ShowError (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="bbd6c-141">Element WrapTables (Format)</span><span class="sxs-lookup"><span data-stu-id="bbd6c-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="bbd6c-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="bbd6c-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
