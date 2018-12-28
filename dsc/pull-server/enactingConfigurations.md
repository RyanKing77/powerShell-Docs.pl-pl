---
ms.date: 10/16/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Realizacja konfiguracji
ms.openlocfilehash: 4a6e7e511446ab27307683ad3d5676391e7c791c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405425"
---
# <a name="enacting-configurations"></a><span data-ttu-id="b4987-103">Realizacja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b4987-103">Enacting configurations</span></span>

><span data-ttu-id="b4987-104">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b4987-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b4987-105">Istnieją dwa sposoby wprowadzenie konfiguracje programu PowerShell Desired State Configuration (DSC): wypychanie trybu ani ściągnięcia.</span><span class="sxs-lookup"><span data-stu-id="b4987-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="b4987-106">Trybie wypychania</span><span class="sxs-lookup"><span data-stu-id="b4987-106">Push mode</span></span>

<span data-ttu-id="b4987-107">![Tryb wypychania](../images/pushModel.png "wypychania jak działa tryb")</span><span class="sxs-lookup"><span data-stu-id="b4987-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="b4987-108">Trybie wypychania, który odwołuje się do użytkownika aktywnie zastosowanie konfiguracji do węzła docelowego przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b4987-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="b4987-109">Po utworzeniu i kompilacji konfiguracji, może ona wprowadza w trybie wypychania — w tym przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet, ustawienie parametru - Path, polecenia cmdlet do ścieżki, w którym znajduje się plik MOF konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b4987-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="b4987-110">Na przykład, jeśli konfiguracja MOF znajduje się w `C:\DSC\Configurations\localhost.mof`, czy dotyczą komputera lokalnego za pomocą następującego polecenia: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="b4987-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="b4987-111">__Uwaga__: Domyślnie DSC uruchamia konfigurację jako zadanie w tle.</span><span class="sxs-lookup"><span data-stu-id="b4987-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="b4987-112">Interaktywnie Uruchom konfigurację, należy wywołać [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) z __— oczekiwania__ parametru.</span><span class="sxs-lookup"><span data-stu-id="b4987-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="b4987-113">Tryb ściągania</span><span class="sxs-lookup"><span data-stu-id="b4987-113">Pull mode</span></span>

<span data-ttu-id="b4987-114">![Tryb ściągania](../images/pullModel.png "jak ściągać działa tryb")</span><span class="sxs-lookup"><span data-stu-id="b4987-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="b4987-115">W trybie ściągnięcia ściągnięcia klienci są skonfigurowani do pobrania ich konfiguracji żądanego stanu z usługi ściągania zdalnego.</span><span class="sxs-lookup"><span data-stu-id="b4987-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="b4987-116">Podobnie usługa ściągania zostało skonfigurowane do hosta DSC usługi i został aprowizowany przy użyciu konfiguracji i zasobów, które są wymagane przez klientów ściągnięcia.</span><span class="sxs-lookup"><span data-stu-id="b4987-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="b4987-117">Każdy z klientów ściągania ma zaplanowane zdarzenie, która sprawdza zgodność okresowe konfiguracji węzła.</span><span class="sxs-lookup"><span data-stu-id="b4987-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="b4987-118">Gdy zdarzenie zostanie wyzwolone po raz pierwszy, lokalnego Menedżera konfiguracji (LCM) na komputerze klienckim ściągnięcia kieruje żądanie do usługi ściągania można pobrać konfiguracji określone w LCM.</span><span class="sxs-lookup"><span data-stu-id="b4987-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="b4987-119">W przypadku tej konfiguracji istnieje na usługi ściągania i przekazuje sprawdzania wstępnego sprawdzania poprawności, konfiguracja jest pobierany do klienta ściągania, gdzie następnie jest wykonywany przez LCM.</span><span class="sxs-lookup"><span data-stu-id="b4987-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="b4987-120">LCM sprawdza, czy klient jest zgodne z konfiguracji w regularnych odstępach czasu określonego przez **ConfigurationModeFrequencyMins** właściwość LCM.</span><span class="sxs-lookup"><span data-stu-id="b4987-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="b4987-121">LCM sprawdza, czy zaktualizowane konfiguracje usługi ściągania w regularnych odstępach czasu określonego przez **RefreshModeFrequency** właściwość LCM.</span><span class="sxs-lookup"><span data-stu-id="b4987-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="b4987-122">Aby dowiedzieć się, jak konfigurowanie programu LCM, zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="b4987-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="b4987-123">Zalecane rozwiązanie do hostowania usługi ściągania, to usługa w chmurze DSC, [usługi Azure Automation](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="b4987-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="b4987-124">Znajduje się to rozwiązanie zapewnia zarządzania w trybie graficznym, raportowanie i scentralizowanej administracji.</span><span class="sxs-lookup"><span data-stu-id="b4987-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="b4987-125">Aby uzyskać więcej informacji na temat konfigurowania usługi ściągania w systemie Windows Server, zobacz [Konfigurowanie internetowego serwera ściągania DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="b4987-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="b4987-126">Dowiedz się, że ta implementacja ma ograniczone funkcje i wymagają do działania integracji niektórych "zrobić to samodzielnie".</span><span class="sxs-lookup"><span data-stu-id="b4987-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="b4987-127">W poniższych tematach opisano usługi ściągania i klientami:</span><span class="sxs-lookup"><span data-stu-id="b4987-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="b4987-128">Omówienie DSC usługi Azure Automation</span><span class="sxs-lookup"><span data-stu-id="b4987-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="b4987-129">Konfigurowanie serwera ściągania SMB</span><span class="sxs-lookup"><span data-stu-id="b4987-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="b4987-130">Konfigurowanie klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="b4987-130">Configuring a pull client</span></span>](pullClientConfigID.md)
