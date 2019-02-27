---
title: Element elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847831"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="5ad44-102">ListControl, element (format)</span><span class="sxs-lookup"><span data-stu-id="5ad44-102">ListControl Element (Format)</span></span>

<span data-ttu-id="5ad44-103">Definiuje format listy dla widoku.</span><span class="sxs-lookup"><span data-stu-id="5ad44-103">Defines a list format for the view.</span></span>

<span data-ttu-id="5ad44-104">Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl elemencie (Format)</span><span class="sxs-lookup"><span data-stu-id="5ad44-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ad44-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ad44-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ad44-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5ad44-106">Attributes and Elements</span></span>

<span data-ttu-id="5ad44-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ListControl` elementu.</span><span class="sxs-lookup"><span data-stu-id="5ad44-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="5ad44-108">Ten element musi zawierać tylko jeden typ elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5ad44-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ad44-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ad44-109">Attributes</span></span>

<span data-ttu-id="5ad44-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="5ad44-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ad44-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5ad44-111">Child Elements</span></span>

|<span data-ttu-id="5ad44-112">Element</span><span class="sxs-lookup"><span data-stu-id="5ad44-112">Element</span></span>|<span data-ttu-id="5ad44-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5ad44-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ad44-114">Element ListEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="5ad44-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="5ad44-115">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="5ad44-115">Required element.</span></span><br /><br /> <span data-ttu-id="5ad44-116">Zawiera definicje w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="5ad44-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ad44-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5ad44-117">Parent Elements</span></span>

|<span data-ttu-id="5ad44-118">Element</span><span class="sxs-lookup"><span data-stu-id="5ad44-118">Element</span></span>|<span data-ttu-id="5ad44-119">Opis</span><span class="sxs-lookup"><span data-stu-id="5ad44-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ad44-120">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="5ad44-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="5ad44-121">Określa widok, który służy do wyświetlania elementów członkowskich co najmniej jeden obiekt.</span><span class="sxs-lookup"><span data-stu-id="5ad44-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ad44-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ad44-122">Remarks</span></span>

<span data-ttu-id="5ad44-123">Aby uzyskać więcej informacji o tworzeniu widoku listy, zobacz [tworzenia widoku listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5ad44-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5ad44-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ad44-124">Example</span></span>

<span data-ttu-id="5ad44-125">W tym przykładzie przedstawiono widok listy dla [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.</span><span class="sxs-lookup"><span data-stu-id="5ad44-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="5ad44-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ad44-126">See Also</span></span>

[<span data-ttu-id="5ad44-127">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="5ad44-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="5ad44-128">Element ListEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="5ad44-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="5ad44-129">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="5ad44-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5ad44-130">Pisanie programu Windows PowerShell, formatowania i typy plików</span><span class="sxs-lookup"><span data-stu-id="5ad44-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
