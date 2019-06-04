---
ms.date: 01/17/2019
keywords: DSC, powershell, konfiguracja, ustawienia
title: Ponowny rozruch węzła
ms.openlocfilehash: 106fa1e7b0e3aaf3070ec05548d51140fe9a7725
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470747"
---
# <a name="reboot-a-node"></a><span data-ttu-id="2125a-103">Ponowny rozruch węzła</span><span class="sxs-lookup"><span data-stu-id="2125a-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="2125a-104">W tym temacie opowiada, jak wykonać ponowny rozruch węzła.</span><span class="sxs-lookup"><span data-stu-id="2125a-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="2125a-105">Aby ponowne uruchomienie w celu pomyślnego **ActionAfterReboot** i **RebootNodeIfNeeded** LCM ustawienia muszą być prawidłowo skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="2125a-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="2125a-106">Aby uzyskać informacje o ustawieniach Local Configuration Manager, zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md), lub [Konfigurowanie programu Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="2125a-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="2125a-107">Węzły mogą być uruchamiane z w ramach zasobu, używając `$global:DSCMachineStatus` flagi.</span><span class="sxs-lookup"><span data-stu-id="2125a-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="2125a-108">Ustawienie tej flagi `1` w `Set-TargetResource` funkcja wymusza LCM wykonać ponowny rozruch węzła, bezpośrednio po **ustaw** metoda bieżącego zasobu.</span><span class="sxs-lookup"><span data-stu-id="2125a-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="2125a-109">Przy użyciu tej flagi **xPendingReboot** zasobów wykrywa, jeśli trwa oczekiwanie na ponowne poza DSC.</span><span class="sxs-lookup"><span data-stu-id="2125a-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="2125a-110">Twoje [konfiguracje](configurations.md) może wykonywać czynności, które wymagają węzłów o ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="2125a-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="2125a-111">Może to obejmować rzeczy, takich jak:</span><span class="sxs-lookup"><span data-stu-id="2125a-111">This could include things such as:</span></span>

- <span data-ttu-id="2125a-112">Aktualizacje Windows</span><span class="sxs-lookup"><span data-stu-id="2125a-112">Windows updates</span></span>
- <span data-ttu-id="2125a-113">Instalacja oprogramowania</span><span class="sxs-lookup"><span data-stu-id="2125a-113">Software install</span></span>
- <span data-ttu-id="2125a-114">Zmienia nazwę pliku</span><span class="sxs-lookup"><span data-stu-id="2125a-114">File renames</span></span>
- <span data-ttu-id="2125a-115">Zmiana nazwy komputera</span><span class="sxs-lookup"><span data-stu-id="2125a-115">Computer rename</span></span>

<span data-ttu-id="2125a-116">**XPendingReboot** zasobów sprawdza, czy określony komputer lokalizacje, aby określić, jeśli trwa oczekiwanie na ponowne.</span><span class="sxs-lookup"><span data-stu-id="2125a-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="2125a-117">Jeśli węzeł wymaga ponownego uruchomienia systemu poza DSC, **xPendingReboot** zestawów zasobów `$global:DSCMachineStatus` flaga `1` wymuszenie ponownego uruchomienia systemu i rozwiązywania oczekujące warunku.</span><span class="sxs-lookup"><span data-stu-id="2125a-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="2125a-118">Dowolny zasób DSC można nakazać LCM wykonać ponowny rozruch węzła przez ustawienie tej flagi `Set-TargetResource` funkcji.</span><span class="sxs-lookup"><span data-stu-id="2125a-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="2125a-119">Aby uzyskać więcej informacji, zobacz [pisanie zasobu DSC niestandardowych z pliku MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="2125a-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="2125a-120">Składnia</span><span class="sxs-lookup"><span data-stu-id="2125a-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="2125a-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2125a-121">Properties</span></span>

| <span data-ttu-id="2125a-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="2125a-122">Property</span></span> | <span data-ttu-id="2125a-123">Opis</span><span class="sxs-lookup"><span data-stu-id="2125a-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2125a-124">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2125a-124">Name</span></span>| <span data-ttu-id="2125a-125">Wymagany parametr, który musi być unikatowy dla każdego wystąpienia zasobów w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2125a-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="2125a-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="2125a-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="2125a-127">Pomiń ponowne uruchamianie wyzwalane przez składnik oparty na komponentach obsługi.</span><span class="sxs-lookup"><span data-stu-id="2125a-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="2125a-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="2125a-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="2125a-129">Pomiń ponowne uruchamianie wyzwalane przez usługę Windows Update.</span><span class="sxs-lookup"><span data-stu-id="2125a-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="2125a-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="2125a-130">SkipPendingFileRename</span></span> | <span data-ttu-id="2125a-131">Pomiń plik oczekujące zmiany nazwy jest uruchamiany ponownie.</span><span class="sxs-lookup"><span data-stu-id="2125a-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="2125a-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="2125a-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="2125a-133">Pomiń ponowne uruchamianie wyzwalane przez klienta programu ConfigMgr.</span><span class="sxs-lookup"><span data-stu-id="2125a-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="2125a-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="2125a-134">SkipComputerRename</span></span> | <span data-ttu-id="2125a-135">Pomiń ponowne uruchamianie wyzwalane przez zmienia nazwę komputera.</span><span class="sxs-lookup"><span data-stu-id="2125a-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="2125a-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="2125a-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="2125a-137">Obsługiwane w wersji 5.</span><span class="sxs-lookup"><span data-stu-id="2125a-137">Supported in v5.</span></span> <span data-ttu-id="2125a-138">Wykonuje zasobu jako określony użytkownik.</span><span class="sxs-lookup"><span data-stu-id="2125a-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="2125a-139">dependsOn</span><span class="sxs-lookup"><span data-stu-id="2125a-139">DependsOn</span></span> | <span data-ttu-id="2125a-140">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="2125a-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2125a-141">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2125a-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="2125a-142">Aby uzyskać więcej informacji, zobacz [DependsOn przy użyciu](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="2125a-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="2125a-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="2125a-143">Example</span></span>

<span data-ttu-id="2125a-144">W poniższym przykładzie instalowana za pomocą programu Microsoft Exchange [xExchange](https://github.com/PowerShell/xExchange) zasobów.</span><span class="sxs-lookup"><span data-stu-id="2125a-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="2125a-145">W całej instalacji **xPendingReboot** zasób służy do ponownego rozruchu węzła.</span><span class="sxs-lookup"><span data-stu-id="2125a-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="2125a-146">W tym przykładzie wymaga poświadczeń konta które ma prawa do dodawania serwera Exchange w lesie.</span><span class="sxs-lookup"><span data-stu-id="2125a-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="2125a-147">Aby uzyskać więcej informacji na temat korzystania z poświadczeń w DSC, zobacz [obsługi poświadczeń w DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="2125a-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="2125a-148">W przykładzie założono, że skonfigurowano usługi Local Configuration Manager, aby zezwolić na ponowne uruchamianie i kontynuować konfigurację po ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="2125a-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="2125a-149">Gdzie można pobrać</span><span class="sxs-lookup"><span data-stu-id="2125a-149">Where to Download</span></span>

<span data-ttu-id="2125a-150">Możesz pobrać zasoby używane w tym temacie w następujących lokalizacjach lub za pomocą galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2125a-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="2125a-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="2125a-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="2125a-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="2125a-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
