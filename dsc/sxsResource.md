---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Korzystanie z zasobów z wieloma wersjami
ms.openlocfilehash: 6400d6506106657ba28fa1f9c83d9f8ee1c93ba3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187014"
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="6db72-103">Korzystanie z zasobów z wieloma wersjami</span><span class="sxs-lookup"><span data-stu-id="6db72-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="6db72-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6db72-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6db72-105">W programie PowerShell 5.0 DSC zasobów może mieć wiele wersji, a wersji można zainstalować na komputerze side-by-side.</span><span class="sxs-lookup"><span data-stu-id="6db72-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="6db72-106">Ten sposób jest implementowany przez korzystanie z kilku wersji moduł zasobów, które są zawarte w tym samym folderze modułu.</span><span class="sxs-lookup"><span data-stu-id="6db72-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="6db72-107">Instalowanie wielu zasobów wersji side-by-side</span><span class="sxs-lookup"><span data-stu-id="6db72-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="6db72-108">Można użyć **MinimumVersion**, **MaximumVersion**, i **RequiredVersion** parametry [instalacji modułu](https://technet.microsoft.com/library/dn807162.aspx) polecenia cmdlet, aby określić która wersja modułu do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="6db72-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="6db72-109">Wywoływanie **instalacji modułu** bez określania wersji instaluje najnowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="6db72-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="6db72-110">Na przykład istnieje wiele wersji **xFailOverCluster** modułu, z których każdy zawiera **xCluster** zasobów.</span><span class="sxs-lookup"><span data-stu-id="6db72-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="6db72-111">Wyniku wywołania metody **instalacji modułu** bez określania wersji numer wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="6db72-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="6db72-112">Teraz, jeśli wywołujesz **instalacji modułu** ponownie, ale określ **RequiredVersion** z 1.1.0.0, wyniki w następujących:</span><span class="sxs-lookup"><span data-stu-id="6db72-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="6db72-113">Określanie wersji zasobu w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6db72-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="6db72-114">Jeśli masz wiele zasobów zainstalowany na komputerze, gdy jest używany w konfiguracji należy określić wersji tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="6db72-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="6db72-115">Aby to zrobić, określając **ModuleVersion** parametr **DscResource importu** — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6db72-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="6db72-116">Jeśli nie można określić wersji modułu zasobów zasobu, na których zainstalowano więcej niż jedną wersję, konfiguracja powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="6db72-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="6db72-117">Następująca konfiguracja pokazano, jak można określić wersji zasobu, aby wywołać:</span><span class="sxs-lookup"><span data-stu-id="6db72-117">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

><span data-ttu-id="6db72-118">Uwaga: Parametr ModuleVersion DscResource importu nie jest dostępny w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="6db72-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="6db72-119">W programie PowerShell 4.0 można określić wersji modułu przez przekazanie obiektu specyfikacji modułu do parametru ModuleName DscResource importu.</span><span class="sxs-lookup"><span data-stu-id="6db72-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="6db72-120">Obiekt specyfikacji modułu jest tablicy skrótów, która zawiera klucze ModuleName i RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="6db72-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="6db72-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="6db72-121">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="6db72-122">To również będą działać w programie PowerShell 5.0, ale zaleca się, że używasz **ModuleVersion** parametru.</span><span class="sxs-lookup"><span data-stu-id="6db72-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="6db72-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6db72-123">See also</span></span>
* [<span data-ttu-id="6db72-124">Konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="6db72-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="6db72-125">Zasoby usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="6db72-125">DSC Resources</span></span>](resources.md)