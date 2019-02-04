---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WaitForAll DSC
ms.openlocfilehash: 1e891f1aecbdbe641973669f71f22664ad8ea16c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686075"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="51cf9-103">Zasób WaitForAll DSC</span><span class="sxs-lookup"><span data-stu-id="51cf9-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="51cf9-104">Dotyczy: Program Windows PowerShell 5.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="51cf9-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="51cf9-105">**WaitForAll** zasobów Desired State Configuration (DSC) mogą być używane w bloku węzła w [konfiguracji DSC](../../../configurations/configurations.md) do określania zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="51cf9-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="51cf9-106">Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkich węzłach docelowych określonych w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="51cf9-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="51cf9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="51cf9-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="51cf9-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="51cf9-108">Properties</span></span>

|  <span data-ttu-id="51cf9-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="51cf9-109">Property</span></span>  |  <span data-ttu-id="51cf9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="51cf9-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="51cf9-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="51cf9-111">ResourceName</span></span>| <span data-ttu-id="51cf9-112">Nazwa zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="51cf9-112">The resource name to depend on.</span></span> <span data-ttu-id="51cf9-113">Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="51cf9-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="51cf9-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="51cf9-114">NodeName</span></span>| <span data-ttu-id="51cf9-115">Węzły docelowe zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="51cf9-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="51cf9-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="51cf9-116">RetryIntervalSec</span></span>| <span data-ttu-id="51cf9-117">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="51cf9-117">The number of seconds before retrying.</span></span> <span data-ttu-id="51cf9-118">Minimalny to 1.</span><span class="sxs-lookup"><span data-stu-id="51cf9-118">Minimum is 1.</span></span>|
| <span data-ttu-id="51cf9-119">retryCount</span><span class="sxs-lookup"><span data-stu-id="51cf9-119">RetryCount</span></span>| <span data-ttu-id="51cf9-120">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="51cf9-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="51cf9-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="51cf9-121">ThrottleLimit</span></span>| <span data-ttu-id="51cf9-122">Liczba maszyn do łączenia z jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="51cf9-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="51cf9-123">Domyślną jest domyślna nowy cimsession.</span><span class="sxs-lookup"><span data-stu-id="51cf9-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="51cf9-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="51cf9-124">DependsOn</span></span> | <span data-ttu-id="51cf9-125">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="51cf9-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="51cf9-126">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="51cf9-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="51cf9-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="51cf9-127">Example</span></span>

<span data-ttu-id="51cf9-128">Na przykład dotyczące używania tego zasobu zobacz [określanie zależności między węzłami](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="51cf9-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
