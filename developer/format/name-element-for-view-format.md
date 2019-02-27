---
title: Nazwa elementu widoku (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849266"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="67c7e-102">Name, element — View (format)</span><span class="sxs-lookup"><span data-stu-id="67c7e-102">Name Element for View (Format)</span></span>

<span data-ttu-id="67c7e-103">Określa nazwę, która służy do identyfikacji tego widoku.</span><span class="sxs-lookup"><span data-stu-id="67c7e-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="67c7e-104">Widok elementu ViewDefinitions (Format) — Element (w formacie) konfiguracji elementu (w formacie) elementu Name (Format)</span><span class="sxs-lookup"><span data-stu-id="67c7e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67c7e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="67c7e-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67c7e-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="67c7e-106">Attributes and Elements</span></span>

<span data-ttu-id="67c7e-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Name` elementu.</span><span class="sxs-lookup"><span data-stu-id="67c7e-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="67c7e-108">Tylko jeden `Name` element jest dozwolony dla każdego widoku.</span><span class="sxs-lookup"><span data-stu-id="67c7e-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="67c7e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="67c7e-109">Attributes</span></span>

<span data-ttu-id="67c7e-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="67c7e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67c7e-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="67c7e-111">Child Elements</span></span>

<span data-ttu-id="67c7e-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="67c7e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67c7e-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="67c7e-113">Parent Elements</span></span>

|<span data-ttu-id="67c7e-114">Element</span><span class="sxs-lookup"><span data-stu-id="67c7e-114">Element</span></span>|<span data-ttu-id="67c7e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="67c7e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67c7e-116">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="67c7e-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="67c7e-117">Określa widok, który służy do wyświetlania elementów członkowskich jeden lub więcej obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="67c7e-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67c7e-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="67c7e-118">Text Value</span></span>

<span data-ttu-id="67c7e-119">Określ unikatową przyjazną nazwę dla widoku.</span><span class="sxs-lookup"><span data-stu-id="67c7e-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="67c7e-120">Ta nazwa może zawierać odwołanie do typu widoku (np. widok tabeli lub widoku listy), które obiekt lub zestaw obiektów przy użyciu widoku, jakie polecenie zwraca obiekty lub kombinację tych.</span><span class="sxs-lookup"><span data-stu-id="67c7e-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="67c7e-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67c7e-121">Remarks</span></span>

<span data-ttu-id="67c7e-122">Aby uzyskać więcej informacji o różnych typach widoków zobacz następujące tematy: [Widok tabeli](./creating-a-table-view.md), [widok listy](./creating-a-list-view.md), [szerokie](./creating-a-wide-view.md), i [widok niestandardowy](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="67c7e-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="67c7e-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="67c7e-123">Example</span></span>

<span data-ttu-id="67c7e-124">W poniższym przykładzie przedstawiono `View` element, który definiuje widoku tabeli dla [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiektu.</span><span class="sxs-lookup"><span data-stu-id="67c7e-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="67c7e-125">Nazwa widoku jest "Usługa".</span><span class="sxs-lookup"><span data-stu-id="67c7e-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="67c7e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67c7e-126">See Also</span></span>

[<span data-ttu-id="67c7e-127">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="67c7e-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="67c7e-128">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="67c7e-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="67c7e-129">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="67c7e-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="67c7e-130">Tworzenie niestandardowych formantów</span><span class="sxs-lookup"><span data-stu-id="67c7e-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="67c7e-131">Widok elementu (w formacie)</span><span class="sxs-lookup"><span data-stu-id="67c7e-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="67c7e-132">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="67c7e-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
