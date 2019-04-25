---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób usługi DSC
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076898"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="650f3-103">Zasób usługi DSC</span><span class="sxs-lookup"><span data-stu-id="650f3-103">DSC Service Resource</span></span>

> <span data-ttu-id="650f3-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="650f3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="650f3-105">**Usługi** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania usługami na węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="650f3-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="650f3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="650f3-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="650f3-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="650f3-107">Properties</span></span>

|  <span data-ttu-id="650f3-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="650f3-108">Property</span></span>  |  <span data-ttu-id="650f3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="650f3-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="650f3-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="650f3-110">Name</span></span>| <span data-ttu-id="650f3-111">Wskazuje nazwę usługi.</span><span class="sxs-lookup"><span data-stu-id="650f3-111">Indicates the service name.</span></span> <span data-ttu-id="650f3-112">Należy pamiętać, że czasami jest inna niż nazwa wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="650f3-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="650f3-113">Możesz uzyskać listę usług i ich bieżący stan za pomocą polecenia cmdlet Get-Service.</span><span class="sxs-lookup"><span data-stu-id="650f3-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="650f3-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="650f3-114">BuiltInAccount</span></span>| <span data-ttu-id="650f3-115">Wskazuje, że konto logowania do użycia dla usługi.</span><span class="sxs-lookup"><span data-stu-id="650f3-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="650f3-116">Wartości, które są dozwolone dla tej właściwości to: **Usługa lokalna**, **LocalSystem**, i **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="650f3-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="650f3-117">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="650f3-117">Credential</span></span>| <span data-ttu-id="650f3-118">Określa poświadczenia dla konta, które będzie działać usługa.</span><span class="sxs-lookup"><span data-stu-id="650f3-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="650f3-119">Ta właściwość i __BuiltinAccount__ właściwości nie mogą być używane razem.</span><span class="sxs-lookup"><span data-stu-id="650f3-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="650f3-120">dependsOn</span><span class="sxs-lookup"><span data-stu-id="650f3-120">DependsOn</span></span>| <span data-ttu-id="650f3-121">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="650f3-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="650f3-122">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="650f3-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="650f3-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="650f3-123">StartupType</span></span>| <span data-ttu-id="650f3-124">Wskazuje typ uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="650f3-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="650f3-125">Wartości, które są dozwolone dla tej właściwości to: **Automatyczne**, **wyłączone**, i **ręczne**</span><span class="sxs-lookup"><span data-stu-id="650f3-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="650f3-126">Stan</span><span class="sxs-lookup"><span data-stu-id="650f3-126">State</span></span>| <span data-ttu-id="650f3-127">Wskazuje stan, który chcesz zapewnić usługę.</span><span class="sxs-lookup"><span data-stu-id="650f3-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="650f3-128">Opis</span><span class="sxs-lookup"><span data-stu-id="650f3-128">Description</span></span> | <span data-ttu-id="650f3-129">Określa opis usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="650f3-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="650f3-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="650f3-130">DisplayName</span></span> | <span data-ttu-id="650f3-131">Określa nazwę wyświetlaną usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="650f3-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="650f3-132">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="650f3-132">Ensure</span></span> | <span data-ttu-id="650f3-133">Wskazuje, czy Usługa docelowa istnieje w systemie.</span><span class="sxs-lookup"><span data-stu-id="650f3-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="650f3-134">Ustaw tę właściwość na **nieobecne** aby upewnić się, że Usługa docelowa nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="650f3-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="650f3-135">Ustawienie **obecne** (wartość domyślna) gwarantuje, czy istnieje usługa docelowa.</span><span class="sxs-lookup"><span data-stu-id="650f3-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="650f3-136">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="650f3-136">Path</span></span> | <span data-ttu-id="650f3-137">Określa ścieżkę do pliku binarnego dla nowej usługi.</span><span class="sxs-lookup"><span data-stu-id="650f3-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="650f3-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="650f3-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```