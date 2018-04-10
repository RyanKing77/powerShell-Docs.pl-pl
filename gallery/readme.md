---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galerii programu powershell, polecenia cmdlet, psgallery, psget
title: Galerii programu PowerShell
ms.openlocfilehash: 9519b8bcca9f43419a33db380c3b852e9bb354ac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="23e2d-103">Galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="23e2d-103">The PowerShell Gallery</span></span>

<span data-ttu-id="23e2d-104">Galerii programu PowerShell jest centralnym repozytorium zawartości programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="23e2d-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="23e2d-105">Nowe polecenia programu PowerShell lub zasobów konfiguracji żądanego stanu (DSC) można znaleźć w galerii.</span><span class="sxs-lookup"><span data-stu-id="23e2d-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="23e2d-106">Omówienie PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="23e2d-106">PowerShellGet Overview</span></span>

<span data-ttu-id="23e2d-107">Moduł PowerShellGet zawiera polecenia cmdlet do wykrywania, instalowania, aktualizowanie i publikowanie programu PowerShell artefaktów, takich jak moduły, zasobów usługi Konfiguracja DSC, możliwości roli i skrypty z [galerii programu PowerShell](https://www.PowerShellGallery.com) i innych prywatnej repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="23e2d-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="23e2d-108">Wprowadzenie do korzystania z galerii</span><span class="sxs-lookup"><span data-stu-id="23e2d-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="23e2d-109">Instalowanie elementów z galerii wymaga najnowszej wersji modułu PowerShellGet, która jest dostępna w systemie Windows 10, w Windows Management Framework (WMF) w wersji 5.0 lub na podstawie pliku MSI Instalatora (PowerShell 3 i 4).</span><span class="sxs-lookup"><span data-stu-id="23e2d-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="23e2d-110">[**Pobierz system Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="23e2d-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="23e2d-111">[**Pobierz WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), lub</span><span class="sxs-lookup"><span data-stu-id="23e2d-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="23e2d-112">**Pobierz instalatora MSI**</span><span class="sxs-lookup"><span data-stu-id="23e2d-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="23e2d-113">Przy użyciu najnowszych [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) modułu, można wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="23e2d-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="23e2d-114">Wyszukiwanie za pomocą elementów galerii z [Znajdź moduł](https://go.microsoft.com/fwlink/?LinkId=821658) i [Znajdź skryptu](https://go.microsoft.com/fwlink/?LinkId=822322)</span><span class="sxs-lookup"><span data-stu-id="23e2d-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="23e2d-115">Zapisuje elementy do systemu z galerii [moduł zapisywania](https://go.microsoft.com/fwlink/?LinkId=821669) i [zapisywania skryptu](https://go.microsoft.com/fwlink/?LinkId=822334)</span><span class="sxs-lookup"><span data-stu-id="23e2d-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="23e2d-116">Instalacji elementów z galerii [instalacji modułu](https://go.microsoft.com/fwlink/?LinkId=821663) i [skrypt instalacji](https://go.microsoft.com/fwlink/?LinkId=822327)</span><span class="sxs-lookup"><span data-stu-id="23e2d-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="23e2d-117">Przekaż elementów galerii z [modułu publikowania](https://go.microsoft.com/fwlink/?LinkId=821666) i [publikowania skryptu](https://go.microsoft.com/fwlink/?LinkId=822331)</span><span class="sxs-lookup"><span data-stu-id="23e2d-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="23e2d-118">Dodawanie niestandardowego repozytorium z [PSRepository rejestru](https://go.microsoft.com/fwlink/?LinkId=821668)</span><span class="sxs-lookup"><span data-stu-id="23e2d-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="23e2d-119">Zapoznaj się z [wprowadzenie](psgallery/psgallery_gettingstarted.md) strony, aby uzyskać więcej informacji na temat korzystania z galerii PowerShellGet poleceń.</span><span class="sxs-lookup"><span data-stu-id="23e2d-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="23e2d-120">Można również uruchomić *Update-Help — moduł PowerShellGet* instalacji lokalnej pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="23e2d-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="23e2d-121">Obsługiwane systemy operacyjne</span><span class="sxs-lookup"><span data-stu-id="23e2d-121">Supported Operating Systems</span></span>

<span data-ttu-id="23e2d-122">**PowerShellGet** module wymaga **programu PowerShell 3.0 lub nowszej**.</span><span class="sxs-lookup"><span data-stu-id="23e2d-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="23e2d-123">W związku z tym **PowerShellGet** wymaga jednego z następujących systemów operacyjnych:</span><span class="sxs-lookup"><span data-stu-id="23e2d-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="23e2d-124">10 systemu Windows</span><span class="sxs-lookup"><span data-stu-id="23e2d-124">Windows 10</span></span>
- <span data-ttu-id="23e2d-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="23e2d-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="23e2d-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="23e2d-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="23e2d-127">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="23e2d-127">Windows 7 SP1</span></span>
- <span data-ttu-id="23e2d-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="23e2d-128">Windows Server 2016</span></span>
- <span data-ttu-id="23e2d-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="23e2d-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="23e2d-130">Windows Server 2008 R2 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="23e2d-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="23e2d-131">**PowerShellGet** również wymaga programu .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="23e2d-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="23e2d-132">Możesz zainstalować program .NET Framework 4.5 lub nowszy z [tutaj](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="23e2d-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="23e2d-133">Masz pytania?</span><span class="sxs-lookup"><span data-stu-id="23e2d-133">Got a question?</span></span> <span data-ttu-id="23e2d-134">Masz opinię?</span><span class="sxs-lookup"><span data-stu-id="23e2d-134">Have feedback?</span></span>

<span data-ttu-id="23e2d-135">Więcej informacji o galerii programu PowerShell i PowerShellGet znajdują się w [wprowadzenie](psgallery/psgallery_gettingstarted.md) strony.</span><span class="sxs-lookup"><span data-stu-id="23e2d-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="23e2d-136">Podaj opinii i raportu problemów przy użyciu [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="23e2d-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>