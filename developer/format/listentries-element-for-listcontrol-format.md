---
title: Element ListEntries dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065397"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="7ec3c-102">ListEntries, element — ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7ec3c-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="7ec3c-103">Zawiera definicje w widoku listy.</span><span class="sxs-lookup"><span data-stu-id="7ec3c-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="7ec3c-104">Widok listy, należy określić co najmniej jedną definicję.</span><span class="sxs-lookup"><span data-stu-id="7ec3c-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="7ec3c-105">Konfiguracji elementu (w formacie) Element ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (w formacie) ListEntries elemencie (Format)</span><span class="sxs-lookup"><span data-stu-id="7ec3c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ec3c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ec3c-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7ec3c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7ec3c-107">Attributes and Elements</span></span>

<span data-ttu-id="7ec3c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `ListEntries` elementu.</span><span class="sxs-lookup"><span data-stu-id="7ec3c-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="7ec3c-109">Należy określić co najmniej jeden element podrzędny elementu.</span><span class="sxs-lookup"><span data-stu-id="7ec3c-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7ec3c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7ec3c-110">Attributes</span></span>

<span data-ttu-id="7ec3c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="7ec3c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7ec3c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7ec3c-112">Child Elements</span></span>

|<span data-ttu-id="7ec3c-113">Element</span><span class="sxs-lookup"><span data-stu-id="7ec3c-113">Element</span></span>|<span data-ttu-id="7ec3c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7ec3c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ec3c-115">Element ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7ec3c-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="7ec3c-116">Zawiera definicję widoku listy.</span><span class="sxs-lookup"><span data-stu-id="7ec3c-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7ec3c-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7ec3c-117">Parent Elements</span></span>

|<span data-ttu-id="7ec3c-118">Element</span><span class="sxs-lookup"><span data-stu-id="7ec3c-118">Element</span></span>|<span data-ttu-id="7ec3c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7ec3c-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ec3c-120">Element elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7ec3c-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="7ec3c-121">Definiuje format listy dla widoku.</span><span class="sxs-lookup"><span data-stu-id="7ec3c-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7ec3c-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ec3c-122">Remarks</span></span>

<span data-ttu-id="7ec3c-123">Aby uzyskać więcej informacji na temat widoki list zobacz [widok listy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7ec3c-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7ec3c-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ec3c-124">Example</span></span>

<span data-ttu-id="7ec3c-125">Elementy XML, które określają widok listy w tym przykładzie [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.</span><span class="sxs-lookup"><span data-stu-id="7ec3c-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="7ec3c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ec3c-126">See Also</span></span>

[<span data-ttu-id="7ec3c-127">Element elementu ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7ec3c-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="7ec3c-128">Element ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7ec3c-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="7ec3c-129">Widok listy</span><span class="sxs-lookup"><span data-stu-id="7ec3c-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7ec3c-130">Pisanie programu Windows PowerShell, formatowania i typy plików</span><span class="sxs-lookup"><span data-stu-id="7ec3c-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
