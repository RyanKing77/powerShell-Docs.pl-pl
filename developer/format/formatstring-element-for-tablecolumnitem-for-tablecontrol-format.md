---
title: Element FormatString dla TableColumnItem dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065637"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="8088d-102">FormatString, element — TableColumnItem, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="8088d-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="8088d-103">Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skrypt tabeli.</span><span class="sxs-lookup"><span data-stu-id="8088d-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="8088d-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) TableColumnItems — Element (Format) TableColumnItem Element konfiguracji (Format) Element FormatString dla TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="8088d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8088d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8088d-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8088d-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8088d-106">Attributes and Elements</span></span>

<span data-ttu-id="8088d-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FormatString` elementu.</span><span class="sxs-lookup"><span data-stu-id="8088d-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8088d-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8088d-108">Attributes</span></span>

<span data-ttu-id="8088d-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="8088d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8088d-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8088d-110">Child Elements</span></span>

<span data-ttu-id="8088d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="8088d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8088d-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8088d-112">Parent Elements</span></span>

|<span data-ttu-id="8088d-113">Element</span><span class="sxs-lookup"><span data-stu-id="8088d-113">Element</span></span>|<span data-ttu-id="8088d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8088d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8088d-115">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="8088d-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="8088d-116">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="8088d-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8088d-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="8088d-117">Text Value</span></span>

<span data-ttu-id="8088d-118">Określ wzorzec, który jest używany do formatowania danych.</span><span class="sxs-lookup"><span data-stu-id="8088d-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="8088d-119">Na przykład, ten wzorzec może służyć do formatowania wartości dowolnej właściwości, która jest typu [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="8088d-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="8088d-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8088d-120">Remarks</span></span>

<span data-ttu-id="8088d-121">Ciągi formatu mogą być używane, podczas tworzenia widoki tabel, widoków listy, widoki szeroki lub widoków niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="8088d-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="8088d-122">Aby uzyskać więcej informacji na temat formatowania wartości wyświetlane w widoku, zobacz [formatowania danych wyświetlane](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="8088d-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="8088d-123">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [widok tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8088d-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8088d-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="8088d-124">Example</span></span>

<span data-ttu-id="8088d-125">Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.</span><span class="sxs-lookup"><span data-stu-id="8088d-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="8088d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8088d-126">See Also</span></span>

[<span data-ttu-id="8088d-127">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="8088d-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8088d-128">Formatowanie wyświetlanych danych</span><span class="sxs-lookup"><span data-stu-id="8088d-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="8088d-129">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="8088d-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="8088d-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="8088d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
