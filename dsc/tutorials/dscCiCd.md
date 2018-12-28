---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Tworzenie potoku ciągłej integracji i ciągłego wdrażania za pomocą DSC
ms.openlocfilehash: c305d9bc7e0f8c659129b5a20d0b7e8b34d09ba8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405246"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="89b2d-103">Tworzenie potoku ciągłej integracji i ciągłego wdrażania za pomocą DSC</span><span class="sxs-lookup"><span data-stu-id="89b2d-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="89b2d-104">W tym przykładzie pokazano, jak utworzyć potok ciągłej integracji i ciągłego wdrażania (CI/CD) przy użyciu programu PowerShell, DSC, usług Pester i Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="89b2d-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="89b2d-105">Po potoku jest utworzony i skonfigurowany, można użyć w pełni wdrażania, konfigurowania i testowania serwera DNS i skojarzonych rekordów hosta.</span><span class="sxs-lookup"><span data-stu-id="89b2d-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="89b2d-106">Ten proces symuluje pierwszą część z potoku, która będzie używana w środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="89b2d-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="89b2d-107">Swój zautomatyzowany potok CI/CD pomaga zaktualizować oprogramowanie szybciej i bardziej niezawodnie zagwarantowanie, że cały kod jest przetestowany i czy bieżąca kompilacja kodu jest dostępny przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="89b2d-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89b2d-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="89b2d-108">Prerequisites</span></span>

