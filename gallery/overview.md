---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galerii programu powershell, polecenia cmdlet, psgallery, psget
title: Galerii programu PowerShell
ms.openlocfilehash: 65e0c427310ac20621109a6620e926a7894cf8f8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="69eea-103">Galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="69eea-103">The PowerShell Gallery</span></span>

<span data-ttu-id="69eea-104">Galerii programu PowerShell jest centralnym repozytorium zawartości programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69eea-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="69eea-105">W ramach tego można znaleźć przydatne moduły programu PowerShell, zawierająca poleceń programu PowerShell i zasoby konfiguracji żądanego stanu (DSC).</span><span class="sxs-lookup"><span data-stu-id="69eea-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="69eea-106">Można również znaleźć skryptów programu PowerShell, niektóre z nich może zawierać przepływów pracy programu PowerShell, a które przedstawiają zestaw zadań i podaj sekwencji zadań.</span><span class="sxs-lookup"><span data-stu-id="69eea-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="69eea-107">Niektóre z tych elementów są utworzone przez firmę Microsoft, a inne są tworzone przez społeczność programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69eea-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="69eea-108">Omówienie PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="69eea-108">PowerShellGet Overview</span></span>

<span data-ttu-id="69eea-109">Moduł PowerShellGet zawiera polecenia cmdlet do wykrywania, instalowania, aktualizowanie i publikowanie programu PowerShell artefaktów, takich jak moduły, zasobów usługi Konfiguracja DSC, możliwości roli i skrypty z [galerii programu PowerShell](https://www.PowerShellGallery.com) i innych prywatnej repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="69eea-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="69eea-110">Wprowadzenie do korzystania z galerii</span><span class="sxs-lookup"><span data-stu-id="69eea-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="69eea-111">Instalowanie elementów z galerii wymaga najnowszej wersji modułu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="69eea-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="69eea-112">Zobacz [instalowanie PowerShellGet](installing-psget.md) Aby uzyskać pełne instrukcje.</span><span class="sxs-lookup"><span data-stu-id="69eea-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="69eea-113">Zapoznaj się z [wprowadzenie](getting-started.md) strony, aby uzyskać więcej informacji na temat korzystania z galerii PowerShellGet poleceń.</span><span class="sxs-lookup"><span data-stu-id="69eea-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="69eea-114">Można również uruchomić *Update-Help — moduł PowerShellGet* instalacji lokalnej pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="69eea-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="69eea-115">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="69eea-115">Supported Operating Systems</span></span>

<span data-ttu-id="69eea-116">**PowerShellGet** module wymaga **programu PowerShell 3.0 lub nowszej**.</span><span class="sxs-lookup"><span data-stu-id="69eea-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="69eea-117">W związku z tym **PowerShellGet** wymaga jednego z następujących systemów operacyjnych:</span><span class="sxs-lookup"><span data-stu-id="69eea-117">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="69eea-118">10 systemu Windows</span><span class="sxs-lookup"><span data-stu-id="69eea-118">Windows 10</span></span>
- <span data-ttu-id="69eea-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="69eea-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="69eea-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="69eea-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="69eea-121">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="69eea-121">Windows 7 SP1</span></span>
- <span data-ttu-id="69eea-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="69eea-122">Windows Server 2016</span></span>
- <span data-ttu-id="69eea-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="69eea-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="69eea-124">Windows Server 2008 R2 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="69eea-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="69eea-125">**PowerShellGet** również wymaga programu .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="69eea-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="69eea-126">Możesz zainstalować program .NET Framework 4.5 lub nowszy z [tutaj](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="69eea-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="69eea-127">Masz pytania?</span><span class="sxs-lookup"><span data-stu-id="69eea-127">Got a question?</span></span> <span data-ttu-id="69eea-128">Masz opinię?</span><span class="sxs-lookup"><span data-stu-id="69eea-128">Have feedback?</span></span>

<span data-ttu-id="69eea-129">Więcej informacji o galerii programu PowerShell i PowerShellGet znajdują się w [wprowadzenie](getting-started.md) strony.</span><span class="sxs-lookup"><span data-stu-id="69eea-129">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="69eea-130">Podaj opinii i raportu problemów przy użyciu [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="69eea-130">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>