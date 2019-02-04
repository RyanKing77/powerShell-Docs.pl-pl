---
ms.date: 1/17/2019
keywords: DSC, powershell, konfiguracja, ustawienia
title: Ponowny rozruch węzła
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685690"
---
# <a name="reboot-a-node"></a><span data-ttu-id="f7148-103">Ponowny rozruch węzła</span><span class="sxs-lookup"><span data-stu-id="f7148-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="f7148-104">W tym temacie opowiada, jak wykonać ponowny rozruch węzła.</span><span class="sxs-lookup"><span data-stu-id="f7148-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="f7148-105">Aby ponowne uruchomienie w celu pomyślnego **ActionAfterReboot** i **RebootNodeIfNeeded** LCM ustawienia muszą być prawidłowo skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="f7148-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="f7148-106">Aby uzyskać informacje o ustawieniach Local Configuration Manager, zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md), lub [Konfigurowanie programu Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="f7148-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="f7148-107">Węzły mogą być uruchamiane z w ramach zasobu, używając `$global:DSCMachineStatus` flagi.</span><span class="sxs-lookup"><span data-stu-id="f7148-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="f7148-108">Ustawienie tej flagi `1` w `Set-TargetResource` funkcja wymusza LCM wykonać ponowny rozruch węzła, bezpośrednio po **ustaw** metoda bieżącego zasobu.</span><span class="sxs-lookup"><span data-stu-id="f7148-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="f7148-109">Przy użyciu tej flagi **xPendingReboot** zasobów wykrywa, jeśli trwa oczekiwanie na ponowne poza DSC.</span><span class="sxs-lookup"><span data-stu-id="f7148-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="f7148-110">Twoje [konfiguracje](configurations.md) może wykonywać czynności, które wymagają węzłów o ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="f7148-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="f7148-111">Może to obejmować rzeczy, takich jak:</span><span class="sxs-lookup"><span data-stu-id="f7148-111">This could include things such as:</span></span>

- <span data-ttu-id="f7148-112">Aktualizacje Windows</span><span class="sxs-lookup"><span data-stu-id="f7148-112">Windows updates</span></span>
- <span data-ttu-id="f7148-113">Instalacja oprogramowania</span><span class="sxs-lookup"><span data-stu-id="f7148-113">Software install</span></span>
- <span data-ttu-id="f7148-114">Zmienia nazwę pliku</span><span class="sxs-lookup"><span data-stu-id="f7148-114">File renames</span></span>
- <span data-ttu-id="f7148-115">Zmiana nazwy komputera</span><span class="sxs-lookup"><span data-stu-id="f7148-115">Computer rename</span></span>

<span data-ttu-id="f7148-116">**XPendingReboot** zasobów sprawdza, czy określony komputer lokalizacje, aby określić, jeśli trwa oczekiwanie na ponowne.</span><span class="sxs-lookup"><span data-stu-id="f7148-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="f7148-117">Jeśli węzeł wymaga ponownego uruchomienia systemu poza DSC, **xPendingReboot** zestawów zasobów `$global:DSCMachineStatus` flaga `1` wymuszenie ponownego uruchomienia systemu i rozwiązywania oczekujące warunku.</span><span class="sxs-lookup"><span data-stu-id="f7148-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="f7148-118">Dowolny zasób DSC można nakazać LCM wykonać ponowny rozruch węzła przez ustawienie tej flagi `Set-TargetResource` funkcji.</span><span class="sxs-lookup"><span data-stu-id="f7148-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="f7148-119">Aby uzyskać więcej informacji, zobacz [pisanie zasobu DSC niestandardowych z pliku MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="f7148-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="f7148-120">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7148-120">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f7148-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f7148-121">Properties</span></span>

| <span data-ttu-id="f7148-122">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f7148-122">Property</span></span> | <span data-ttu-id="f7148-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f7148-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="f7148-124">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f7148-124">Name</span></span>| <span data-ttu-id="f7148-125">Wymagany parametr, który musi być unikatowy dla każdego wystąpienia zasobów w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f7148-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="f7148-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="f7148-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="f7148-127">Pomiń ponowne uruchamianie wyzwalane przez składnik oparty na komponentach obsługi.</span><span class="sxs-lookup"><span data-stu-id="f7148-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="f7148-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="f7148-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="f7148-129">Pomiń ponowne uruchamianie wyzwalane przez usługę Windows Update.</span><span class="sxs-lookup"><span data-stu-id="f7148-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="f7148-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="f7148-130">SkipPendingFileRename</span></span> | <span data-ttu-id="f7148-131">Pomiń plik oczekujące zmiany nazwy jest uruchamiany ponownie.</span><span class="sxs-lookup"><span data-stu-id="f7148-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="f7148-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="f7148-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="f7148-133">Pomiń ponowne uruchamianie wyzwalane przez klienta programu ConfigMgr.</span><span class="sxs-lookup"><span data-stu-id="f7148-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="f7148-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="f7148-134">SkipComputerRename</span></span> | <span data-ttu-id="f7148-135">Pomiń ponowny rozruch wyzwolone przez zmienia nazwę komputera.</span><span class="sxs-lookup"><span data-stu-id="f7148-135">Skip reboots triggerd by Computer renames.</span></span> |
| <span data-ttu-id="f7148-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f7148-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="f7148-137">Obsługiwane w wersji 5.</span><span class="sxs-lookup"><span data-stu-id="f7148-137">Supported in v5.</span></span> <span data-ttu-id="f7148-138">Wykonuje zasobu jako określony użytkownik.</span><span class="sxs-lookup"><span data-stu-id="f7148-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="f7148-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f7148-139">DependsOn</span></span> | <span data-ttu-id="f7148-140">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="f7148-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f7148-141">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f7148-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="f7148-142">Aby uzyskać więcej informacji, zobacz [DependsOn przy użyciu](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="f7148-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="f7148-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7148-143">Example</span></span>

<span data-ttu-id="f7148-144">W poniższym przykładzie instalowana za pomocą programu Microsoft Exchange [xExchange](https://github.com/PowerShell/xExchange) zasobów.</span><span class="sxs-lookup"><span data-stu-id="f7148-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="f7148-145">W całej instalacji **xPendingReboot** zasób służy do ponownego rozruchu węzła.</span><span class="sxs-lookup"><span data-stu-id="f7148-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="f7148-146">W tym przykładzie wymaga poświadczeń konta które ma prawa do dodawania serwera Exchange w lesie.</span><span class="sxs-lookup"><span data-stu-id="f7148-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="f7148-147">Aby uzyskać więcej informacji na temat korzystania z poświadczeń w DSC, zobacz [obsługi poświadczeń w DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="f7148-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
> <span data-ttu-id="f7148-148">W przykładzie założono, że skonfigurowano usługi Local Configuration Manager, aby zezwolić na ponowne uruchamianie i kontynuować konfigurację po ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="f7148-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="f7148-149">Gdzie można pobrać</span><span class="sxs-lookup"><span data-stu-id="f7148-149">Where to Download</span></span>

<span data-ttu-id="f7148-150">Możesz pobrać zasoby używane w tym temacie w następujących lokalizacjach lub za pomocą galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7148-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="f7148-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="f7148-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="f7148-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="f7148-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