<span data-ttu-id="89b2d-109">Aby użyć tego przykładu, należy zapoznać się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="89b2d-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="89b2d-110">Pojęcia dotyczące ciągłej integracji ciągłego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="89b2d-110">CI-CD concepts.</span></span> <span data-ttu-id="89b2d-111">Wartościowa dokumentacja ułatwiająca znajduje się w temacie [Model potoku wydania](http://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="89b2d-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="89b2d-112">[Git](https://git-scm.com/) kontroli źródła</span><span class="sxs-lookup"><span data-stu-id="89b2d-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="89b2d-113">[Usług Pester](https://github.com/pester/Pester) struktury testowania</span><span class="sxs-lookup"><span data-stu-id="89b2d-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="89b2d-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="89b2d-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="89b2d-115">Będą potrzebne</span><span class="sxs-lookup"><span data-stu-id="89b2d-115">What you will need</span></span>

<span data-ttu-id="89b2d-116">Aby skompilować i uruchomić ten przykład, konieczne będzie środowisko z kilku komputerów i/lub maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="89b2d-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="89b2d-117">Client</span><span class="sxs-lookup"><span data-stu-id="89b2d-117">Client</span></span>

<span data-ttu-id="89b2d-118">Jest to komputer, na którym odbywa się na wszystkie zadania konfigurowania i uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="89b2d-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="89b2d-119">Komputer kliencki musi być komputerem Windows za pomocą zainstalowane następujące oprogramowanie:</span><span class="sxs-lookup"><span data-stu-id="89b2d-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="89b2d-120">usługi git</span><span class="sxs-lookup"><span data-stu-id="89b2d-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="89b2d-121">sklonowany z repozytorium lokalnego narzędzia git https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="89b2d-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="89b2d-122">Edytor tekstu, takie jak [programu Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="89b2d-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="89b2d-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="89b2d-123">TFSSrv1</span></span>

<span data-ttu-id="89b2d-124">Komputer, który jest hostem serwera TFS, w którym będzie definicji kompilacji i wydania.</span><span class="sxs-lookup"><span data-stu-id="89b2d-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="89b2d-125">Ten komputer musi mieć [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="89b2d-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="89b2d-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="89b2d-126">BuildAgent</span></span>

<span data-ttu-id="89b2d-127">Komputer z systemem Windows agenta kompilacji, który tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="89b2d-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="89b2d-128">Ten komputer musi mieć Windows, zainstaluj i uruchom agenta kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="89b2d-129">Zobacz [wdrażanie agenta w Windows](/azure/devops/pipelines/agents/v2-windows) dla agenta kompilacji, instrukcje dotyczące sposobu instalowania i uruchamiania Windows.</span><span class="sxs-lookup"><span data-stu-id="89b2d-129">See [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="89b2d-130">Należy również zainstalować zarówno `xDnsServer` i `xNetworking` modułów DSC na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="89b2d-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="89b2d-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="89b2d-131">TestAgent1</span></span>

<span data-ttu-id="89b2d-132">Jest to komputer, który jest skonfigurowany jako serwer DNS za pomocą konfiguracji DSC, w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="89b2d-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="89b2d-133">Na komputerze musi być uruchomiona [systemu Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="89b2d-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="89b2d-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="89b2d-134">TestAgent2</span></span>

<span data-ttu-id="89b2d-135">Jest to komputer, który jest hostem witryny sieci Web, który określa, w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="89b2d-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="89b2d-136">Na komputerze musi być uruchomiona [systemu Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="89b2d-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="89b2d-137">Dodaj kod programem TFS</span><span class="sxs-lookup"><span data-stu-id="89b2d-137">Add the code to TFS</span></span>

<span data-ttu-id="89b2d-138">Rozpoczniemy tworzenia repozytorium Git w programie TFS, a następnie importując kod ze swojego lokalnego repozytorium na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="89b2d-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="89b2d-139">Jeśli nie zostały jeszcze sklonowane repozytorium Demo_CI na swoim komputerze klienckim, wykonaj teraz przez uruchomienie następującego polecenia git:</span><span class="sxs-lookup"><span data-stu-id="89b2d-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="89b2d-140">Na komputerze klienckim przejdź do serwera TFS w przeglądarce sieci web.</span><span class="sxs-lookup"><span data-stu-id="89b2d-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="89b2d-141">W programie TFS [Tworzenie nowego projektu zespołowego](/azure/devops/organizations/projects/create-project) o nazwie Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="89b2d-141">In TFS, [Create a new team project](/azure/devops/organizations/projects/create-project) named Demo_CI.</span></span>

   <span data-ttu-id="89b2d-142">Upewnij się, że **kontroli wersji** ustawiono **Git**.</span><span class="sxs-lookup"><span data-stu-id="89b2d-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="89b2d-143">Na komputerze klienckim należy dodać element zdalny do repozytorium, który został utworzony w programie TFS za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="89b2d-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="89b2d-144">Gdzie `<YourTFSRepoURL>` jest adres URL klonowania repozytorium TFS został utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="89b2d-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="89b2d-145">Jeśli nie wiesz, gdzie można znaleźć ten adres URL, zobacz [sklonować istniejące repozytorium Git](/azure/devops/repos/git/clone).</span><span class="sxs-lookup"><span data-stu-id="89b2d-145">If you don't know where to find this URL, see [Clone an existing Git repo](/azure/devops/repos/git/clone).</span></span>
1. <span data-ttu-id="89b2d-146">Polecenia push Przenieś kod ze swojego lokalnego repozytorium do repozytorium programu TFS za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="89b2d-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="89b2d-147">Repozytorium TFS zostanie wypełniona przy użyciu kodu Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="89b2d-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="89b2d-148">W tym przykładzie użyto kod w `ci-cd-example` gałęzi repozytorium Git.</span><span class="sxs-lookup"><span data-stu-id="89b2d-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="89b2d-149">Pamiętaj określić tę gałąź jako domyślną gałąź w projekcie programu TFS, a dla wyzwalaczy CI/CD można utworzyć.</span><span class="sxs-lookup"><span data-stu-id="89b2d-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="89b2d-150">Znajomość kodu</span><span class="sxs-lookup"><span data-stu-id="89b2d-150">Understanding the code</span></span>

<span data-ttu-id="89b2d-151">Przed utworzeniem potoki kompilacji i wdrażania, Przyjrzyjmy się część kodu, aby zrozumieć, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="89b2d-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="89b2d-152">Na komputerze klienckim otwórz swoim ulubionym edytorze tekstów, a następnie przejdź do katalogu głównego repozytorium Demo_CI Git.</span><span class="sxs-lookup"><span data-stu-id="89b2d-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="89b2d-153">Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="89b2d-153">The DSC configuration</span></span>

<span data-ttu-id="89b2d-154">Otwórz plik `DNSServer.ps1` (z katalogu głównego lokalnego repozytorium Demo_CI `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="89b2d-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="89b2d-155">Ten plik zawiera konfigurację DSC, który konfiguruje serwer DNS.</span><span class="sxs-lookup"><span data-stu-id="89b2d-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="89b2d-156">W tym miejscu jest w całości:</span><span class="sxs-lookup"><span data-stu-id="89b2d-156">Here it is in its entirety:</span></span>

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

<span data-ttu-id="89b2d-157">Zwróć uwagę `Node` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="89b2d-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="89b2d-158">To znajdzie wszystkie węzły, które zostały zdefiniowane jako mające rolę `DNSServer` w [dane konfiguracyjne](../configurations/configData.md), który jest tworzony przez `DevEnv.ps1` skryptu.</span><span class="sxs-lookup"><span data-stu-id="89b2d-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](../configurations/configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="89b2d-159">Przeczytaj więcej o `Where` method in Class metoda [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="89b2d-159">You can read more about the `Where` method in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

<span data-ttu-id="89b2d-160">Ważne jest korzystanie z danych konfiguracji do definiowania węzły, podczas wykonywania ciągłej integracji, ponieważ informacje o węźle najprawdopodobniej ulegną zmianom między środowiskami i korzystanie z danych konfiguracji pozwala łatwo dokonać zmian bez konieczności zmieniania kodu konfiguracji informacje o węźle.</span><span class="sxs-lookup"><span data-stu-id="89b2d-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="89b2d-161">W pierwszym bloku zasobów, konfiguracji wywołuje **WindowsFeature** aby upewnić się, że włączona jest funkcja DNS.</span><span class="sxs-lookup"><span data-stu-id="89b2d-161">In the first resource block, the configuration calls the **WindowsFeature** to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="89b2d-162">Bloków zasobów, które należy wykonać wywołanie zasobów z [xDnsServer](https://github.com/PowerShell/xDnsServer) modułu do skonfigurowania podstawowej strefy i rekordy DNS.</span><span class="sxs-lookup"><span data-stu-id="89b2d-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="89b2d-163">Należy zauważyć, że dwa `xDnsRecord` bloki są opakowane w `foreach` pętli, które przechodzą przez tablice w danych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="89b2d-164">Ponownie, dane konfiguracji są tworzone przez `DevEnv.ps1` skryptu, który kolejności przyjrzymy się dalej.</span><span class="sxs-lookup"><span data-stu-id="89b2d-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="89b2d-165">Dane konfiguracji</span><span class="sxs-lookup"><span data-stu-id="89b2d-165">Configuration data</span></span>

<span data-ttu-id="89b2d-166">`DevEnv.ps1` Pliku (z katalogu głównego lokalnego repozytorium Demo_CI `./InfraDNS/DevEnv.ps1`) określa danych konfiguracyjnych środowisku w tablicy skrótów, a następnie przekazuje tej tablicy skrótów do wywołania `New-DscConfigurationDataDocument` funkcji, która jest zdefiniowana w `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="89b2d-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="89b2d-167">`DevEnv.ps1` Pliku:</span><span class="sxs-lookup"><span data-stu-id="89b2d-167">The `DevEnv.ps1` file:</span></span>

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

<span data-ttu-id="89b2d-168">`New-DscConfigurationDataDocument` — Funkcja (zdefiniowane w `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programowo tworzy dokument danych konfiguracji na podstawie hashtable (dane węzła) i tablicy (węzeł-danych), które są przekazywane jako `RawEnvData` i `OtherEnvData` parametrów.</span><span class="sxs-lookup"><span data-stu-id="89b2d-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="89b2d-169">W naszym przypadku tylko `RawEnvData` parametr jest używany.</span><span class="sxs-lookup"><span data-stu-id="89b2d-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="89b2d-170">Skrypt kompilacji psake</span><span class="sxs-lookup"><span data-stu-id="89b2d-170">The psake build script</span></span>

<span data-ttu-id="89b2d-171">[Psake](https://github.com/psake/psake) zdefiniowane w skrypcie kompilacji `Build.ps1` (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Build.ps1`) definiuje zadań, które są częścią kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="89b2d-172">Definiuje również inne zadania, które zależy od każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="89b2d-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="89b2d-173">Po wywołaniu skryptu psake zapewnia, że określonego zadania (lub zadania o nazwie `Default` Jeśli nie określono) działa i że wszystkie zależności również uruchomić (jest cykliczna, tak, aby uruchomić zależności zależności, i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="89b2d-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="89b2d-174">W tym przykładzie `Default` zadania jest zdefiniowany jako:</span><span class="sxs-lookup"><span data-stu-id="89b2d-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="89b2d-175">`Default` Zadanie nie ma implementacji sam, ale ma zależność od `CompileConfigs` zadania.</span><span class="sxs-lookup"><span data-stu-id="89b2d-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="89b2d-176">Wynikowy łańcuch zależności zadań podrzędnych gwarantuje, czy działają wszystkie zadania w skrypcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="89b2d-177">W tym przykładzie skrypt psake zostanie wywołana przez wywołanie `Invoke-PSake` w `Initiate.ps1` plik (znajdujący się w katalogu głównym repozytorium Demo_CI):</span><span class="sxs-lookup"><span data-stu-id="89b2d-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

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

<span data-ttu-id="89b2d-178">Podczas tworzenia definicji kompilacji w tym przykładzie w programie TFS, firma Microsoft będzie dostarczać naszym pliku skryptu psake jako `fileName` parametr tego skryptu.</span><span class="sxs-lookup"><span data-stu-id="89b2d-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="89b2d-179">Skrypt kompilacji definiuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="89b2d-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="89b2d-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="89b2d-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="89b2d-181">Przebiegi `DevEnv.ps1`, która generuje plik danych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="89b2d-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="89b2d-182">InstallModules</span></span>

<span data-ttu-id="89b2d-183">Instaluje moduły wymagane przez tę konfigurację `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="89b2d-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="89b2d-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="89b2d-184">ScriptAnalysis</span></span>

<span data-ttu-id="89b2d-185">Wywołania [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="89b2d-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="89b2d-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="89b2d-186">UnitTests</span></span>

<span data-ttu-id="89b2d-187">Przebiegi [usług Pester](https://github.com/pester/Pester/wiki) testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="89b2d-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="89b2d-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="89b2d-188">CompileConfigs</span></span>

<span data-ttu-id="89b2d-189">Kompiluje konfigurację (`DNSServer.ps1`) do pliku MOF przy użyciu danych konfiguracji, generowane przez `GenerateEnvironmentFiles` zadania.</span><span class="sxs-lookup"><span data-stu-id="89b2d-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="89b2d-190">Czyszczenie</span><span class="sxs-lookup"><span data-stu-id="89b2d-190">Clean</span></span>

<span data-ttu-id="89b2d-191">Tworzy foldery używane dla przykładu, a następnie usuwa wszystkie wyniki testów, pliki danych konfiguracji i modułów z poprzednich przebiegów.</span><span class="sxs-lookup"><span data-stu-id="89b2d-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="89b2d-192">Psake wdrożenia skryptu</span><span class="sxs-lookup"><span data-stu-id="89b2d-192">The psake deploy script</span></span>

<span data-ttu-id="89b2d-193">[Psake](https://github.com/psake/psake) skrypt wdrożenia zdefiniowany w `Deploy.ps1` (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Deploy.ps1`) definiuje zadania, które są wdrażanie i uruchamianie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="89b2d-194">`Deploy.ps1` definiuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="89b2d-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="89b2d-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="89b2d-195">DeployModules</span></span>

<span data-ttu-id="89b2d-196">Uruchamia sesję programu PowerShell na `TestAgent1` i instaluje moduły zawierające zasoby DSC, wymagane do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="89b2d-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="89b2d-197">DeployConfigs</span></span>

<span data-ttu-id="89b2d-198">Wywołania [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet, aby uruchomić konfigurację na `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="89b2d-198">Calls the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="89b2d-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="89b2d-199">IntegrationTests</span></span>

<span data-ttu-id="89b2d-200">Przebiegi [usług Pester](https://github.com/pester/Pester/wiki) testów integracji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="89b2d-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="89b2d-201">AcceptanceTests</span></span>

<span data-ttu-id="89b2d-202">Przebiegi [usług Pester](https://github.com/pester/Pester/wiki) testów akceptacyjnych.</span><span class="sxs-lookup"><span data-stu-id="89b2d-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="89b2d-203">Czyszczenie</span><span class="sxs-lookup"><span data-stu-id="89b2d-203">Clean</span></span>

<span data-ttu-id="89b2d-204">Usuwa wszystkie moduły zainstalowane w poprzednich przebiegów i gwarantuje, że istnieje folder wynik testu.</span><span class="sxs-lookup"><span data-stu-id="89b2d-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="89b2d-205">Testowanie skryptów</span><span class="sxs-lookup"><span data-stu-id="89b2d-205">Test scripts</span></span>

<span data-ttu-id="89b2d-206">Akceptacji, integracja i testy jednostkowe są zdefiniowane w skryptach w `Tests` folderu (z katalogu głównego repozytorium Demo_CI `./InfraDNS/Tests`), każde WE plików o nazwie `DNSServer.tests.ps1` w ich odpowiednich folderów.</span><span class="sxs-lookup"><span data-stu-id="89b2d-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="89b2d-207">Test skrypty użyj [usług Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.</span><span class="sxs-lookup"><span data-stu-id="89b2d-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="89b2d-208">Testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="89b2d-208">Unit tests</span></span>

<span data-ttu-id="89b2d-209">Konfiguracje testowe DSC, samodzielnie, aby upewnić się, konfiguracje będzie wykonywał, czego oczekuje się, gdy uruchamiają oni testy jednostek.</span><span class="sxs-lookup"><span data-stu-id="89b2d-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="89b2d-210">Skrypt używa testów jednostkowych [usług Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="89b2d-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="89b2d-211">Testy integracji</span><span class="sxs-lookup"><span data-stu-id="89b2d-211">Integration tests</span></span>

<span data-ttu-id="89b2d-212">Testy integracji testu konfiguracji systemu, aby upewnić się, że gdy zintegrowana z innymi składnikami, system jest skonfigurowany zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="89b2d-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="89b2d-213">Te testy w docelowym węźle po został skonfigurowany za pomocą DSC.</span><span class="sxs-lookup"><span data-stu-id="89b2d-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="89b2d-214">Skrypt testu integracji używa kombinacji [usług Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.</span><span class="sxs-lookup"><span data-stu-id="89b2d-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="89b2d-215">Testy odbiorcze</span><span class="sxs-lookup"><span data-stu-id="89b2d-215">Acceptance tests</span></span>

<span data-ttu-id="89b2d-216">Testy odbiorcze przetestowanie systemu, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="89b2d-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="89b2d-217">Na przykład sprawdza, aby upewnić się, że strony sieci web zwraca potrzebnych informacji po otrzymaniu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="89b2d-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="89b2d-218">Te testy zdalnie korzystać z węzła docelowego w celu przetestowania scenariusze ze świata rzeczywistego.</span><span class="sxs-lookup"><span data-stu-id="89b2d-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="89b2d-219">Skrypt testu integracji używa kombinacji [usług Pester](https://github.com/pester/Pester/wiki) i [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) składni.</span><span class="sxs-lookup"><span data-stu-id="89b2d-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="89b2d-220">Definiowanie kompilacji</span><span class="sxs-lookup"><span data-stu-id="89b2d-220">Define the build</span></span>

<span data-ttu-id="89b2d-221">Teraz, gdy firma Microsoft przekazaniu nasz kod programem TFS i przyjrzano się, jak działa czynnością jest zdefiniowanie naszych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="89b2d-222">W tym miejscu omówimy kroki kompilacji, które należy dodać do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="89b2d-223">Aby uzyskać instrukcje dotyczące sposobu tworzenia definicji kompilacji w programie TFS, zobacz [Utwórz i kolejki definicję kompilacji](/azure/devops/pipelines/get-started-designer).</span><span class="sxs-lookup"><span data-stu-id="89b2d-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](/azure/devops/pipelines/get-started-designer).</span></span>

<span data-ttu-id="89b2d-224">Utwórz nową definicję kompilacji (wybierz **pusty** szablonu) o nazwie "InfraDNS".</span><span class="sxs-lookup"><span data-stu-id="89b2d-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="89b2d-225">Dodaj poniższe kroki, aby użytkownik definicja kompilacji:</span><span class="sxs-lookup"><span data-stu-id="89b2d-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="89b2d-226">Skrypt programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="89b2d-226">PowerShell Script</span></span>
- <span data-ttu-id="89b2d-227">Publikuj wyniki testu</span><span class="sxs-lookup"><span data-stu-id="89b2d-227">Publish Test Results</span></span>
- <span data-ttu-id="89b2d-228">Kopiowanie plików</span><span class="sxs-lookup"><span data-stu-id="89b2d-228">Copy Files</span></span>
- <span data-ttu-id="89b2d-229">Publikowanie artefaktów</span><span class="sxs-lookup"><span data-stu-id="89b2d-229">Publish Artifact</span></span>

<span data-ttu-id="89b2d-230">Po dodaniu tych kroków kompilacji, Edytuj właściwości każdego kroku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="89b2d-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="89b2d-231">Skrypt programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="89b2d-231">PowerShell Script</span></span>

1. <span data-ttu-id="89b2d-232">Ustaw **typu** właściwość `File Path`.</span><span class="sxs-lookup"><span data-stu-id="89b2d-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="89b2d-233">Ustaw **ścieżka skryptu** właściwość `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="89b2d-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="89b2d-234">Dodaj `-fileName build` do **argumenty** właściwości.</span><span class="sxs-lookup"><span data-stu-id="89b2d-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="89b2d-235">Ten krok kompilacji działa `initiate.ps1` pliku, który wywołuje skrypt kompilacji psake.</span><span class="sxs-lookup"><span data-stu-id="89b2d-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="89b2d-236">Publikuj wyniki testu</span><span class="sxs-lookup"><span data-stu-id="89b2d-236">Publish Test Results</span></span>

1. <span data-ttu-id="89b2d-237">Ustaw **Format wyniku testu** do `NUnit`</span><span class="sxs-lookup"><span data-stu-id="89b2d-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="89b2d-238">Ustaw **plików z wynikami testów** do `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="89b2d-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="89b2d-239">Ustaw **tytuł przebiegu testu** do `Unit`.</span><span class="sxs-lookup"><span data-stu-id="89b2d-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="89b2d-240">Upewnij się, że **opcje sterowania** **włączone** i **są zawsze uruchamiane** są zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="89b2d-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="89b2d-241">Ten krok kompilacji, uruchamia testy jednostkowe w skrypcie usług Pester przyjrzeliśmy się wcześniej i zapisuje wyniki w `InfraDNS/Tests/Results/*.xml` folderu.</span><span class="sxs-lookup"><span data-stu-id="89b2d-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="89b2d-242">Kopiowanie plików</span><span class="sxs-lookup"><span data-stu-id="89b2d-242">Copy Files</span></span>

1. <span data-ttu-id="89b2d-243">Dodaj wszystkie następujące wiersze do **zawartość**:</span><span class="sxs-lookup"><span data-stu-id="89b2d-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="89b2d-244">Ustaw **TargetFolder** do `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="89b2d-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="89b2d-245">W tym kroku kopiuje kompilacji i test skrypty w katalogu przemieszczania tak, mogą być publikowane jako artefaktów kompilacji w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="89b2d-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="89b2d-246">Publikowanie artefaktów</span><span class="sxs-lookup"><span data-stu-id="89b2d-246">Publish Artifact</span></span>

1. <span data-ttu-id="89b2d-247">Ustaw **ścieżka do publikowania** do `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="89b2d-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="89b2d-248">Ustaw **nazwa artefaktu** do `Deploy`</span><span class="sxs-lookup"><span data-stu-id="89b2d-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="89b2d-249">Ustaw **typ artefaktu** do `Server`</span><span class="sxs-lookup"><span data-stu-id="89b2d-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="89b2d-250">Wybierz `Enabled` w **opcje kontroli**</span><span class="sxs-lookup"><span data-stu-id="89b2d-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="89b2d-251">Włącz ciągłą integrację</span><span class="sxs-lookup"><span data-stu-id="89b2d-251">Enable continuous integration</span></span>

<span data-ttu-id="89b2d-252">Teraz możemy skonfigurować wyzwalacz, który powoduje, że projekt do tworzenia w dowolnym momencie celu ewidencjonowana jest zmiana `ci-cd-example` gałęzi repozytorium git.</span><span class="sxs-lookup"><span data-stu-id="89b2d-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="89b2d-253">W programie TFS, kliknij przycisk **kompilowanie i wydawanie** kartę</span><span class="sxs-lookup"><span data-stu-id="89b2d-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="89b2d-254">Wybierz `DNS Infra` definicji kompilacji, a następnie kliknij przycisk **edycji**</span><span class="sxs-lookup"><span data-stu-id="89b2d-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="89b2d-255">Kliknij przycisk **wyzwalaczy** kartę</span><span class="sxs-lookup"><span data-stu-id="89b2d-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="89b2d-256">Wybierz **ciągłej integracji (CI)** i wybierz `refs/heads/ci-cd-example` na liście rozwijanej gałęzi</span><span class="sxs-lookup"><span data-stu-id="89b2d-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="89b2d-257">Kliknij przycisk **Zapisz** i następnie **OK**</span><span class="sxs-lookup"><span data-stu-id="89b2d-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="89b2d-258">Obecnie każda zmiana wyzwalacze repozytorium usługi git w programie TFS zautomatyzowanej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="89b2d-259">Tworzenie definicji wydania</span><span class="sxs-lookup"><span data-stu-id="89b2d-259">Create the release definition</span></span>

<span data-ttu-id="89b2d-260">Utwórzmy definicji wydania, tak aby projekt został wdrożony do środowiska deweloperskiego przy każdym zaewidencjonowaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="89b2d-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="89b2d-261">Aby to zrobić, Dodaj nowe definicja wydania skojarzona z `InfraDNS` wcześniej utworzoną definicję kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="89b2d-262">Pamiętaj o wybraniu **ciągłe wdrażanie** tak, aby nowe wydanie zostaną wyzwolone za każdym zakończeniu nowej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="89b2d-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="89b2d-263">([Jak: Praca z definicji wersji](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) i skonfiguruj ją w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="89b2d-263">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="89b2d-264">Z definicją wydania, należy dodać następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="89b2d-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="89b2d-265">Skrypt programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="89b2d-265">PowerShell Script</span></span>
- <span data-ttu-id="89b2d-266">Publikuj wyniki testu</span><span class="sxs-lookup"><span data-stu-id="89b2d-266">Publish Test Results</span></span>
- <span data-ttu-id="89b2d-267">Publikuj wyniki testu</span><span class="sxs-lookup"><span data-stu-id="89b2d-267">Publish Test Results</span></span>

<span data-ttu-id="89b2d-268">Edytuj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="89b2d-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="89b2d-269">Skrypt programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="89b2d-269">PowerShell Script</span></span>

1. <span data-ttu-id="89b2d-270">Ustaw **ścieżka skryptu** pole `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="89b2d-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="89b2d-271">Ustaw **argumenty** pole `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="89b2d-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="89b2d-272">Najpierw opublikować wyniki testu</span><span class="sxs-lookup"><span data-stu-id="89b2d-272">First Publish Test Results</span></span>

1. <span data-ttu-id="89b2d-273">Wybierz `NUnit` dla **Format wyniku testu** pola</span><span class="sxs-lookup"><span data-stu-id="89b2d-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="89b2d-274">Ustaw **pliki wyników testu** pole `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="89b2d-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="89b2d-275">Ustaw **tytuł przebiegu testu** do `Integration`</span><span class="sxs-lookup"><span data-stu-id="89b2d-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="89b2d-276">W obszarze **opcje sterowania**, sprawdź **są zawsze uruchamiane**</span><span class="sxs-lookup"><span data-stu-id="89b2d-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="89b2d-277">Po drugie opublikować wyniki testu</span><span class="sxs-lookup"><span data-stu-id="89b2d-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="89b2d-278">Wybierz `NUnit` dla **Format wyniku testu** pola</span><span class="sxs-lookup"><span data-stu-id="89b2d-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="89b2d-279">Ustaw **pliki wyników testu** pole `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="89b2d-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="89b2d-280">Ustaw **tytuł przebiegu testu** do `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="89b2d-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="89b2d-281">W obszarze **opcje sterowania**, sprawdź **są zawsze uruchamiane**</span><span class="sxs-lookup"><span data-stu-id="89b2d-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="89b2d-282">Sprawdź wyniki</span><span class="sxs-lookup"><span data-stu-id="89b2d-282">Verify your results</span></span>

<span data-ttu-id="89b2d-283">Teraz, ilekroć możesz wypychać zmiany `ci-cd-example` gałąź do TFS, nowa kompilacja zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="89b2d-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="89b2d-284">Jeśli kompilacja zakończy się pomyślnie, zostanie wywołany nowego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="89b2d-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="89b2d-285">Wynik wdrożenia można sprawdzić, otwierając przeglądarki na komputerze klienckim i przechodząc do `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="89b2d-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="89b2d-286">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="89b2d-286">Next steps</span></span>

<span data-ttu-id="89b2d-287">Ten przykład umożliwia skonfigurowanie serwera DNS `TestAgent1` tak, aby adres URL `www.contoso.com` jest rozpoznawana jako `TestAgent2`, ale nie wdrażają faktycznie witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="89b2d-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="89b2d-288">Szkielet, aby to zrobić, znajduje się w repozytorium, w obszarze `WebApp` folderu.</span><span class="sxs-lookup"><span data-stu-id="89b2d-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="89b2d-289">Wycinki kodu, aby utworzyć skrypty psake, testy usług Pester i konfiguracje DSC umożliwia wdrażanie własnych witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="89b2d-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>
