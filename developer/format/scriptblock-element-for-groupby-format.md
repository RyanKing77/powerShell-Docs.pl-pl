---
title: Element ScriptBlock GroupBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846956"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="566cc-102">ScriptBlock, element — GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="566cc-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="566cc-103">Określa skrypt, który uruchamia nową grupę, zmianie wartości.</span><span class="sxs-lookup"><span data-stu-id="566cc-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="566cc-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu ScriptBlock widoku (w formacie) dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="566cc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="566cc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="566cc-105">Syntax</span></span>

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="566cc-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="566cc-106">Attributes and Elements</span></span>

<span data-ttu-id="566cc-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="566cc-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="566cc-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="566cc-108">Attributes</span></span>

<span data-ttu-id="566cc-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="566cc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="566cc-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="566cc-110">Child Elements</span></span>

<span data-ttu-id="566cc-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="566cc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="566cc-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="566cc-112">Parent Elements</span></span>

|<span data-ttu-id="566cc-113">Element</span><span class="sxs-lookup"><span data-stu-id="566cc-113">Element</span></span>|<span data-ttu-id="566cc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="566cc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="566cc-115">GroupBy — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="566cc-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="566cc-116">Definiuje sposób wyświetlania grupy obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="566cc-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="566cc-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="566cc-117">Text Value</span></span>

<span data-ttu-id="566cc-118">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="566cc-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="566cc-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="566cc-119">Remarks</span></span>

<span data-ttu-id="566cc-120">Rozpoczyna się nowej grupy programu Windows PowerShell, zawsze wtedy, gdy zmieni się wartość tego skryptu.</span><span class="sxs-lookup"><span data-stu-id="566cc-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="566cc-121">Gdy ten element jest określony, nie można określić [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element, aby rozpocząć nową grupę.</span><span class="sxs-lookup"><span data-stu-id="566cc-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="566cc-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="566cc-122">See Also</span></span>

[<span data-ttu-id="566cc-123">Element PropertyName GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="566cc-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="566cc-124">GroupBy — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="566cc-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="566cc-125">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="566cc-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
