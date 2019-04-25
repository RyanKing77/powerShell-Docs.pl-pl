---
title: Element FormatString dla elementu listy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065624"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="80d81-102">FormatString, element — ListItem, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="80d81-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="80d81-103">Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="80d81-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="80d81-104">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji dla elementu ListEntry elementu ListControl (w formacie) dla elementu ListItems elementu ListControl (w formacie) dla elementu ListControl (Format) Element ListItem dla elementu FormatString elementu ListControl (w formacie) dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80d81-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80d81-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="80d81-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80d81-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80d81-106">Attributes and Elements</span></span>

<span data-ttu-id="80d81-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FormatString` elementu.</span><span class="sxs-lookup"><span data-stu-id="80d81-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80d81-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80d81-108">Attributes</span></span>

<span data-ttu-id="80d81-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="80d81-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80d81-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80d81-110">Child Elements</span></span>

<span data-ttu-id="80d81-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="80d81-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="80d81-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80d81-112">Parent Elements</span></span>

|<span data-ttu-id="80d81-113">Element</span><span class="sxs-lookup"><span data-stu-id="80d81-113">Element</span></span>|<span data-ttu-id="80d81-114">Opis</span><span class="sxs-lookup"><span data-stu-id="80d81-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80d81-115">ListItem — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="80d81-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="80d81-116">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="80d81-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="80d81-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="80d81-117">Text Value</span></span>

<span data-ttu-id="80d81-118">Określ wzorzec, który jest używany do formatowania danych.</span><span class="sxs-lookup"><span data-stu-id="80d81-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="80d81-119">Na przykład, można używać tego wzorca do formatowania wartości dowolnej właściwości, która jest typu [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="80d81-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="80d81-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80d81-120">Remarks</span></span>

<span data-ttu-id="80d81-121">Ciągi formatu mogą być używane, podczas tworzenia widoki tabel, widoków listy, widoki szeroki lub widoków niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="80d81-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="80d81-122">Aby uzyskać więcej informacji na temat formatowania wartości wyświetlane w widoku, zobacz [formatowania danych wyświetlane](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="80d81-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="80d81-123">Aby uzyskać więcej informacji na temat używania ciągów formatu w widokach list, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="80d81-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="80d81-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="80d81-124">Example</span></span>

<span data-ttu-id="80d81-125">Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.</span><span class="sxs-lookup"><span data-stu-id="80d81-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="80d81-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80d81-126">See Also</span></span>

[<span data-ttu-id="80d81-127">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="80d81-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="80d81-128">ListItem — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="80d81-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="80d81-129">Pisanie programu Windows PowerShell, formatowania i typy plików</span><span class="sxs-lookup"><span data-stu-id="80d81-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
