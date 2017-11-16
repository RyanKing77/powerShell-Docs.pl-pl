---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Tworzenie potoku ciągłej integracji i ciągłe wdrażanie w usłudze Konfiguracja DSC"
ms.openlocfilehash: 60b41c5d279560d0121372e593879fe03cd52f7a
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="293fb-103">Tworzenie potoku ciągłej integracji i ciągłe wdrażanie w usłudze Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="293fb-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="293fb-104">W tym przykładzie pokazano, jak utworzyć potok ciągłe wdrażanie ciągłe/integracji (CI/CD) przy użyciu programu PowerShell, DSC Pester i Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="293fb-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="293fb-105">Po potoku jest utworzony i skonfigurowany, można użyć pełni wdrożenia, skonfigurowania i przetestowania serwera DNS i skojarzonych rekordów hosta.</span><span class="sxs-lookup"><span data-stu-id="293fb-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span> <span data-ttu-id="293fb-106">Ten proces symuluje pierwsza część potok, który będzie używany w środowisku projektowym.</span><span class="sxs-lookup"><span data-stu-id="293fb-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="293fb-107">Automatyczne potoku CI/CD pomaga w aktualizacji oprogramowania szybciej i bardziej niezawodnie zapewnienie, że cały kod jest przetestowany i czy bieżąca kompilacja kodu jest dostępna przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="293fb-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="293fb-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="293fb-108">Prerequisites</span></span>

