---
title: Tablecontrol — Element (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848853"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="1f2ca-102">TableControl, element (format)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-102">TableControl Element (Format)</span></span>

<span data-ttu-id="1f2ca-103">Definiuje format tabeli w celu wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-103">Defines a table format for a view.</span></span>

<span data-ttu-id="1f2ca-104">Element ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f2ca-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f2ca-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f2ca-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1f2ca-106">Attributes and Elements</span></span>

<span data-ttu-id="1f2ca-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TableControl` elementu.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="1f2ca-108">Należy określić wiersze z tabeli.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-108">You must specify the rows of the table.</span></span> <span data-ttu-id="1f2ca-109">Wszystkie inne elementy podrzędne są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f2ca-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1f2ca-110">Attributes</span></span>

<span data-ttu-id="1f2ca-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f2ca-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1f2ca-112">Child Elements</span></span>

|<span data-ttu-id="1f2ca-113">Element</span><span class="sxs-lookup"><span data-stu-id="1f2ca-113">Element</span></span>|<span data-ttu-id="1f2ca-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1f2ca-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f2ca-115">Element AutoSize tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="1f2ca-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1f2ca-117">Określa, czy rozmiar kolumny i liczba kolumn są dostosowywane na podstawie rozmiaru danych.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="1f2ca-118">Element HideTableHeaders tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="1f2ca-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1f2ca-120">Wskazuje, czy nagłówek tabeli nie jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="1f2ca-121">Element TableHeaders tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="1f2ca-122">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-122">Required element.</span></span><br /><br /> <span data-ttu-id="1f2ca-123">Definiuje etykiety, szerokości i wyrównania danych dla kolumn w widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="1f2ca-124">Element TableRowEntries TableCotrol (Format)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-124">TableRowEntries Element for TableCotrol (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="1f2ca-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-125">Optional element.</span></span><br /><br /> <span data-ttu-id="1f2ca-126">Zawiera definicje widoku tabeli.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f2ca-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1f2ca-127">Parent Elements</span></span>

|<span data-ttu-id="1f2ca-128">Element</span><span class="sxs-lookup"><span data-stu-id="1f2ca-128">Element</span></span>|<span data-ttu-id="1f2ca-129">Opis</span><span class="sxs-lookup"><span data-stu-id="1f2ca-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f2ca-130">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="1f2ca-131">Określa widok, który służy do wyświetlania elementów członkowskich co najmniej jeden obiekt.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f2ca-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f2ca-132">Remarks</span></span>

<span data-ttu-id="1f2ca-133">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1f2ca-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1f2ca-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f2ca-134">Example</span></span>

<span data-ttu-id="1f2ca-135">W tym przykładzie `TableControl` element, który służy do wyświetlania właściwości [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f2ca-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="1f2ca-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f2ca-136">See Also</span></span>

[<span data-ttu-id="1f2ca-137">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="1f2ca-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1f2ca-138">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="1f2ca-139">Element AutoSize tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="1f2ca-140">Element HideTableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="1f2ca-141">Element TableHeaders (Format)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="1f2ca-142">Element TableRowEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="1f2ca-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="1f2ca-143">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="1f2ca-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
