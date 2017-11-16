---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="3b4ae-102">Rozdzielenie węzłów i identyfikatorów konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3b4ae-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="3b4ae-103">Przegląd</span><span class="sxs-lookup"><span data-stu-id="3b4ae-103">Overview</span></span>

<span data-ttu-id="3b4ae-104">Aby zapewnić bardziej elastyczne i prostsze środowisko, korzystając z usługi Konfiguracja DSC w trybie ściągania, dodano wiele funkcji w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="3b4ae-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="3b4ae-105">Te funkcje są przeznaczone do może być elastyczność w prosty sposób instalacji i wdrażanie konfiguracji na wielu węzłach śledzenie stanu i indywidualnie raportowania informacji dla każdego węzła.</span><span class="sxs-lookup"><span data-stu-id="3b4ae-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span> <span data-ttu-id="3b4ae-106">Te funkcje są następujące:</span><span class="sxs-lookup"><span data-stu-id="3b4ae-106">These features are as follows:</span></span>

* <span data-ttu-id="3b4ae-107">Nazwa konfiguracji, który identyfikuje konfiguracji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3b4ae-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="3b4ae-108">Ta nazwa może być współużytkowane przez wiele węzłów docelowych</span><span class="sxs-lookup"><span data-stu-id="3b4ae-108">This name can be shared by multiple target nodes</span></span> 
* <span data-ttu-id="3b4ae-109">Identyfikator agenta, które jednoznacznie identyfikuje jeden węzeł</span><span class="sxs-lookup"><span data-stu-id="3b4ae-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="3b4ae-110">Krok rejestracji, który występuje tylko po raz pierwszy węzeł docelowy łączy się z serwerem ściągania</span><span class="sxs-lookup"><span data-stu-id="3b4ae-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="3b4ae-111">**Uwaga:** te funkcje i możliwości zostały dodane, a nie zastępują istniejące funkcje ściągania i pojęcia.</span><span class="sxs-lookup"><span data-stu-id="3b4ae-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="3b4ae-112">Możesz użyć tych nowych funkcji lub starsze z nowym serwerem ściągania wysyłania w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="3b4ae-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="3b4ae-113">Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania przy użyciu nazwy konfiguracji](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="3b4ae-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>

