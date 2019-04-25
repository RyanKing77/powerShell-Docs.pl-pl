---
title: Element DisplayError (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066264"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="14f00-102">DisplayError, element (format)</span><span class="sxs-lookup"><span data-stu-id="14f00-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="14f00-103">Określa, czy ciąg #ERR są wyświetlane, gdy wystąpi błąd wyświetlania elementu danych.</span><span class="sxs-lookup"><span data-stu-id="14f00-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="14f00-104">Element DisplayError DefaultSettings — Element (w formacie) — Element (w formacie) konfiguracji (Format)</span><span class="sxs-lookup"><span data-stu-id="14f00-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="14f00-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="14f00-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="14f00-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="14f00-106">Attributes and Elements</span></span>

<span data-ttu-id="14f00-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `DisplayError` elementu.</span><span class="sxs-lookup"><span data-stu-id="14f00-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="14f00-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="14f00-108">Attributes</span></span>

<span data-ttu-id="14f00-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="14f00-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="14f00-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="14f00-110">Child Elements</span></span>

<span data-ttu-id="14f00-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="14f00-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="14f00-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="14f00-112">Parent Elements</span></span>

|<span data-ttu-id="14f00-113">Element</span><span class="sxs-lookup"><span data-stu-id="14f00-113">Element</span></span>|<span data-ttu-id="14f00-114">Opis</span><span class="sxs-lookup"><span data-stu-id="14f00-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="14f00-115">Element DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="14f00-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="14f00-116">Definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku.</span><span class="sxs-lookup"><span data-stu-id="14f00-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="14f00-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14f00-117">Remarks</span></span>

<span data-ttu-id="14f00-118">Domyślnie gdy wystąpi błąd podczas próby wyświetlenia elementu danych, lokalizacja danych jest puste.</span><span class="sxs-lookup"><span data-stu-id="14f00-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="14f00-119">Gdy ten element jest ustawiony na wartość true, ciąg #ERR będą wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="14f00-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="14f00-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14f00-120">See Also</span></span>

[<span data-ttu-id="14f00-121">Element DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="14f00-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="14f00-122">Pisanie programu PowerShell, formatowanie pliku</span><span class="sxs-lookup"><span data-stu-id="14f00-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
