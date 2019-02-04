---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria programu powershell, polecenie cmdlet, galerii programu PowerShell, psget
title: Galeria programu PowerShell
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685459"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="5fed7-103">Galeria programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fed7-103">The PowerShell Gallery</span></span>

<span data-ttu-id="5fed7-104">Galeria programu PowerShell jest centralnym repozytorium zawartość programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fed7-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="5fed7-105">Znajdziesz przydatne modułów programu PowerShell zawierający poleceń programu PowerShell i zasoby Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="5fed7-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="5fed7-106">Można również znaleźć skryptów programu PowerShell, niektóre z nich może zawierać przepływów pracy programu PowerShell i które opisują zestaw zadań i podać sekwencji zadań.</span><span class="sxs-lookup"><span data-stu-id="5fed7-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="5fed7-107">Niektóre z tych pakietów są tworzone przez firmę Microsoft, a inne są tworzone przez społeczność użytkowników programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fed7-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="5fed7-108">Omówienie modułu PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="5fed7-108">PowerShellGet Overview</span></span>

<span data-ttu-id="5fed7-109">Moduł PowerShellGet zawiera polecenia cmdlet na potrzeby odnajdywania, instalowania, aktualizowania i publikowania pakietów programu PowerShell, które zawierają artefaktów, takich jak moduły, zasoby DSC, możliwości roli i skryptów [galerii programu PowerShell](https://www.PowerShellGallery.com)i innych repozytoriów prywatnych.</span><span class="sxs-lookup"><span data-stu-id="5fed7-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="5fed7-110">Wprowadzenie do galerii</span><span class="sxs-lookup"><span data-stu-id="5fed7-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="5fed7-111">Instalowanie pakietów z galerii wymaga najnowszej wersji modułu PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="5fed7-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="5fed7-112">Zobacz [instalacji PowerShellGet](installing-psget.md) pełne instrukcje.</span><span class="sxs-lookup"><span data-stu-id="5fed7-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="5fed7-113">Zapoznaj się z [wprowadzenie](getting-started.md) strony, aby uzyskać więcej informacji na temat korzystania z poleceń modułu PowerShellGet z galerią.</span><span class="sxs-lookup"><span data-stu-id="5fed7-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="5fed7-114">Można również uruchomić *Update-Help-Module PowerShellGet* zainstalować lokalną pomoc dotyczącą tych poleceń.</span><span class="sxs-lookup"><span data-stu-id="5fed7-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="5fed7-115">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="5fed7-115">Supported Operating Systems</span></span>

<span data-ttu-id="5fed7-116">**PowerShellGet** moduł wymaga **programu Windows PowerShell w wersji 3.0 lub nowszej**, lub **programu PowerShell Core 6.0 lub nowszej**.</span><span class="sxs-lookup"><span data-stu-id="5fed7-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="5fed7-117">Odpowiedniej wersji **programu Windows PowerShell** jest dostępny dla tych systemów operacyjnych:</span><span class="sxs-lookup"><span data-stu-id="5fed7-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="5fed7-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="5fed7-118">Windows 10</span></span>
- <span data-ttu-id="5fed7-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="5fed7-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="5fed7-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="5fed7-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="5fed7-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="5fed7-121">Windows 7 SP1</span></span>
- <span data-ttu-id="5fed7-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="5fed7-122">Windows Server 2019</span></span>
- <span data-ttu-id="5fed7-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="5fed7-123">Windows Server 2016</span></span>
- <span data-ttu-id="5fed7-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5fed7-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="5fed7-125">Windows Server 2008 R2 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="5fed7-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="5fed7-126">**Moduł PowerShellGet** wymaga programu .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="5fed7-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="5fed7-127">Możesz zainstalować program .NET Framework 4.5 lub nowszy z [tutaj](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="5fed7-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="5fed7-128">Ponieważ **programu PowerShell Core** jest dla wielu platform i że oznacza, że działa ona na Windows, Linux i MacOS, który sprawia, że **PowerShellGet** dostępnych w tych systemach.</span><span class="sxs-lookup"><span data-stu-id="5fed7-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="5fed7-129">Aby uzyskać pełną listę obsługiwanych przez systemy **programu PowerShell Core** zobacz [Instalowanie programu PowerShell](/powershell/scripting/setup/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="5fed7-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="5fed7-130">Wiele modułów hostowanych w galerii będzie obsługiwać różnych systemów operacyjnych i mają dodatkowe wymagania.</span><span class="sxs-lookup"><span data-stu-id="5fed7-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="5fed7-131">Zapoznaj się z dokumentacją dla modułów, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="5fed7-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="5fed7-132">Masz pytanie?</span><span class="sxs-lookup"><span data-stu-id="5fed7-132">Got a question?</span></span> <span data-ttu-id="5fed7-133">Chcesz przesłać opinię?</span><span class="sxs-lookup"><span data-stu-id="5fed7-133">Have feedback?</span></span>

<span data-ttu-id="5fed7-134">Więcej informacji o galerii programu PowerShell i moduł PowerShellGet można znaleźć w [wprowadzenie](getting-started.md) strony.</span><span class="sxs-lookup"><span data-stu-id="5fed7-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="5fed7-135">Podaj opinię i raport problemów za pomocą [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="5fed7-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
