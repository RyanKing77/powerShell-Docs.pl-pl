---
title: Element SelectionSetName ViewSelectedBy (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848447"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="9dd36-102">SelectionSetName, element — ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="9dd36-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="9dd36-103">Określa zestaw obiektów platformy .NET, które są wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="9dd36-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="9dd36-104">— Element (Format) ViewDefinitions — Element (w formacie) widoku elementu (w formacie) elementu ViewSelectedBy (Format) SelectionSetName Element konfiguracji dla ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9dd36-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9dd36-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9dd36-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9dd36-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9dd36-106">Attributes and Elements</span></span>

<span data-ttu-id="9dd36-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `SelectionSetName` elementu.</span><span class="sxs-lookup"><span data-stu-id="9dd36-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9dd36-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9dd36-108">Attributes</span></span>

<span data-ttu-id="9dd36-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="9dd36-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9dd36-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9dd36-110">Child Elements</span></span>

<span data-ttu-id="9dd36-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="9dd36-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9dd36-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9dd36-112">Parent Elements</span></span>

|<span data-ttu-id="9dd36-113">Element</span><span class="sxs-lookup"><span data-stu-id="9dd36-113">Element</span></span>|<span data-ttu-id="9dd36-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9dd36-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9dd36-115">Element ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9dd36-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="9dd36-116">Definiuje obiekty .NET, które są wyświetlane w widoku.</span><span class="sxs-lookup"><span data-stu-id="9dd36-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9dd36-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="9dd36-117">Text Value</span></span>

<span data-ttu-id="9dd36-118">Określ nazwę zestawu wyboru, który jest definiowany przez `Name` element do zestawu wyboru.</span><span class="sxs-lookup"><span data-stu-id="9dd36-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9dd36-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9dd36-119">Remarks</span></span>

<span data-ttu-id="9dd36-120">Można użyć zestawów zaznaczenie, gdy masz zestaw powiązanych obiektów, które odwołują się za pomocą jednej nazwy, takiego jak zestaw obiektów, które są powiązane z dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="9dd36-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="9dd36-121">Aby uzyskać więcej informacji o definiowaniu i odwołania do zestawów wyboru, zobacz [Definiowanie ustawia z obiektów](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9dd36-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="9dd36-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="9dd36-122">Example</span></span>

<span data-ttu-id="9dd36-123">Poniższy przykład pokazuje, jak określić zbiór w celu wyświetlenia listy opcji.</span><span class="sxs-lookup"><span data-stu-id="9dd36-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="9dd36-124">Ten sam schemat jest używany dla tabeli, szeroką i niestandardowe widoki.</span><span class="sxs-lookup"><span data-stu-id="9dd36-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="9dd36-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9dd36-125">See Also</span></span>

[<span data-ttu-id="9dd36-126">Definiowanie zestawów zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="9dd36-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9dd36-127">Element ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9dd36-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="9dd36-128">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9dd36-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
