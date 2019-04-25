---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Informacje o wersji programu WMF 5.1
ms.openlocfilehash: 61ca854cf8f26a9e96c6c5b5c06f6b54d08fb4ea
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055585"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="6c760-103">Windows Management Framework (WMF) 5.1 — informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="6c760-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span>

<span data-ttu-id="6c760-104">Program WMF 5.1 obejmuje składniki programu PowerShell, usługi WMI, usługi WinRM i rejestrowania spisu oprogramowania (SIL), które zostały wydane z systemem Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="6c760-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="6c760-105">Program WMF 5.1 można zainstalować w systemie Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 i 2012 R2. Oferuje on szereg ulepszeń w porównaniu z programem WMF 5.0 RTM, w tym:</span><span class="sxs-lookup"><span data-stu-id="6c760-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="6c760-106">Nowe polecenia cmdlet: lokalni użytkownicy i grupy; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="6c760-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="6c760-107">Ulepszenia rozwiązania PowerShellGet obejmują wymuszanie podpisanych modułów i instalowanie modułów JEA</span><span class="sxs-lookup"><span data-stu-id="6c760-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="6c760-108">Dodano obsługę funkcji PackageManagement na potrzeby kontenerów, instalacji CBS, instalacji opartej na plikach EXE i pakietów CAB</span><span class="sxs-lookup"><span data-stu-id="6c760-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="6c760-109">Ulepszenia debugowania dla klas konfiguracji DSC i programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6c760-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="6c760-110">Ulepszenia zabezpieczeń obejmują wymuszanie modułów podpisanych w wykazie pochodzących z serwera ściągania oraz w przypadku korzystania z poleceń cmdlet PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6c760-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="6c760-111">Odpowiedzi na wiele problemów i żądań użytkowników</span><span class="sxs-lookup"><span data-stu-id="6c760-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="6c760-112">**Ważne uwagi:**</span><span class="sxs-lookup"><span data-stu-id="6c760-112">**Important notes:**</span></span>

- <span data-ttu-id="6c760-113">**Program WMF 5.1 wymaga programu .NET Framework 4.5.2** (lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="6c760-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="6c760-114">Instalacja się powiedzie, ale najważniejsze funkcje zakończy się niepowodzeniem, jeśli .NET 4.5.2 (lub nowszej) nie jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="6c760-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="6c760-115">Instrukcje są dostępne w [Zainstaluj i skonfiguruj program WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) tematu.</span><span class="sxs-lookup"><span data-stu-id="6c760-115">Instructions are available in the [Install and Configure WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="6c760-116">WMF 5.1 w wersji zapoznawczej, należy odinstalować przed zainstalowaniem programu WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="6c760-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="6c760-117">Program WMF 5.1 można zainstalować bezpośrednio przez program WMF 5.0 lub WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="6c760-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="6c760-118">Jest __niewymagane__ instalacji programu WMF 4.0 przed zainstalowaniem programu WMF 5.1 na Windows 7 i Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="6c760-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="6c760-119">Który problem w wersji programu WMF 5.1 w wersji zapoznawczej i zostanie rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="6c760-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>
