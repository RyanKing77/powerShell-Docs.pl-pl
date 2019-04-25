---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób środowiska DSC
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077538"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="eed2a-103">Zasób środowiska DSC</span><span class="sxs-lookup"><span data-stu-id="eed2a-103">DSC Environment Resource</span></span>

> <span data-ttu-id="eed2a-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eed2a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="eed2a-105">__Środowiska__ zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania systemowe zmienne środowiskowe.</span><span class="sxs-lookup"><span data-stu-id="eed2a-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="eed2a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="eed2a-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="eed2a-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="eed2a-107">Properties</span></span>

|  <span data-ttu-id="eed2a-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="eed2a-108">Property</span></span>  |  <span data-ttu-id="eed2a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="eed2a-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="eed2a-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="eed2a-110">Name</span></span>| <span data-ttu-id="eed2a-111">Wskazuje nazwę zmiennej środowiskowej, dla którego chcesz zapewnić określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="eed2a-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="eed2a-112">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="eed2a-112">Ensure</span></span>| <span data-ttu-id="eed2a-113">Wskazuje, czy zmienna istnieje.</span><span class="sxs-lookup"><span data-stu-id="eed2a-113">Indicates if a variable exists.</span></span> <span data-ttu-id="eed2a-114">Ustaw tę właściwość na __obecne__ Utwórz zmienną środowiskową, jeśli nie istnieje lub upewnij się, że jego wartość odpowiada, co to jest oferowana w ramach __wartość__ właściwość, jeśli zmienna już istnieje.</span><span class="sxs-lookup"><span data-stu-id="eed2a-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="eed2a-115">Ustaw ją na __nieobecne__ można usunąć zmiennej, jeśli taki istnieje.</span><span class="sxs-lookup"><span data-stu-id="eed2a-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="eed2a-116">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="eed2a-116">Path</span></span>| <span data-ttu-id="eed2a-117">Definiuje zmienną środowiskową, która jest konfigurowana.</span><span class="sxs-lookup"><span data-stu-id="eed2a-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="eed2a-118">Ustaw tę właściwość na __$true__ , gdy zmienna __ścieżki__ zmiennej; w przeciwnym razie ustaw ją na __$false__.</span><span class="sxs-lookup"><span data-stu-id="eed2a-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="eed2a-119">Wartość domyślna to __$false__.</span><span class="sxs-lookup"><span data-stu-id="eed2a-119">The default is __$false__.</span></span> <span data-ttu-id="eed2a-120">Jeśli zmienna konfigurowany jest __ścieżki__ podana wartość zmiennej, za pośrednictwem __wartość__ właściwości, które zostaną dołączone do istniejącej wartości.</span><span class="sxs-lookup"><span data-stu-id="eed2a-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="eed2a-121">dependsOn</span><span class="sxs-lookup"><span data-stu-id="eed2a-121">DependsOn</span></span> | <span data-ttu-id="eed2a-122">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="eed2a-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="eed2a-123">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="eed2a-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="eed2a-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="eed2a-124">Value</span></span>| <span data-ttu-id="eed2a-125">Wartość do przypisania do zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="eed2a-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="eed2a-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="eed2a-126">Example</span></span>

<span data-ttu-id="eed2a-127">Poniższy przykład zapewnia, że __TestEnvironmentVariable__ jest obecny i ma wartość __WartośćTestowa__.</span><span class="sxs-lookup"><span data-stu-id="eed2a-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="eed2a-128">Jeśli nie jest obecny, tworzy go.</span><span class="sxs-lookup"><span data-stu-id="eed2a-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```