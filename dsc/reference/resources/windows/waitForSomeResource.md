---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WaitForSome DSC
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726771"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="3cba9-103">Zasób WaitForSome DSC</span><span class="sxs-lookup"><span data-stu-id="3cba9-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="3cba9-104">Dotyczy: Program Windows PowerShell 5.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="3cba9-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="3cba9-105">**WaitForSome** zasobów Desired State Configuration (DSC) mogą być używane w bloku węzła w [konfiguracji DSC](../../../configurations/configurations.md) do określania zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="3cba9-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="3cba9-106">Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na minimalna liczba węzłów (określony przez **NodeCount**) zdefiniowane przez **NodeName**  właściwości.</span><span class="sxs-lookup"><span data-stu-id="3cba9-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="3cba9-107">**WaitForSome** zasobów używa Windows Remote Management, aby sprawdzić stan innych węzłów.</span><span class="sxs-lookup"><span data-stu-id="3cba9-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="3cba9-108">Aby uzyskać więcej informacji na temat wymagania dotyczące portów i zabezpieczeń dla usługi WinRM, zobacz [zagadnienia dotyczące zabezpieczeń komunikacji zdalnej programu PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="3cba9-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="3cba9-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="3cba9-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="3cba9-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3cba9-110">Properties</span></span>

|  <span data-ttu-id="3cba9-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3cba9-111">Property</span></span>  |  <span data-ttu-id="3cba9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3cba9-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="3cba9-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="3cba9-113">NodeCount</span></span>| <span data-ttu-id="3cba9-114">Minimalna liczba węzłów, które muszą być w żądanym stanie dla tego zasobu została wykonana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3cba9-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="3cba9-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="3cba9-115">NodeName</span></span>| <span data-ttu-id="3cba9-116">Węzły docelowe zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="3cba9-116">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="3cba9-117">ResourceName</span><span class="sxs-lookup"><span data-stu-id="3cba9-117">ResourceName</span></span>| <span data-ttu-id="3cba9-118">Nazwa zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="3cba9-118">The resource name to depend on.</span></span> <span data-ttu-id="3cba9-119">Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="3cba9-119">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="3cba9-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="3cba9-120">RetryIntervalSec</span></span>| <span data-ttu-id="3cba9-121">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="3cba9-121">The number of seconds before retrying.</span></span> <span data-ttu-id="3cba9-122">Minimalny to 1.</span><span class="sxs-lookup"><span data-stu-id="3cba9-122">Minimum is 1.</span></span>|
| <span data-ttu-id="3cba9-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="3cba9-123">RetryCount</span></span>| <span data-ttu-id="3cba9-124">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="3cba9-124">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="3cba9-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="3cba9-125">ThrottleLimit</span></span>| <span data-ttu-id="3cba9-126">Liczba maszyn do łączenia z jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="3cba9-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="3cba9-127">Domyślną jest domyślna nowy cimsession.</span><span class="sxs-lookup"><span data-stu-id="3cba9-127">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="3cba9-128">dependsOn</span><span class="sxs-lookup"><span data-stu-id="3cba9-128">DependsOn</span></span> | <span data-ttu-id="3cba9-129">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="3cba9-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3cba9-130">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3cba9-130">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="3cba9-131">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="3cba9-131">PsDscRunAsCredential</span></span> | <span data-ttu-id="3cba9-132">Zobacz [DSC przy użyciu poświadczeń użytkownika](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="3cba9-132">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="3cba9-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cba9-133">Example</span></span>

<span data-ttu-id="3cba9-134">Na przykład dotyczące używania tego zasobu zobacz [określanie zależności między węzłami](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="3cba9-134">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
