---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób Serviceset DSC
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076839"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="5bd08-103">Zasób Serviceset DSC</span><span class="sxs-lookup"><span data-stu-id="5bd08-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="5bd08-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5bd08-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5bd08-105">**ServiceSet** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania usługami na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="5bd08-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="5bd08-106">Ten zasób jest [złożonego zasobów](../../../resources/authoringResourceComposite.md) wywołująca [usługi zasobów](serviceResource.md) każdą usług określonych w `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="5bd08-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="5bd08-107">Korzystając z tego zasobu, gdy użytkownik chce skonfigurować wiele usług, aby ten sam stan.</span><span class="sxs-lookup"><span data-stu-id="5bd08-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="5bd08-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bd08-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="5bd08-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5bd08-109">Properties</span></span>

|  <span data-ttu-id="5bd08-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5bd08-110">Property</span></span>  |  <span data-ttu-id="5bd08-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5bd08-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="5bd08-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5bd08-112">Name</span></span>| <span data-ttu-id="5bd08-113">Określa nazwy usług.</span><span class="sxs-lookup"><span data-stu-id="5bd08-113">Indicates the service names.</span></span> <span data-ttu-id="5bd08-114">Należy pamiętać, że czasami to różni się od nazw wyświetlanych.</span><span class="sxs-lookup"><span data-stu-id="5bd08-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="5bd08-115">Możesz uzyskać listę usług i ich bieżący stan z [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5bd08-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="5bd08-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="5bd08-116">StartupType</span></span>| <span data-ttu-id="5bd08-117">Wskazuje typ uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd08-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="5bd08-118">Wartości, które są dozwolone dla tej właściwości to: **Automatyczne**, **wyłączone**, i **ręczne**</span><span class="sxs-lookup"><span data-stu-id="5bd08-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="5bd08-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="5bd08-119">BuiltInAccount</span></span>| <span data-ttu-id="5bd08-120">Wskazuje, że konto logowania do użycia dla usług.</span><span class="sxs-lookup"><span data-stu-id="5bd08-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="5bd08-121">Wartości, które są dozwolone dla tej właściwości to: **Usługa lokalna**, **LocalSystem**, i **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="5bd08-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="5bd08-122">Stan</span><span class="sxs-lookup"><span data-stu-id="5bd08-122">State</span></span>| <span data-ttu-id="5bd08-123">Wskazuje stan, który chcesz mieć pewność, czy usługi: **Zatrzymano** lub **systemem**.</span><span class="sxs-lookup"><span data-stu-id="5bd08-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="5bd08-124">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="5bd08-124">Ensure</span></span>| <span data-ttu-id="5bd08-125">Wskazuje, czy usługi istnieje w systemie.</span><span class="sxs-lookup"><span data-stu-id="5bd08-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="5bd08-126">Ustaw tę właściwość na **nieobecne** aby upewnić się, że usługi nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="5bd08-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="5bd08-127">Ustawienie **obecne** (wartość domyślna) zapewnia, że istnieją usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="5bd08-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="5bd08-128">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="5bd08-128">Credential</span></span>| <span data-ttu-id="5bd08-129">Określa poświadczenia dla konta, które zostaną uruchomione zasób usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd08-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="5bd08-130">Ta właściwość i **BuiltinAccount** właściwości nie mogą być używane razem.</span><span class="sxs-lookup"><span data-stu-id="5bd08-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="5bd08-131">dependsOn</span><span class="sxs-lookup"><span data-stu-id="5bd08-131">DependsOn</span></span>| <span data-ttu-id="5bd08-132">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="5bd08-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5bd08-133">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest *ResourceName* a jej typ jest *ResourceType*, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5bd08-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="5bd08-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bd08-134">Example</span></span>

<span data-ttu-id="5bd08-135">Następująca konfiguracja uruchamia usługi "Windows Audio" i "Usług pulpitu zdalnego".</span><span class="sxs-lookup"><span data-stu-id="5bd08-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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
