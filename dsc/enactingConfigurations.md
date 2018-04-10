---
ms.date: 10/16/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Realizacja konfiguracji
ms.openlocfilehash: 28ca852eb00298c229be8104ecdfeabc47a10abc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="enacting-configurations"></a><span data-ttu-id="c8d8f-103">Realizacja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c8d8f-103">Enacting configurations</span></span>

><span data-ttu-id="c8d8f-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c8d8f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c8d8f-105">Istnieją dwa sposoby wprowadza konfiguracje konfiguracji żądanego stanu środowiska PowerShell (DSC): push trybu ani ściągania.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="c8d8f-106">Tryb wypychania</span><span class="sxs-lookup"><span data-stu-id="c8d8f-106">Push mode</span></span>

<span data-ttu-id="c8d8f-107">![Tryb wypychania](images/pushModel.png "push jak działa tryb")</span><span class="sxs-lookup"><span data-stu-id="c8d8f-107">![Push mode](images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="c8d8f-108">Tryb wypychania odwołuje się do użytkownika aktywnie stosowania konfiguracji do węzła docelowego przez wywołanie metody [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="c8d8f-109">Po utworzeniu i kompilowania konfiguracji, można go wprowadza w trybie wypychania — w tym wywołując [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) polecenia cmdlet, ustawienie parametru - Path, polecenia cmdlet do ścieżki, w którym znajduje się konfiguracji MOF.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="c8d8f-110">Na przykład, jeśli konfiguracja MOF znajduje się pod adresem `C:\DSC\Configurations\localhost.mof`, czy zastosować je na komputerze lokalnym przy użyciu następującego polecenia: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="c8d8f-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="c8d8f-111">__Uwaga__: domyślnie DSC uruchamia konfigurację jako zadanie w tle.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="c8d8f-112">Aby pracować w trybie interakcyjnym konfiguracji, należy wywołać [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) z __— oczekiwania__ parametru.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="c8d8f-113">Tryb ściągania</span><span class="sxs-lookup"><span data-stu-id="c8d8f-113">Pull mode</span></span>

<span data-ttu-id="c8d8f-114">![Ściąganie tryb](images/pullModel.png "ściągnięcia jak działa tryb")</span><span class="sxs-lookup"><span data-stu-id="c8d8f-114">![Pull Mode](images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="c8d8f-115">W trybie ściągania ściągania klienci są skonfigurowani do pobrania ich konfiguracji żądanego stanu z usługi zdalnego ściągania.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="c8d8f-116">Podobnie usługa ściągania nie został skonfigurowany do usługi hosta DSC i zainicjowano z konfiguracjami i zasobów, które są wymagane przez klientów ściągania.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="c8d8f-117">Każda klientów ściągania ma zaplanowane zdarzenie, który sprawdza zgodność okresowe konfiguracji węzła.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="c8d8f-118">Gdy zdarzenie jest wywoływane po raz pierwszy, lokalnego Menedżera konfiguracji (LCM) na komputerze klienckim ściągania zgłasza żądanie do usługi ściągania można pobrać konfiguracji określone w LCM.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="c8d8f-119">Jeśli istnieje tej konfiguracji w usłudze ściągania i przekazaniem sprawdzanie poprawności początkowej, konfiguracji są pobierane klienta ściągania, gdzie następnie jest wykonywany przez LCM.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="c8d8f-120">LCM sprawdza, czy klient jest zgodność z konfiguracji w regularnych odstępach czasu określonego przez **ConfigurationModeFrequencyMins** właściwości LCM.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="c8d8f-121">LCM wyszukuje zaktualizowanej konfiguracji w usłudze replikacji ściąganej w regularnych odstępach czasu określonego przez **RefreshModeFrequency** właściwości LCM.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="c8d8f-122">Aby uzyskać informacje o konfigurowaniu LCM, zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="c8d8f-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="c8d8f-123">Zalecane rozwiązanie w celu hostowania usługi ściągnięcia jest DSC usługi w chmurze, [usługi Automatyzacja Azure](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="c8d8f-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="c8d8f-124">Znajduje to rozwiązanie zapewnia zarządzania w trybie graficznym, raportowanie i scentralizowane administrowanie.</span><span class="sxs-lookup"><span data-stu-id="c8d8f-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="c8d8f-125">Aby uzyskać więcej informacji na temat konfigurowania usługi ściągnięcia w systemie Windows Server, zobacz [ustawienie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="c8d8f-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="c8d8f-126">Zrozumieć jednak, że ta implementacja ma ograniczone funkcje i wymagają do działania integracji niektórych "to zrobić samodzielnie".</span><span class="sxs-lookup"><span data-stu-id="c8d8f-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="c8d8f-127">W poniższych tematach opisano ściągania usług i klientów:</span><span class="sxs-lookup"><span data-stu-id="c8d8f-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="c8d8f-128">Przegląd usługi Konfiguracja DSC automatyzacji Azure</span><span class="sxs-lookup"><span data-stu-id="c8d8f-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="c8d8f-129">Konfigurowanie serwera ściągania SMB</span><span class="sxs-lookup"><span data-stu-id="c8d8f-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="c8d8f-130">Konfigurowanie klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="c8d8f-130">Configuring a pull client</span></span>](pullClientConfigID.md)