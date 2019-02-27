---
title: Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850918"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="976d6-102">ItemSelectionCondition, element — ListItem, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="976d6-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="976d6-103">Określa warunek, który musi istnieć przez ten element listy do użycia.</span><span class="sxs-lookup"><span data-stu-id="976d6-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="976d6-104">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListEntries elementu ListControl (Format) elementu ListItems ListEntry dla elementu ListControl (Format) elementu ListItem ListItems elementu ListControl (Format) ItemSelectionCondition elementu ListItem dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="976d6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="976d6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="976d6-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="976d6-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="976d6-106">Attributes and Elements</span></span>

<span data-ttu-id="976d6-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ItemSelectionCondition` elementu.</span><span class="sxs-lookup"><span data-stu-id="976d6-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="976d6-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="976d6-108">Attributes</span></span>

<span data-ttu-id="976d6-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="976d6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="976d6-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="976d6-110">Child Elements</span></span>

|<span data-ttu-id="976d6-111">Element</span><span class="sxs-lookup"><span data-stu-id="976d6-111">Element</span></span>|<span data-ttu-id="976d6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="976d6-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="976d6-113">Element PropertyName ItemSelectionCondition dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="976d6-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="976d6-114">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="976d6-114">Optional element.</span></span><br /><br /> <span data-ttu-id="976d6-115">Określa właściwości platformy .NET, która wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="976d6-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="976d6-116">Element ScriptBlock ItemSelectionCondition dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="976d6-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="976d6-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="976d6-117">Optional element.</span></span><br /><br /> <span data-ttu-id="976d6-118">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="976d6-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="976d6-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="976d6-119">Parent Elements</span></span>

|<span data-ttu-id="976d6-120">Element</span><span class="sxs-lookup"><span data-stu-id="976d6-120">Element</span></span>|<span data-ttu-id="976d6-121">Opis</span><span class="sxs-lookup"><span data-stu-id="976d6-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="976d6-122">Element ListItem ListItems dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="976d6-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="976d6-123">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="976d6-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="976d6-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="976d6-124">Remarks</span></span>

<span data-ttu-id="976d6-125">Można określić jedną nazwę właściwości lub skrypt dla tego warunku, ale nie można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="976d6-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="976d6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="976d6-126">See Also</span></span>

[<span data-ttu-id="976d6-127">Element ListItem ListItems dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="976d6-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="976d6-128">Element PropertyName ItemSelectionCondition dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="976d6-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="976d6-129">Element ScriptBlock ItemSelectionCondition dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="976d6-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="976d6-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="976d6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
