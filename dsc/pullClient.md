---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie klienta ściągania usługi Konfiguracja DSC
ms.openlocfilehash: 7f8758bd7145518e30e9c28b74d0db5d74dfaab3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186664"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="22624-103">Konfigurowanie klienta ściągania usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="22624-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="22624-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="22624-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22624-105">Ściągnięcia serwera (funkcja Windows *DSC usługi*) jest obsługiwanych składników systemu Windows Server jednak nie ma żadnych planów oferować nowe funkcje lub możliwości.</span><span class="sxs-lookup"><span data-stu-id="22624-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="22624-106">Zaleca się rozpocząć przechodzenie zarządzanych klientów do [Konfiguracja DSC automatyzacji Azure](/azure/automation/automation-dsc-getting-started) (w tym funkcji poza ściągnięcia serwera w systemie Windows Server) lub jednego z rozwiązań społeczności wymienionych [tutaj](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="22624-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="22624-107">Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL lub pliku w lokalizacji, gdzie można skontaktować się z serwerem ściągania można pobrać konfiguracji i zasobów, a ma wysyłać dane raportu.</span><span class="sxs-lookup"><span data-stu-id="22624-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="22624-108">W poniższych tematach opisano sposób skonfigurować klientów ściągania:</span><span class="sxs-lookup"><span data-stu-id="22624-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="22624-109">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="22624-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="22624-110">Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="22624-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="22624-111">**Uwaga**: te tematy dotyczą PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="22624-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="22624-112">Aby skonfigurować klienta ściągania w programie PowerShell 4.0, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="22624-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>