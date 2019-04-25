---
title: Element FormatString dla WideItem dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065686"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="7658b-102">FormatString, element — WideItem, WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="7658b-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="7658b-103">Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku.</span><span class="sxs-lookup"><span data-stu-id="7658b-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="7658b-104">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry Element konfiguracji dla elementu WideItem WideControl (w formacie) dla elementu FormatString WideControl (Format) Aby uzyskać WideItem dla WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7658b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7658b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7658b-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7658b-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7658b-106">Attributes and Elements</span></span>

<span data-ttu-id="7658b-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FormatString` elementu.</span><span class="sxs-lookup"><span data-stu-id="7658b-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7658b-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7658b-108">Attributes</span></span>

<span data-ttu-id="7658b-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="7658b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7658b-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7658b-110">Child Elements</span></span>

<span data-ttu-id="7658b-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="7658b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7658b-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7658b-112">Parent Elements</span></span>

|<span data-ttu-id="7658b-113">Element</span><span class="sxs-lookup"><span data-stu-id="7658b-113">Element</span></span>|<span data-ttu-id="7658b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7658b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7658b-115">Element WideItem WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7658b-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="7658b-116">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="7658b-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7658b-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="7658b-117">Text Value</span></span>

<span data-ttu-id="7658b-118">Określ wzorzec, który jest używany do formatowania danych.</span><span class="sxs-lookup"><span data-stu-id="7658b-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="7658b-119">Na przykład, można używać tego wzorca do formatowania wartości dowolnej właściwości, która jest typu [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="7658b-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="7658b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7658b-120">Remarks</span></span>

<span data-ttu-id="7658b-121">Ciągi formatu mogą być używane, podczas tworzenia widoki tabel, widoków listy, widoki szeroki lub widoków niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7658b-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="7658b-122">Aby uzyskać więcej informacji na temat formatowania wartości wyświetlane w widoku, zobacz [formatowania danych wyświetlane](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="7658b-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="7658b-123">Aby uzyskać więcej informacji na temat używania ciągów formatu w widokach szerokiego zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7658b-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7658b-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="7658b-124">Example</span></span>

<span data-ttu-id="7658b-125">Poniższy przykład pokazuje jak zdefiniować ciąg formatowania dla wartości `StartTime` właściwości.</span><span class="sxs-lookup"><span data-stu-id="7658b-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="7658b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7658b-126">See Also</span></span>

[<span data-ttu-id="7658b-127">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="7658b-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7658b-128">Element WideItem WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7658b-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="7658b-129">Pisanie programu Windows PowerShell, formatowania i typy plików</span><span class="sxs-lookup"><span data-stu-id="7658b-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
