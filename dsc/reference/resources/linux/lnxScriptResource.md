---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux nxScript zasobów
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048401"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="5280e-103">DSC dla systemu Linux nxScript zasobów</span><span class="sxs-lookup"><span data-stu-id="5280e-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="5280e-104">**NxScript** zasobów w programie PowerShell Desired State Configuration (DSC) udostępnia mechanizm do uruchamiania skryptów systemu Linux w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="5280e-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5280e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5280e-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="5280e-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5280e-106">Properties</span></span>

|  <span data-ttu-id="5280e-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5280e-107">Property</span></span> |  <span data-ttu-id="5280e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5280e-108">Description</span></span> |
|---|---|
| <span data-ttu-id="5280e-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="5280e-109">GetScript</span></span>| <span data-ttu-id="5280e-110">Zawiera skrypt, który jest uruchamiany, gdy wywołujesz [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5280e-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="5280e-111">Skrypt musi zaczynać się od shebang, takich jak #! / bin/powłoki bash.</span><span class="sxs-lookup"><span data-stu-id="5280e-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="5280e-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="5280e-112">SetScript</span></span>| <span data-ttu-id="5280e-113">Zawiera skrypt.</span><span class="sxs-lookup"><span data-stu-id="5280e-113">Provides a script.</span></span> <span data-ttu-id="5280e-114">Gdy wywołujesz [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, **TestScript** działa jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="5280e-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="5280e-115">Jeśli **TestScript** bloku zwraca kod zakończenia różny od 0, **SetScript** blok zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5280e-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="5280e-116">Jeśli **TestScript** zwraca kod zakończenia 0, **SetScript** nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="5280e-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="5280e-117">Skrypt musi zaczynać się od shebang, takich jak `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="5280e-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="5280e-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="5280e-118">TestScript</span></span>| <span data-ttu-id="5280e-119">Zawiera skrypt.</span><span class="sxs-lookup"><span data-stu-id="5280e-119">Provides a script.</span></span> <span data-ttu-id="5280e-120">Gdy wywołujesz [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, ten skrypt jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="5280e-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="5280e-121">Jeśli zwróci ona kod zakończenia różny od 0, SetScript zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5280e-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="5280e-122">Jeśli zwróci ona kod zakończenia 0, **SetScript** nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="5280e-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="5280e-123">**TestScript** również jest uruchamiany, gdy wywołujesz [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5280e-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="5280e-124">Jednak w tym przypadku **SetScript** nie będzie działać niezależnie od tego, jaki kod zakończenia jest zwracana z **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="5280e-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="5280e-125">**TestScript** musi zwracać kod zakończenia 0, jeśli rzeczywistą konfigurację odpowiada bieżącej konfiguracji żądanego stanu, a wyjście kodu inne niż 0, jeśli nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="5280e-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="5280e-126">(Ostatnia konfiguracja wdrożonymi na węzeł, który używa DSC jest bieżąca konfiguracja żądanego stanu).</span><span class="sxs-lookup"><span data-stu-id="5280e-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="5280e-127">Skrypt musi zaczynać się od shebang, na przykład 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="5280e-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="5280e-128">Użytkownik</span><span class="sxs-lookup"><span data-stu-id="5280e-128">User</span></span>| <span data-ttu-id="5280e-129">Użytkownik do uruchomienia skryptu jako.</span><span class="sxs-lookup"><span data-stu-id="5280e-129">The user to run the script as.</span></span>|
| <span data-ttu-id="5280e-130">Grupa</span><span class="sxs-lookup"><span data-stu-id="5280e-130">Group</span></span>| <span data-ttu-id="5280e-131">Grupa, aby uruchomić skrypt jako.</span><span class="sxs-lookup"><span data-stu-id="5280e-131">The group to run the script as.</span></span>|
| <span data-ttu-id="5280e-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5280e-132">DependsOn</span></span> | <span data-ttu-id="5280e-133">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="5280e-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5280e-134">Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5280e-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="5280e-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="5280e-135">Example</span></span>

<span data-ttu-id="5280e-136">W poniższym przykładzie pokazano użycie **nxScript** zasobów do wykonania dodatkowych funkcji zarządzania konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="5280e-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

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