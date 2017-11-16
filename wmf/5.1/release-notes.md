---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
title: Informacje o wersji platformy WMF 5.1
ms.openlocfilehash: ce9bc7791facfcc2cce9468689e88a26154bda7d
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="e96f8-103">Informacje o wersji Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="e96f8-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="e96f8-104">WMF 5.1 zawiera składniki programu PowerShell, usługi WMI Usługa WinRM i rejestrowania spisu oprogramowania (SIL), które zostały wydane z systemem Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="e96f8-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="e96f8-105">WMF 5.1 można zainstalować w systemie Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 i 2012 R2 i udostępnia szereg ulepszeń w porównaniu z WMF 5.0 RTM, w tym:</span><span class="sxs-lookup"><span data-stu-id="e96f8-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="e96f8-106">Nowe polecenia cmdlet: lokalnych użytkowników i grup; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="e96f8-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="e96f8-107">PowerShellGet ulepszenia wymuszania podpisem moduły i instalowanie modułów JEA</span><span class="sxs-lookup"><span data-stu-id="e96f8-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="e96f8-108">PackageManagement dodano obsługę kontenerów, Instalator CBS EXE instalacji pliku CAB pakietów</span><span class="sxs-lookup"><span data-stu-id="e96f8-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="e96f8-109">Ulepszenia debugowania dla klas DSC i programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e96f8-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="e96f8-110">W tym wyegzekwowania modułów podpisany katalogu pochodzących z serwera ściągania i przy użyciu poleceń cmdlet PowerShellGet ulepszenia zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e96f8-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="e96f8-111">Odpowiedzi na wiele żądań użytkowników i problemów</span><span class="sxs-lookup"><span data-stu-id="e96f8-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="e96f8-112">**Ważne informacje:**</span><span class="sxs-lookup"><span data-stu-id="e96f8-112">**Important notes:**</span></span>

- <span data-ttu-id="e96f8-113">**WMF 5.1 wymaga programu .NET Framework 4.5.2** (lub nowszej).</span><span class="sxs-lookup"><span data-stu-id="e96f8-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="e96f8-114">Instalacja zostanie wykonana pomyślnie, ale najważniejsze funkcje zakończy się niepowodzeniem, jeśli .NET 4.5.2 (lub nowszej) nie jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="e96f8-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="e96f8-115">Instrukcje są dostępne w [Instalowanie i konfigurowanie 5.1 WMF ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) tematu.</span><span class="sxs-lookup"><span data-stu-id="e96f8-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="e96f8-116">Podgląd 5.1 WMF należy odinstalować przed zainstalowaniem WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="e96f8-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="e96f8-117">WMF 5.1 mogą być zainstalowane bezpośrednio za pośrednictwem WMF 5.0 lub WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="e96f8-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="e96f8-118">Jest __niewymagane__ do zainstalowania WMF 4.0 przed zainstalowaniem programu WMF 5.1 w systemie Windows 7 i Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="e96f8-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="e96f8-119">Czy problem w wersji zapoznawczej 5.1 WMF i został rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="e96f8-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>  


