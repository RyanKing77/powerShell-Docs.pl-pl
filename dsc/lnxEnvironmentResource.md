---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxEnvironment zasobów
ms.openlocfilehash: 6d1d5e578e9a7ddda0e70063f86867de2e87a52e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="25bae-103">DSC dla systemu Linux nxEnvironment zasobów</span><span class="sxs-lookup"><span data-stu-id="25bae-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="25bae-104">**NxEnvironment** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do zarządzania systemowe zmienne środowiskowe w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="25bae-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="25bae-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="25bae-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="25bae-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="25bae-106">Properties</span></span>

|  <span data-ttu-id="25bae-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="25bae-107">Property</span></span> |  <span data-ttu-id="25bae-108">Opis</span><span class="sxs-lookup"><span data-stu-id="25bae-108">Description</span></span> |
|---|---|
| <span data-ttu-id="25bae-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="25bae-109">Name</span></span>| <span data-ttu-id="25bae-110">Wskazuje nazwę zmiennej środowiskowej, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="25bae-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="25bae-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="25bae-111">Value</span></span>| <span data-ttu-id="25bae-112">Wartość do przypisania do zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="25bae-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="25bae-113">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="25bae-113">Ensure</span></span>| <span data-ttu-id="25bae-114">Określa, czy sprawdzić, czy istnieje zmienna.</span><span class="sxs-lookup"><span data-stu-id="25bae-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="25bae-115">Ustaw tę właściwość na "Brak", aby upewnić się, że istnieje zmienna.</span><span class="sxs-lookup"><span data-stu-id="25bae-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="25bae-116">Ustaw ją na "Brak", aby upewnić się, że zmienna nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="25bae-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="25bae-117">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="25bae-117">The default value is "Present".</span></span>|
| <span data-ttu-id="25bae-118">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="25bae-118">Path</span></span>| <span data-ttu-id="25bae-119">Definiuje zmienną środowiskową, który jest konfigurowany.</span><span class="sxs-lookup"><span data-stu-id="25bae-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="25bae-120">Ta właściwość jest ustawiana **$true** Jeśli zmienna jest **ścieżki** zmiennej; w przeciwnym razie ustaw ją na **$false**.</span><span class="sxs-lookup"><span data-stu-id="25bae-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="25bae-121">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="25bae-121">The default is **$false**.</span></span> <span data-ttu-id="25bae-122">Jeśli zmienna konfigurowany jest **ścieżki** wartość zmiennej, realizowane za pośrednictwem **wartość** właściwości, które zostaną dołączone do istniejącej wartości.</span><span class="sxs-lookup"><span data-stu-id="25bae-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="25bae-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="25bae-123">DependsOn</span></span> | <span data-ttu-id="25bae-124">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="25bae-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="25bae-125">Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="25bae-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="25bae-126">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="25bae-126">Additional Information</span></span>

* <span data-ttu-id="25bae-127">Jeśli **ścieżki** jest nieobecny lub ustawić **$false**, zmienne środowiskowe są zarządzane w `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="25bae-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="25bae-128">Programy i skrypty może być wymagana konfiguracja źródła `/etc/environment` pliku do uzyskania dostępu do zmiennych środowiskowych zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="25bae-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="25bae-129">Jeśli **ścieżki** ustawiono **$true**, zmienna środowiskowa odbywa się w pliku `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="25bae-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="25bae-130">Ten plik zostanie utworzona, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="25bae-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="25bae-131">Jeśli **upewnij się, że** jest ustawiona na "Brak" i **ścieżki** ustawiono **$true**, zmienna środowiskowa zostanie tylko usunięte z `/etc/profile.d/DSCenvironment.sh` , a nie z innych plików.</span><span class="sxs-lookup"><span data-stu-id="25bae-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="25bae-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="25bae-132">Example</span></span>

<span data-ttu-id="25bae-133">Poniższy przykład przedstawia użycie **nxEnvironment** zasobów, aby upewnić się, że **TestEnvironmentVariable** jest obecny i ma wartość "Test-Value".</span><span class="sxs-lookup"><span data-stu-id="25bae-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="25bae-134">Jeśli **TestEnvironmentVariable** jest nieobecna, zostanie on utworzony.</span><span class="sxs-lookup"><span data-stu-id="25bae-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```