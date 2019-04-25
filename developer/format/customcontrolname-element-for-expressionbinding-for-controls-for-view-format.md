---
title: Element CustomControlName ExpressionBinding dla formantów widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066655"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="55719-102">CustomControlName, element — ExpressionBinding, Controls, View (format)</span><span class="sxs-lookup"><span data-stu-id="55719-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="55719-103">Określa nazwę wspólne kontrolki lub kontrolki widoku.</span><span class="sxs-lookup"><span data-stu-id="55719-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="55719-104">Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.</span><span class="sxs-lookup"><span data-stu-id="55719-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="55719-105">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) kontrolki elementu (w formacie) kontroli Element konfiguracji dla formantów dla elementu formant niestandardowy widok (w formacie) dla formantu dla formantów elementu CustomEntries widoku (Format) Formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla formantów widoku (Format) elementu CustomItem CustomEntry dla formantów widoku (Format) elementu ExpressionBinding CustomItem dla kontrolki CustomControlName widoku (Format) Element ExpressionBindine dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="55719-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55719-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="55719-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55719-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="55719-107">Attributes and Elements</span></span>

<span data-ttu-id="55719-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomControlName` elementu.</span><span class="sxs-lookup"><span data-stu-id="55719-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55719-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="55719-109">Attributes</span></span>

<span data-ttu-id="55719-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="55719-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55719-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="55719-111">Child Elements</span></span>

<span data-ttu-id="55719-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="55719-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55719-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="55719-113">Parent Elements</span></span>

|<span data-ttu-id="55719-114">Element</span><span class="sxs-lookup"><span data-stu-id="55719-114">Element</span></span>|<span data-ttu-id="55719-115">Opis</span><span class="sxs-lookup"><span data-stu-id="55719-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55719-116">Element ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="55719-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="55719-117">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="55719-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="55719-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="55719-118">Text Value</span></span>

<span data-ttu-id="55719-119">Należy określić nazwę formantu.</span><span class="sxs-lookup"><span data-stu-id="55719-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="55719-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55719-120">Remarks</span></span>

<span data-ttu-id="55719-121">Można utworzyć wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku, a następnie można utworzyć kontrolki widoku, które mogą być używane przez określonego widoku.</span><span class="sxs-lookup"><span data-stu-id="55719-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="55719-122">Następujące elementy określane są nazwy tych formantów:</span><span class="sxs-lookup"><span data-stu-id="55719-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="55719-123">Name — Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="55719-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="55719-124">Name — Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="55719-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="55719-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55719-125">See Also</span></span>

[<span data-ttu-id="55719-126">Name — Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="55719-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="55719-127">Name — Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="55719-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="55719-128">Element ExpressionBinding CustomItem dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="55719-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="55719-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="55719-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
