---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Określanie zależności między węzłami
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734673"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="ead87-103">Określanie zależności między węzłami</span><span class="sxs-lookup"><span data-stu-id="ead87-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="ead87-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ead87-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ead87-105">DSC udostępnia specjalne zasoby **WaitForAll**, **WaitForAny**, i **WaitForSome** który może służyć w konfiguracji do określania zależności w konfiguracji na innych węzły.</span><span class="sxs-lookup"><span data-stu-id="ead87-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="ead87-106">Zachowanie tych zasobów jest następująca:</span><span class="sxs-lookup"><span data-stu-id="ead87-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="ead87-107">**WaitForAll**: Powiedzie się, jeśli określony zasób jest w żądanym stanie na wszystkich węzłach docelowych określonych w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="ead87-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="ead87-108">**WaitForAny**: Powiedzie się, jeśli określony zasób jest w żądanym stanie na co najmniej jednym z węzłów docelowych określonych w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="ead87-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="ead87-109">**WaitForSome**: Określa **NodeCount** właściwość oprócz **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="ead87-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="ead87-110">Zasób zakończy się pomyślnie, jeśli zasób jest w żądanym stanie na minimalna liczba węzłów (określony przez **NodeCount**) zdefiniowane przez **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="ead87-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="ead87-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ead87-111">Syntax</span></span>

<span data-ttu-id="ead87-112">**WaitForAll** i **WaitForAny** zasoby udostępnionej w tej samej składni.</span><span class="sxs-lookup"><span data-stu-id="ead87-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="ead87-113">Zastąp \<ResourceType\> w poniższym przykładzie z oboma **WaitForAny** lub **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="ead87-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="ead87-114">Podobnie jak **DependsOn** — słowo kluczowe, konieczne będzie format nazwy, jako "ResourceName [ResourceType]".</span><span class="sxs-lookup"><span data-stu-id="ead87-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="ead87-115">Jeśli zasób należy do osobnego [konfiguracji](configurations.md), obejmują **ConfigurationName** w sformatowanym ciągu "ResourceName [ResourceType]:: [ConfigurationName]:: [ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="ead87-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="ead87-116">**NodeName** jest komputer lub węzła, w którym powinien zaczekać na bieżącego zasobu.</span><span class="sxs-lookup"><span data-stu-id="ead87-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="ead87-117">**WaitForSome** zasobu ma składnię podobny do powyższego przykładu, ale dodaje **NodeCount** klucza.</span><span class="sxs-lookup"><span data-stu-id="ead87-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="ead87-118">**NodeCount** wskazuje, ilu węzłów bieżącego zasobu ma oczekiwać na.</span><span class="sxs-lookup"><span data-stu-id="ead87-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

<span data-ttu-id="ead87-119">Wszystkie **WaitForXXXX** udostępnianie następujące klucze składni.</span><span class="sxs-lookup"><span data-stu-id="ead87-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="ead87-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ead87-120">Property</span></span>|  <span data-ttu-id="ead87-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ead87-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="ead87-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="ead87-122">RetryIntervalSec</span></span>| <span data-ttu-id="ead87-123">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="ead87-123">The number of seconds before retrying.</span></span> <span data-ttu-id="ead87-124">Minimalny to 1.</span><span class="sxs-lookup"><span data-stu-id="ead87-124">Minimum is 1.</span></span>|
| <span data-ttu-id="ead87-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="ead87-125">RetryCount</span></span>| <span data-ttu-id="ead87-126">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="ead87-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="ead87-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ead87-127">ThrottleLimit</span></span>| <span data-ttu-id="ead87-128">Liczba maszyn do łączenia z jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="ead87-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ead87-129">Wartość domyślna to `New-CimSession` domyślne.</span><span class="sxs-lookup"><span data-stu-id="ead87-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="ead87-130">dependsOn</span><span class="sxs-lookup"><span data-stu-id="ead87-130">DependsOn</span></span> | <span data-ttu-id="ead87-131">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="ead87-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ead87-132">Aby uzyskać więcej informacji, zobacz [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="ead87-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="ead87-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ead87-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="ead87-134">Zobacz [DSC przy użyciu poświadczeń użytkownika](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="ead87-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="ead87-135">Korzystanie z zasobów WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="ead87-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="ead87-136">Każdy **WaitForXXXX** zasobów czeka, aż określone zasoby zakończyć w określonym węźle.</span><span class="sxs-lookup"><span data-stu-id="ead87-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="ead87-137">Inne zasoby w tej samej konfiguracji można następnie *zależą od* **WaitForXXXX** zasobów przy użyciu **DependsOn** klucza.</span><span class="sxs-lookup"><span data-stu-id="ead87-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="ead87-138">Na przykład w następującej konfiguracji węzła docelowego oczekuje na **xADDomain** zasobów, aby zdążyć na **Kontroler_domeny** węzły maksymalną liczbą 30 ponawia próbę, w 15-sekundowych odstępach czasu, zanim węzeł docelowy mogą dołączyć do domeny.</span><span class="sxs-lookup"><span data-stu-id="ead87-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="ead87-139">Domyślnie **WaitForXXX** zasobów spróbuj jeden raz, a następnie zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ead87-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="ead87-140">Chociaż nie jest wymagane, będzie zazwyczaj chcesz określić **RetryCount** i **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="ead87-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="ead87-141">Podczas kompilowania konfiguracji są generowane dwa pliki "MOF".</span><span class="sxs-lookup"><span data-stu-id="ead87-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="ead87-142">Dotyczy zarówno pliki "MOF" węzłów docelowych przy użyciu [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="ead87-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="ead87-143">**WaitForXXX** zasobów Użyj Windows Remote Management, aby sprawdzić stan innych węzłów.</span><span class="sxs-lookup"><span data-stu-id="ead87-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="ead87-144">Aby uzyskać więcej informacji na temat wymagania dotyczące portów i zabezpieczeń dla usługi WinRM, zobacz [zagadnienia dotyczące zabezpieczeń komunikacji zdalnej programu PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="ead87-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="ead87-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ead87-145">See Also</span></span>

- [<span data-ttu-id="ead87-146">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="ead87-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="ead87-147">Użyj zależności zasobów</span><span class="sxs-lookup"><span data-stu-id="ead87-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="ead87-148">Zasoby DSC</span><span class="sxs-lookup"><span data-stu-id="ead87-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="ead87-149">Konfigurowanie programu Local Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="ead87-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
