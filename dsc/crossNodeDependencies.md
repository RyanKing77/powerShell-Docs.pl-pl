---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Określenie zależności między węzłami"
ms.openlocfilehash: 885c130fb050629aac4c072e18a147d77b9deb8f
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="22eaf-103">Określenie zależności między węzłami</span><span class="sxs-lookup"><span data-stu-id="22eaf-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="22eaf-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="22eaf-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="22eaf-105">DSC zawiera specjalne zasoby **WaitForAll**, **WaitForAny**, i **WaitForSome** który można określić zależności na konfiguracji na innych w konfiguracji węzły.</span><span class="sxs-lookup"><span data-stu-id="22eaf-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="22eaf-106">Zachowanie tych zasobów jest następujący:</span><span class="sxs-lookup"><span data-stu-id="22eaf-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="22eaf-107">**WaitForAll**: zakończy się pomyślnie, jeśli określony zasób jest w żądanym stanie na wszystkich węzłach docelowych określonych w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="22eaf-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="22eaf-108">**WaitForAny**: zakończy się pomyślnie, jeśli określony zasób jest w żądanym stanie na co najmniej jednym z węzłów docelowych określonych w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="22eaf-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="22eaf-109">**WaitForSome**: Określa **NodeCount** właściwość oprócz **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="22eaf-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="22eaf-110">Zasób zakończy się pomyślnie, jeśli zasób jest w żądanym stanie na minimalna liczba węzłów (określonego przez **NodeCount**) określone przez **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="22eaf-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="22eaf-111">Korzystanie z zasobów WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="22eaf-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="22eaf-112">Aby użyć **WaitForXXXX** zasoby, utworzyć bloku zasobu tego typu zasobu, które określa DSC zasobów i węzłów oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="22eaf-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="22eaf-113">Następnie należy użyć **DependsOn** blokuje właściwość w innych zasobów w konfiguracji, aby czekać na warunki określone w **WaitForXXXX** węzła powiodło się.</span><span class="sxs-lookup"><span data-stu-id="22eaf-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="22eaf-114">Na przykład, w następującej konfiguracji węzła docelowego oczekuje na **xADDomain** zasobów do zakończenia **Kontroler_domeny** węzeł z maksymalnie 30 ponownych prób, na 15 sekund, zanim węzeł docelowy można przyłączyć do domeny.</span><span class="sxs-lookup"><span data-stu-id="22eaf-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

><span data-ttu-id="22eaf-115">**Uwaga:** domyślnie WaitForXXX zasobów spróbuj jeden raz, a następnie kończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="22eaf-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="22eaf-116">Chociaż nie jest wymagana, zwykle można określić interwał ponawiania prób i liczba.</span><span class="sxs-lookup"><span data-stu-id="22eaf-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="22eaf-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22eaf-117">See Also</span></span>
* [<span data-ttu-id="22eaf-118">Konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="22eaf-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="22eaf-119">Zasoby usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="22eaf-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="22eaf-120">Konfigurowanie lokalny program Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="22eaf-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

