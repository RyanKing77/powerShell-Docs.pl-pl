---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxPackage zasobów
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218709"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="3849b-103">DSC dla systemu Linux nxPackage zasobów</span><span class="sxs-lookup"><span data-stu-id="3849b-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="3849b-104">**NxPackage** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm zarządzania pakietami w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="3849b-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="3849b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3849b-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="3849b-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3849b-106">Properties</span></span>

|  <span data-ttu-id="3849b-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3849b-107">Property</span></span> |  <span data-ttu-id="3849b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="3849b-108">Description</span></span> |
|---|---|
| <span data-ttu-id="3849b-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3849b-109">Name</span></span>| <span data-ttu-id="3849b-110">Nazwa pakietu, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="3849b-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="3849b-111">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="3849b-111">Ensure</span></span>| <span data-ttu-id="3849b-112">Określa, czy sprawdzić, czy istnieje pakiet.</span><span class="sxs-lookup"><span data-stu-id="3849b-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="3849b-113">Ustaw tę właściwość na "Brak", aby upewnić się, że pakiet istnieje.</span><span class="sxs-lookup"><span data-stu-id="3849b-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="3849b-114">Ustaw ją na "Brak", aby upewnić się, że pakiet nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3849b-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="3849b-115">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="3849b-115">The default value is "Present".</span></span>|
| <span data-ttu-id="3849b-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="3849b-116">PackageManager</span></span>| <span data-ttu-id="3849b-117">Obsługiwane wartości to "yum", "stanie" i "zypper".</span><span class="sxs-lookup"><span data-stu-id="3849b-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="3849b-118">Określa Menedżera pakietów do użycia podczas instalowania pakietów.</span><span class="sxs-lookup"><span data-stu-id="3849b-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="3849b-119">Jeśli **FilePath** określono, że podana ścieżka będzie służyć do zainstalowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="3849b-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="3849b-120">W przeciwnym razie Menedżera pakietów będzie służyć do zainstalowania pakietu z wstępnie skonfigurowane repozytorium.</span><span class="sxs-lookup"><span data-stu-id="3849b-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="3849b-121">Jeśli żadna **PackageManager** ani **FilePath** podano w nim domyślnego menedżera pakietów dla będzie używana przez system.</span><span class="sxs-lookup"><span data-stu-id="3849b-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="3849b-122">Ścieżka pliku</span><span class="sxs-lookup"><span data-stu-id="3849b-122">FilePath</span></span>| <span data-ttu-id="3849b-123">Ścieżka pliku, w którym znajduje się pakiet</span><span class="sxs-lookup"><span data-stu-id="3849b-123">The file path where the package resides</span></span>|
| <span data-ttu-id="3849b-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="3849b-124">PackageGroup</span></span>| <span data-ttu-id="3849b-125">Jeśli **$true**, **nazwa** powinien być nazwą grupy pakiet do użycia z **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="3849b-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="3849b-126">**PacakgeGroup** jest nieprawidłowa, podczas dostarczania **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="3849b-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="3849b-127">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3849b-127">Arguments</span></span>| <span data-ttu-id="3849b-128">Ciąg argumentów, które zostaną przekazane do pakietu, tak jak została podana.</span><span class="sxs-lookup"><span data-stu-id="3849b-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="3849b-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="3849b-129">ReturnCode</span></span>| <span data-ttu-id="3849b-130">Oczekiwany kod powrotu.</span><span class="sxs-lookup"><span data-stu-id="3849b-130">The expected return code.</span></span> <span data-ttu-id="3849b-131">Jeśli kod powrotu rzeczywiste nie odpowiada oczekiwanej wartości podane w tym miejscu konfiguracji spowoduje zwrócenie błędu.</span><span class="sxs-lookup"><span data-stu-id="3849b-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="3849b-132">dependsOn</span><span class="sxs-lookup"><span data-stu-id="3849b-132">DependsOn</span></span> | <span data-ttu-id="3849b-133">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="3849b-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3849b-134">Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3849b-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="3849b-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="3849b-135">Example</span></span>

<span data-ttu-id="3849b-136">Poniższy przykład określa, że pakiet o nazwie "host z wieloma adresami" jest instalowany na komputer z systemem Linux, używając Menedżera pakietów "Yum".</span><span class="sxs-lookup"><span data-stu-id="3849b-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```