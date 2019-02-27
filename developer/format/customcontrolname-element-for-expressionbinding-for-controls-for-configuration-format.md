---
title: Element CustomControlName ExpressionBinding dla formantów dla konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847033"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="c0671-102">CustomControlName, element — ExpressionBinding, Controls, Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="c0671-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c0671-103">Określa nazwę formantu wspólnego.</span><span class="sxs-lookup"><span data-stu-id="c0671-103">Specifies the name of a common control.</span></span> <span data-ttu-id="c0671-104">Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.</span><span class="sxs-lookup"><span data-stu-id="c0671-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c0671-105">Konfiguracji elementu (w formacie) kontrolki elementu konfiguracji (Format) formantu dla formantów dla elementu formant niestandardowy konfiguracji (w formacie) dla kontrolki elementu CustomEntries konfiguracji (Format), formant niestandardowy do konfiguracji ( Format) elementu CustomEntry formant niestandardowy dla formantów CustomItem elementu konfiguracji (Format) CustomEntry dla formantów dla konfiguracji elementu ExpressionBinding CustomItem dla kontrolki CustomControlName konfiguracji (Format) Element ExpressionBinding dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c0671-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0671-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0671-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0671-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c0671-107">Attributes and Elements</span></span>

<span data-ttu-id="c0671-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomControlName` elementu.</span><span class="sxs-lookup"><span data-stu-id="c0671-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0671-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c0671-109">Attributes</span></span>

<span data-ttu-id="c0671-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="c0671-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0671-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c0671-111">Child Elements</span></span>

<span data-ttu-id="c0671-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="c0671-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c0671-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c0671-113">Parent Elements</span></span>

|<span data-ttu-id="c0671-114">Element</span><span class="sxs-lookup"><span data-stu-id="c0671-114">Element</span></span>|<span data-ttu-id="c0671-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c0671-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0671-116">Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c0671-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="c0671-117">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="c0671-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c0671-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="c0671-118">Text Value</span></span>

<span data-ttu-id="c0671-119">Należy określić nazwę formantu.</span><span class="sxs-lookup"><span data-stu-id="c0671-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0671-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0671-120">Remarks</span></span>

<span data-ttu-id="c0671-121">Można utworzyć wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku, a następnie można utworzyć kontrolki widoku, które mogą być używane przez określonego widoku.</span><span class="sxs-lookup"><span data-stu-id="c0671-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="c0671-122">Następujące elementy określane są nazwy tych formantów:</span><span class="sxs-lookup"><span data-stu-id="c0671-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="c0671-123">Name — Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c0671-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="c0671-124">Name — Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="c0671-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="c0671-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0671-125">See Also</span></span>

[<span data-ttu-id="c0671-126">Name — Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c0671-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="c0671-127">Name — Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="c0671-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c0671-128">Element ExpressionBinding CustomItem dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="c0671-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="c0671-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="c0671-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
