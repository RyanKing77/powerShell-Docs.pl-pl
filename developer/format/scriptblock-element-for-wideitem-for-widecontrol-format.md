---
title: Element ScriptBlock WideItem dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064207"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="27fdd-102">ScriptBlock, element — WideItem, WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="27fdd-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="27fdd-103">Określa skrypt, którego wartość jest wyświetlana w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="27fdd-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="27fdd-104">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) elementu WideEntry (Format) WideItem — Element (Format) ScriptBlock Element konfiguracji dla WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="27fdd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27fdd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="27fdd-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27fdd-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="27fdd-106">Attributes and Elements</span></span>

<span data-ttu-id="27fdd-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="27fdd-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="27fdd-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="27fdd-108">Attributes</span></span>

<span data-ttu-id="27fdd-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="27fdd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27fdd-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="27fdd-110">Child Elements</span></span>

<span data-ttu-id="27fdd-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="27fdd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="27fdd-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="27fdd-112">Parent Elements</span></span>

|<span data-ttu-id="27fdd-113">Element</span><span class="sxs-lookup"><span data-stu-id="27fdd-113">Element</span></span>|<span data-ttu-id="27fdd-114">Opis</span><span class="sxs-lookup"><span data-stu-id="27fdd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27fdd-115">Element WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="27fdd-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="27fdd-116">Definiuje właściwości lub skrypt bloku, którego wartość jest wyświetlana w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="27fdd-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="27fdd-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="27fdd-117">Text Value</span></span>

<span data-ttu-id="27fdd-118">Określ skrypt, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="27fdd-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="27fdd-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27fdd-119">Remarks</span></span>

<span data-ttu-id="27fdd-120">Aby uzyskać więcej informacji na temat składników szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="27fdd-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="27fdd-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="27fdd-121">Example</span></span>

<span data-ttu-id="27fdd-122">W tym przykładzie `WideItem` element, który definiuje skryptu, którego wartość jest wyświetlana w widoku.</span><span class="sxs-lookup"><span data-stu-id="27fdd-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="27fdd-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27fdd-123">See Also</span></span>

[<span data-ttu-id="27fdd-124">Element WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="27fdd-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="27fdd-125">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="27fdd-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="27fdd-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="27fdd-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
