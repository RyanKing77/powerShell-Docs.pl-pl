---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Aktualizowanie węzłów z serwera ściągania
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079102"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="edbc2-103">Aktualizowanie węzłów z serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="edbc2-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="edbc2-104">W poniższych sekcjach przyjęto założenie, że już zdefiniowano serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="edbc2-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="edbc2-105">Jeśli nie zdefiniowano z serwera ściągania, można użyć następujących przewodników:</span><span class="sxs-lookup"><span data-stu-id="edbc2-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="edbc2-106">Konfigurowanie serwera ściągania SMB DSC</span><span class="sxs-lookup"><span data-stu-id="edbc2-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="edbc2-107">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="edbc2-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="edbc2-108">Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu.</span><span class="sxs-lookup"><span data-stu-id="edbc2-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="edbc2-109">W tym artykule pokazano sposób przekazywania zasobów, dzięki czemu są one dostępne do pobrania, a następnie skonfigurować klientów, aby pobrać zasoby automatycznie.</span><span class="sxs-lookup"><span data-stu-id="edbc2-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="edbc2-110">Gdy węzeł odbiera przypisanej konfiguracji, za pośrednictwem **ściągnięcia** lub **wypychania** (v5), automatycznie pobiera wszystkie zasoby wymagane przez tę konfigurację w lokalizacji określonej w LCM.</span><span class="sxs-lookup"><span data-stu-id="edbc2-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="edbc2-111">Za pomocą polecenia cmdlet Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="edbc2-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="edbc2-112">Począwszy od programu PowerShell w wersji 5.0 [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) polecenia cmdlet wymusza węzła do zaktualizowania jego konfiguracji z serwera ściągania skonfigurowany w LCM.</span><span class="sxs-lookup"><span data-stu-id="edbc2-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="edbc2-113">Za pomocą Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="edbc2-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="edbc2-114">W programie PowerShell 4.0, można nadal ręcznie wymusić na kliencie ściągania aktualizacji, jego konfigurację za pomocą polecenia [polecenia Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="edbc2-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="edbc2-115">Poniższy przykład tworzy sesję modelu wspólnych informacji przy użyciu podanych poświadczeń, wywołuje odpowiednią metodę modelu wspólnych informacji i usuwa sesji.</span><span class="sxs-lookup"><span data-stu-id="edbc2-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="edbc2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edbc2-116">See Also</span></span>

[<span data-ttu-id="edbc2-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="edbc2-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
