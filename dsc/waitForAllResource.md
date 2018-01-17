---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób WaitForAll DSC"
ms.openlocfilehash: 2054d2af7cd7dd839c62e77c1d4b6eee5cff34ab
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="a739d-103">Zasób WaitForAll DSC</span><span class="sxs-lookup"><span data-stu-id="a739d-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="a739d-104">Dotyczy: Windows PowerShell 5.0 i nowszych</span><span class="sxs-lookup"><span data-stu-id="a739d-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="a739d-105">**WaitForAll** zasobów konfiguracji żądanego stanu (DSC) może być używana w bloku węzła w [konfiguracji DSC](configurations.md) Aby określić zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="a739d-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="a739d-106">Ten zasób zakończy się powodzeniem, czy jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkich węzłach docelowych określonych w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="a739d-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="a739d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a739d-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="a739d-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a739d-108">Properties</span></span>

|  <span data-ttu-id="a739d-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a739d-109">Property</span></span>  |  <span data-ttu-id="a739d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a739d-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="a739d-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="a739d-111">ResourceName</span></span>| <span data-ttu-id="a739d-112">Nazwa zasobu zależne.</span><span class="sxs-lookup"><span data-stu-id="a739d-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="a739d-113">nodeName</span><span class="sxs-lookup"><span data-stu-id="a739d-113">NodeName</span></span>| <span data-ttu-id="a739d-114">Węzły docelowe są zależne od zasobu.</span><span class="sxs-lookup"><span data-stu-id="a739d-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="a739d-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a739d-115">RetryIntervalSec</span></span>| <span data-ttu-id="a739d-116">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="a739d-116">The number of seconds before retrying.</span></span> <span data-ttu-id="a739d-117">Minimalną jest 1.</span><span class="sxs-lookup"><span data-stu-id="a739d-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="a739d-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="a739d-118">RetryCount</span></span>| <span data-ttu-id="a739d-119">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="a739d-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="a739d-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a739d-120">ThrottleLimit</span></span>| <span data-ttu-id="a739d-121">Liczba maszyn nawiązać jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a739d-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a739d-122">Domyślna to nowy cimsession domyślne.</span><span class="sxs-lookup"><span data-stu-id="a739d-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="a739d-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a739d-123">DependsOn</span></span> | <span data-ttu-id="a739d-124">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="a739d-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a739d-125">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a739d-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="a739d-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="a739d-126">Example</span></span>

<span data-ttu-id="a739d-127">Na przykład sposobu używania tego zasobu zobacz [określania zależności między węzłami](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a739d-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

