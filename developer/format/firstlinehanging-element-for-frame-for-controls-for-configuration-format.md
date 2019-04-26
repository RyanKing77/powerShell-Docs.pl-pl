---
title: Element FirstLineHanging ramki dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065890"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="b0cc5-102">FirstLineHanging, element — Frame, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b0cc5-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b0cc5-103">Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.</span><span class="sxs-lookup"><span data-stu-id="b0cc5-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="b0cc5-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="b0cc5-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b0cc5-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ramki CustomItem dla formantów dla elementu FirstLineHanging konfiguracji (w formacie) dla ramki dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="b0cc5-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b0cc5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0cc5-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b0cc5-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b0cc5-107">Attributes and Elements</span></span>

<span data-ttu-id="b0cc5-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `FirstLineHanging` elementu.</span><span class="sxs-lookup"><span data-stu-id="b0cc5-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b0cc5-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b0cc5-109">Attributes</span></span>

<span data-ttu-id="b0cc5-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="b0cc5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b0cc5-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b0cc5-111">Child Elements</span></span>

<span data-ttu-id="b0cc5-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="b0cc5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b0cc5-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b0cc5-113">Parent Elements</span></span>

|<span data-ttu-id="b0cc5-114">Element</span><span class="sxs-lookup"><span data-stu-id="b0cc5-114">Element</span></span>|<span data-ttu-id="b0cc5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b0cc5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0cc5-116">Element ramki dla CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="b0cc5-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b0cc5-117">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="b0cc5-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b0cc5-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="b0cc5-118">Text Value</span></span>

<span data-ttu-id="b0cc5-119">Określ liczbę znaków, które mają zostać przesunięte na pierwszy wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="b0cc5-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0cc5-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0cc5-120">Remarks</span></span>

<span data-ttu-id="b0cc5-121">Jeśli ten element jest określony, nie można określić `FirstLineIndent` elementu.</span><span class="sxs-lookup"><span data-stu-id="b0cc5-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0cc5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0cc5-122">See Also</span></span>

[<span data-ttu-id="b0cc5-123">Element ramki dla CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="b0cc5-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b0cc5-124">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="b0cc5-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
