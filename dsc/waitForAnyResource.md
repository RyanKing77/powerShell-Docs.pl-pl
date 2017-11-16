---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób WaitForAny DSC"
ms.openlocfilehash: ba1873cc0ecfc4596cbad5b61b4a52b61ea4778a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="ea844-103">Zasób WaitForAny DSC</span><span class="sxs-lookup"><span data-stu-id="ea844-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="ea844-104">Dotyczy: Windows PowerShell 5.1 i nowszych</span><span class="sxs-lookup"><span data-stu-id="ea844-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="ea844-105">**WaitForSome** zasobów konfiguracji żądanego stanu (DSC) może być używana w bloku węzła w [konfiguracji DSC](configurations.md) Aby określić zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="ea844-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="ea844-106">Ten zasób zakończy się pomyślnie, jeśli Jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkie węzły docelowe zdefiniowane w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea844-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="ea844-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea844-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="ea844-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ea844-108">Properties</span></span>

|  <span data-ttu-id="ea844-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ea844-109">Property</span></span>  |  <span data-ttu-id="ea844-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ea844-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="ea844-111">resourceName</span><span class="sxs-lookup"><span data-stu-id="ea844-111">ResourceName</span></span>| <span data-ttu-id="ea844-112">Nazwa zasobu zależne.</span><span class="sxs-lookup"><span data-stu-id="ea844-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="ea844-113">nodeName</span><span class="sxs-lookup"><span data-stu-id="ea844-113">NodeName</span></span>| <span data-ttu-id="ea844-114">Węzły docelowe są zależne od zasobu.</span><span class="sxs-lookup"><span data-stu-id="ea844-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="ea844-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="ea844-115">RetryIntervalSec</span></span>| <span data-ttu-id="ea844-116">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="ea844-116">The number of seconds before retrying.</span></span> <span data-ttu-id="ea844-117">Minimalną jest 1.</span><span class="sxs-lookup"><span data-stu-id="ea844-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="ea844-118">retryCount</span><span class="sxs-lookup"><span data-stu-id="ea844-118">RetryCount</span></span>| <span data-ttu-id="ea844-119">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="ea844-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="ea844-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ea844-120">ThrottleLimit</span></span>| <span data-ttu-id="ea844-121">Liczba maszyn nawiązać jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="ea844-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ea844-122">Domyślna to nowy cimsession domyślne.</span><span class="sxs-lookup"><span data-stu-id="ea844-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="ea844-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="ea844-123">DependsOn</span></span> | <span data-ttu-id="ea844-124">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="ea844-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ea844-125">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ea844-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="ea844-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea844-126">Example</span></span>

<span data-ttu-id="ea844-127">Na przykład sposobu używania tego zasobu zobacz [określania zależności między węzłami](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="ea844-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

