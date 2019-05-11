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
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229313"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="7ccd4-102">ScriptBlock, element — GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7ccd4-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="7ccd4-103">Określa skrypt, który uruchamia nową grupę, zmianie wartości.</span><span class="sxs-lookup"><span data-stu-id="7ccd4-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="7ccd4-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu ScriptBlock widoku (w formacie) dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="7ccd4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ccd4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ccd4-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7ccd4-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7ccd4-106">Attributes and Elements</span></span>

<span data-ttu-id="7ccd4-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="7ccd4-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7ccd4-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7ccd4-108">Attributes</span></span>

<span data-ttu-id="7ccd4-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="7ccd4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7ccd4-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7ccd4-110">Child Elements</span></span>

<span data-ttu-id="7ccd4-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="7ccd4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7ccd4-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7ccd4-112">Parent Elements</span></span>

|<span data-ttu-id="7ccd4-113">Element</span><span class="sxs-lookup"><span data-stu-id="7ccd4-113">Element</span></span>|<span data-ttu-id="7ccd4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7ccd4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ccd4-115">GroupBy — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="7ccd4-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7ccd4-116">Definiuje sposób wyświetlania grupy obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="7ccd4-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7ccd4-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="7ccd4-117">Text Value</span></span>

<span data-ttu-id="7ccd4-118">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="7ccd4-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ccd4-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ccd4-119">Remarks</span></span>

<span data-ttu-id="7ccd4-120">Zawsze wtedy, gdy zmieni się wartość ten skrypt programu PowerShell rozpoczyna się nowej grupy.</span><span class="sxs-lookup"><span data-stu-id="7ccd4-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="7ccd4-121">Gdy ten element jest określony, nie można określić [PropertyName](propertyname-element-for-groupby-format.md) element, aby rozpocząć nową grupę.</span><span class="sxs-lookup"><span data-stu-id="7ccd4-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ccd4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ccd4-122">See Also</span></span>

[<span data-ttu-id="7ccd4-123">Element PropertyName GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7ccd4-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="7ccd4-124">GroupBy — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="7ccd4-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="7ccd4-125">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="7ccd4-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
