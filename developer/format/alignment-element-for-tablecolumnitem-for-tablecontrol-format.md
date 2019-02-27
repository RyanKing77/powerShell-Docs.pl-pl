---
title: Wyrównanie elementu TableColumnItem dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848356"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="64fb3-102">Alignment, element — TableColumnItem, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="64fb3-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="64fb3-103">Definiuje sposób wyświetlania danych w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="64fb3-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="64fb3-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) TableColumnItems — Element (Format) TableColumnItem Element konfiguracji (Format) Wyrównanie elementu TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="64fb3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64fb3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="64fb3-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64fb3-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="64fb3-106">Attributes and Elements</span></span>

<span data-ttu-id="64fb3-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Alignment` elementu.</span><span class="sxs-lookup"><span data-stu-id="64fb3-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="64fb3-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="64fb3-108">Attributes</span></span>

<span data-ttu-id="64fb3-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="64fb3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64fb3-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="64fb3-110">Child Elements</span></span>

<span data-ttu-id="64fb3-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="64fb3-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="64fb3-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="64fb3-112">Parent Elements</span></span>

|<span data-ttu-id="64fb3-113">Element</span><span class="sxs-lookup"><span data-stu-id="64fb3-113">Element</span></span>|<span data-ttu-id="64fb3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="64fb3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64fb3-115">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="64fb3-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="64fb3-116">Definiuje etykietę, szerokości i wyrównania danych dla kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="64fb3-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="64fb3-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="64fb3-117">Text Value</span></span>

<span data-ttu-id="64fb3-118">Określ jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="64fb3-118">Specify one of the following values.</span></span> <span data-ttu-id="64fb3-119">(Te wartości nie jest rozróżniana wielkość liter).</span><span class="sxs-lookup"><span data-stu-id="64fb3-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="64fb3-120">Przesunięcia w lewo dane wyświetlane w kolumnie z lewej strony.</span><span class="sxs-lookup"><span data-stu-id="64fb3-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="64fb3-121">(Jest to wartość domyślna, gdy ten element nie jest określony).</span><span class="sxs-lookup"><span data-stu-id="64fb3-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="64fb3-122">Przesunięcia w prawo dane wyświetlane w kolumnie z prawej strony.</span><span class="sxs-lookup"><span data-stu-id="64fb3-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="64fb3-123">Centra centrum danych wyświetlanych w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="64fb3-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="64fb3-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64fb3-124">Remarks</span></span>

<span data-ttu-id="64fb3-125">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [widok tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="64fb3-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64fb3-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64fb3-126">See Also</span></span>

[<span data-ttu-id="64fb3-127">Widok tabeli</span><span class="sxs-lookup"><span data-stu-id="64fb3-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="64fb3-128">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="64fb3-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
