---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Instrukcje warunkowe i pętle w konfiguracjach
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55689050"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="8612b-103">Instrukcje warunkowe i pętle w konfiguracjach</span><span class="sxs-lookup"><span data-stu-id="8612b-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="8612b-104">Możesz wprowadzić swoje [konfiguracje](configurations.md) bardziej dynamiczne, przy użyciu słów kluczowych sterowanie przepływem programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8612b-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="8612b-105">W tym artykule opisano, jak można użyć instrukcje warunkowe i pętle się bardziej dynamiczne konfiguracje.</span><span class="sxs-lookup"><span data-stu-id="8612b-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="8612b-106">Połączenie warunkowe i pętle z [parametry](add-parameters-to-a-configuration.md) i [dane konfiguracyjne](configData.md) umożliwia większą elastyczność i kontrolę podczas kompilowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8612b-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="8612b-107">Podobnie jak funkcja lub blok skryptu można użyć dowolnego języka programu PowerShell w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8612b-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="8612b-108">Instrukcji, których można używać tylko zostaną ocenione, gdy wywołujesz konfigurację tak, aby skompilować pliku "MOF".</span><span class="sxs-lookup"><span data-stu-id="8612b-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="8612b-109">Poniższe przykłady pokazują prostych scenariuszy do zademonstrowania koncepcji.</span><span class="sxs-lookup"><span data-stu-id="8612b-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="8612b-110">Instrukcje warunkowe są pętli częściej są używane z parametrami i dane konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8612b-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="8612b-111">W tym prostym przykładzie **usługi** bloku zasobów pobiera bieżący stan usługi w czasie kompilacji, aby wygenerować plik "MOF", który przechowuje swojego bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="8612b-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="8612b-112">Przy użyciu dynamicznych bloków zasobów będzie wywłaszczenia skuteczności Intellisense.</span><span class="sxs-lookup"><span data-stu-id="8612b-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="8612b-113">Analizator składni programu PowerShell nie można określić, jeśli określone wartości są akceptowane, dopóki jest kompilowana konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="8612b-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="8612b-114">Ponadto można utworzyć **usługi** blokowania zasobów dla każdej usługi na bieżącym komputerze przy użyciu `foreach` pętli.</span><span class="sxs-lookup"><span data-stu-id="8612b-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="8612b-115">Można również tylko utworzyć konfiguracje dla maszyn, które są w trybie online, za pomocą prostego `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8612b-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="8612b-116">Zasób dynamiczny bloków w powyższych odwołań przykłady bieżącej maszyny.</span><span class="sxs-lookup"><span data-stu-id="8612b-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="8612b-117">W tym wystąpieniu, które będą maszyny tworzenia konfiguracji na nie element docelowy węzła.</span><span class="sxs-lookup"><span data-stu-id="8612b-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="8612b-118">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="8612b-118">Summary</span></span>

<span data-ttu-id="8612b-119">Podsumowując można użyć dowolnego języka programu PowerShell w ramach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8612b-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="8612b-120">Obejmuje to np.:</span><span class="sxs-lookup"><span data-stu-id="8612b-120">This includes things like:</span></span>

- <span data-ttu-id="8612b-121">Niestandardowe obiekty</span><span class="sxs-lookup"><span data-stu-id="8612b-121">Custom Objects</span></span>
- <span data-ttu-id="8612b-122">Tabele</span><span class="sxs-lookup"><span data-stu-id="8612b-122">Hashtables</span></span>
- <span data-ttu-id="8612b-123">Manipulowanie ciągami</span><span class="sxs-lookup"><span data-stu-id="8612b-123">String manipulation</span></span>
- <span data-ttu-id="8612b-124">Komunikacja zdalna</span><span class="sxs-lookup"><span data-stu-id="8612b-124">Remoting</span></span>
- <span data-ttu-id="8612b-125">Usługa WMI i CIM</span><span class="sxs-lookup"><span data-stu-id="8612b-125">WMI and CIM</span></span>
- <span data-ttu-id="8612b-126">Obiekty ActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="8612b-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="8612b-127">i więcej...</span><span class="sxs-lookup"><span data-stu-id="8612b-127">and more...</span></span>

<span data-ttu-id="8612b-128">Każdy kod programu PowerShell, zdefiniowane w konfiguracji będą oceniane czasu kompilacji, ale możesz również umieścić kod w skrypcie zawierający konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8612b-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="8612b-129">Każdy kod poza blokiem konfiguracji zostaną wykonane podczas importowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8612b-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="8612b-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8612b-130">See also</span></span>

- [<span data-ttu-id="8612b-131">Dodaj parametry konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8612b-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="8612b-132">Oddzielenie danych konfiguracji z konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8612b-132">Separate Configuration data from Configurations</span></span>](configData.md)
