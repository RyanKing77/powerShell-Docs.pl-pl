---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WaitForAny DSC
ms.openlocfilehash: 39100f0fc52092c54bbecab55e3ef3dfabb4c70e
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226053"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="caae7-103">Zasób WaitForAny DSC</span><span class="sxs-lookup"><span data-stu-id="caae7-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="caae7-104">Mają zastosowanie do: Program Windows PowerShell 5.1 i nowszych</span><span class="sxs-lookup"><span data-stu-id="caae7-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="caae7-105">**WaitForSome** zasobów Desired State Configuration (DSC) mogą być używane w bloku węzła w [konfiguracji DSC](configurations.md) do określania zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="caae7-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="caae7-106">Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkie węzły docelowe, zdefiniowane w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="caae7-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="caae7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="caae7-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="caae7-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="caae7-108">Properties</span></span>

|  <span data-ttu-id="caae7-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="caae7-109">Property</span></span>  |  <span data-ttu-id="caae7-110">Opis</span><span class="sxs-lookup"><span data-stu-id="caae7-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="caae7-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="caae7-111">ResourceName</span></span>| <span data-ttu-id="caae7-112">Nazwa zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="caae7-112">The resource name to depend on.</span></span> <span data-ttu-id="caae7-113">Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="caae7-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="caae7-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="caae7-114">NodeName</span></span>| <span data-ttu-id="caae7-115">Węzły docelowe zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="caae7-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="caae7-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="caae7-116">RetryIntervalSec</span></span>| <span data-ttu-id="caae7-117">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="caae7-117">The number of seconds before retrying.</span></span> <span data-ttu-id="caae7-118">Minimalny to 1.</span><span class="sxs-lookup"><span data-stu-id="caae7-118">Minimum is 1.</span></span>|
| <span data-ttu-id="caae7-119">retryCount</span><span class="sxs-lookup"><span data-stu-id="caae7-119">RetryCount</span></span>| <span data-ttu-id="caae7-120">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="caae7-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="caae7-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="caae7-121">ThrottleLimit</span></span>| <span data-ttu-id="caae7-122">Liczba maszyn do łączenia z jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="caae7-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="caae7-123">Domyślną jest domyślna nowy cimsession.</span><span class="sxs-lookup"><span data-stu-id="caae7-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="caae7-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="caae7-124">DependsOn</span></span> | <span data-ttu-id="caae7-125">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="caae7-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="caae7-126">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="caae7-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="caae7-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="caae7-127">Example</span></span>

<span data-ttu-id="caae7-128">Na przykład dotyczące używania tego zasobu zobacz [określanie zależności między węzłami](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="caae7-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>