---
title: Ramkę elementu CustomItem dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065601"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="f26cc-102">Frame, element — CustomItem, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f26cc-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="f26cc-103">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="f26cc-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="f26cc-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="f26cc-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f26cc-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ramki CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f26cc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f26cc-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f26cc-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f26cc-107">Attributes and Elements</span></span>

<span data-ttu-id="f26cc-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="f26cc-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f26cc-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f26cc-109">Attributes</span></span>

<span data-ttu-id="f26cc-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="f26cc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f26cc-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f26cc-111">Child Elements</span></span>

|<span data-ttu-id="f26cc-112">Element</span><span class="sxs-lookup"><span data-stu-id="f26cc-112">Element</span></span>|<span data-ttu-id="f26cc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f26cc-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="f26cc-114">Wymagany Element</span><span class="sxs-lookup"><span data-stu-id="f26cc-114">Required Element</span></span>|
|[<span data-ttu-id="f26cc-115">Element FirstLineHanging ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="f26cc-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f26cc-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f26cc-117">Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.</span><span class="sxs-lookup"><span data-stu-id="f26cc-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="f26cc-118">Element FirstLineIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="f26cc-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f26cc-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f26cc-120">Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.</span><span class="sxs-lookup"><span data-stu-id="f26cc-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="f26cc-121">Element LeftIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="f26cc-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f26cc-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f26cc-123">Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="f26cc-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="f26cc-124">[Element RightIndent ramki dla grupowania (w formacie)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent — Element</span><span class="sxs-lookup"><span data-stu-id="f26cc-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="f26cc-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f26cc-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f26cc-126">Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="f26cc-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f26cc-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f26cc-127">Parent Elements</span></span>

|<span data-ttu-id="f26cc-128">Element</span><span class="sxs-lookup"><span data-stu-id="f26cc-128">Element</span></span>|<span data-ttu-id="f26cc-129">Opis</span><span class="sxs-lookup"><span data-stu-id="f26cc-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f26cc-130">Element CustomItem CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="f26cc-131">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="f26cc-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f26cc-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f26cc-132">Remarks</span></span>

<span data-ttu-id="f26cc-133">Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementów w tym samym `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="f26cc-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f26cc-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f26cc-134">See Also</span></span>

[<span data-ttu-id="f26cc-135">Element FirstLineHanging ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="f26cc-136">Element FirstLineIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="f26cc-137">Element LeftIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="f26cc-138">Element RightIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="f26cc-139">Element CustomItem CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="f26cc-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="f26cc-140">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="f26cc-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
