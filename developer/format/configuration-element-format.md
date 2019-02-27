---
title: Element konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847040"
---
# <a name="configuration-element-format"></a><span data-ttu-id="3995d-102">Configuration, element (format)</span><span class="sxs-lookup"><span data-stu-id="3995d-102">Configuration Element (Format)</span></span>

<span data-ttu-id="3995d-103">Reprezentuje element najwyższego poziomu w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="3995d-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="3995d-104">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3995d-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="3995d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3995d-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3995d-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3995d-106">Attributes and Elements</span></span>

<span data-ttu-id="3995d-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Configuration` elementu.</span><span class="sxs-lookup"><span data-stu-id="3995d-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="3995d-108">Ten element musi być elementem głównym dla każdego pliku formatowania, a ten element musi zawierać co najmniej jeden element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="3995d-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3995d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3995d-109">Attributes</span></span>

<span data-ttu-id="3995d-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="3995d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3995d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3995d-111">Child Elements</span></span>

|<span data-ttu-id="3995d-112">Element</span><span class="sxs-lookup"><span data-stu-id="3995d-112">Element</span></span>|<span data-ttu-id="3995d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3995d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3995d-114">Kontrolki elementu konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="3995d-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="3995d-115">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3995d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3995d-116">Definiuje typowe formanty, które mogą być używane przez wszystkie widoki formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="3995d-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="3995d-117">Element DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="3995d-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="3995d-118">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3995d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3995d-119">Definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="3995d-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="3995d-120">Format elementu SelectionSets</span><span class="sxs-lookup"><span data-stu-id="3995d-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="3995d-121">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3995d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3995d-122">Definiuje typowe rodzaje obiektów platformy .NET, które mogą być używane przez wszystkie widoki formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="3995d-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="3995d-123">Element ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="3995d-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="3995d-124">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3995d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3995d-125">Zawiera definicje widoków, używany do wyświetlania obiektów.</span><span class="sxs-lookup"><span data-stu-id="3995d-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3995d-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3995d-126">Parent Elements</span></span>

<span data-ttu-id="3995d-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="3995d-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="3995d-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3995d-128">Remarks</span></span>

<span data-ttu-id="3995d-129">Pliki formatowania zdefiniować sposób wyświetlania obiektów.</span><span class="sxs-lookup"><span data-stu-id="3995d-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="3995d-130">W większości przypadków zawiera ten element główny [ViewDefinitions](./viewdefinitions-element-format.md) element, który definiuje tabel, list i szeroki widoków formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="3995d-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="3995d-131">Oprócz definicji widoku formatowania pliku można zdefiniować wspólne zestawów zaznaczenia, ustawienia i kontrolki używające tych widoków.</span><span class="sxs-lookup"><span data-stu-id="3995d-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="3995d-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3995d-132">See Also</span></span>

[<span data-ttu-id="3995d-133">Kontrolki elementu konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="3995d-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="3995d-134">Element DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="3995d-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="3995d-135">Element SelectionSets (Format)</span><span class="sxs-lookup"><span data-stu-id="3995d-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="3995d-136">Element ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="3995d-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="3995d-137">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="3995d-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
