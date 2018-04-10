---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób ServiceSet DSC
ms.openlocfilehash: a7516120f0c4bc1c91031adc8aabf6a59b845246
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="12f2c-103">Zasób ServiceSet DSC</span><span class="sxs-lookup"><span data-stu-id="12f2c-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="12f2c-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="12f2c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="12f2c-105">**ServiceSet** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania usługami w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="12f2c-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="12f2c-106">Ten zasób jest [złożonego zasobów](authoringResourceComposite.md) wywołującym [usługi zasobów](serviceResource.md) dla każdej usługi określone w `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="12f2c-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="12f2c-107">Jeśli chcesz skonfigurować liczbę usług do tego samego stanu, należy użyć tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="12f2c-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="12f2c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="12f2c-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="12f2c-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="12f2c-109">Properties</span></span>

|  <span data-ttu-id="12f2c-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="12f2c-110">Property</span></span>  |  <span data-ttu-id="12f2c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="12f2c-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="12f2c-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="12f2c-112">Name</span></span>| <span data-ttu-id="12f2c-113">Wskazuje nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="12f2c-113">Indicates the service names.</span></span> <span data-ttu-id="12f2c-114">Należy pamiętać, że czasami to różni się od nazwy wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="12f2c-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="12f2c-115">Można uzyskać listę usług i ich bieżącego stanu z [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="12f2c-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="12f2c-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="12f2c-116">StartupType</span></span>| <span data-ttu-id="12f2c-117">Wskazuje typ uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="12f2c-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="12f2c-118">Wartości, które są dozwolone dla tej właściwości to: **automatyczne**, **wyłączone**, i **ręczne**</span><span class="sxs-lookup"><span data-stu-id="12f2c-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="12f2c-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="12f2c-119">BuiltInAccount</span></span>| <span data-ttu-id="12f2c-120">Wskazuje, że konto logowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="12f2c-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="12f2c-121">Wartości, które są dozwolone dla tej właściwości to: **Usługa lokalna**, **LocalSystem**, i **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="12f2c-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="12f2c-122">Stan</span><span class="sxs-lookup"><span data-stu-id="12f2c-122">State</span></span>| <span data-ttu-id="12f2c-123">Wskazuje stan chcesz zapewnić usługę: **zatrzymane** lub **systemem**.</span><span class="sxs-lookup"><span data-stu-id="12f2c-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="12f2c-124">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="12f2c-124">Ensure</span></span>| <span data-ttu-id="12f2c-125">Wskazuje, czy istnieją usługi w systemie.</span><span class="sxs-lookup"><span data-stu-id="12f2c-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="12f2c-126">Ta właściwość jest ustawiana **nieobecne** aby upewnić się, że nie istnieją usługi.</span><span class="sxs-lookup"><span data-stu-id="12f2c-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="12f2c-127">Ustawieniem dla niego **obecny** (wartość domyślna) zapewnia, że istnieją usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="12f2c-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="12f2c-128">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="12f2c-128">Credential</span></span>| <span data-ttu-id="12f2c-129">Określa poświadczenia dla konta, na którym będzie uruchamiana zasobów usługi.</span><span class="sxs-lookup"><span data-stu-id="12f2c-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="12f2c-130">Ta właściwość i **BuiltinAccount** właściwości nie mogą być używane razem.</span><span class="sxs-lookup"><span data-stu-id="12f2c-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="12f2c-131">dependsOn</span><span class="sxs-lookup"><span data-stu-id="12f2c-131">DependsOn</span></span>| <span data-ttu-id="12f2c-132">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="12f2c-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="12f2c-133">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest *ResourceName* i jej typ jest *ResourceType*, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="12f2c-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="12f2c-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="12f2c-134">Example</span></span>

<span data-ttu-id="12f2c-135">Następującej konfiguracji uruchamiania usługi "Windows Audio" i "Usług pulpitu zdalnego".</span><span class="sxs-lookup"><span data-stu-id="12f2c-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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