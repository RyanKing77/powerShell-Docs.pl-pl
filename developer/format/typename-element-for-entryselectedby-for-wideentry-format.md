---
title: Element TypeName dla EntrySelectedBy dla WideEntry (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083930"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="7d9a7-102">TypeName, element — EntrySelectedBy, WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="7d9a7-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="7d9a7-103">Określa typ architektury .NET w definicji.</span><span class="sxs-lookup"><span data-stu-id="7d9a7-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="7d9a7-104">Definicja jest używana zawsze, gdy zostanie wyświetlony ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="7d9a7-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="7d9a7-105">— Element (Format) ViewDefinitions — Element (Format) widoku elementu (w formacie) WideControl — Element (Format) WideEntries — Element (Format) WideEntry — Element (w formacie) EntrySelectedBy Element konfiguracji elementu TypeName WideEntry (Format) WideEntry ( Format)</span><span class="sxs-lookup"><span data-stu-id="7d9a7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d9a7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d9a7-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d9a7-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d9a7-107">Attributes and Elements</span></span>

<span data-ttu-id="7d9a7-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `TypeName` elementu.</span><span class="sxs-lookup"><span data-stu-id="7d9a7-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d9a7-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d9a7-109">Attributes</span></span>

<span data-ttu-id="7d9a7-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d9a7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d9a7-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d9a7-111">Child Elements</span></span>

<span data-ttu-id="7d9a7-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d9a7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7d9a7-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d9a7-113">Parent Elements</span></span>

|<span data-ttu-id="7d9a7-114">Element</span><span class="sxs-lookup"><span data-stu-id="7d9a7-114">Element</span></span>|<span data-ttu-id="7d9a7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7d9a7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d9a7-116">Element EntrySelectedBy WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7d9a7-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="7d9a7-117">Definiuje typy .NET, korzystające z tego wpisu szeroki lub warunek, który musi istnieć dla tego wpisu do użycia.</span><span class="sxs-lookup"><span data-stu-id="7d9a7-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7d9a7-118">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="7d9a7-118">Text Value</span></span>

<span data-ttu-id="7d9a7-119">Określ w pełni kwalifikowaną nazwę typu .NET, taki jak `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="7d9a7-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7d9a7-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d9a7-120">Remarks</span></span>

<span data-ttu-id="7d9a7-121">Każdy wpis szeroki należy określić co najmniej jednego typu .NET, zestaw zaznaczenia lub warunek wyboru, który musi istnieć dla definicji, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="7d9a7-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="7d9a7-122">Aby uzyskać więcej informacji o innych składnikach szerokie, zobacz [tworzenia szerokiej widoku](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7d9a7-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d9a7-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d9a7-123">See Also</span></span>

[<span data-ttu-id="7d9a7-124">Tworzenie szerokiej widoku</span><span class="sxs-lookup"><span data-stu-id="7d9a7-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7d9a7-125">Element EntrySelectedBy WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7d9a7-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="7d9a7-126">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="7d9a7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
