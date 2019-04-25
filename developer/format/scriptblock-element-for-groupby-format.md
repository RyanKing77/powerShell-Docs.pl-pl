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
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064513"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="9e146-102">ScriptBlock, element — GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="9e146-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="9e146-103">Określa skrypt, który uruchamia nową grupę, zmianie wartości.</span><span class="sxs-lookup"><span data-stu-id="9e146-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="9e146-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu ScriptBlock widoku (w formacie) dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="9e146-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9e146-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e146-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9e146-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9e146-106">Attributes and Elements</span></span>

<span data-ttu-id="9e146-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="9e146-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9e146-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9e146-108">Attributes</span></span>

<span data-ttu-id="9e146-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="9e146-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9e146-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9e146-110">Child Elements</span></span>

<span data-ttu-id="9e146-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="9e146-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9e146-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9e146-112">Parent Elements</span></span>

|<span data-ttu-id="9e146-113">Element</span><span class="sxs-lookup"><span data-stu-id="9e146-113">Element</span></span>|<span data-ttu-id="9e146-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9e146-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e146-115">GroupBy — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="9e146-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="9e146-116">Definiuje sposób wyświetlania grupy obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="9e146-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9e146-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="9e146-117">Text Value</span></span>

<span data-ttu-id="9e146-118">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="9e146-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e146-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e146-119">Remarks</span></span>

<span data-ttu-id="9e146-120">Rozpoczyna się nowej grupy programu Windows PowerShell, zawsze wtedy, gdy zmieni się wartość tego skryptu.</span><span class="sxs-lookup"><span data-stu-id="9e146-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="9e146-121">Gdy ten element jest określony, nie można określić [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element, aby rozpocząć nową grupę.</span><span class="sxs-lookup"><span data-stu-id="9e146-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e146-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e146-122">See Also</span></span>

[<span data-ttu-id="9e146-123">Element PropertyName GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9e146-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="9e146-124">GroupBy — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="9e146-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="9e146-125">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9e146-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
