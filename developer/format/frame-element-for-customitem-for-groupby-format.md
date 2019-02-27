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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846004"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="90600-102">Frame, element — CustomItem, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="90600-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="90600-103">Definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony.</span><span class="sxs-lookup"><span data-stu-id="90600-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="90600-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="90600-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="90600-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ramki CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90600-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="90600-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90600-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="90600-107">Attributes and Elements</span></span>

<span data-ttu-id="90600-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="90600-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="90600-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="90600-109">Attributes</span></span>

<span data-ttu-id="90600-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="90600-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90600-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="90600-111">Child Elements</span></span>

|<span data-ttu-id="90600-112">Element</span><span class="sxs-lookup"><span data-stu-id="90600-112">Element</span></span>|<span data-ttu-id="90600-113">Opis</span><span class="sxs-lookup"><span data-stu-id="90600-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="90600-114">Wymagany Element</span><span class="sxs-lookup"><span data-stu-id="90600-114">Required Element</span></span>|
|[<span data-ttu-id="90600-115">Element FirstLineHanging ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="90600-116">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="90600-116">Optional element.</span></span><br /><br /> <span data-ttu-id="90600-117">Określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo.</span><span class="sxs-lookup"><span data-stu-id="90600-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="90600-118">Element FirstLineIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="90600-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="90600-119">Optional element.</span></span><br /><br /> <span data-ttu-id="90600-120">Określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo.</span><span class="sxs-lookup"><span data-stu-id="90600-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="90600-121">Element LeftIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="90600-122">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="90600-122">Optional element.</span></span><br /><br /> <span data-ttu-id="90600-123">Określa liczbę znaków od lewego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="90600-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="90600-124">[Element RightIndent ramki dla grupowania (w formacie)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent — Element</span><span class="sxs-lookup"><span data-stu-id="90600-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="90600-125">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="90600-125">Optional element.</span></span><br /><br /> <span data-ttu-id="90600-126">Określa liczbę znaków od prawego marginesu zostanie przesunięty w danych.</span><span class="sxs-lookup"><span data-stu-id="90600-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="90600-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="90600-127">Parent Elements</span></span>

|<span data-ttu-id="90600-128">Element</span><span class="sxs-lookup"><span data-stu-id="90600-128">Element</span></span>|<span data-ttu-id="90600-129">Opis</span><span class="sxs-lookup"><span data-stu-id="90600-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90600-130">Element CustomItem CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="90600-131">Definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="90600-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="90600-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90600-132">Remarks</span></span>

<span data-ttu-id="90600-133">Nie można określić [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) i [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementów w tym samym `Frame` elementu.</span><span class="sxs-lookup"><span data-stu-id="90600-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="90600-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90600-134">See Also</span></span>

[<span data-ttu-id="90600-135">Element FirstLineHanging ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="90600-136">Element FirstLineIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="90600-137">Element LeftIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="90600-138">Element RightIndent ramki dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="90600-139">Element CustomItem CustomEntry dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="90600-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="90600-140">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="90600-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
