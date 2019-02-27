---
title: Element PropertyName TableColumnItem dla tablecontrol — (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849238"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="1a4b0-102">PropertyName, element — TableColumnItem, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="1a4b0-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="1a4b0-103">Określa właściwość, której wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="1a4b0-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="1a4b0-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) TableColumnItems — Element (Format) TableColumnItem Element konfiguracji (Format) Element PropertyName TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="1a4b0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1a4b0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a4b0-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1a4b0-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a4b0-106">Attributes and Elements</span></span>

<span data-ttu-id="1a4b0-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="1a4b0-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1a4b0-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a4b0-108">Attributes</span></span>

<span data-ttu-id="1a4b0-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="1a4b0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1a4b0-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a4b0-110">Child Elements</span></span>

<span data-ttu-id="1a4b0-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="1a4b0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1a4b0-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a4b0-112">Parent Elements</span></span>

|<span data-ttu-id="1a4b0-113">Element</span><span class="sxs-lookup"><span data-stu-id="1a4b0-113">Element</span></span>|<span data-ttu-id="1a4b0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1a4b0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1a4b0-115">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="1a4b0-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="1a4b0-116">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="1a4b0-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1a4b0-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="1a4b0-117">Text Value</span></span>

<span data-ttu-id="1a4b0-118">Określ nazwę właściwości, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="1a4b0-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a4b0-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a4b0-119">Remarks</span></span>

<span data-ttu-id="1a4b0-120">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1a4b0-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1a4b0-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a4b0-121">Example</span></span>

<span data-ttu-id="1a4b0-122">W tym przykładzie `TableColumnItem` element, który określa `Status` właściwość [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="1a4b0-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="1a4b0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a4b0-123">See Also</span></span>

[<span data-ttu-id="1a4b0-124">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="1a4b0-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1a4b0-125">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="1a4b0-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="1a4b0-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="1a4b0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
