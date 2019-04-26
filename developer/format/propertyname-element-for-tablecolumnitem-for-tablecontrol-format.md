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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064617"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="f5a8a-102">PropertyName, element — TableColumnItem, TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="f5a8a-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="f5a8a-103">Określa właściwość, której wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="f5a8a-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) tablecontrol — Element (Format) elementu TableRowEntries (Format) TableRowEntry — Element (Format) TableColumnItems — Element (Format) TableColumnItem Element konfiguracji (Format) Element PropertyName TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f5a8a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5a8a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5a8a-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5a8a-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f5a8a-106">Attributes and Elements</span></span>

<span data-ttu-id="f5a8a-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5a8a-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f5a8a-108">Attributes</span></span>

<span data-ttu-id="f5a8a-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5a8a-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f5a8a-110">Child Elements</span></span>

<span data-ttu-id="f5a8a-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5a8a-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f5a8a-112">Parent Elements</span></span>

|<span data-ttu-id="f5a8a-113">Element</span><span class="sxs-lookup"><span data-stu-id="f5a8a-113">Element</span></span>|<span data-ttu-id="f5a8a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f5a8a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5a8a-115">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f5a8a-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="f5a8a-116">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f5a8a-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="f5a8a-117">Text Value</span></span>

<span data-ttu-id="f5a8a-118">Określ nazwę właściwości, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5a8a-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5a8a-119">Remarks</span></span>

<span data-ttu-id="f5a8a-120">Aby uzyskać więcej informacji o składnikach w widoku tabeli, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f5a8a-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f5a8a-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5a8a-121">Example</span></span>

<span data-ttu-id="f5a8a-122">W tym przykładzie `TableColumnItem` element, który określa `Status` właściwość [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="f5a8a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5a8a-123">See Also</span></span>

[<span data-ttu-id="f5a8a-124">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="f5a8a-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f5a8a-125">Element TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f5a8a-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="f5a8a-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="f5a8a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
