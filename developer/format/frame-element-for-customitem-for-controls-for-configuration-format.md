---
title: Ramkę elementu CustomItem dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065567"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="37fca-102">Frame, element — CustomItem, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="37fca-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="37fca-103">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="37fca-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="37fca-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="37fca-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="37fca-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ramki CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="37fca-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37fca-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="37fca-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37fca-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37fca-107">Attributes and Elements</span></span>

<span data-ttu-id="37fca-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="37fca-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37fca-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37fca-109">Attributes</span></span>

<span data-ttu-id="37fca-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="37fca-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37fca-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37fca-111">Child Elements</span></span>

|<span data-ttu-id="37fca-112">Element</span><span class="sxs-lookup"><span data-stu-id="37fca-112">Element</span></span>|<span data-ttu-id="37fca-113">Opis</span><span class="sxs-lookup"><span data-stu-id="37fca-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="37fca-114">Wymagany Element</span><span class="sxs-lookup"><span data-stu-id="37fca-114">Required Element</span></span>|
|[<span data-ttu-id="37fca-115">Element FirstLineHanging ramki dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="37fca-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="37fca-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="37fca-116">Optional element.</span></span><br /><br /> <span data-ttu-id="37fca-117">Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.</span><span class="sxs-lookup"><span data-stu-id="37fca-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="37fca-118">Element FirstLineIndent ramki dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="37fca-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="37fca-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="37fca-119">Optional element.</span></span><br /><br /> <span data-ttu-id="37fca-120">Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.</span><span class="sxs-lookup"><span data-stu-id="37fca-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="37fca-121">Element LeftIndent ramki dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="37fca-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="37fca-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="37fca-122">Optional element.</span></span><br /><br /> <span data-ttu-id="37fca-123">Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="37fca-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="37fca-124">Element RightIndent ramki dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="37fca-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="37fca-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="37fca-125">Optional element.</span></span><br /><br /> <span data-ttu-id="37fca-126">Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="37fca-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="37fca-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37fca-127">Parent Elements</span></span>

|<span data-ttu-id="37fca-128">Element</span><span class="sxs-lookup"><span data-stu-id="37fca-128">Element</span></span>|<span data-ttu-id="37fca-129">Opis</span><span class="sxs-lookup"><span data-stu-id="37fca-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37fca-130">Element CustomItem CustomEntry dla formantów dla konfiguracji</span><span class="sxs-lookup"><span data-stu-id="37fca-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="37fca-131">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="37fca-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="37fca-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37fca-132">Remarks</span></span>

<span data-ttu-id="37fca-133">Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementów w tym samym `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="37fca-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="37fca-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37fca-134">See Also</span></span>

[<span data-ttu-id="37fca-135">Element FirstLineHanging ramki dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="37fca-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="37fca-136">Element FirstLineIndent ramki dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="37fca-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="37fca-137">Element LeftIndent ramki dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="37fca-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="37fca-138">Element RightIndent ramki dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="37fca-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="37fca-139">Element CustomItem CustomEntry dla formantów dla konfiguracji</span><span class="sxs-lookup"><span data-stu-id="37fca-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="37fca-140">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="37fca-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
