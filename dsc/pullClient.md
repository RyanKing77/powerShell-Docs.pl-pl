---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Konfigurowanie klienta ściągania usługi Konfiguracja DSC"
ms.openlocfilehash: d2d1bab7ba2b482b2a66ce59b5f80ea32c242c47
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="edc8d-103">Konfigurowanie klienta ściągania usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="edc8d-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="edc8d-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="edc8d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="edc8d-105">Każdy węzeł docelowy musi być informację do używania trybu ściągania i podany adres URL lub pliku w lokalizacji, gdzie można skontaktować się z serwerem ściągania można pobrać konfiguracji i zasobów, a ma wysyłać dane raportu.</span><span class="sxs-lookup"><span data-stu-id="edc8d-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="edc8d-106">W poniższych tematach opisano sposób skonfigurować klientów ściągania:</span><span class="sxs-lookup"><span data-stu-id="edc8d-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="edc8d-107">Konfigurowanie klienta ściągania przy użyciu nazwy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="edc8d-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="edc8d-108">Konfigurowanie klienta ściągania przy użyciu identyfikator konfiguracji</span><span class="sxs-lookup"><span data-stu-id="edc8d-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="edc8d-109">**Uwaga**: te tematy dotyczą PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="edc8d-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="edc8d-110">Aby skonfigurować klienta ściągania w programie PowerShell 4.0, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji w programie PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="edc8d-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

