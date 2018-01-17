---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "DSC dla systemu Linux nxScript zasobów"
ms.openlocfilehash: c12fb3b405d84eedd13e4cbebf2b2bf0d7cfb4d3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="51b5b-103">DSC dla systemu Linux nxScript zasobów</span><span class="sxs-lookup"><span data-stu-id="51b5b-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="51b5b-104">**NxScript** zasobów w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm na uruchamianie skryptów systemu Linux w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="51b5b-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="51b5b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="51b5b-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="51b5b-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="51b5b-106">Properties</span></span>

|  <span data-ttu-id="51b5b-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="51b5b-107">Property</span></span> |  <span data-ttu-id="51b5b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="51b5b-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="51b5b-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="51b5b-109">GetScript</span></span>| <span data-ttu-id="51b5b-110">Udostępnia skryptu uruchamianego po wywołaniu [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51b5b-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="51b5b-111">Skrypt musi rozpoczynać się od shebang, takie jak #! / bin/bash.</span><span class="sxs-lookup"><span data-stu-id="51b5b-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>| 
| <span data-ttu-id="51b5b-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="51b5b-112">SetScript</span></span>| <span data-ttu-id="51b5b-113">Zawiera skrypt.</span><span class="sxs-lookup"><span data-stu-id="51b5b-113">Provides a script.</span></span> <span data-ttu-id="51b5b-114">Gdy wywołanie [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, **TestScript** jest uruchamiany pierwszy.</span><span class="sxs-lookup"><span data-stu-id="51b5b-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="51b5b-115">Jeśli **TestScript** bloku zwraca kod zakończenia innego niż 0, **SetScript** bloku zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="51b5b-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="51b5b-116">Jeśli **TestScript** zwraca kod zakończenia 0, **SetScript** nie zostaną uruchomione.</span><span class="sxs-lookup"><span data-stu-id="51b5b-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="51b5b-117">Skrypt musi rozpoczynać się od shebang, takich jak `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="51b5b-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>| 
| <span data-ttu-id="51b5b-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="51b5b-118">TestScript</span></span>| <span data-ttu-id="51b5b-119">Zawiera skrypt.</span><span class="sxs-lookup"><span data-stu-id="51b5b-119">Provides a script.</span></span> <span data-ttu-id="51b5b-120">Gdy wywołanie [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, ten skrypt jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="51b5b-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="51b5b-121">Jeśli zwróci ona kod zakończenia innego niż 0, SetScript zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="51b5b-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="51b5b-122">Jeśli zwróci ona kod zakończenia 0, **SetScript** nie zostaną uruchomione.</span><span class="sxs-lookup"><span data-stu-id="51b5b-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="51b5b-123">**TestScript** również uruchamiane przy wywołaniu [DscConfiguration testu](https://technet.microsoft.com/en-us/library/dn407382.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51b5b-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="51b5b-124">Jednak w tym przypadku **SetScript** nie zostaną uruchomione, niezależnie od tego, jaki kod zakończenia jest zwracana z **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="51b5b-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="51b5b-125">**TestScript** musi zwracać kod zakończenia 0, jeśli rzeczywista konfiguracja pasuje bieżącej konfiguracji żądanego stanu, a wyjście kodu inne niż 0, jeśli nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="51b5b-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="51b5b-126">(W bieżącej konfiguracji żądanego stanu jest ostatniej konfiguracji wdrożonymi na węźle, który używa DSC).</span><span class="sxs-lookup"><span data-stu-id="51b5b-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="51b5b-127">Skrypt musi rozpoczynać się od shebang, takich jak 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="51b5b-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>| 
| <span data-ttu-id="51b5b-128">Użytkownik</span><span class="sxs-lookup"><span data-stu-id="51b5b-128">User</span></span>| <span data-ttu-id="51b5b-129">Użytkownik, który umożliwia uruchomienie skryptu jako.</span><span class="sxs-lookup"><span data-stu-id="51b5b-129">The user to run the script as.</span></span>| 
| <span data-ttu-id="51b5b-130">Grupa</span><span class="sxs-lookup"><span data-stu-id="51b5b-130">Group</span></span>| <span data-ttu-id="51b5b-131">Grupa, aby uruchomić skrypt jako.</span><span class="sxs-lookup"><span data-stu-id="51b5b-131">The group to run the script as.</span></span>| 
| <span data-ttu-id="51b5b-132">dependsOn</span><span class="sxs-lookup"><span data-stu-id="51b5b-132">DependsOn</span></span> | <span data-ttu-id="51b5b-133">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="51b5b-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="51b5b-134">Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="51b5b-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="51b5b-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="51b5b-135">Example</span></span>

<span data-ttu-id="51b5b-136">W poniższym przykładzie pokazano użycie **nxScript** zasobów do wykonania dodatkowych czynności konfiguracyjnych zarządzania.</span><span class="sxs-lookup"><span data-stu-id="51b5b-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

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

