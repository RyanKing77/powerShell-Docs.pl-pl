---
title: Element FirstLineHanging ramki dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065809"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="bf9b6-102">FirstLineHanging, element — Frame, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="bf9b6-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="bf9b6-103">Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.</span><span class="sxs-lookup"><span data-stu-id="bf9b6-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="bf9b6-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="bf9b6-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="bf9b6-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ramki CustomItem dla formantów dla elementu FirstLineHanging widoku (Format) Ramka kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="bf9b6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bf9b6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf9b6-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf9b6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf9b6-107">Attributes and Elements</span></span>

<span data-ttu-id="bf9b6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FirstLineHanging` elementu.</span><span class="sxs-lookup"><span data-stu-id="bf9b6-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf9b6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf9b6-109">Attributes</span></span>

<span data-ttu-id="bf9b6-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf9b6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bf9b6-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf9b6-111">Child Elements</span></span>

<span data-ttu-id="bf9b6-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf9b6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bf9b6-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf9b6-113">Parent Elements</span></span>

|<span data-ttu-id="bf9b6-114">Element</span><span class="sxs-lookup"><span data-stu-id="bf9b6-114">Element</span></span>|<span data-ttu-id="bf9b6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="bf9b6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bf9b6-116">Element ramki dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="bf9b6-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="bf9b6-117">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="bf9b6-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bf9b6-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="bf9b6-118">Text Value</span></span>

<span data-ttu-id="bf9b6-119">Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="bf9b6-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf9b6-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf9b6-120">Remarks</span></span>

<span data-ttu-id="bf9b6-121">Jeśli ten element jest określony, nie można określić [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="bf9b6-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf9b6-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf9b6-122">See Also</span></span>

[<span data-ttu-id="bf9b6-123">Element FirstLineIndent ramki dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="bf9b6-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="bf9b6-124">Element ramki dla CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="bf9b6-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="bf9b6-125">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="bf9b6-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
