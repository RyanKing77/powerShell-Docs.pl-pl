---
title: Wyświetlanie elementu (w formacie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846914"
---
# <a name="view-element-format"></a><span data-ttu-id="593d3-102">View, element (format)</span><span class="sxs-lookup"><span data-stu-id="593d3-102">View Element (Format)</span></span>

<span data-ttu-id="593d3-103">Określa widok, który zawiera jeden lub więcej obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="593d3-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="593d3-104">Nie ma żadnego limitu liczby widoków, które mogą być definiowane w pliku formatowania.</span><span class="sxs-lookup"><span data-stu-id="593d3-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="593d3-105">Element widoku elementu ViewDefinitions (Format) — Element (w formacie) konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="593d3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="593d3-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="593d3-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="593d3-107">Attributes and Elements</span></span>

<span data-ttu-id="593d3-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `View` elementu.</span><span class="sxs-lookup"><span data-stu-id="593d3-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="593d3-109">Należy określić jeden i tylko jeden z elementów podrzędnych kontrolki, a następnie należy określić nazwę tego widoku i obiekty przez nie przy użyciu widoku.</span><span class="sxs-lookup"><span data-stu-id="593d3-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="593d3-110">Definiowanie kontrolek niestandardowych, jak należy zgrupować obiekty i określanie, czy widok jest poza pasmem są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="593d3-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="593d3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="593d3-111">Attributes</span></span>

<span data-ttu-id="593d3-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="593d3-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="593d3-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="593d3-113">Child Elements</span></span>

|<span data-ttu-id="593d3-114">Element</span><span class="sxs-lookup"><span data-stu-id="593d3-114">Element</span></span>|<span data-ttu-id="593d3-115">Opis</span><span class="sxs-lookup"><span data-stu-id="593d3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="593d3-116">Kontrolki elementu widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="593d3-117">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="593d3-117">Optional element.</span></span><br /><br /> <span data-ttu-id="593d3-118">Definiuje zestaw elementów sterujących, które mogą być przywoływane przez ich nazwy z w widoku.</span><span class="sxs-lookup"><span data-stu-id="593d3-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="593d3-119">Formant niestandardowy, Element (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="593d3-120">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="593d3-120">Optional element.</span></span><br /><br /> <span data-ttu-id="593d3-121">Definiuje format formantu niestandardowego dla widoku.</span><span class="sxs-lookup"><span data-stu-id="593d3-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="593d3-122">GroupBy — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="593d3-123">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="593d3-123">Optional element.</span></span><br /><br /> <span data-ttu-id="593d3-124">Definiuje sposób grupowania elementów członkowskich obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="593d3-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="593d3-125">Element elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="593d3-126">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="593d3-126">Optional element.</span></span><br /><br /> <span data-ttu-id="593d3-127">Definiuje format listy dla widoku.</span><span class="sxs-lookup"><span data-stu-id="593d3-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="593d3-128">Name — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="593d3-129">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="593d3-129">Required element.</span></span><br /><br /> <span data-ttu-id="593d3-130">Określa nazwę używaną do odwoływać się do widoku.</span><span class="sxs-lookup"><span data-stu-id="593d3-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="593d3-131">Tablecontrol — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="593d3-132">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="593d3-132">Optional element.</span></span><br /><br /> <span data-ttu-id="593d3-133">Definiuje format tabeli, widoku.</span><span class="sxs-lookup"><span data-stu-id="593d3-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="593d3-134">Element ViewSelectedBy widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="593d3-135">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="593d3-135">Required element.</span></span><br /><br /> <span data-ttu-id="593d3-136">Definiuje obiekty .NET, które ten widok przedstawia.</span><span class="sxs-lookup"><span data-stu-id="593d3-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="593d3-137">Element WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="593d3-138">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="593d3-138">Optional element.</span></span><br /><br /> <span data-ttu-id="593d3-139">Definiuje całej (pojedyncza wartość) format listy dla widoku.</span><span class="sxs-lookup"><span data-stu-id="593d3-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="593d3-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="593d3-140">Parent Elements</span></span>

|<span data-ttu-id="593d3-141">Element</span><span class="sxs-lookup"><span data-stu-id="593d3-141">Element</span></span>|<span data-ttu-id="593d3-142">Opis</span><span class="sxs-lookup"><span data-stu-id="593d3-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="593d3-143">Element ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="593d3-144">Zawiera definicje widoków, używany do wyświetlania obiektów.</span><span class="sxs-lookup"><span data-stu-id="593d3-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="593d3-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="593d3-145">Remarks</span></span>

<span data-ttu-id="593d3-146">Aby uzyskać więcej informacji o składnikach z różnych widoków i kontrolek niestandardowych zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="593d3-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="593d3-147">Składniki widoków tabeli</span><span class="sxs-lookup"><span data-stu-id="593d3-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="593d3-148">Składniki widoków list</span><span class="sxs-lookup"><span data-stu-id="593d3-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="593d3-149">Szerokie składników</span><span class="sxs-lookup"><span data-stu-id="593d3-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="593d3-150">Formanty niestandardowe</span><span class="sxs-lookup"><span data-stu-id="593d3-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="593d3-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="593d3-151">Example</span></span>

<span data-ttu-id="593d3-152">W tym przykładzie `View` element, który definiuje widoku tabeli dla [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.</span><span class="sxs-lookup"><span data-stu-id="593d3-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="593d3-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="593d3-153">See Also</span></span>

[<span data-ttu-id="593d3-154">Element ViewDefinitions (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="593d3-155">Name — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="593d3-156">Element ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="593d3-157">Kontrolki elementu widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="593d3-158">GroupBy — Element dla widoku (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="593d3-159">Tablecontrol — Element (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="593d3-160">Element elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="593d3-161">Element WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="593d3-162">Formant niestandardowy, Element (Format)</span><span class="sxs-lookup"><span data-stu-id="593d3-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="593d3-163">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="593d3-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
