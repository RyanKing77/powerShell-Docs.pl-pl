---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxEnvironment
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225985"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="931bd-103">DSC dla systemu Linux zasób nxEnvironment</span><span class="sxs-lookup"><span data-stu-id="931bd-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="931bd-104">**NxEnvironment** zasób w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania systemowe zmienne środowiskowe w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="931bd-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="931bd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="931bd-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="931bd-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="931bd-106">Properties</span></span>

|  <span data-ttu-id="931bd-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="931bd-107">Property</span></span> |  <span data-ttu-id="931bd-108">Opis</span><span class="sxs-lookup"><span data-stu-id="931bd-108">Description</span></span> |
|---|---|
| <span data-ttu-id="931bd-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="931bd-109">Name</span></span>| <span data-ttu-id="931bd-110">Wskazuje nazwę zmiennej środowiskowej, dla którego chcesz zapewnić określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="931bd-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="931bd-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="931bd-111">Value</span></span>| <span data-ttu-id="931bd-112">Wartość do przypisania do zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="931bd-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="931bd-113">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="931bd-113">Ensure</span></span>| <span data-ttu-id="931bd-114">Określa, czy należy sprawdzić, czy zmienna istnieje.</span><span class="sxs-lookup"><span data-stu-id="931bd-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="931bd-115">Ustaw tę właściwość "Present", aby upewnić się, że istnieje zmienna.</span><span class="sxs-lookup"><span data-stu-id="931bd-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="931bd-116">Ustaw ją na "Brak", aby upewnić się, że nie istnieje zmienna.</span><span class="sxs-lookup"><span data-stu-id="931bd-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="931bd-117">Wartość domyślna to "Istnieje".</span><span class="sxs-lookup"><span data-stu-id="931bd-117">The default value is "Present".</span></span>|
| <span data-ttu-id="931bd-118">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="931bd-118">Path</span></span>| <span data-ttu-id="931bd-119">Definiuje zmienną środowiskową, która jest konfigurowana.</span><span class="sxs-lookup"><span data-stu-id="931bd-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="931bd-120">Ustaw tę właściwość na **$true** , gdy zmienna **ścieżki** zmiennej; w przeciwnym razie ustaw ją na **$false**.</span><span class="sxs-lookup"><span data-stu-id="931bd-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="931bd-121">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="931bd-121">The default is **$false**.</span></span> <span data-ttu-id="931bd-122">Jeśli zmienna konfigurowany jest **ścieżki** podana wartość zmiennej, za pośrednictwem **wartość** właściwości, które zostaną dołączone do istniejącej wartości.</span><span class="sxs-lookup"><span data-stu-id="931bd-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="931bd-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="931bd-123">DependsOn</span></span> | <span data-ttu-id="931bd-124">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="931bd-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="931bd-125">Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="931bd-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="931bd-126">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="931bd-126">Additional Information</span></span>

* <span data-ttu-id="931bd-127">Jeśli **ścieżki** jest nieobecny lub równa **$false**, zmienne środowiskowe są zarządzane w `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="931bd-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="931bd-128">Programy i skrypty może wymagać konfiguracji źródłowej `/etc/environment` plik, aby uzyskać dostęp do zmiennych w środowisku zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="931bd-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="931bd-129">Jeśli **ścieżki** ustawiono **$true**, zmienna środowiskowa odbywa się w pliku `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="931bd-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="931bd-130">Ten plik zostanie utworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="931bd-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="931bd-131">Jeśli **upewnij się, że** jest ustawiona na "Brak" i **ścieżki** ustawiono **$true**, zmienna środowiskowa tylko zostaną usunięte z `/etc/profile.d/DSCenvironment.sh` , a nie z innych plików.</span><span class="sxs-lookup"><span data-stu-id="931bd-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="931bd-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="931bd-132">Example</span></span>

<span data-ttu-id="931bd-133">Poniższy przykład pokazuje, jak używać **nxEnvironment** zasób, aby upewnić się, że **TestEnvironmentVariable** jest obecny i ma wartość "Test-Value".</span><span class="sxs-lookup"><span data-stu-id="931bd-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="931bd-134">Jeśli **TestEnvironmentVariable** jest nieobecna, zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="931bd-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```