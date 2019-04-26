---
title: Element CustomControlName ExpressionBinding dla formant niestandardowy dla widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066621"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="a14c8-102">CustomControlName, element — ExpressionBinding, CustomControl, View (format)</span><span class="sxs-lookup"><span data-stu-id="a14c8-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="a14c8-103">Określa nazwę wspólne kontrolki lub kontrolki widoku.</span><span class="sxs-lookup"><span data-stu-id="a14c8-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="a14c8-104">Ten element jest używany podczas definiowania widoku formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a14c8-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="a14c8-105">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) formant niestandardowy Element konfiguracji elementu CustomEntries widoku (Format), formant niestandardowy widok (w formacie) elementu CustomEntry CustomEntries dla CustomItem widoku (Format) Element CustomEntry dla elementu ExpressionBinding widoku (w formacie) dla elementu CustomControlName CustomItem (w formacie) dla wyrażenia wiązania dla CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="a14c8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a14c8-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a14c8-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a14c8-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a14c8-107">Attributes and Elements</span></span>

<span data-ttu-id="a14c8-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `CustomControlName` elementu.</span><span class="sxs-lookup"><span data-stu-id="a14c8-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a14c8-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a14c8-109">Attributes</span></span>

<span data-ttu-id="a14c8-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="a14c8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a14c8-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a14c8-111">Child Elements</span></span>

<span data-ttu-id="a14c8-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="a14c8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a14c8-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a14c8-113">Parent Elements</span></span>

|<span data-ttu-id="a14c8-114">Element</span><span class="sxs-lookup"><span data-stu-id="a14c8-114">Element</span></span>|<span data-ttu-id="a14c8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a14c8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a14c8-116">Element ExpressionBinding CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="a14c8-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="a14c8-117">Definiuje dane, które jest wyświetlany przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="a14c8-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a14c8-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="a14c8-118">Text Value</span></span>

<span data-ttu-id="a14c8-119">Należy określić nazwę formantu.</span><span class="sxs-lookup"><span data-stu-id="a14c8-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="a14c8-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a14c8-120">Remarks</span></span>

<span data-ttu-id="a14c8-121">Można utworzyć wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku, a następnie można utworzyć kontrolki widoku, które mogą być używane przez określonego widoku.</span><span class="sxs-lookup"><span data-stu-id="a14c8-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="a14c8-122">Nazwy te kontrolki są określone przez następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="a14c8-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="a14c8-123">Name — Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="a14c8-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="a14c8-124">Name — Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="a14c8-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="a14c8-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a14c8-125">See Also</span></span>

[<span data-ttu-id="a14c8-126">Name — Element dla formantu dla formantów dla konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="a14c8-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a14c8-127">Name — Element dla formantu dla formantów widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="a14c8-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a14c8-128">Element ExpressionBinding CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="a14c8-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="a14c8-129">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="a14c8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
