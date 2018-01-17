---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób WaitForSome DSC"
ms.openlocfilehash: cbe16c543f0eeb62dbe1fb439af2f9147f1bc210
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="91c5b-103">Zasób WaitForSome DSC</span><span class="sxs-lookup"><span data-stu-id="91c5b-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="91c5b-104">Dotyczy: Windows PowerShell 5.0 i nowszych</span><span class="sxs-lookup"><span data-stu-id="91c5b-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="91c5b-105">**WaitForAny** zasobów konfiguracji żądanego stanu (DSC) może być używana w bloku węzła w [konfiguracji DSC](configurations.md) Aby określić zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="91c5b-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="91c5b-106">Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na minimalna liczba węzłów (określonego przez **NodeCount**) zdefiniowanych przez **NodeName**  właściwości.</span><span class="sxs-lookup"><span data-stu-id="91c5b-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="91c5b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="91c5b-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="91c5b-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="91c5b-108">Properties</span></span>

|  <span data-ttu-id="91c5b-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="91c5b-109">Property</span></span>  |  <span data-ttu-id="91c5b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="91c5b-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="91c5b-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="91c5b-111">NodeCount</span></span>| <span data-ttu-id="91c5b-112">Minimalna liczba węzłów, które muszą być w żądanym stanie dla tego zasobu powiodło się.</span><span class="sxs-lookup"><span data-stu-id="91c5b-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="91c5b-113">nodeName</span><span class="sxs-lookup"><span data-stu-id="91c5b-113">NodeName</span></span>| <span data-ttu-id="91c5b-114">Węzły docelowe są zależne od zasobu.</span><span class="sxs-lookup"><span data-stu-id="91c5b-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="91c5b-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="91c5b-115">ResourceName</span></span>| <span data-ttu-id="91c5b-116">Nazwa zasobu zależne.</span><span class="sxs-lookup"><span data-stu-id="91c5b-116">The resource name to depend on.</span></span>| 
| <span data-ttu-id="91c5b-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="91c5b-117">RetryIntervalSec</span></span>| <span data-ttu-id="91c5b-118">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="91c5b-118">The number of seconds before retrying.</span></span> <span data-ttu-id="91c5b-119">Minimalną jest 1.</span><span class="sxs-lookup"><span data-stu-id="91c5b-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="91c5b-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="91c5b-120">RetryCount</span></span>| <span data-ttu-id="91c5b-121">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="91c5b-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="91c5b-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="91c5b-122">ThrottleLimit</span></span>| <span data-ttu-id="91c5b-123">Liczba maszyn nawiązać jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="91c5b-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="91c5b-124">Domyślna to nowy cimsession domyślne.</span><span class="sxs-lookup"><span data-stu-id="91c5b-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="91c5b-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="91c5b-125">DependsOn</span></span> | <span data-ttu-id="91c5b-126">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="91c5b-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="91c5b-127">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="91c5b-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="91c5b-128">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="91c5b-128">PsDscRunAsCredential</span></span> | <span data-ttu-id="91c5b-129">Zobacz [przy użyciu poświadczeń użytkownika przy użyciu usługi Konfiguracja DSC](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="91c5b-129">See [Using DSC with User Credentials](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="91c5b-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="91c5b-130">Example</span></span>

<span data-ttu-id="91c5b-131">Na przykład sposobu używania tego zasobu zobacz [określania zależności między węzłami](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="91c5b-131">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

