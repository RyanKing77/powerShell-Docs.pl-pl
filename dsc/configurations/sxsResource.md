---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zaimportować określoną wersję zainstalowanego zasobów
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404688"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="ae192-103">Zaimportować określoną wersję zainstalowanego zasobów</span><span class="sxs-lookup"><span data-stu-id="ae192-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="ae192-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ae192-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ae192-105">W programie PowerShell w wersji 5.0 oddzielnych wersji zasobów DSC można zainstalować na komputerze obok siebie.</span><span class="sxs-lookup"><span data-stu-id="ae192-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="ae192-106">Moduł zasobów można przechowywać różne wersje zasobu w wersji o nazwie folderów.</span><span class="sxs-lookup"><span data-stu-id="ae192-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="ae192-107">Instalowanie wersji osobny zasób obok siebie</span><span class="sxs-lookup"><span data-stu-id="ae192-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="ae192-108">Możesz użyć **MinimumVersion**, **MaximumVersion**, i **RequiredVersion** parametry [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby określić która wersja modułu do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="ae192-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="ae192-109">Wywoływanie **Install-Module** bez określenia wersji instaluje najnowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="ae192-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="ae192-110">Na przykład, istnieje wiele wersji **xFailOverCluster** modułu, z których każdy zawiera **xCluster** zasobów.</span><span class="sxs-lookup"><span data-stu-id="ae192-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="ae192-111">Wywoływanie **Install-Module** bez określenia wersji numer instaluje najnowszą wersję modułu.</span><span class="sxs-lookup"><span data-stu-id="ae192-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="ae192-112">Aby zainstalować określoną wersję modułu, należy określić **RequiredVersion** z 1.1.0.0.</span><span class="sxs-lookup"><span data-stu-id="ae192-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="ae192-113">Spowoduje to zainstalowanie określonej wersji równolegle z zainstalowaną wersją.</span><span class="sxs-lookup"><span data-stu-id="ae192-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="ae192-114">Teraz można zobaczyć zarówno wersji modułu liście przy użyciu `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="ae192-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="ae192-115">Określanie wersji zasobu w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ae192-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="ae192-116">Jeśli masz osobnego zasobu wersje zainstalowane na komputerze, należy określić wersję tego zasobu, gdy używasz w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ae192-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="ae192-117">Można to zrobić, określając **ModuleVersion** parametru **Import-DscResource** — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="ae192-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="ae192-118">Jeśli nie można określić wersję modułu zasobów, zasobów, które mają więcej niż jedna wersja zainstalowana, dana konfiguracja taką generuje błąd.</span><span class="sxs-lookup"><span data-stu-id="ae192-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="ae192-119">Następująca konfiguracja pokazuje, jak określać wersję zasobu do wywołania:</span><span class="sxs-lookup"><span data-stu-id="ae192-119">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="ae192-120">Uwaga: Parametr ModuleVersion Import-DscResource nie jest dostępny w programie PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="ae192-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="ae192-121">W programie PowerShell 4.0 można określić wersji modułu, przekazując obiekt specyfikacji modułu do parametru ModuleName Import-DscResource.</span><span class="sxs-lookup"><span data-stu-id="ae192-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="ae192-122">Obiekt specyfikacji modułu jest tabeli wyznaczania wartości skrótu, która zawiera klucze ModuleName i RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="ae192-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="ae192-123">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ae192-123">For example:</span></span>

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

<span data-ttu-id="ae192-124">Spowoduje to działa również w programie PowerShell 5.0, ale zaleca się, że używasz **ModuleVersion** parametru.</span><span class="sxs-lookup"><span data-stu-id="ae192-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae192-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae192-125">See also</span></span>

- [<span data-ttu-id="ae192-126">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="ae192-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="ae192-127">Zasoby DSC</span><span class="sxs-lookup"><span data-stu-id="ae192-127">DSC Resources</span></span>](../resources/resources.md)
