---
title: Ramkę elementu CustomItem dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849483"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="52854-102">Frame, element — CustomItem, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="52854-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="52854-103">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="52854-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="52854-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="52854-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="52854-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ramki CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52854-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="52854-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52854-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="52854-107">Attributes and Elements</span></span>

<span data-ttu-id="52854-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="52854-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="52854-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="52854-109">Attributes</span></span>

<span data-ttu-id="52854-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="52854-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52854-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="52854-111">Child Elements</span></span>

|<span data-ttu-id="52854-112">Element</span><span class="sxs-lookup"><span data-stu-id="52854-112">Element</span></span>|<span data-ttu-id="52854-113">Opis</span><span class="sxs-lookup"><span data-stu-id="52854-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="52854-114">Wymagany Element</span><span class="sxs-lookup"><span data-stu-id="52854-114">Required Element</span></span>|
|[<span data-ttu-id="52854-115">Element FirstLineHanging ramki kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="52854-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="52854-116">Optional element.</span></span><br /><br /> <span data-ttu-id="52854-117">Określa, ile znaków pierwszy wiersz jest przesuwane w lewo.</span><span class="sxs-lookup"><span data-stu-id="52854-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="52854-118">Element FirstLineIndent ramki kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="52854-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="52854-119">Optional element.</span></span><br /><br /> <span data-ttu-id="52854-120">Określa, ile znaków pierwszy wiersz jest przesuwany w prawo.</span><span class="sxs-lookup"><span data-stu-id="52854-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="52854-121">Element LeftIndent ramki kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="52854-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="52854-122">Optional element.</span></span><br /><br /> <span data-ttu-id="52854-123">Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="52854-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="52854-124">Element RightIndent ramki kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="52854-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="52854-125">Optional element.</span></span><br /><br /> <span data-ttu-id="52854-126">Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="52854-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="52854-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="52854-127">Parent Elements</span></span>

|<span data-ttu-id="52854-128">Element</span><span class="sxs-lookup"><span data-stu-id="52854-128">Element</span></span>|<span data-ttu-id="52854-129">Opis</span><span class="sxs-lookup"><span data-stu-id="52854-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52854-130">Element CustomItem CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="52854-131">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="52854-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52854-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52854-132">Remarks</span></span>

<span data-ttu-id="52854-133">Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementów w tym samym `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="52854-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="52854-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52854-134">See Also</span></span>

[<span data-ttu-id="52854-135">Element FirstLineHanging ramki kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="52854-136">Element FirstLineIndent ramki kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="52854-137">Element LeftIndent ramki kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="52854-138">Element RightIndent ramki kontrolki widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="52854-139">Element CustomItem CustomEntry dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="52854-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="52854-140">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="52854-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
