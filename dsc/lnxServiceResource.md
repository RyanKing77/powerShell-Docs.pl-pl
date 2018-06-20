---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxService zasobów
ms.openlocfilehash: 9cab889368469f2c854a387b919aea58a49f2210
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187722"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="4a932-103">DSC dla systemu Linux nxService zasobów</span><span class="sxs-lookup"><span data-stu-id="4a932-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="4a932-104">**NxService** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm zarządzania usługami w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4a932-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a932-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a932-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="4a932-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4a932-106">Properties</span></span>
|  <span data-ttu-id="4a932-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4a932-107">Property</span></span> |  <span data-ttu-id="4a932-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4a932-108">Description</span></span> |
|---|---|
| <span data-ttu-id="4a932-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4a932-109">Name</span></span>| <span data-ttu-id="4a932-110">Nazwa usługi/demona do skonfigurowania.</span><span class="sxs-lookup"><span data-stu-id="4a932-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="4a932-111">Kontrolera</span><span class="sxs-lookup"><span data-stu-id="4a932-111">Controller</span></span>| <span data-ttu-id="4a932-112">Typ kontrolera usługi do użycia podczas konfigurowania usługi.</span><span class="sxs-lookup"><span data-stu-id="4a932-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="4a932-113">Włącz</span><span class="sxs-lookup"><span data-stu-id="4a932-113">Enabled</span></span>| <span data-ttu-id="4a932-114">Wskazuje, czy usługa jest uruchamiana podczas rozruchu.</span><span class="sxs-lookup"><span data-stu-id="4a932-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="4a932-115">Stan</span><span class="sxs-lookup"><span data-stu-id="4a932-115">State</span></span>| <span data-ttu-id="4a932-116">Wskazuje, czy usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="4a932-116">Indicates whether the service is running.</span></span> <span data-ttu-id="4a932-117">Ustaw tę właściwość na "Zatrzymane", aby upewnić się, że usługa nie jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="4a932-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="4a932-118">Ustaw ją na "Uruchomiona", aby upewnić się, że usługa nie jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="4a932-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="4a932-119">dependsOn</span><span class="sxs-lookup"><span data-stu-id="4a932-119">DependsOn</span></span> | <span data-ttu-id="4a932-120">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="4a932-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4a932-121">Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4a932-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="additional-information"></a><span data-ttu-id="4a932-122">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="4a932-122">Additional Information</span></span>

<span data-ttu-id="4a932-123">**NxService** zasobów nie utworzy definicji usługi lub skryptu usługi, gdy nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="4a932-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="4a932-124">Można użyć konfiguracji żądanego stanu środowiska PowerShell **nxFile** zasób zasobów do zarządzania istnienie lub zawartość skryptu lub pliku definicji usługi.</span><span class="sxs-lookup"><span data-stu-id="4a932-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="4a932-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a932-125">Example</span></span>

<span data-ttu-id="4a932-126">W poniższym przykładzie przedstawiono konfigurację usługi "host z wieloma adresami" (dla Apache HTTP Server), zarejestrowany **SystemD** kontrolera usług.</span><span class="sxs-lookup"><span data-stu-id="4a932-126">The following example shows configuration of the “httpd” service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```
Import-DSCResource -Module nx

Node $node {
#Apache Service
nxService ApacheService
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```