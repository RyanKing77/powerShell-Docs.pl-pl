---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="4cb3a-102">Oddzielanie identyfikatorów konfiguracji i węzłów</span><span class="sxs-lookup"><span data-stu-id="4cb3a-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="4cb3a-103">Przegląd</span><span class="sxs-lookup"><span data-stu-id="4cb3a-103">Overview</span></span>

<span data-ttu-id="4cb3a-104">Aby zapewnić bardziej elastyczne i prostsze środowisko, korzystając z usługi Konfiguracja DSC w trybie ściągania, dodano wiele funkcji w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="4cb3a-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="4cb3a-105">Te funkcje są przeznaczone do może być elastyczność w prosty sposób instalacji i wdrażanie konfiguracji na wielu węzłach śledzenie stanu i indywidualnie raportowania informacji dla każdego węzła.</span><span class="sxs-lookup"><span data-stu-id="4cb3a-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="4cb3a-106">Te funkcje są następujące:</span><span class="sxs-lookup"><span data-stu-id="4cb3a-106">These features are as follows:</span></span>

* <span data-ttu-id="4cb3a-107">Nazwa konfiguracji, który identyfikuje konfiguracji na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4cb3a-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="4cb3a-108">Ta nazwa może być współużytkowane przez wiele węzłów docelowych</span><span class="sxs-lookup"><span data-stu-id="4cb3a-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="4cb3a-109">Identyfikator agenta, które jednoznacznie identyfikuje jeden węzeł</span><span class="sxs-lookup"><span data-stu-id="4cb3a-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="4cb3a-110">Krok rejestracji, który występuje tylko po raz pierwszy węzeł docelowy łączy się z serwerem ściągania</span><span class="sxs-lookup"><span data-stu-id="4cb3a-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="4cb3a-111">**Uwaga:** te funkcje i możliwości zostały dodane, a nie zastępują istniejące funkcje ściągania i pojęcia.</span><span class="sxs-lookup"><span data-stu-id="4cb3a-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="4cb3a-112">Możesz użyć tych nowych funkcji lub starsze z nowym serwerem ściągania wysyłania w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="4cb3a-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="4cb3a-113">Aby uzyskać więcej informacji, zobacz [Konfigurowanie klienta ściągania przy użyciu nazwy konfiguracji](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="4cb3a-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
