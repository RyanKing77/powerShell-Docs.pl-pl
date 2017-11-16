---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Hierarchia modelu obiektów ISE"
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="9d8b2-103">Hierarchia modelu obiektów ISE</span><span class="sxs-lookup"><span data-stu-id="9d8b2-103">The ISE Object Model Hierarchy</span></span>
<span data-ttu-id="9d8b2-104">W tym temacie przedstawiono hierarchię obiektów, które należą do programu Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="9d8b2-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="9d8b2-105">Windows PowerShell ISE znajduje się w środowisku Windows PowerShell 3.0 i Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="9d8b2-106">Kliknij obiekt, aby przejść do dokumentacji dla klasy, który definiuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="9d8b2-107">Obiekt $psISE</span><span class="sxs-lookup"><span data-stu-id="9d8b2-107">$psISE Object</span></span>

<span data-ttu-id="9d8b2-108">**$PsISE** obiekt jest [główny obiekt](The-ObjectModelRoot-Object.md) hierarchii obiektów programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="9d8b2-109">Znajduje się na najwyższym poziomie, ułatwia następujące obiekty dostępne dla skryptów:</span><span class="sxs-lookup"><span data-stu-id="9d8b2-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="9d8b2-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="9d8b2-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="9d8b2-111">**$PsISE.CurrentFile** obiektu jest wystąpieniem [ISEFile](The-ISEFile-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="9d8b2-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="9d8b2-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="9d8b2-113">**$PsISE.CurrentPowerShellTab** obiektu jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="9d8b2-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="9d8b2-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="9d8b2-115">**$PsISE.CurrentVisibleHorizontalTool** obiektu jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="9d8b2-116">Reprezentuje narzędzia zainstalowany dodatek, który obecnie jest zadokowany do górnej krawędzi okna programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="9d8b2-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="9d8b2-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="9d8b2-118">**$PsISE.CurrentVisibleHorizontalTool** obiektu jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="9d8b2-119">Reprezentuje narzędzia zainstalowany dodatek, który obecnie jest zadokowany do prawej krawędzi okna programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="9d8b2-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="9d8b2-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="9d8b2-121">**$PsISE.Options** obiektu jest wystąpieniem [ISEOptions](The-ISEOptions-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="9d8b2-122">Obiekt ISEOptions reprezentuje różne ustawienia dla programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="9d8b2-123">To wystąpienie klasy Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="9d8b2-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="9d8b2-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="9d8b2-125">**$PsISE.PowerShellTabs** obiektu jest wystąpieniem [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="9d8b2-126">Jest to zbiór wszystkich aktualnie otwartych PowerShell kart, które reprezentują dostępne środowiska Windows PowerShell Uruchom środowiskach, na komputerze lokalnym lub komputerach zdalnych połączonych.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="9d8b2-127">Każdy element członkowski w kolekcji jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.</span><span class="sxs-lookup"><span data-stu-id="9d8b2-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d8b2-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d8b2-128">See Also</span></span>
- [<span data-ttu-id="9d8b2-129">Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="9d8b2-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9d8b2-130">Dotyczące modelu obiektów programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9d8b2-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
