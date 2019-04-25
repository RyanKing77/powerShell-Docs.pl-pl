---
title: Element PropertyName WideItem dla WideControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064649"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="fcb53-102">PropertyName, element — WideItem, WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="fcb53-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="fcb53-103">Określa właściwość obiektu, którego wartość jest wyświetlana w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="fcb53-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="fcb53-104">— Element (Format) elementu ViewDefinitions (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (Format) WideItem — Element (Format) PropertyName Element konfiguracji dla WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="fcb53-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fcb53-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcb53-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fcb53-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fcb53-106">Attributes and Elements</span></span>

<span data-ttu-id="fcb53-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `PropertyName` elementu.</span><span class="sxs-lookup"><span data-stu-id="fcb53-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fcb53-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fcb53-108">Attributes</span></span>

<span data-ttu-id="fcb53-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="fcb53-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fcb53-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fcb53-110">Child Elements</span></span>

<span data-ttu-id="fcb53-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="fcb53-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fcb53-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fcb53-112">Parent Elements</span></span>

|<span data-ttu-id="fcb53-113">Element</span><span class="sxs-lookup"><span data-stu-id="fcb53-113">Element</span></span>|<span data-ttu-id="fcb53-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fcb53-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fcb53-115">Element WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="fcb53-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="fcb53-116">Definiuje właściwości lub skryptu, którego wartość jest wyświetlana w szerokim oknie.</span><span class="sxs-lookup"><span data-stu-id="fcb53-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fcb53-117">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="fcb53-117">Text Value</span></span>

<span data-ttu-id="fcb53-118">Określ nazwę właściwości, którego wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="fcb53-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcb53-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fcb53-119">Remarks</span></span>

<span data-ttu-id="fcb53-120">Aby uzyskać więcej informacji na temat składników szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="fcb53-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fcb53-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="fcb53-121">Example</span></span>

<span data-ttu-id="fcb53-122">Ten przykład przedstawia szerokie, który wyświetla wartość właściwości ProcessName [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu.</span><span class="sxs-lookup"><span data-stu-id="fcb53-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="fcb53-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcb53-123">See Also</span></span>

[<span data-ttu-id="fcb53-124">Element WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="fcb53-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="fcb53-125">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="fcb53-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fcb53-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="fcb53-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
