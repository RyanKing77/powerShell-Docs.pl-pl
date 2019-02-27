---
title: Element TypeName dla ViewSelectedBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848139"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="2785e-102">TypeName, element — ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="2785e-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="2785e-103">Określa obiekt .NET, który jest wyświetlany w widoku.</span><span class="sxs-lookup"><span data-stu-id="2785e-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="2785e-104">— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) ViewSelectedBy — Element (Format) TypeName Element konfiguracji dla ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2785e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2785e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2785e-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2785e-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2785e-106">Attributes and Elements</span></span>

<span data-ttu-id="2785e-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="2785e-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2785e-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2785e-108">Attributes</span></span>

<span data-ttu-id="2785e-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="2785e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2785e-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2785e-110">Child Elements</span></span>

<span data-ttu-id="2785e-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="2785e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2785e-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2785e-112">Parent Elements</span></span>

|<span data-ttu-id="2785e-113">Element</span><span class="sxs-lookup"><span data-stu-id="2785e-113">Element</span></span>|<span data-ttu-id="2785e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2785e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2785e-115">Element ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2785e-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="2785e-116">Definiuje obiekty .NET, które są wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="2785e-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2785e-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="2785e-117">Text Value</span></span>

<span data-ttu-id="2785e-118">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="2785e-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2785e-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2785e-119">Remarks</span></span>

<span data-ttu-id="2785e-120">Aby uzyskać więcej informacji o sposobie korzystania z tego elementu w różnych widokach, zobacz [tworzenia widoku tabeli](./creating-a-table-view.md), [tworzenia widoku listy](./creating-a-list-view.md), [tworzenia szerokiej widoku](./creating-a-wide-view.md), i [ Składniki widoków niestandardowych](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2785e-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="2785e-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="2785e-121">Example</span></span>

<span data-ttu-id="2785e-122">Poniższy przykład pokazuje, jak określić [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) obiekt widoku listy.</span><span class="sxs-lookup"><span data-stu-id="2785e-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="2785e-123">Ten sam schemat jest używany dla tabeli, szeroką i niestandardowe widoki.</span><span class="sxs-lookup"><span data-stu-id="2785e-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="2785e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2785e-124">See Also</span></span>

[<span data-ttu-id="2785e-125">Tworzenie widoku listy</span><span class="sxs-lookup"><span data-stu-id="2785e-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2785e-126">Tworzenie widoku tabeli</span><span class="sxs-lookup"><span data-stu-id="2785e-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2785e-127">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="2785e-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2785e-128">Tworzenie niestandardowych formantów</span><span class="sxs-lookup"><span data-stu-id="2785e-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="2785e-129">Element ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2785e-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="2785e-130">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="2785e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
