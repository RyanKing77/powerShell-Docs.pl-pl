---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galerii programu powershell, polecenia cmdlet, psgallery, psget
title: Galerii programu PowerShell
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482934"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="3e416-103">Galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e416-103">The PowerShell Gallery</span></span>

<span data-ttu-id="3e416-104">Galerii programu PowerShell jest centralnym repozytorium zawartości programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e416-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="3e416-105">W ramach tego można znaleźć przydatne moduły programu PowerShell, zawierająca poleceń programu PowerShell i zasoby konfiguracji żądanego stanu (DSC).</span><span class="sxs-lookup"><span data-stu-id="3e416-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="3e416-106">Można również znaleźć skryptów programu PowerShell, niektóre z nich może zawierać przepływów pracy programu PowerShell, a które przedstawiają zestaw zadań i podaj sekwencji zadań.</span><span class="sxs-lookup"><span data-stu-id="3e416-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="3e416-107">Niektóre z tych elementów są utworzone przez firmę Microsoft, a inne są tworzone przez społeczność programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e416-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="3e416-108">Omówienie PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="3e416-108">PowerShellGet Overview</span></span>

<span data-ttu-id="3e416-109">Moduł PowerShellGet zawiera polecenia cmdlet do wykrywania, instalowania, aktualizowanie i publikowanie programu PowerShell artefaktów, takich jak moduły, zasobów usługi Konfiguracja DSC, możliwości roli i skrypty z [galerii programu PowerShell](https://www.PowerShellGallery.com) i innych prywatnej repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="3e416-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="3e416-110">Wprowadzenie do korzystania z galerii</span><span class="sxs-lookup"><span data-stu-id="3e416-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="3e416-111">Instalowanie elementów z galerii wymaga najnowszej wersji modułu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="3e416-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="3e416-112">Zobacz [instalowanie PowerShellGet](installing-psget.md) Aby uzyskać pełne instrukcje.</span><span class="sxs-lookup"><span data-stu-id="3e416-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="3e416-113">Zapoznaj się z [wprowadzenie](getting-started.md) strony, aby uzyskać więcej informacji na temat korzystania z galerii PowerShellGet poleceń.</span><span class="sxs-lookup"><span data-stu-id="3e416-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="3e416-114">Można również uruchomić *Update-Help — moduł PowerShellGet* instalacji lokalnej pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e416-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="3e416-115">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="3e416-115">Supported Operating Systems</span></span>

<span data-ttu-id="3e416-116">**PowerShellGet** module wymaga **programu Windows PowerShell 3.0 lub nowszej**, lub **Core PowerShell 6.0 lub nowszej**.</span><span class="sxs-lookup"><span data-stu-id="3e416-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="3e416-117">Odpowiedniej wersji **programu Windows PowerShell** jest dostępna dla tych systemów operacyjnych:</span><span class="sxs-lookup"><span data-stu-id="3e416-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="3e416-118">10 systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3e416-118">Windows 10</span></span>
- <span data-ttu-id="3e416-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="3e416-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="3e416-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="3e416-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="3e416-121">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="3e416-121">Windows 7 SP1</span></span>
- <span data-ttu-id="3e416-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3e416-122">Windows Server 2016</span></span>
- <span data-ttu-id="3e416-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3e416-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="3e416-124">Windows Server 2008 R2 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="3e416-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="3e416-125">**PowerShellGet** również wymaga programu .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="3e416-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="3e416-126">Możesz zainstalować program .NET Framework 4.5 lub nowszy z [tutaj](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="3e416-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="3e416-127">**Podstawowe programu PowerShell** obsługuje wiele systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="3e416-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="3e416-128">Zobacz [w tym artykule](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) pełną listę.</span><span class="sxs-lookup"><span data-stu-id="3e416-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="3e416-129">Wiele modułów hostowanej w galerii obsługi różnych systemów operacyjnych i mieć dodatkowe wymagania.</span><span class="sxs-lookup"><span data-stu-id="3e416-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="3e416-130">Zapoznaj się z dokumentacją dla modułów, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="3e416-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="3e416-131">Masz pytania?</span><span class="sxs-lookup"><span data-stu-id="3e416-131">Got a question?</span></span> <span data-ttu-id="3e416-132">Masz opinię?</span><span class="sxs-lookup"><span data-stu-id="3e416-132">Have feedback?</span></span>

<span data-ttu-id="3e416-133">Więcej informacji o galerii programu PowerShell i PowerShellGet znajdują się w [wprowadzenie](getting-started.md) strony.</span><span class="sxs-lookup"><span data-stu-id="3e416-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="3e416-134">Podaj opinii i raportu problemów przy użyciu [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="3e416-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
