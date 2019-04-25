---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WaitForSome DSC
ms.openlocfilehash: 888da1810f0a9233579bad5eef8d5dd556947c61
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076858"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="a947f-103">Zasób WaitForSome DSC</span><span class="sxs-lookup"><span data-stu-id="a947f-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="a947f-104">Dotyczy: Program Windows PowerShell 5.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="a947f-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="a947f-105">**WaitForSome** zasobów Desired State Configuration (DSC) mogą być używane w bloku węzła w [konfiguracji DSC](../../../configurations/configurations.md) do określania zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="a947f-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="a947f-106">Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na minimalna liczba węzłów (określony przez **NodeCount**) zdefiniowane przez **NodeName**  właściwości.</span><span class="sxs-lookup"><span data-stu-id="a947f-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="a947f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a947f-107">Syntax</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a><span data-ttu-id="a947f-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a947f-108">Properties</span></span>

|  <span data-ttu-id="a947f-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a947f-109">Property</span></span>  |  <span data-ttu-id="a947f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a947f-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="a947f-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="a947f-111">NodeCount</span></span>| <span data-ttu-id="a947f-112">Minimalna liczba węzłów, które muszą być w żądanym stanie dla tego zasobu została wykonana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a947f-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="a947f-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="a947f-113">NodeName</span></span>| <span data-ttu-id="a947f-114">Węzły docelowe zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="a947f-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="a947f-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="a947f-115">ResourceName</span></span>| <span data-ttu-id="a947f-116">Nazwa zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="a947f-116">The resource name to depend on.</span></span> <span data-ttu-id="a947f-117">Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="a947f-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="a947f-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a947f-118">RetryIntervalSec</span></span>| <span data-ttu-id="a947f-119">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="a947f-119">The number of seconds before retrying.</span></span> <span data-ttu-id="a947f-120">Minimalny to 1.</span><span class="sxs-lookup"><span data-stu-id="a947f-120">Minimum is 1.</span></span>|
| <span data-ttu-id="a947f-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="a947f-121">RetryCount</span></span>| <span data-ttu-id="a947f-122">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="a947f-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="a947f-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a947f-123">ThrottleLimit</span></span>| <span data-ttu-id="a947f-124">Liczba maszyn do łączenia z jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a947f-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a947f-125">Domyślną jest domyślna nowy cimsession.</span><span class="sxs-lookup"><span data-stu-id="a947f-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="a947f-126">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a947f-126">DependsOn</span></span> | <span data-ttu-id="a947f-127">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="a947f-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a947f-128">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a947f-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="a947f-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a947f-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="a947f-130">Zobacz [DSC przy użyciu poświadczeń użytkownika](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="a947f-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="a947f-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="a947f-131">Example</span></span>

<span data-ttu-id="a947f-132">Na przykład dotyczące używania tego zasobu zobacz [określanie zależności między węzłami](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a947f-132">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
