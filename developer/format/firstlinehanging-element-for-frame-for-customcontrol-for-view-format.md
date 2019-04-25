---
title: Element FirstLineHanging ramki dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065975"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="e1f6c-102">FirstLineHanging, element — Frame, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="e1f6c-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="e1f6c-103">Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.</span><span class="sxs-lookup"><span data-stu-id="e1f6c-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="e1f6c-104">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="e1f6c-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e1f6c-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry CustomControlView (Format) elementu ramki CustomItem dla formant niestandardowy widok (w formacie) elementu FirstLineHanging ramki dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="e1f6c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1f6c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1f6c-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1f6c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e1f6c-107">Attributes and Elements</span></span>

<span data-ttu-id="e1f6c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FirstLineHanging` elementu.</span><span class="sxs-lookup"><span data-stu-id="e1f6c-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1f6c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e1f6c-109">Attributes</span></span>

<span data-ttu-id="e1f6c-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="e1f6c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1f6c-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e1f6c-111">Child Elements</span></span>

<span data-ttu-id="e1f6c-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="e1f6c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e1f6c-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e1f6c-113">Parent Elements</span></span>

|<span data-ttu-id="e1f6c-114">Element</span><span class="sxs-lookup"><span data-stu-id="e1f6c-114">Element</span></span>|<span data-ttu-id="e1f6c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e1f6c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1f6c-116">Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="e1f6c-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="e1f6c-117">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="e1f6c-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e1f6c-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="e1f6c-118">Text Value</span></span>

<span data-ttu-id="e1f6c-119">Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="e1f6c-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1f6c-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1f6c-120">Remarks</span></span>

<span data-ttu-id="e1f6c-121">Jeśli ten element jest określony, nie można określić [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e1f6c-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1f6c-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1f6c-122">See Also</span></span>

[<span data-ttu-id="e1f6c-123">Element FirstLineIndent ramki dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="e1f6c-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e1f6c-124">Element ramki dla CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="e1f6c-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e1f6c-125">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="e1f6c-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
