---
title: Element FirstLineIndent ramki dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848601"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a><span data-ttu-id="469ef-102">FirstLineIndent, element — Frame, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="469ef-102">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="469ef-103">Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.</span><span class="sxs-lookup"><span data-stu-id="469ef-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="469ef-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="469ef-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="469ef-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ramki CustomItem GroupBy (Format) elementu FirstLineIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="469ef-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="469ef-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="469ef-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="469ef-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="469ef-107">Attributes and Elements</span></span>

<span data-ttu-id="469ef-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FirstLineIndent` elementu.</span><span class="sxs-lookup"><span data-stu-id="469ef-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="469ef-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="469ef-109">Attributes</span></span>

<span data-ttu-id="469ef-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="469ef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="469ef-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="469ef-111">Child Elements</span></span>

<span data-ttu-id="469ef-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="469ef-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="469ef-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="469ef-113">Parent Elements</span></span>

|<span data-ttu-id="469ef-114">Element</span><span class="sxs-lookup"><span data-stu-id="469ef-114">Element</span></span>|<span data-ttu-id="469ef-115">Opis</span><span class="sxs-lookup"><span data-stu-id="469ef-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="469ef-116">Element ramki dla CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="469ef-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="469ef-117">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="469ef-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="469ef-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="469ef-118">Text Value</span></span>

<span data-ttu-id="469ef-119">Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="469ef-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="469ef-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="469ef-120">Remarks</span></span>

<span data-ttu-id="469ef-121">Jeśli ten element jest określony, nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="469ef-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="469ef-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="469ef-122">See Also</span></span>

[<span data-ttu-id="469ef-123">Element FirstLineHanging ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="469ef-123">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="469ef-124">Element ramki dla CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="469ef-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="469ef-125">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="469ef-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
