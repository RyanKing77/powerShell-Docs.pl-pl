---
title: Element CustomControlName ExpressionBinding dla grupowania (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845619"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="4b46d-102">CustomControlName, element — ExpressionBinding, GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="4b46d-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="4b46d-103">Określa nazwę wspólne kontrolki lub kontrolki widoku.</span><span class="sxs-lookup"><span data-stu-id="4b46d-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="4b46d-104">Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.</span><span class="sxs-lookup"><span data-stu-id="4b46d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4b46d-105">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) GroupBy Element konfiguracji dla elementu formant niestandardowy widok (w formacie) dla elementu CustomEntries GroupBy (Format), formant niestandardowy elementu CustomEntry GroupBy (Format) Formant niestandardowy GroupBy (Format) elementu CustomItem CustomEntry GroupBy (Format) elementu ExpressionBinding CustomItem GroupBy (Format) elementu CustomControlName ExpressionBinding dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="4b46d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b46d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b46d-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b46d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4b46d-107">Attributes and Elements</span></span>

<span data-ttu-id="4b46d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomControlName` elementu.</span><span class="sxs-lookup"><span data-stu-id="4b46d-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b46d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4b46d-109">Attributes</span></span>

<span data-ttu-id="4b46d-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="4b46d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b46d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4b46d-111">Child Elements</span></span>

<span data-ttu-id="4b46d-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="4b46d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4b46d-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4b46d-113">Parent Elements</span></span>

|<span data-ttu-id="4b46d-114">Element</span><span class="sxs-lookup"><span data-stu-id="4b46d-114">Element</span></span>|<span data-ttu-id="4b46d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4b46d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b46d-116">Element ExpressionBinding CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="4b46d-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="4b46d-117">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="4b46d-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4b46d-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="4b46d-118">Text Value</span></span>

<span data-ttu-id="4b46d-119">Należy określić nazwę formantu.</span><span class="sxs-lookup"><span data-stu-id="4b46d-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b46d-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b46d-120">Remarks</span></span>

<span data-ttu-id="4b46d-121">Można utworzyć wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku, a następnie można utworzyć kontrolki widoku, które mogą być używane przez określonego widoku.</span><span class="sxs-lookup"><span data-stu-id="4b46d-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="4b46d-122">Następujące elementy określane są nazwy tych formantów:</span><span class="sxs-lookup"><span data-stu-id="4b46d-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="4b46d-123">Name — Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="4b46d-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="4b46d-124">Name — Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="4b46d-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="4b46d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b46d-125">See Also</span></span>

[<span data-ttu-id="4b46d-126">Name — Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="4b46d-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="4b46d-127">Name — Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="4b46d-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="4b46d-128">Element ExpressionBinding CustomItem dla grupowania (w formacie)</span><span class="sxs-lookup"><span data-stu-id="4b46d-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="4b46d-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="4b46d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
