---
title: GroupBy — Element dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849280"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="79718-102">GroupBy, element — View (format)</span><span class="sxs-lookup"><span data-stu-id="79718-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="79718-103">Definiuje sposób wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="79718-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="79718-104">Ten element jest używany podczas definiowania tabel, list, szeroki lub niestandardowe kontrolki widoku.</span><span class="sxs-lookup"><span data-stu-id="79718-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="79718-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="79718-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79718-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="79718-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79718-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="79718-107">Attributes and Elements</span></span>

<span data-ttu-id="79718-108">Poniżej opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="79718-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="79718-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="79718-109">Attributes</span></span>

<span data-ttu-id="79718-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="79718-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79718-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="79718-111">Child Elements</span></span>

|<span data-ttu-id="79718-112">Element</span><span class="sxs-lookup"><span data-stu-id="79718-112">Element</span></span>|<span data-ttu-id="79718-113">Opis</span><span class="sxs-lookup"><span data-stu-id="79718-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79718-114">Element formant niestandardowy do grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="79718-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="79718-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="79718-115">Optional element.</span></span><br /><br /> <span data-ttu-id="79718-116">Definiuje kontrolki niestandardowej, która wyświetlanie nowych grup.</span><span class="sxs-lookup"><span data-stu-id="79718-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="79718-117">Element CustomControlName GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79718-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="79718-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="79718-118">Optional element.</span></span><br /><br /> <span data-ttu-id="79718-119">Określa nazwę formant, który służy do wyświetlania nowej grupy.</span><span class="sxs-lookup"><span data-stu-id="79718-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="79718-120">Element LABEL dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="79718-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="79718-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="79718-121">Optional element.</span></span><br /><br /> <span data-ttu-id="79718-122">Określa etykietę, która jest wyświetlana, gdy zostanie osiągnięty nowej grupy.</span><span class="sxs-lookup"><span data-stu-id="79718-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="79718-123">Element PropertyName GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79718-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="79718-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="79718-124">Optional element.</span></span><br /><br /> <span data-ttu-id="79718-125">Określa właściwości platformy .NET tak, rozpoczyna się nowa grupa zmianie wartości.</span><span class="sxs-lookup"><span data-stu-id="79718-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="79718-126">Element ScriptBlock GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79718-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="79718-127">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="79718-127">Optional element.</span></span><br /><br /> <span data-ttu-id="79718-128">Określa skrypt, który uruchamia nową grupę, zmianie wartości.</span><span class="sxs-lookup"><span data-stu-id="79718-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="79718-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="79718-129">Parent Elements</span></span>

|<span data-ttu-id="79718-130">Element</span><span class="sxs-lookup"><span data-stu-id="79718-130">Element</span></span>|<span data-ttu-id="79718-131">Opis</span><span class="sxs-lookup"><span data-stu-id="79718-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79718-132">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="79718-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="79718-133">Określa widok, który zawiera jeden lub więcej obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="79718-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="79718-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79718-134">Remarks</span></span>

<span data-ttu-id="79718-135">Podczas definiowania sposobu wyświetlania nowej grupy obiektów, należy określić właściwość lub skryptu, który rozpocznie się do nowej grupy; jednak nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="79718-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="79718-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79718-136">See Also</span></span>

[<span data-ttu-id="79718-137">Element CustomControlName GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79718-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="79718-138">Element LABEL dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="79718-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="79718-139">Element PropertyName GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79718-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="79718-140">Element ScriptBlock GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="79718-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="79718-141">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="79718-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="79718-142">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="79718-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
