---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie klienta ściągania platformy DSC
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079646"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="f22c0-103">Konfigurowanie klienta ściągania platformy DSC</span><span class="sxs-lookup"><span data-stu-id="f22c0-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="f22c0-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f22c0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f22c0-105">Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno.</span><span class="sxs-lookup"><span data-stu-id="f22c0-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="f22c0-106">Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="f22c0-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="f22c0-107">Każdy węzeł docelowy musi być informację do używania trybu ściągania i podanej lokalizacji adresu URL lub pliku, gdzie można skontaktować się z serwera ściągania konfiguracji i zasobów, a jego powinien wysyłać dane raportu.</span><span class="sxs-lookup"><span data-stu-id="f22c0-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="f22c0-108">W poniższych tematach opisano sposób konfigurowania klientów ściągnięcia:</span><span class="sxs-lookup"><span data-stu-id="f22c0-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="f22c0-109">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f22c0-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="f22c0-110">Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f22c0-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="f22c0-111">Następujące tematy dotyczą PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="f22c0-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="f22c0-112">Aby skonfigurować klienta ściągania w programie PowerShell 4.0, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="f22c0-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>