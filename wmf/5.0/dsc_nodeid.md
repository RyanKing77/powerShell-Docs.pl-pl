---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058203"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="831e3-102">Oddzielanie identyfikatorów konfiguracji i węzłów</span><span class="sxs-lookup"><span data-stu-id="831e3-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="831e3-103">Omówienie</span><span class="sxs-lookup"><span data-stu-id="831e3-103">Overview</span></span>

<span data-ttu-id="831e3-104">Aby zapewnić bardziej elastyczne i usprawnione środowisko, gdy usługi DSC w trybie ściągnięcia, dodaliśmy wiele funkcji w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="831e3-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="831e3-105">Funkcje te mają na celu umożliwiają elastyczne łatwe konfigurowanie i wdrażanie konfiguracji w wielu węzłach stan śledzenia i raportowania informacji dla każdego węzła indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="831e3-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="831e3-106">Te funkcje są następujące:</span><span class="sxs-lookup"><span data-stu-id="831e3-106">These features are as follows:</span></span>

* <span data-ttu-id="831e3-107">Nazwa konfiguracji, który identyfikuje konfiguracji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="831e3-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="831e3-108">Ta nazwa może być współużytkowany przez wiele węzłów docelowych</span><span class="sxs-lookup"><span data-stu-id="831e3-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="831e3-109">Identyfikator agenta, które jednoznacznie identyfikuje jeden węzeł</span><span class="sxs-lookup"><span data-stu-id="831e3-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="831e3-110">Krok rejestracji, który występuje tylko po raz pierwszy węzeł docelowy łączy się z serwerem ściągania</span><span class="sxs-lookup"><span data-stu-id="831e3-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="831e3-111">**Uwaga:** Te funkcje i możliwości zostały dodane, a nie zastępują istniejące ściągnięcia funkcje i pojęcia.</span><span class="sxs-lookup"><span data-stu-id="831e3-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="831e3-112">Można użyć tych nowych funkcji lub starsze z nowym serwerem ściągania wysyłania w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="831e3-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="831e3-113">Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="831e3-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
