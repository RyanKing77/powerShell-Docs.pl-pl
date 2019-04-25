---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WaitForAll DSC
ms.openlocfilehash: 1e891f1aecbdbe641973669f71f22664ad8ea16c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076926"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="5d2b0-103">Zasób WaitForAll DSC</span><span class="sxs-lookup"><span data-stu-id="5d2b0-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="5d2b0-104">Dotyczy: Program Windows PowerShell 5.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="5d2b0-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="5d2b0-105">**WaitForAll** zasobów Desired State Configuration (DSC) mogą być używane w bloku węzła w [konfiguracji DSC](../../../configurations/configurations.md) do określania zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="5d2b0-106">Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkich węzłach docelowych określonych w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d2b0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d2b0-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="5d2b0-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5d2b0-108">Properties</span></span>

|  <span data-ttu-id="5d2b0-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5d2b0-109">Property</span></span>  |  <span data-ttu-id="5d2b0-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5d2b0-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="5d2b0-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="5d2b0-111">ResourceName</span></span>| <span data-ttu-id="5d2b0-112">Nazwa zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-112">The resource name to depend on.</span></span> <span data-ttu-id="5d2b0-113">Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="5d2b0-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="5d2b0-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="5d2b0-114">NodeName</span></span>| <span data-ttu-id="5d2b0-115">Węzły docelowe zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="5d2b0-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="5d2b0-116">RetryIntervalSec</span></span>| <span data-ttu-id="5d2b0-117">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-117">The number of seconds before retrying.</span></span> <span data-ttu-id="5d2b0-118">Minimalny to 1.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-118">Minimum is 1.</span></span>|
| <span data-ttu-id="5d2b0-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="5d2b0-119">RetryCount</span></span>| <span data-ttu-id="5d2b0-120">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="5d2b0-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="5d2b0-121">ThrottleLimit</span></span>| <span data-ttu-id="5d2b0-122">Liczba maszyn do łączenia z jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="5d2b0-123">Domyślną jest domyślna nowy cimsession.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="5d2b0-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="5d2b0-124">DependsOn</span></span> | <span data-ttu-id="5d2b0-125">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5d2b0-126">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5d2b0-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="5d2b0-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d2b0-127">Example</span></span>

<span data-ttu-id="5d2b0-128">Na przykład dotyczące używania tego zasobu zobacz [określanie zależności między węzłami](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="5d2b0-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
