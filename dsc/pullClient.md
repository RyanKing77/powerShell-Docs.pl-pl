---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie klienta ściągania usługi Konfiguracja DSC
ms.openlocfilehash: e6d73187566db2756ae24dabe0a825fffb5ecce0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="769ef-103">Konfigurowanie klienta ściągania usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="769ef-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="769ef-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="769ef-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="769ef-105">Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL lub pliku w lokalizacji, gdzie można skontaktować się z serwerem ściągania można pobrać konfiguracji i zasobów, a ma wysyłać dane raportu.</span><span class="sxs-lookup"><span data-stu-id="769ef-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="769ef-106">W poniższych tematach opisano sposób skonfigurować klientów ściągania:</span><span class="sxs-lookup"><span data-stu-id="769ef-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="769ef-107">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji</span><span class="sxs-lookup"><span data-stu-id="769ef-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="769ef-108">Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="769ef-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="769ef-109">**Uwaga**: te tematy dotyczą PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="769ef-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="769ef-110">Aby skonfigurować klienta ściągania w programie PowerShell 4.0, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="769ef-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>