<span data-ttu-id="293fb-109">Aby użyć tego przykładu, należy zapoznać się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="293fb-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="293fb-110">Pojęcia dotyczące elementu konfiguracji CD.</span><span class="sxs-lookup"><span data-stu-id="293fb-110">CI-CD concepts.</span></span> <span data-ttu-id="293fb-111">Dobrym odwołanie znajduje się w temacie [Model potoku wersji](http://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="293fb-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="293fb-112">[Git](https://git-scm.com/) kontroli źródła</span><span class="sxs-lookup"><span data-stu-id="293fb-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="293fb-113">[Pester](https://github.com/pester/Pester) testowania framework</span><span class="sxs-lookup"><span data-stu-id="293fb-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="293fb-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="293fb-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="293fb-115">Dane będą potrzebne</span><span class="sxs-lookup"><span data-stu-id="293fb-115">What you will need</span></span>

<span data-ttu-id="293fb-116">Aby skompilować i uruchomić ten przykład, należy w środowisku zawierającym wiele komputerów i/lub maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="293fb-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="293fb-117">Client</span><span class="sxs-lookup"><span data-stu-id="293fb-117">Client</span></span>

<span data-ttu-id="293fb-118">Jest to komputer, na którym będzie wykonywać wszystkie pracy konfigurowania i uruchamiania przykładzie.</span><span class="sxs-lookup"><span data-stu-id="293fb-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="293fb-119">Komputer kliencki musi być komputerem z systemem Windows z zainstalowane następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="293fb-119">The client computer must be a Windows computer with the following installed:</span></span>
- [<span data-ttu-id="293fb-120">Git</span><span class="sxs-lookup"><span data-stu-id="293fb-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="293fb-121">sklonowany z https://github.com/PowerShell/Demo_CI repozytorium git lokalnego</span><span class="sxs-lookup"><span data-stu-id="293fb-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="293fb-122">Edytor tekstu, takich jak [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="293fb-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="293fb-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="293fb-123">TFSSrv1</span></span>

<span data-ttu-id="293fb-124">Komputer obsługujący serwer TFS, w którym zostaną zdefiniowane kompilacji i wydania.</span><span class="sxs-lookup"><span data-stu-id="293fb-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="293fb-125">Ten komputer musi mieć [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="293fb-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="293fb-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="293fb-126">BuildAgent</span></span>

<span data-ttu-id="293fb-127">Komputer z systemem Windows kompilacji agenta, która tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="293fb-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="293fb-128">Ten komputer musi mieć i uruchom agenta kompilacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="293fb-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="293fb-129">Zobacz [wdrażania agenta w systemie Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) dla agenta kompilacji instrukcje dotyczące sposobu instalowania i uruchamiania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="293fb-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="293fb-130">Należy również zainstalować zarówno `xDnsServer` i `xNetworking` DSC modułów na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="293fb-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="293fb-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="293fb-131">TestAgent1</span></span>

<span data-ttu-id="293fb-132">Jest to komputer, który jest skonfigurowany jako serwer DNS za pomocą konfiguracji DSC w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="293fb-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="293fb-133">Na komputerze musi być uruchomiona [systemu Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="293fb-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="293fb-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="293fb-134">TestAgent2</span></span>

<span data-ttu-id="293fb-135">Jest to komputer, który obsługuje ten przykład konfiguruje witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="293fb-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="293fb-136">Na komputerze musi być uruchomiona [systemu Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="293fb-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> 

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="293fb-137">Dodaj kod do TFS</span><span class="sxs-lookup"><span data-stu-id="293fb-137">Add the code to TFS</span></span>

<span data-ttu-id="293fb-138">Zaczniemy Tworzenie repozytorium Git w programie TFS, a następnie importowanie kod z lokalnym repozytorium na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="293fb-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="293fb-139">Jeśli nie ma już sklonować repozytorium Demo_CI na komputerze klienckim, zrób tak teraz za pomocą następującego polecenia git:</span><span class="sxs-lookup"><span data-stu-id="293fb-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="293fb-140">Na komputerze klienckim przejdź do serwera TFS w przeglądarce sieci web.</span><span class="sxs-lookup"><span data-stu-id="293fb-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="293fb-141">W programie TFS [Tworzenie nowego projektu zespołowego](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) o nazwie Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="293fb-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

    <span data-ttu-id="293fb-142">Upewnij się, że **kontroli wersji** ustawiono **Git**.</span><span class="sxs-lookup"><span data-stu-id="293fb-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="293fb-143">Na komputerze klienckim należy dodać zdalnej do repozytorium, utworzony w programie TFS przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="293fb-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

    `git remote add tfs <YourTFSRepoURL>`

    <span data-ttu-id="293fb-144">Gdzie `<YourTFSRepoURL>` jest adres URL klonowania służący do repozytorium TFS utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="293fb-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

    <span data-ttu-id="293fb-145">Jeśli nie wiadomo, gdzie można znaleźć ten adres URL, zobacz [istniejące repozytorium Git Clone](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span><span class="sxs-lookup"><span data-stu-id="293fb-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="293fb-146">Wypchnij kod z lokalnym repozytorium do repozytorium TFS przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="293fb-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

    `git push tfs --all`
1. <span data-ttu-id="293fb-147">Repozytorium TFS zostaną wypełnione z kodem Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="293fb-147">The TFS repository will be populated with the Demo_CI code.</span></span>

><span data-ttu-id="293fb-148">**Uwaga:** w tym przykładzie użyto kod w `ci-cd-example` gałęzi repozytorium Git.</span><span class="sxs-lookup"><span data-stu-id="293fb-148">**Note:** This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
><span data-ttu-id="293fb-149">Należy określić gałęzi jako gałąź domyślną projektu TFS i wyzwalaczy CI/CD tworzenia.</span><span class="sxs-lookup"><span data-stu-id="293fb-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="293fb-150">Opis kodu</span><span class="sxs-lookup"><span data-stu-id="293fb-150">Understanding the code</span></span>

<span data-ttu-id="293fb-151">Przed utworzymy potoki kompilowanie i wdrażanie przyjrzymy kodu, aby zrozumieć, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="293fb-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="293fb-152">Na komputerze klienckim otwórz w ulubionym edytorze tekstów i przejdź do katalogu głównego repozytorium Demo_CI Git.</span><span class="sxs-lookup"><span data-stu-id="293fb-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="293fb-153">Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="293fb-153">The DSC configuration</span></span>

<span data-ttu-id="293fb-154">Otwórz plik `DNSServer.ps1` (od głównego lokalnego repozytorium Demo_CI `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="293fb-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="293fb-155">Ten plik zawiera konfiguracji DSC, który konfiguruje serwer DNS.</span><span class="sxs-lookup"><span data-stu-id="293fb-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="293fb-156">Poniżej przedstawiono w całości:</span><span class="sxs-lookup"><span data-stu-id="293fb-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="293fb-157">Powiadomienie `Node` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="293fb-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="293fb-158">Znajduje to węzły, które zostały zdefiniowane jako mający rolę `DNSServer` w [dane konfiguracji](configData.md), który jest tworzony przez `DevEnv.ps1` skryptu.</span><span class="sxs-lookup"><span data-stu-id="293fb-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="293fb-159">Ważne jest określenie węzłów przy użyciu danych konfiguracji, podczas wykonywania elementu konfiguracji, ponieważ węzeł informacji prawdopodobnie spowoduje zmianę między środowiskami i przy użyciu danych konfiguracji umożliwia łatwe wprowadzić zmiany w informacjach węzła bez konieczności zmieniania kodu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="293fb-159">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="293fb-160">W pierwszym bloku zasobów, wywołuje konfiguracji [WindowsFeature](windowsFeatureResource.md) aby upewnić się, że jest włączona funkcja DNS.</span><span class="sxs-lookup"><span data-stu-id="293fb-160">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span> <span data-ttu-id="293fb-161">Bloki zasobów, które należy wykonać wywołanie zasobów z [xDnsServer](https://github.com/PowerShell/xDnsServer) modułu, aby skonfigurować strefa podstawowa i rekordów DNS.</span><span class="sxs-lookup"><span data-stu-id="293fb-161">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="293fb-162">Zwróć uwagę, że dwa `xDnsRecord` bloki są ujęte w `foreach` pętli, które iterację tablic w danych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="293fb-162">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="293fb-163">Ponownie, dane konfiguracji są tworzone przez `DevEnv.ps1` skryptu, który przyjrzymy dalej.</span><span class="sxs-lookup"><span data-stu-id="293fb-163">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="293fb-164">Dane konfiguracji</span><span class="sxs-lookup"><span data-stu-id="293fb-164">Configuration data</span></span>

<span data-ttu-id="293fb-165">`DevEnv.ps1` Pliku (z katalogu lokalnego repozytorium Demo_CI `./InfraDNS/DevEnv.ps1`) określa dane konfiguracyjne specyficzne dla środowiska w tablicy skrótów, a następnie przekazuje tego obiektu hashtable do wywołania `New-DscConfigurationDataDocument` funkcja, która jest zdefiniowana w `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="293fb-165">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="293fb-166">`DevEnv.ps1` Pliku:</span><span class="sxs-lookup"><span data-stu-id="293fb-166">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="293fb-167">`New-DscConfigurationDataDocument` — Funkcja (zdefiniowany w `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programowo tworzy dokument danych konfiguracji z hashtable (dane węzła) i tablicy (z systemem innym niż węzeł danych), które są przekazywane jako `RawEnvData` i `OtherEnvData` parametrów.</span><span class="sxs-lookup"><span data-stu-id="293fb-167">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="293fb-168">W tym przypadku tylko `RawEnvData` parametr jest używany.</span><span class="sxs-lookup"><span data-stu-id="293fb-168">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="293fb-169">Psake skryptu kompilacji</span><span class="sxs-lookup"><span data-stu-id="293fb-169">The psake build script</span></span>

<span data-ttu-id="293fb-170">[Psake](https://github.com/psake/psake) kompilacji skryptu zdefiniowane w `Build.ps1` (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Build.ps1`) definiuje zadania, które są częścią kompilacji.</span><span class="sxs-lookup"><span data-stu-id="293fb-170">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="293fb-171">Definiuje również inne zadania zależy od każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="293fb-171">It also defines which other tasks each task depends on.</span></span> <span data-ttu-id="293fb-172">Po wywołaniu, skrypt psake upewnia się, że określonego zadania (lub zadania o nazwie `Default` Jeśli nie zostanie określona) działa i że wszystkie zależności również uruchomić (tak, aby uruchomić zależności zależności, jest rekursywny, i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="293fb-172">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="293fb-173">W tym przykładzie `Default` zadań jest zdefiniowany jako:</span><span class="sxs-lookup"><span data-stu-id="293fb-173">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="293fb-174">`Default` Zadanie ma się implementacji, ale zależy `CompileConfigs` zadań.</span><span class="sxs-lookup"><span data-stu-id="293fb-174">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="293fb-175">Wynikowa łańcuch zależności zadań zapewnia, że wszystkie zadania w skrypcie kompilacji są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="293fb-175">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="293fb-176">W tym przykładzie skrypt psake jest wywoływany przez wywołanie do `Invoke-PSake` w `Initiate.ps1` (znajdującym się w folderze głównym repozytorium Demo_CI):</span><span class="sxs-lookup"><span data-stu-id="293fb-176">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="293fb-177">Gdy utworzymy definicję kompilacji w naszym przykładzie w programie TFS, firma Microsoft będzie dostarczać naszych pliku skryptu psake jako `fileName` parametru w ramach tego skryptu.</span><span class="sxs-lookup"><span data-stu-id="293fb-177">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="293fb-178">Skrypt kompilacji definiuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="293fb-178">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="293fb-179">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="293fb-179">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="293fb-180">Uruchamia `DevEnv.ps1`, który generuje plik danych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="293fb-180">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="293fb-181">InstallModules</span><span class="sxs-lookup"><span data-stu-id="293fb-181">InstallModules</span></span>

<span data-ttu-id="293fb-182">Instaluje moduły wymagane przez konfigurację `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="293fb-182">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="293fb-183">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="293fb-183">ScriptAnalysis</span></span>

<span data-ttu-id="293fb-184">Wywołania [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="293fb-184">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="293fb-185">UnitTests</span><span class="sxs-lookup"><span data-stu-id="293fb-185">UnitTests</span></span>

<span data-ttu-id="293fb-186">Uruchamia [Pester](https://github.com/pester/Pester/wiki) testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="293fb-186">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="293fb-187">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="293fb-187">CompileConfigs</span></span>

<span data-ttu-id="293fb-188">Kompiluje konfigurację (`DNSServer.ps1`) do pliku MOF przy użyciu danych konfiguracji wygenerowane przez `GenerateEnvironmentFiles` zadań.</span><span class="sxs-lookup"><span data-stu-id="293fb-188">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="293fb-189">Czyszczenie</span><span class="sxs-lookup"><span data-stu-id="293fb-189">Clean</span></span>

<span data-ttu-id="293fb-190">Tworzy foldery używane dla przykładu i usuwa wszystkie wyniki testów, pliki danych konfiguracji i moduły poprzedniej działa.</span><span class="sxs-lookup"><span data-stu-id="293fb-190">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="293fb-191">Psake wdrożenia skryptu</span><span class="sxs-lookup"><span data-stu-id="293fb-191">The psake deploy script</span></span>

<span data-ttu-id="293fb-192">[Psake](https://github.com/psake/psake) skrypt wdrożenia zdefiniowane w `Deploy.ps1` (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Deploy.ps1`) definiuje zadań, które wdrażanie i uruchamianie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="293fb-192">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="293fb-193">`Deploy.ps1`definiuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="293fb-193">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="293fb-194">DeployModules</span><span class="sxs-lookup"><span data-stu-id="293fb-194">DeployModules</span></span>

<span data-ttu-id="293fb-195">Uruchamia sesję programu PowerShell na `TestAgent1` i instaluje modułów zawierających DSC zasoby wymagane do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="293fb-195">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="293fb-196">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="293fb-196">DeployConfigs</span></span>

<span data-ttu-id="293fb-197">Wywołania [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) polecenia cmdlet, aby uruchomić konfigurację na `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="293fb-197">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="293fb-198">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="293fb-198">IntegrationTests</span></span>

<span data-ttu-id="293fb-199">Uruchamia [Pester](https://github.com/pester/Pester/wiki) testów integracji.</span><span class="sxs-lookup"><span data-stu-id="293fb-199">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="293fb-200">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="293fb-200">AcceptanceTests</span></span>

<span data-ttu-id="293fb-201">Uruchamia [Pester](https://github.com/pester/Pester/wiki) testy akceptacji.</span><span class="sxs-lookup"><span data-stu-id="293fb-201">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="293fb-202">Czyszczenie</span><span class="sxs-lookup"><span data-stu-id="293fb-202">Clean</span></span>

<span data-ttu-id="293fb-203">Usunięcie wszelkich modułów zainstalowanych w poprzedniej uruchamia i zapewnia, że istnieje folder wyników testu.</span><span class="sxs-lookup"><span data-stu-id="293fb-203">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="293fb-204">Testowanie skryptów</span><span class="sxs-lookup"><span data-stu-id="293fb-204">Test scripts</span></span>

<span data-ttu-id="293fb-205">Testy akceptacji, integracja i jednostki są zdefiniowane w skryptach w `Tests` folder (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Tests`), każdy w plikach o nazwie `DNSServer.tests.ps1` w ich odpowiednich folderów.</span><span class="sxs-lookup"><span data-stu-id="293fb-205">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="293fb-206">Użyj skryptów testu [Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.</span><span class="sxs-lookup"><span data-stu-id="293fb-206">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="293fb-207">Testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="293fb-207">Unit tests</span></span>

<span data-ttu-id="293fb-208">Konfiguracje testów DSC, aby upewnić się, czy konfiguracje wykona, czego oczekuje się po uruchomieniu testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="293fb-208">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="293fb-209">Skrypt używa testu jednostkowego [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="293fb-209">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="293fb-210">Testy integracji</span><span class="sxs-lookup"><span data-stu-id="293fb-210">Integration tests</span></span>

<span data-ttu-id="293fb-211">Testy integracji jest przetestowanie konfiguracji systemu, aby upewnić się, że gdy zintegrowana z innymi składnikami, system jest skonfigurowany zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="293fb-211">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="293fb-212">Te testy wykonywane w docelowym węźle po skonfigurowaniu usłudze Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="293fb-212">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="293fb-213">Skrypt testu integracji używa kombinację [Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.</span><span class="sxs-lookup"><span data-stu-id="293fb-213">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="293fb-214">Testy akceptacji</span><span class="sxs-lookup"><span data-stu-id="293fb-214">Acceptance tests</span></span>

<span data-ttu-id="293fb-215">Testy akceptacji testu systemu, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="293fb-215">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="293fb-216">Na przykład testy, aby upewnić się, że właściwe informacje, gdy kwerenda zwraca stronę sieci web.</span><span class="sxs-lookup"><span data-stu-id="293fb-216">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="293fb-217">Te testy uruchomić zdalnie w węźle docelowym w celu przetestowania rzeczywistych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="293fb-217">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="293fb-218">Skrypt testu integracji używa kombinację [Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.</span><span class="sxs-lookup"><span data-stu-id="293fb-218">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="293fb-219">Zdefiniuj kompilacji</span><span class="sxs-lookup"><span data-stu-id="293fb-219">Define the build</span></span>

<span data-ttu-id="293fb-220">Firma Microsoft przekazanego naszego kodu do TFS i przeglądał tak jest, zdefiniujmy naszych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="293fb-220">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="293fb-221">W tym miejscu omówione zostaną następujące czynności kroków kompilacji, które dodasz do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="293fb-221">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="293fb-222">Aby uzyskać instrukcje dotyczące sposobu tworzenia definicji kompilacji w programie TFS, zobacz [tworzenie i kolejki definicję kompilacji](https://www.visualstudio.com/en-us/docs/build/define/create).</span><span class="sxs-lookup"><span data-stu-id="293fb-222">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="293fb-223">Utwórz nową definicję kompilacji (wybierz **pusty** szablonu) o nazwie "InfraDNS".</span><span class="sxs-lookup"><span data-stu-id="293fb-223">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="293fb-224">Dodaj następujące kroki, aby użytkownik definicji kompilacji:</span><span class="sxs-lookup"><span data-stu-id="293fb-224">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="293fb-225">Skrypt programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="293fb-225">PowerShell Script</span></span>
- <span data-ttu-id="293fb-226">Publikowanie wyników testu</span><span class="sxs-lookup"><span data-stu-id="293fb-226">Publish Test Results</span></span>
- <span data-ttu-id="293fb-227">Skopiuj pliki</span><span class="sxs-lookup"><span data-stu-id="293fb-227">Copy Files</span></span>
- <span data-ttu-id="293fb-228">Publikowanie artefaktów</span><span class="sxs-lookup"><span data-stu-id="293fb-228">Publish Artifact</span></span>

<span data-ttu-id="293fb-229">Po dodaniu te kroki procesu kompilacji, Edytuj właściwości każdego kroku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="293fb-229">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="293fb-230">Skrypt programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="293fb-230">PowerShell Script</span></span>

1. <span data-ttu-id="293fb-231">Ustaw **typu** właściwości `File Path`.</span><span class="sxs-lookup"><span data-stu-id="293fb-231">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="293fb-232">Ustaw **ścieżka skryptu** właściwości `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="293fb-232">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="293fb-233">Dodaj `-fileName build` do **argumenty** właściwości.</span><span class="sxs-lookup"><span data-stu-id="293fb-233">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="293fb-234">Ten krok kompilacji działa `initiate.ps1` pliku, który wywołuje psake skryptu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="293fb-234">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="293fb-235">Publikowanie wyników testu</span><span class="sxs-lookup"><span data-stu-id="293fb-235">Publish Test Results</span></span>

1. <span data-ttu-id="293fb-236">Ustaw **Format wyniku testu** do`NUnit`</span><span class="sxs-lookup"><span data-stu-id="293fb-236">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="293fb-237">Ustaw **plików z wynikami testów** do`InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="293fb-237">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="293fb-238">Ustaw **tytułu uruchomienia testu** do `Unit`.</span><span class="sxs-lookup"><span data-stu-id="293fb-238">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="293fb-239">Upewnij się, że **opcje sterowania** **włączone** i **są zawsze uruchamiane** są wybrane.</span><span class="sxs-lookup"><span data-stu-id="293fb-239">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="293fb-240">Ten krok kompilacji uruchamia testy jednostkowe w skrypcie Pester analizujemy wcześniej i przechowuje wyniki w `InfraDNS/Tests/Results/*.xml` folderu.</span><span class="sxs-lookup"><span data-stu-id="293fb-240">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="293fb-241">Skopiuj pliki</span><span class="sxs-lookup"><span data-stu-id="293fb-241">Copy Files</span></span>

1. <span data-ttu-id="293fb-242">Każdy z poniższych wierszy, aby dodać **zawartość**:</span><span class="sxs-lookup"><span data-stu-id="293fb-242">Add each of the following lines to **Contents**:</span></span>

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. <span data-ttu-id="293fb-243">Ustaw **TargetFolder** do`$(BuildArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="293fb-243">Set **TargetFolder** to `$(BuildArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="293fb-244">Ten krok umożliwia skopiowanie kompilacji i test skryptów w katalogu przemieszczania więc zostać opublikowane zgodnie z kompilacji artefakty przez następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="293fb-244">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="293fb-245">Publikowanie artefaktów</span><span class="sxs-lookup"><span data-stu-id="293fb-245">Publish Artifact</span></span>

1. <span data-ttu-id="293fb-246">Ustaw **ścieżka do publikowania** do`$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="293fb-246">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="293fb-247">Ustaw **nazwa artefaktu** do`Deploy`</span><span class="sxs-lookup"><span data-stu-id="293fb-247">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="293fb-248">Ustaw **typu artefaktu** do`Server`</span><span class="sxs-lookup"><span data-stu-id="293fb-248">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="293fb-249">Wybierz `Enabled` w **opcje sterowania**</span><span class="sxs-lookup"><span data-stu-id="293fb-249">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="293fb-250">Włącz ciągłej integracji</span><span class="sxs-lookup"><span data-stu-id="293fb-250">Enable continuous integration</span></span>

<span data-ttu-id="293fb-251">Teraz wyzwalacz, który powoduje, że projekt do kompilacji w dowolnej chwili zaplanujemy zmiany jest zaewidencjonowany do `ci-cd-example` gałęzi repozytorium git.</span><span class="sxs-lookup"><span data-stu-id="293fb-251">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="293fb-252">W programie TFS, kliknij przycisk **kompilacji i wydania** kartę</span><span class="sxs-lookup"><span data-stu-id="293fb-252">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="293fb-253">Wybierz `DNS Infra` definicji kompilacji, a następnie kliknij przycisk **edycji**</span><span class="sxs-lookup"><span data-stu-id="293fb-253">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="293fb-254">Kliknij przycisk **wyzwalaczy** kartę</span><span class="sxs-lookup"><span data-stu-id="293fb-254">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="293fb-255">Wybierz **ciągłej integracji (CI)**i wybierz `refs/heads/ci-cd-example` na liście rozwijanej gałęzi</span><span class="sxs-lookup"><span data-stu-id="293fb-255">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="293fb-256">Kliknij przycisk **zapisać** , a następnie **OK**</span><span class="sxs-lookup"><span data-stu-id="293fb-256">Click **Save** and then **OK**</span></span>

<span data-ttu-id="293fb-257">Teraz wszelkie zmiany wyzwalaczy repozytorium git TFS automatyczne kompilacji.</span><span class="sxs-lookup"><span data-stu-id="293fb-257">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="293fb-258">Utwórz definicję zlecenia</span><span class="sxs-lookup"><span data-stu-id="293fb-258">Create the release definition</span></span>

<span data-ttu-id="293fb-259">Teraz należy utworzyć definicji wersji, tak aby projektu została wdrożona do środowiska projektowego z każdym ewidencjonowania kodu.</span><span class="sxs-lookup"><span data-stu-id="293fb-259">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="293fb-260">Aby to zrobić, Dodaj nową definicję wersji skojarzony z `InfraDNS` wcześniej utworzonego definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="293fb-260">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="293fb-261">Należy wybrać **ciągłe wdrażanie** tak, aby nowej wersji zostanie wywołane dowolnej chwili ukończenia nowej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="293fb-261">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="293fb-262">([Porady: Praca z definicji wersji](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) i skonfigurować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="293fb-262">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="293fb-263">Do definicji wersji, należy dodać następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="293fb-263">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="293fb-264">Skrypt programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="293fb-264">PowerShell Script</span></span>
- <span data-ttu-id="293fb-265">Publikowanie wyników testu</span><span class="sxs-lookup"><span data-stu-id="293fb-265">Publish Test Results</span></span>
- <span data-ttu-id="293fb-266">Publikowanie wyników testu</span><span class="sxs-lookup"><span data-stu-id="293fb-266">Publish Test Results</span></span>

<span data-ttu-id="293fb-267">Edytuj kroki w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="293fb-267">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="293fb-268">Skrypt programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="293fb-268">PowerShell Script</span></span>

1. <span data-ttu-id="293fb-269">Ustaw **ścieżka skryptu** do`$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="293fb-269">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="293fb-270">Ustaw **argumenty** do`-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="293fb-270">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="293fb-271">Najpierw opublikować wyniki testu</span><span class="sxs-lookup"><span data-stu-id="293fb-271">First Publish Test Results</span></span>

1. <span data-ttu-id="293fb-272">Wybierz `NUnit` dla **Format wyniku testu** pola</span><span class="sxs-lookup"><span data-stu-id="293fb-272">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="293fb-273">Ustaw **plików wyników testu** do`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="293fb-273">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="293fb-274">Ustaw **tytułu uruchomienia testu** do`Integration`</span><span class="sxs-lookup"><span data-stu-id="293fb-274">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="293fb-275">W obszarze **opcje sterowania**, sprawdź **są zawsze uruchamiane**</span><span class="sxs-lookup"><span data-stu-id="293fb-275">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="293fb-276">Drugi opublikować wyniki testu</span><span class="sxs-lookup"><span data-stu-id="293fb-276">Second Publish Test Results</span></span>

1. <span data-ttu-id="293fb-277">Wybierz `NUnit` dla **Format wyniku testu** pola</span><span class="sxs-lookup"><span data-stu-id="293fb-277">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="293fb-278">Ustaw **plików wyników testu** do`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="293fb-278">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="293fb-279">Ustaw **tytułu uruchomienia testu** do`Acceptance`</span><span class="sxs-lookup"><span data-stu-id="293fb-279">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="293fb-280">W obszarze **opcje sterowania**, sprawdź **są zawsze uruchamiane**</span><span class="sxs-lookup"><span data-stu-id="293fb-280">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="293fb-281">Sprawdź wyniki</span><span class="sxs-lookup"><span data-stu-id="293fb-281">Verify your results</span></span>

<span data-ttu-id="293fb-282">Teraz, dowolnej chwili możesz wypchnąć zmiany `ci-cd-example` rozpocznie gałęzi do programu TFS, nowej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="293fb-282">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="293fb-283">Jeśli kompilacja zakończy się pomyślnie, zostanie wywołany nowego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="293fb-283">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="293fb-284">Wynik wdrożenia można sprawdzić, otwierając przeglądarki na komputerze klienckim i przechodząc do `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="293fb-284">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="293fb-285">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="293fb-285">Next steps</span></span>

<span data-ttu-id="293fb-286">Ten przykład konfiguruje serwer DNS `TestAgent1` , aby adres URL `www.contoso.com` jest rozpoznawana jako `TestAgent2`, ale nie faktycznie wdrażać witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="293fb-286">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="293fb-287">Szkielet dokonaniem znajduje się w repozytorium w obszarze `WebApp` folderu.</span><span class="sxs-lookup"><span data-stu-id="293fb-287">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="293fb-288">Zastępcze dostarczony do tworzenia skryptów psake, Pester testów i konfiguracji DSC umożliwia wdrażanie własnych witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="293fb-288">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>







