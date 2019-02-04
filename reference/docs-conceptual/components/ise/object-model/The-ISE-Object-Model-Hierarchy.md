---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Hierarchia modeli obiektów środowiska ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683772"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="9798b-103">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="9798b-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="9798b-104">W tym temacie przedstawiono hierarchię obiektów, które są dostępne w ramach programu Windows PowerShell zintegrowane Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="9798b-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="9798b-105">Windows PowerShell ISE i jest dołączone w środowisku Windows PowerShell 3.0 w programie Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="9798b-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="9798b-106">Kliknij obiekt, aby przejść do dokumentacji dla klasy, która definiuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="9798b-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="9798b-107">$psISE Object</span><span class="sxs-lookup"><span data-stu-id="9798b-107">$psISE Object</span></span>

<span data-ttu-id="9798b-108">**$PsISE** obiekt jest [główny obiekt](The-ObjectModelRoot-Object.md) hierarchii obiektów programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9798b-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="9798b-109">Znajduje się na najwyższym poziomie, zapewnia następujące obiekty dostępne dla skryptów:</span><span class="sxs-lookup"><span data-stu-id="9798b-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="9798b-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="9798b-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="9798b-111">**$PsISE.CurrentFile** obiekt jest wystąpieniem [ISEFile](The-ISEFile-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9798b-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="9798b-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="9798b-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="9798b-113">**$PsISE.CurrentPowerShellTab** obiekt jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9798b-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="9798b-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="9798b-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="9798b-115">**$PsISE.CurrentVisibleHorizontalTool** obiekt jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9798b-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="9798b-116">Reprezentuje narzędzie zainstalowany dodatek, który aktualnie jest zadokowany do górnej krawędzi okna środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9798b-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="9798b-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="9798b-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="9798b-118">**$PsISE.CurrentVisibleHorizontalTool** obiekt jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9798b-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="9798b-119">Reprezentuje narzędzie zainstalowany dodatek, który aktualnie jest zadokowany na prawej krawędzi okna środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9798b-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="9798b-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="9798b-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="9798b-121">**$PsISE.Options** obiekt jest wystąpieniem [ISEOptions](The-ISEOptions-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9798b-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="9798b-122">Obiekt ISEOptions reprezentuje różne ustawienia dla środowiska Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9798b-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="9798b-123">Jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="9798b-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="9798b-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="9798b-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="9798b-125">**$PsISE.PowerShellTabs** obiekt jest wystąpieniem [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9798b-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="9798b-126">Jest to kolekcja wszystkie aktualnie otwarte PowerShell karty, które reprezentują dostępne programu Windows PowerShell środowiska są uruchomione na komputerze lokalnym lub połączonych komputerów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="9798b-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="9798b-127">Każdy element członkowski w kolekcji jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9798b-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9798b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9798b-128">See Also</span></span>

- [<span data-ttu-id="9798b-129">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9798b-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9798b-130">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="9798b-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)