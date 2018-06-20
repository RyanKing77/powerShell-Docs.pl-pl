---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Hierarchia modeli obiektów środowiska ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950696"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="d0c6d-103">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="d0c6d-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="d0c6d-104">W tym temacie przedstawiono hierarchię obiektów, które należą do programu Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="d0c6d-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="d0c6d-105">Windows PowerShell ISE znajduje się w środowisku Windows PowerShell 3.0 i Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="d0c6d-106">Kliknij obiekt, aby przejść do dokumentacji dla klasy, który definiuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="d0c6d-107">Obiekt $psISE</span><span class="sxs-lookup"><span data-stu-id="d0c6d-107">$psISE Object</span></span>

<span data-ttu-id="d0c6d-108">**$PsISE** obiekt jest [główny obiekt](The-ObjectModelRoot-Object.md) hierarchii obiektów programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="d0c6d-109">Znajduje się na najwyższym poziomie, ułatwia następujące obiekty dostępne dla skryptów:</span><span class="sxs-lookup"><span data-stu-id="d0c6d-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="d0c6d-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="d0c6d-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="d0c6d-111">**$PsISE.CurrentFile** obiektu jest wystąpieniem [ISEFile](The-ISEFile-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="d0c6d-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="d0c6d-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="d0c6d-113">**$PsISE.CurrentPowerShellTab** obiektu jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="d0c6d-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="d0c6d-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="d0c6d-115">**$PsISE.CurrentVisibleHorizontalTool** obiektu jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="d0c6d-116">Reprezentuje narzędzia zainstalowany dodatek, który obecnie jest zadokowany do górnej krawędzi okna programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="d0c6d-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="d0c6d-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="d0c6d-118">**$PsISE.CurrentVisibleHorizontalTool** obiektu jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="d0c6d-119">Reprezentuje narzędzia zainstalowany dodatek, który obecnie jest zadokowany do prawej krawędzi okna programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="d0c6d-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="d0c6d-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="d0c6d-121">**$PsISE.Options** obiektu jest wystąpieniem [ISEOptions](The-ISEOptions-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="d0c6d-122">Obiekt ISEOptions reprezentuje różne ustawienia dla programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="d0c6d-123">To wystąpienie klasy Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="d0c6d-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="d0c6d-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="d0c6d-125">**$PsISE.PowerShellTabs** obiektu jest wystąpieniem [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="d0c6d-126">Jest to zbiór wszystkich aktualnie otwartych PowerShell kart, które reprezentują dostępne środowiska Windows PowerShell Uruchom środowiskach, na komputerze lokalnym lub komputerach zdalnych połączonych.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="d0c6d-127">Każdy element członkowski w kolekcji jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="d0c6d-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0c6d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0c6d-128">See Also</span></span>

- [<span data-ttu-id="d0c6d-129">Cel programu Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="d0c6d-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d0c6d-130">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="d0c6d-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)