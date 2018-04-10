---
ms.date: 08/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Informacje o wersji programu WMF 5.1
ms.openlocfilehash: 9df21afe52e79dc248871b999afead21f8678d52
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="9b7fd-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="9b7fd-103">Windows Management Framework (WMF) 5.1</span></span> #

<span data-ttu-id="9b7fd-104">Program WMF umożliwia użytkownikom aktualizowanie istniejących systemów Windows do wersji składników programu PowerShell, usługi WMI, usługi WinRM i funkcji Rejestrowanie spisu oprogramowania (SIL, Software Inventory Logging), które zostały wydane z systemem Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="9b7fd-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="9b7fd-105">Program WMF 5.1 można zainstalować w systemie Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 i 2012 R2. Oferuje on szereg ulepszeń w porównaniu z programem WMF 5.0 RTM, w tym:</span><span class="sxs-lookup"><span data-stu-id="9b7fd-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="9b7fd-106">Nowe polecenia cmdlet: lokalni użytkownicy i grupy; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="9b7fd-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="9b7fd-107">Ulepszenia rozwiązania PowerShellGet obejmują wymuszanie podpisanych modułów i instalowanie modułów JEA</span><span class="sxs-lookup"><span data-stu-id="9b7fd-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="9b7fd-108">Dodano obsługę funkcji PackageManagement na potrzeby kontenerów, instalacji CBS, instalacji opartej na plikach EXE i pakietów CAB</span><span class="sxs-lookup"><span data-stu-id="9b7fd-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="9b7fd-109">Ulepszenia debugowania dla klas konfiguracji DSC i programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b7fd-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="9b7fd-110">Ulepszenia zabezpieczeń obejmują wymuszanie modułów podpisanych w wykazie pochodzących z serwera ściągania oraz w przypadku korzystania z poleceń cmdlet PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="9b7fd-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="9b7fd-111">Odpowiedzi na wiele problemów i żądań użytkowników</span><span class="sxs-lookup"><span data-stu-id="9b7fd-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="9b7fd-112">Aby dowiedzieć się więcej na temat nowości w tej wersji, przejrzyj tematy w artykule dotyczącym [nowych scenariuszy i funkcji](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span><span class="sxs-lookup"><span data-stu-id="9b7fd-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="9b7fd-113">W temacie dotyczącym [instalowania i konfigurowania](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) podano listę wymagań i instrukcje dotyczące instalacji programu WMF.</span><span class="sxs-lookup"><span data-stu-id="9b7fd-113">The [Install and Configure](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="9b7fd-114">W temacie dotyczącym [zgodności](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) znajduje się lista wersji programu WMF, które można zainstalować w poszczególnych wydaniach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9b7fd-114">The [Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="9b7fd-115">W temacie dotyczącym [zgodności produktów](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) znajduje się lista aplikacji firmy Microsoft, które do tego momentu nie zostały zatwierdzone do użycia z programem WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="9b7fd-115">[Product Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="9b7fd-116">Szczegóły dotyczące składników WMF można znaleźć w dokumentacji MSDN:</span><span class="sxs-lookup"><span data-stu-id="9b7fd-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="9b7fd-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="9b7fd-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/en-us/powershell/)
- <span data-ttu-id="9b7fd-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="9b7fd-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="9b7fd-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="9b7fd-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="9b7fd-120">[Rejestrowanie spisu oprogramowania](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="9b7fd-120">[Software Inventory Logging](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span></span>