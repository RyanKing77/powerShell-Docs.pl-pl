---
title: Wyrównanie elementu TableColumnHeader dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067012"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="2db6e-102">Alignment, element — TableColumnHeader, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2db6e-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="2db6e-103">Definiuje sposób wyświetlania danych w nagłówkach kolumn.</span><span class="sxs-lookup"><span data-stu-id="2db6e-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="2db6e-104">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) tablecontrol — Element (Format) TableHeaders — Element (Format) TableColumnHeader — Element (Format) wyrównanie Element konfiguracji dla TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="2db6e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2db6e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2db6e-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2db6e-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2db6e-106">Attributes and Elements</span></span>

<span data-ttu-id="2db6e-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Alignment` elementu.</span><span class="sxs-lookup"><span data-stu-id="2db6e-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2db6e-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2db6e-108">Attributes</span></span>

<span data-ttu-id="2db6e-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="2db6e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2db6e-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2db6e-110">Child Elements</span></span>

<span data-ttu-id="2db6e-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="2db6e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2db6e-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2db6e-112">Parent Elements</span></span>

|<span data-ttu-id="2db6e-113">Element</span><span class="sxs-lookup"><span data-stu-id="2db6e-113">Element</span></span>|<span data-ttu-id="2db6e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2db6e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2db6e-115">Element TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="2db6e-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="2db6e-116">Definiuje etykietę, szerokości i wyrównania danych dla kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="2db6e-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2db6e-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="2db6e-117">Text Value</span></span>

<span data-ttu-id="2db6e-118">Określ jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="2db6e-118">Specify one of the following values.</span></span> <span data-ttu-id="2db6e-119">Te wartości nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="2db6e-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="2db6e-120">Lewy Wyrównuje dane wyświetlane w kolumnie po lewej stronie jest to wartość domyślna, jeśli nie określono tego elementu.</span><span class="sxs-lookup"><span data-stu-id="2db6e-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="2db6e-121">Prawy Wyrównuje dane wyświetlane w kolumnie po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="2db6e-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="2db6e-122">Centra centrum danych wyświetlanych w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="2db6e-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="2db6e-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2db6e-123">Remarks</span></span>

<span data-ttu-id="2db6e-124">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="2db6e-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2db6e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="2db6e-125">Example</span></span>

<span data-ttu-id="2db6e-126">W tym przykładzie `TableColumnHeader` elementu, którego dane są wyrównane po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="2db6e-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="2db6e-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2db6e-127">See Also</span></span>

[<span data-ttu-id="2db6e-128">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="2db6e-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2db6e-129">Element TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="2db6e-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="2db6e-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="2db6e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
