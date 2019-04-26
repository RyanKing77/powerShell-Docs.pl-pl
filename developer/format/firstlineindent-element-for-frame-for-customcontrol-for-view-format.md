---
title: Element FirstLineIndent ramki dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065873"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="66f3d-102">FirstLineIndent, element — Frame, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="66f3d-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="66f3d-103">Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.</span><span class="sxs-lookup"><span data-stu-id="66f3d-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="66f3d-104">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="66f3d-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="66f3d-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry CustomControlView (Format) elementu ramki CustomItem dla formant niestandardowy do elementu FirstLineIndent widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="66f3d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="66f3d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="66f3d-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="66f3d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="66f3d-107">Attributes and Elements</span></span>

<span data-ttu-id="66f3d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FirstLineIndent` elementu.</span><span class="sxs-lookup"><span data-stu-id="66f3d-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="66f3d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="66f3d-109">Attributes</span></span>

<span data-ttu-id="66f3d-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="66f3d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="66f3d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="66f3d-111">Child Elements</span></span>

<span data-ttu-id="66f3d-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="66f3d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="66f3d-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="66f3d-113">Parent Elements</span></span>

|<span data-ttu-id="66f3d-114">Element</span><span class="sxs-lookup"><span data-stu-id="66f3d-114">Element</span></span>|<span data-ttu-id="66f3d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="66f3d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66f3d-116">Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="66f3d-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="66f3d-117">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="66f3d-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="66f3d-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="66f3d-118">Text Value</span></span>

<span data-ttu-id="66f3d-119">Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="66f3d-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="66f3d-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66f3d-120">Remarks</span></span>

<span data-ttu-id="66f3d-121">Jeśli ten element jest określony, nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="66f3d-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="66f3d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66f3d-122">See Also</span></span>

[<span data-ttu-id="66f3d-123">Element FirstLineHanging ramki dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="66f3d-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="66f3d-124">Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="66f3d-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="66f3d-125">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="66f3d-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
