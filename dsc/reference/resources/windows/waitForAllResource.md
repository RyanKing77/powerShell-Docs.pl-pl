---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób WaitForAll DSC
ms.openlocfilehash: c1125b7c5b68b9b520ed052800b6a2abf4e53b85
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726865"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="7e877-103">Zasób WaitForAll DSC</span><span class="sxs-lookup"><span data-stu-id="7e877-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="7e877-104">Dotyczy: Program Windows PowerShell 5.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="7e877-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="7e877-105">**WaitForAll** zasobów Desired State Configuration (DSC) mogą być używane w bloku węzła w [konfiguracji DSC](../../../configurations/configurations.md) do określania zależności w konfiguracji na innych węzłach.</span><span class="sxs-lookup"><span data-stu-id="7e877-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="7e877-106">Ten zasób zakończy się pomyślnie, jeśli zasób określony przez **ResourceName** właściwość jest w żądanym stanie na wszystkich węzłach docelowych określonych w **NodeName** właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e877-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="7e877-107">**WaitForAll** zasobów używa Windows Remote Management, aby sprawdzić stan innych węzłów.</span><span class="sxs-lookup"><span data-stu-id="7e877-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="7e877-108">Aby uzyskać więcej informacji na temat wymagania dotyczące portów i zabezpieczeń dla usługi WinRM, zobacz [zagadnienia dotyczące zabezpieczeń komunikacji zdalnej programu PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="7e877-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="7e877-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e877-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="7e877-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7e877-110">Properties</span></span>

|  <span data-ttu-id="7e877-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7e877-111">Property</span></span>  |  <span data-ttu-id="7e877-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7e877-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="7e877-113">ResourceName</span><span class="sxs-lookup"><span data-stu-id="7e877-113">ResourceName</span></span>| <span data-ttu-id="7e877-114">Nazwa zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="7e877-114">The resource name to depend on.</span></span> <span data-ttu-id="7e877-115">Jeśli ten zasób należy do innej konfiguracji, format nazwy jako "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="7e877-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="7e877-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="7e877-116">NodeName</span></span>| <span data-ttu-id="7e877-117">Węzły docelowe zasobu, aby była zależna od.</span><span class="sxs-lookup"><span data-stu-id="7e877-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="7e877-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="7e877-118">RetryIntervalSec</span></span>| <span data-ttu-id="7e877-119">Liczba sekund przed ponowną próbą.</span><span class="sxs-lookup"><span data-stu-id="7e877-119">The number of seconds before retrying.</span></span> <span data-ttu-id="7e877-120">Minimalny to 1.</span><span class="sxs-lookup"><span data-stu-id="7e877-120">Minimum is 1.</span></span>|
| <span data-ttu-id="7e877-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="7e877-121">RetryCount</span></span>| <span data-ttu-id="7e877-122">Maksymalna liczba ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="7e877-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="7e877-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="7e877-123">ThrottleLimit</span></span>| <span data-ttu-id="7e877-124">Liczba maszyn do łączenia z jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="7e877-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="7e877-125">Domyślną jest domyślna nowy cimsession.</span><span class="sxs-lookup"><span data-stu-id="7e877-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="7e877-126">dependsOn</span><span class="sxs-lookup"><span data-stu-id="7e877-126">DependsOn</span></span> | <span data-ttu-id="7e877-127">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="7e877-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7e877-128">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7e877-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="7e877-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e877-129">Example</span></span>

<span data-ttu-id="7e877-130">Na przykład dotyczące używania tego zasobu zobacz [określanie zależności między węzłami](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="7e877-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
