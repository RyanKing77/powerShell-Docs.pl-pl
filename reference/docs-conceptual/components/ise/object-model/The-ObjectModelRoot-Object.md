---
ms.date: 08/25/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405586"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="14057-103">Obiekt ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="14057-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="14057-104">**$PsISE** obiektu, który jest obiektem głównym jednostki w Windows PowerShell® zintegrowane Scripting Environment (ISE) jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="14057-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="14057-105">W tym temacie opisano właściwości obiektu **ObjectModelRoot** obiektu.</span><span class="sxs-lookup"><span data-stu-id="14057-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="14057-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="14057-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="14057-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="14057-107">CurrentFile</span></span>

> <span data-ttu-id="14057-108">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="14057-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="14057-109">Właściwość tylko do odczytu, która umożliwia pobieranie pliku, który jest skojarzony z tym obiektem hosta, który aktualnie ma fokus.</span><span class="sxs-lookup"><span data-stu-id="14057-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="14057-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="14057-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="14057-111">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="14057-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="14057-112">Właściwość tylko do odczytu, która kartę programu PowerShell, który ma fokus.</span><span class="sxs-lookup"><span data-stu-id="14057-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="14057-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="14057-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="14057-114">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="14057-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="14057-115">Właściwość tylko do odczytu, która pobiera aktualnie widoczne narzędzia Windows PowerShell ISE w dodatku, który znajduje się w okienku narzędzie poziomy w dolnej części edytora.</span><span class="sxs-lookup"><span data-stu-id="14057-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="14057-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="14057-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="14057-117">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="14057-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="14057-118">Właściwość tylko do odczytu, która pobiera aktualnie widoczne narzędzia Windows PowerShell ISE w dodatku, który znajduje się w okienku pionowy narzędzi po prawej stronie edytora.</span><span class="sxs-lookup"><span data-stu-id="14057-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="14057-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="14057-119">Options</span></span>

> <span data-ttu-id="14057-120">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="14057-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="14057-121">Właściwość tylko do odczytu, która pobiera różne opcje, które można zmienić ustawienia w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="14057-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="14057-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="14057-122">PowerShellTabs</span></span>

> <span data-ttu-id="14057-123">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="14057-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="14057-124">Właściwość tylko do odczytu, która kolekcji kart programu PowerShell, które są otwarte w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="14057-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="14057-125">Domyślnie ten obiekt zawiera jedną kartę programu PowerShell. Można jednak dodać więcej kart programu PowerShell do tego obiektu, za pomocą skryptów lub przy użyciu menu w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="14057-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="14057-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14057-126">See Also</span></span>

- [<span data-ttu-id="14057-127">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="14057-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="14057-128">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="14057-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)