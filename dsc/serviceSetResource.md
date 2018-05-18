---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób ServiceSet DSC
ms.openlocfilehash: 1f879d2eafeb11e69968252a11f0c550c9b103f3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="5b4b9-103">Zasób ServiceSet DSC</span><span class="sxs-lookup"><span data-stu-id="5b4b9-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="5b4b9-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5b4b9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="5b4b9-105">**ServiceSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania usługami w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="5b4b9-106">Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) wywołującym [usługi zasobów](serviceResource.md) dla każdej usługi określone w `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="5b4b9-107">Jeśli chcesz skonfigurować liczbę usług do tego samego stanu, należy użyć tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b4b9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b4b9-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="5b4b9-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5b4b9-109">Properties</span></span>

|  <span data-ttu-id="5b4b9-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5b4b9-110">Property</span></span>  |  <span data-ttu-id="5b4b9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5b4b9-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="5b4b9-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5b4b9-112">Name</span></span>| <span data-ttu-id="5b4b9-113">Wskazuje nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-113">Indicates the service names.</span></span> <span data-ttu-id="5b4b9-114">Należy pamiętać, że czasami to różni się od nazwy wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="5b4b9-115">Można uzyskać listę usług i ich bieżącego stanu z [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="5b4b9-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="5b4b9-116">StartupType</span></span>| <span data-ttu-id="5b4b9-117">Wskazuje typ uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="5b4b9-118">Wartości, które są dozwolone dla tej właściwości to: **automatyczne**, **wyłączone**, i **ręczne**</span><span class="sxs-lookup"><span data-stu-id="5b4b9-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="5b4b9-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="5b4b9-119">BuiltInAccount</span></span>| <span data-ttu-id="5b4b9-120">Wskazuje, że konto logowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="5b4b9-121">Wartości, które są dozwolone dla tej właściwości to: **Usługa lokalna**, **LocalSystem**, i **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="5b4b9-122">Stan</span><span class="sxs-lookup"><span data-stu-id="5b4b9-122">State</span></span>| <span data-ttu-id="5b4b9-123">Wskazuje stan chcesz zapewnić usługę: **zatrzymane** lub **systemem**.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="5b4b9-124">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="5b4b9-124">Ensure</span></span>| <span data-ttu-id="5b4b9-125">Wskazuje, czy istnieją usługi w systemie.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="5b4b9-126">Ta właściwość jest ustawiana **nieobecne** aby upewnić się, że nie istnieją usługi.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="5b4b9-127">Ustawieniem dla niego **obecny** (wartość domyślna) zapewnia, że istnieją usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="5b4b9-128">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="5b4b9-128">Credential</span></span>| <span data-ttu-id="5b4b9-129">Określa poświadczenia dla konta, na którym będzie uruchamiana zasobów usługi.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="5b4b9-130">Ta właściwość i **BuiltinAccount** właściwości nie mogą być używane razem.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="5b4b9-131">dependsOn</span><span class="sxs-lookup"><span data-stu-id="5b4b9-131">DependsOn</span></span>| <span data-ttu-id="5b4b9-132">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5b4b9-133">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest *ResourceName* i jej typ jest *ResourceType*, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5b4b9-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="5b4b9-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b4b9-134">Example</span></span>

<span data-ttu-id="5b4b9-135">Następującej konfiguracji uruchamiania usługi "Windows Audio" i "Usług pulpitu zdalnego".</span><span class="sxs-lookup"><span data-stu-id="5b4b9-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```