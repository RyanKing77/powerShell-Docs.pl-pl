---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a6366e18b4b6478bfab89475bc6975e6491da9f7
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482866"
---
# <a name="windows-management-framework-wmf-50-rtm-release-notes-overview"></a><span data-ttu-id="26f07-102">Zarządzania Windows Framework (WMF) wersja 5.0 RTM notatki — omówienie</span><span class="sxs-lookup"><span data-stu-id="26f07-102">Windows Management Framework (WMF) 5.0 RTM Release Notes Overview</span></span>

<span data-ttu-id="26f07-103">**WMF 5.0 jest superceeded przez WMF 5.1. Użytkownicy z WMF 5.0 należy uaktualnić do wersji 5.1 WMF uzyskanie pomocy technicznej. Wykonaj [intructions instalacji programu WMF 5.1](../5.1/install-configure.md)**</span><span class="sxs-lookup"><span data-stu-id="26f07-103">**WMF 5.0 is superceeded by WMF 5.1. Users with WMF 5.0 must upgrade to WMF 5.1 to receive support. Please follow the [installation intructions of WMF 5.1](../5.1/install-configure.md)**</span></span>

<span data-ttu-id="26f07-104">Windows Management Framework (WMF) 5.0 RTM udostępnia funkcje, które zostały zaktualizowane z WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="26f07-104">Windows Management Framework (WMF) 5.0 RTM brings functionality that has been updated from WMF 4.0.</span></span> <span data-ttu-id="26f07-105">WMF 5.0 RTM jest można zainstalować tylko na **systemu Windows Server 2012 R2**, **systemu Windows Server 2012**, **systemu Windows Server 2008 R2**, **Windows 8.1**, i **systemu Windows 7 z dodatkiem SP1** i zawiera zaktualizowane wersje lub wprowadzenie następujących funkcji:</span><span class="sxs-lookup"><span data-stu-id="26f07-105">WMF 5.0 RTM is available for installation only on **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, and **Windows 7 SP1** and contains updated versions or introduction of the following features:</span></span>

- <span data-ttu-id="26f07-106">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="26f07-106">Windows PowerShell</span></span>
- <span data-ttu-id="26f07-107">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="26f07-107">Just Enough Administration (JEA)</span></span>
- <span data-ttu-id="26f07-108">Konfiguracja żądanego stanu programu Windows PowerShell (DSC)</span><span class="sxs-lookup"><span data-stu-id="26f07-108">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="26f07-109">Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="26f07-109">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>
- <span data-ttu-id="26f07-110">Usługi sieci Web programu PowerShell systemu Windows (rozszerzenie OData IIS zarządzania)</span><span class="sxs-lookup"><span data-stu-id="26f07-110">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="26f07-111">Zdalne zarządzanie systemem Windows (WinRM)</span><span class="sxs-lookup"><span data-stu-id="26f07-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="26f07-112">Instrumentacja zarządzania Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="26f07-112">Windows Management Instrumentation (WMI)</span></span>

<span data-ttu-id="26f07-113">Zastępuje WMF 5.0 RTM [WMF 5.0 produkcji Podgląd](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span><span class="sxs-lookup"><span data-stu-id="26f07-113">WMF 5.0 RTM replaces the [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span></span> <span data-ttu-id="26f07-114">WMF 5.0 RTM, można zainstalować bez odinstalowania WMF 5.0 produkcji Podgląd, ale inne starsze wersje wersji zapoznawczych platformy WMF 5.0 należy odinstalować przed zainstalowaniem programu WMF 5.0 RTM.</span><span class="sxs-lookup"><span data-stu-id="26f07-114">You can install WMF 5.0 RTM without uninstalling WMF 5.0 Production Preview, but you must uninstall all other older releases of WMF 5.0 previews before installing the WMF 5.0 RTM.</span></span>

<span data-ttu-id="26f07-115">*Uwaga:* korzystający z systemu Windows 10 można uzyskać ten sam zestaw funkcji dostępnych w WMF 5.0 RTM, aktualizując do listopada aktualizacji systemu Windows 10 (wersja 1511).</span><span class="sxs-lookup"><span data-stu-id="26f07-115">*Note:* If you are running Windows 10, you can get the same set of functionality available in WMF 5.0 RTM by updating to the November update of Windows 10 (Version 1511).</span></span> <span data-ttu-id="26f07-116">Jeśli system Windows 10 nie jest już zaktualizowany, wybierz przycisk Start, a następnie wybierz Ustawienia > Aktualizacja i Zabezpieczenia > usługi Windows Update > sprawdzić aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="26f07-116">If you have not already updated your Windows 10 system, select the Start button, then select Settings > Update & security > Windows Update > Check for updates.</span></span>
