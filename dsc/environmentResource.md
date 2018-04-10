---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC środowiska zasobów
ms.openlocfilehash: 4f024afe2d70c13e19406745ec7fd69821ab229b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="1b279-103">DSC środowiska zasobów</span><span class="sxs-lookup"><span data-stu-id="1b279-103">DSC Environment Resource</span></span>

> <span data-ttu-id="1b279-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1b279-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1b279-105">__Środowiska__ zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania zmiennych środowiskowych systemu.</span><span class="sxs-lookup"><span data-stu-id="1b279-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b279-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b279-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="1b279-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1b279-107">Properties</span></span>

|  <span data-ttu-id="1b279-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1b279-108">Property</span></span>  |  <span data-ttu-id="1b279-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1b279-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="1b279-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1b279-110">Name</span></span>| <span data-ttu-id="1b279-111">Wskazuje nazwę zmiennej środowiskowej, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="1b279-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="1b279-112">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="1b279-112">Ensure</span></span>| <span data-ttu-id="1b279-113">Wskazuje, czy istnieje zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1b279-113">Indicates if a variable exists.</span></span> <span data-ttu-id="1b279-114">Ustawić tę właściwość na __obecny__ utworzyć zmienną środowiskową, jeśli nie istnieje lub upewnij się, że jego wartość odpowiada, jaka jest dostępna za pośrednictwem __wartość__ właściwości, jeśli zmienna już istnieje.</span><span class="sxs-lookup"><span data-stu-id="1b279-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="1b279-115">Ustaw ją na __nieobecne__ można usunąć zmiennej, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="1b279-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="1b279-116">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="1b279-116">Path</span></span>| <span data-ttu-id="1b279-117">Definiuje zmienną środowiskową, który jest konfigurowany.</span><span class="sxs-lookup"><span data-stu-id="1b279-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="1b279-118">Ta właściwość jest ustawiana __$true__ Jeśli zmienna jest __ścieżki__ zmiennej; w przeciwnym razie ustaw ją na __$false__.</span><span class="sxs-lookup"><span data-stu-id="1b279-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="1b279-119">Wartość domyślna to __$false__.</span><span class="sxs-lookup"><span data-stu-id="1b279-119">The default is __$false__.</span></span> <span data-ttu-id="1b279-120">Jeśli zmienna konfigurowany jest __ścieżki__ wartość zmiennej, realizowane za pośrednictwem __wartość__ właściwości, które zostaną dołączone do istniejącej wartości.</span><span class="sxs-lookup"><span data-stu-id="1b279-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="1b279-121">dependsOn</span><span class="sxs-lookup"><span data-stu-id="1b279-121">DependsOn</span></span> | <span data-ttu-id="1b279-122">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="1b279-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1b279-123">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1b279-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="1b279-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="1b279-124">Value</span></span>| <span data-ttu-id="1b279-125">Wartość do przypisania do zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="1b279-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="1b279-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b279-126">Example</span></span>

<span data-ttu-id="1b279-127">Poniższy przykład upewnia się, że __TestEnvironmentVariable__ jest obecny i ma wartość __WartośćTestowa__.</span><span class="sxs-lookup"><span data-stu-id="1b279-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="1b279-128">Jeśli nie jest obecny, tworzy go.</span><span class="sxs-lookup"><span data-stu-id="1b279-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```