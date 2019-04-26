---
title: Element ScriptBlock ItemSelectionCondition dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064411"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="4ee99-102">ScriptBlock, element — ItemSelectionCondition, ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="4ee99-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="4ee99-103">Określa skrypt, który wyzwala warunku.</span><span class="sxs-lookup"><span data-stu-id="4ee99-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="4ee99-104">Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany w elemencie listy.</span><span class="sxs-lookup"><span data-stu-id="4ee99-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="4ee99-105">Ten element jest używany podczas definiowania widoku listy.</span><span class="sxs-lookup"><span data-stu-id="4ee99-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="4ee99-106">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListEntries elementu ListControl (Format) elementu ListItems ListEntry dla elementu ListControl (Format) elementu ListItem ListItems listy kontroli (Format) ItemSelectionCondition elementu ListItem elementu ListControl (Format) elementu ScriptBlock ItemSelectionCondition dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4ee99-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ee99-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ee99-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ee99-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4ee99-108">Attributes and Elements</span></span>

<span data-ttu-id="4ee99-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `ScriptBlock` elementu.</span><span class="sxs-lookup"><span data-stu-id="4ee99-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ee99-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4ee99-110">Attributes</span></span>

<span data-ttu-id="4ee99-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="4ee99-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ee99-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4ee99-112">Child Elements</span></span>

<span data-ttu-id="4ee99-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="4ee99-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ee99-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4ee99-114">Parent Elements</span></span>

|<span data-ttu-id="4ee99-115">Element</span><span class="sxs-lookup"><span data-stu-id="4ee99-115">Element</span></span>|<span data-ttu-id="4ee99-116">Opis</span><span class="sxs-lookup"><span data-stu-id="4ee99-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ee99-117">Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4ee99-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="4ee99-118">Określa warunek, który musi istnieć przez ten element listy do użycia.</span><span class="sxs-lookup"><span data-stu-id="4ee99-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4ee99-119">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="4ee99-119">Text Value</span></span>

<span data-ttu-id="4ee99-120">Określ skrypt, który jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="4ee99-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ee99-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ee99-121">Remarks</span></span>

<span data-ttu-id="4ee99-122">Jeśli ten element jest używany, nie można określić `PropertyName` elementu podczas definiowania warunek wyboru.</span><span class="sxs-lookup"><span data-stu-id="4ee99-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ee99-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ee99-123">See Also</span></span>

[<span data-ttu-id="4ee99-124">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="4ee99-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
