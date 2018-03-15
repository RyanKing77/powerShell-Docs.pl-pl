---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób WaitForAny DSC"
ms.openlocfilehash: 43922dbcccb6d06d7d9edfcf16ce4eb107e9d4e6
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="141a9-103">Zasób WaitForAny DSC</span><span class="sxs-lookup"><span data-stu-id="141a9-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="141a9-104">Dotyczy: Windows PowerShell 5.1 i nowszych</span><span class="sxs-lookup"><span data-stu-id="141a9-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="141a9-105">**WaitForSome** zasobów konfiguracji żądanego stanu (DSC) może być używana w bloku węzła w [konfiguracji DSC](configurations.md) Aby określić zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="141a9-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="141a9-106">Ten zasób zakończy się pomyślnie, jeśli Jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkie węzły docelowe zdefiniowane w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="141a9-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="141a9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="141a9-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="141a9-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="141a9-108">Properties</span></span>

|  <span data-ttu-id="141a9-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="141a9-109">Property</span></span>  |  <span data-ttu-id="141a9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="141a9-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="141a9-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="141a9-111">ResourceName</span></span>| <span data-ttu-id="141a9-112">Nazwa zasobu zależne.</span><span class="sxs-lookup"><span data-stu-id="141a9-112">The resource name to depend on.</span></span> <span data-ttu-id="141a9-113">Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="141a9-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>| 
| <span data-ttu-id="141a9-114">nodeName</span><span class="sxs-lookup"><span data-stu-id="141a9-114">NodeName</span></span>| <span data-ttu-id="141a9-115">Węzły docelowe są zależne od zasobu.</span><span class="sxs-lookup"><span data-stu-id="141a9-115">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="141a9-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="141a9-116">RetryIntervalSec</span></span>| <span data-ttu-id="141a9-117">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="141a9-117">The number of seconds before retrying.</span></span> <span data-ttu-id="141a9-118">Minimalną jest 1.</span><span class="sxs-lookup"><span data-stu-id="141a9-118">Minimum is 1.</span></span>| 
| <span data-ttu-id="141a9-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="141a9-119">RetryCount</span></span>| <span data-ttu-id="141a9-120">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="141a9-120">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="141a9-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="141a9-121">ThrottleLimit</span></span>| <span data-ttu-id="141a9-122">Liczba maszyn nawiązać jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="141a9-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="141a9-123">Domyślna to nowy cimsession domyślne.</span><span class="sxs-lookup"><span data-stu-id="141a9-123">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="141a9-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="141a9-124">DependsOn</span></span> | <span data-ttu-id="141a9-125">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="141a9-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="141a9-126">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="141a9-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="141a9-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="141a9-127">Example</span></span>

<span data-ttu-id="141a9-128">Na przykład sposobu używania tego zasobu zobacz [określania zależności między węzłami](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="141a9-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

