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
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850806"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="89644-102">Frame, element — CustomItem, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="89644-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="89644-103">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="89644-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="89644-104">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="89644-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="89644-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy, Element (Format) CustomEntries Element konfiguracji dla formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries elementu CustomItem widoku (Format) CustomEntry CutomControlView (Format) elementu ramki CustomItem dla formant niestandardowy dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="89644-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="89644-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="89644-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89644-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="89644-107">Attributes and Elements</span></span>

<span data-ttu-id="89644-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="89644-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="89644-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="89644-109">Attributes</span></span>

<span data-ttu-id="89644-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="89644-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89644-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="89644-111">Child Elements</span></span>

|<span data-ttu-id="89644-112">Element</span><span class="sxs-lookup"><span data-stu-id="89644-112">Element</span></span>|<span data-ttu-id="89644-113">Opis</span><span class="sxs-lookup"><span data-stu-id="89644-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="89644-114">Wymagany Element</span><span class="sxs-lookup"><span data-stu-id="89644-114">Required Element</span></span>|
|[<span data-ttu-id="89644-115">FirstLineHanging Element</span><span class="sxs-lookup"><span data-stu-id="89644-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="89644-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="89644-116">Optional element.</span></span><br /><br /> <span data-ttu-id="89644-117">Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.</span><span class="sxs-lookup"><span data-stu-id="89644-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="89644-118">FirstLineIndent Element</span><span class="sxs-lookup"><span data-stu-id="89644-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="89644-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="89644-119">Optional element.</span></span><br /><br /> <span data-ttu-id="89644-120">Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.</span><span class="sxs-lookup"><span data-stu-id="89644-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="89644-121">LeftIndent Element</span><span class="sxs-lookup"><span data-stu-id="89644-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="89644-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="89644-122">Optional element.</span></span><br /><br /> <span data-ttu-id="89644-123">Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="89644-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="89644-124">RightIndent Element</span><span class="sxs-lookup"><span data-stu-id="89644-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="89644-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="89644-125">Optional element.</span></span><br /><br /> <span data-ttu-id="89644-126">Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="89644-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="89644-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="89644-127">Parent Elements</span></span>

|<span data-ttu-id="89644-128">Element</span><span class="sxs-lookup"><span data-stu-id="89644-128">Element</span></span>|<span data-ttu-id="89644-129">Opis</span><span class="sxs-lookup"><span data-stu-id="89644-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89644-130">Element CustomItem CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="89644-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="89644-131">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="89644-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89644-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89644-132">Remarks</span></span>

<span data-ttu-id="89644-133">Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementów w tym samym `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="89644-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="89644-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89644-134">See Also</span></span>

[<span data-ttu-id="89644-135">FirstLineHanging Element</span><span class="sxs-lookup"><span data-stu-id="89644-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="89644-136">FirstLineIndent Element</span><span class="sxs-lookup"><span data-stu-id="89644-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="89644-137">LeftIndent Element</span><span class="sxs-lookup"><span data-stu-id="89644-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="89644-138">RightIndent Element</span><span class="sxs-lookup"><span data-stu-id="89644-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="89644-139">Element CustomItem CustomEntry widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="89644-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="89644-140">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="89644-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
