---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Zasób DSC dla nxScript systemu Linux
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372163"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="4d073-103">Zasób DSC dla nxScript systemu Linux</span><span class="sxs-lookup"><span data-stu-id="4d073-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="4d073-104">Zasób **nxScript** w konfiguracji żądanego stanu (DSC) programu PowerShell zapewnia mechanizm uruchamiania skryptów systemu Linux w węźle z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="4d073-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d073-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d073-105">Syntax</span></span>

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="4d073-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4d073-106">Properties</span></span>

|  <span data-ttu-id="4d073-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4d073-107">Property</span></span> |  <span data-ttu-id="4d073-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4d073-108">Description</span></span> |
|---|---|
| <span data-ttu-id="4d073-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="4d073-109">GetScript</span></span>| <span data-ttu-id="4d073-110">Zapewnia skrypt do zwrócenia bieżącego stanu maszyny.</span><span class="sxs-lookup"><span data-stu-id="4d073-110">Provides a script to return current status of the machine.</span></span>  <span data-ttu-id="4d073-111">Ten skrypt jest uruchamiany po wywołaniu skryptu [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) .</span><span class="sxs-lookup"><span data-stu-id="4d073-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="4d073-112">Skrypt musi rozpoczynać się od Shebang, na przykład #!/bin/bash.</span><span class="sxs-lookup"><span data-stu-id="4d073-112">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="4d073-113">Setscript</span><span class="sxs-lookup"><span data-stu-id="4d073-113">SetScript</span></span>| <span data-ttu-id="4d073-114">Zapewnia skrypt, który umieszcza maszynę w poprawnym stanie.</span><span class="sxs-lookup"><span data-stu-id="4d073-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="4d073-115">Po wywołaniu skryptu [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) , **TestScript** działa najpierw.</span><span class="sxs-lookup"><span data-stu-id="4d073-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="4d073-116">Jeśli blok **TestScript** zwraca kod zakończenia inny niż 0, zostanie uruchomiony blok **setscript** .</span><span class="sxs-lookup"><span data-stu-id="4d073-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="4d073-117">Jeśli **TestScript** zwraca kod zakończenia 0, setscript nie zostanie  uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="4d073-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="4d073-118">Skrypt musi rozpoczynać się od Shebang, `#!/bin/bash`na przykład.</span><span class="sxs-lookup"><span data-stu-id="4d073-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="4d073-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="4d073-119">TestScript</span></span>| <span data-ttu-id="4d073-120">Zawiera skrypt, który sprawdza, czy węzeł jest aktualnie w odpowiednim stanie.</span><span class="sxs-lookup"><span data-stu-id="4d073-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="4d073-121">Po wywołaniu skryptu [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) ten skrypt jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="4d073-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="4d073-122">Jeśli zwraca kod zakończenia inny niż 0, zostanie uruchomiony setscript.</span><span class="sxs-lookup"><span data-stu-id="4d073-122">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="4d073-123">Jeśli zwraca kod zakończenia 0, setscript nie zostanie  uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="4d073-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="4d073-124">**TestScript** jest również uruchamiany po wywołaniu skryptu [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) .</span><span class="sxs-lookup"><span data-stu-id="4d073-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="4d073-125">Jednak w tym przypadku setscript nie  zostanie uruchomiony, niezależnie od tego, jaki kod zakończenia jest zwracany z **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="4d073-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="4d073-126">**TestScript** musi zawierać zawartość i musi zwracać kod zakończenia 0, jeśli rzeczywista konfiguracja jest zgodna z bieżącą konfiguracją żądanego stanu, a kod zakończenia inny niż 0, jeśli jest niezgodny.</span><span class="sxs-lookup"><span data-stu-id="4d073-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="4d073-127">(Bieżąca Konfiguracja żądanego stanu to Ostatnia konfiguracja wdrożona w węźle, który korzysta z DSC).</span><span class="sxs-lookup"><span data-stu-id="4d073-127">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="4d073-128">Skrypt musi rozpoczynać się od elementu Shebang, takiego jak 1 #!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="4d073-128">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="4d073-129">Użytkownik</span><span class="sxs-lookup"><span data-stu-id="4d073-129">User</span></span>| <span data-ttu-id="4d073-130">Użytkownik uruchamiający skrypt jako.</span><span class="sxs-lookup"><span data-stu-id="4d073-130">The user to run the script as.</span></span>|
| <span data-ttu-id="4d073-131">Grupa</span><span class="sxs-lookup"><span data-stu-id="4d073-131">Group</span></span>| <span data-ttu-id="4d073-132">Grupa, w której ma zostać uruchomiony skrypt.</span><span class="sxs-lookup"><span data-stu-id="4d073-132">The group to run the script as.</span></span>|
| <span data-ttu-id="4d073-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4d073-133">DependsOn</span></span> | <span data-ttu-id="4d073-134">Wskazuje, że konfiguracja innego zasobu musi być uruchomiona przed skonfigurowaniem tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="4d073-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4d073-135">Na przykład, jeśli **Identyfikator** bloku skryptu konfiguracji zasobu, który ma zostać uruchomiony jako pierwszy jest resourceName, a jego typ to ResourceType, Składnia służąca do użycia tej `DependsOn = "[ResourceType]ResourceName"`właściwości to.</span><span class="sxs-lookup"><span data-stu-id="4d073-135">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="4d073-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d073-136">Example</span></span>

<span data-ttu-id="4d073-137">Poniższy przykład demonstruje użycie zasobu **nxScript** do wykonania dodatkowego zarządzania konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="4d073-137">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```
