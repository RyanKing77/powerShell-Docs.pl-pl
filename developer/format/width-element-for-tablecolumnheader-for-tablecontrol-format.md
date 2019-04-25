---
title: Szerokość elementu TableColumnHeader dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083624"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="9ced0-102">Width, element — TableColumnHeader, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="9ced0-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="9ced0-103">Określa szerokość (w znakach) kolumny.</span><span class="sxs-lookup"><span data-stu-id="9ced0-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="9ced0-104">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableHeaders Element konfiguracji dla TableHeaders elementu TableColumnHeader tablecontrol — (w formacie) dla elementu szerokość (w formacie) tablecontrol — TableColumnHeader dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9ced0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ced0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ced0-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ced0-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9ced0-106">Attributes and Elements</span></span>

<span data-ttu-id="9ced0-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Width` element używany podczas definiowania nagłówków kolumn.</span><span class="sxs-lookup"><span data-stu-id="9ced0-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ced0-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9ced0-108">Attributes</span></span>

<span data-ttu-id="9ced0-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="9ced0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ced0-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9ced0-110">Child Elements</span></span>

<span data-ttu-id="9ced0-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="9ced0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9ced0-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9ced0-112">Parent Elements</span></span>

|<span data-ttu-id="9ced0-113">Element</span><span class="sxs-lookup"><span data-stu-id="9ced0-113">Element</span></span>|<span data-ttu-id="9ced0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9ced0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ced0-115">Element TableColumnHeader TableHeaders dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9ced0-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="9ced0-116">Definiuje etykietę, szerokości i wyrównania danych dla kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="9ced0-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9ced0-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="9ced0-117">Text Value</span></span>

<span data-ttu-id="9ced0-118">Gdy na wszystkich możliwych określić szerokość (w znakach), która jest większa niż długość wartości właściwości wyświetlanych.</span><span class="sxs-lookup"><span data-stu-id="9ced0-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ced0-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ced0-119">Remarks</span></span>

<span data-ttu-id="9ced0-120">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9ced0-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9ced0-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ced0-121">Example</span></span>

<span data-ttu-id="9ced0-122">W poniższym przykładzie przedstawiono `TableColumnHeader` elementu, którego szerokość jest 16 znaków.</span><span class="sxs-lookup"><span data-stu-id="9ced0-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="9ced0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ced0-123">See Also</span></span>

[<span data-ttu-id="9ced0-124">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="9ced0-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9ced0-125">Element TableColumnHeader TableHeader dla tablecontrol — (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9ced0-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="9ced0-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9ced0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
