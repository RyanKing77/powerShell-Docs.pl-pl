---
title: Ramkę elementu dla CustomItem formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054785"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="27508-102">Frame, element — CustomItem, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="27508-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="27508-103">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="27508-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="27508-104">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="27508-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="27508-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry CustomControlView (Format) elementu ramki CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="27508-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27508-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="27508-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27508-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="27508-107">Attributes and Elements</span></span>

<span data-ttu-id="27508-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="27508-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="27508-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="27508-109">Attributes</span></span>

<span data-ttu-id="27508-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="27508-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27508-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="27508-111">Child Elements</span></span>

|<span data-ttu-id="27508-112">Element</span><span class="sxs-lookup"><span data-stu-id="27508-112">Element</span></span>|<span data-ttu-id="27508-113">Opis</span><span class="sxs-lookup"><span data-stu-id="27508-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="27508-114">Wymagany Element</span><span class="sxs-lookup"><span data-stu-id="27508-114">Required Element</span></span>|
|[<span data-ttu-id="27508-115">FirstLineHanging Element</span><span class="sxs-lookup"><span data-stu-id="27508-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="27508-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="27508-116">Optional element.</span></span><br /><br /> <span data-ttu-id="27508-117">Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.</span><span class="sxs-lookup"><span data-stu-id="27508-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="27508-118">FirstLineIndent Element</span><span class="sxs-lookup"><span data-stu-id="27508-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="27508-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="27508-119">Optional element.</span></span><br /><br /> <span data-ttu-id="27508-120">Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.</span><span class="sxs-lookup"><span data-stu-id="27508-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="27508-121">LeftIndent Element</span><span class="sxs-lookup"><span data-stu-id="27508-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="27508-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="27508-122">Optional element.</span></span><br /><br /> <span data-ttu-id="27508-123">Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="27508-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="27508-124">RightIndent Element</span><span class="sxs-lookup"><span data-stu-id="27508-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="27508-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="27508-125">Optional element.</span></span><br /><br /> <span data-ttu-id="27508-126">Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="27508-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="27508-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="27508-127">Parent Elements</span></span>

|<span data-ttu-id="27508-128">Element</span><span class="sxs-lookup"><span data-stu-id="27508-128">Element</span></span>|<span data-ttu-id="27508-129">Opis</span><span class="sxs-lookup"><span data-stu-id="27508-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27508-130">Element CustomItem CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="27508-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="27508-131">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="27508-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="27508-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27508-132">Remarks</span></span>

<span data-ttu-id="27508-133">Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementów w tym samym `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="27508-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="27508-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27508-134">See Also</span></span>

[<span data-ttu-id="27508-135">FirstLineHanging Element</span><span class="sxs-lookup"><span data-stu-id="27508-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27508-136">FirstLineIndent Element</span><span class="sxs-lookup"><span data-stu-id="27508-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27508-137">LeftIndent Element</span><span class="sxs-lookup"><span data-stu-id="27508-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27508-138">RightIndent Element</span><span class="sxs-lookup"><span data-stu-id="27508-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27508-139">Element CustomItem CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="27508-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27508-140">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="27508-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
