---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux nxScript zasobów
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077827"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="f0270-103">DSC dla systemu Linux nxScript zasobów</span><span class="sxs-lookup"><span data-stu-id="f0270-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="f0270-104">**NxScript** zasobów w programie PowerShell Desired State Configuration (DSC) udostępnia mechanizm do uruchamiania skryptów systemu Linux w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="f0270-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0270-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0270-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f0270-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f0270-106">Properties</span></span>

|  <span data-ttu-id="f0270-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f0270-107">Property</span></span> |  <span data-ttu-id="f0270-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f0270-108">Description</span></span> |
|---|---|
| <span data-ttu-id="f0270-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="f0270-109">GetScript</span></span>| <span data-ttu-id="f0270-110">Zawiera skrypt, który jest uruchamiany, gdy wywołujesz [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0270-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="f0270-111">Skrypt musi zaczynać się od shebang, takich jak #! / bin/powłoki bash.</span><span class="sxs-lookup"><span data-stu-id="f0270-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="f0270-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="f0270-112">SetScript</span></span>| <span data-ttu-id="f0270-113">Zawiera skrypt.</span><span class="sxs-lookup"><span data-stu-id="f0270-113">Provides a script.</span></span> <span data-ttu-id="f0270-114">Gdy wywołujesz [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, **TestScript** działa jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="f0270-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="f0270-115">Jeśli **TestScript** bloku zwraca kod zakończenia różny od 0, **SetScript** blok zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="f0270-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="f0270-116">Jeśli **TestScript** zwraca kod zakończenia 0, **SetScript** nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="f0270-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="f0270-117">Skrypt musi zaczynać się od shebang, takich jak `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="f0270-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="f0270-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="f0270-118">TestScript</span></span>| <span data-ttu-id="f0270-119">Zawiera skrypt.</span><span class="sxs-lookup"><span data-stu-id="f0270-119">Provides a script.</span></span> <span data-ttu-id="f0270-120">Gdy wywołujesz [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, ten skrypt jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="f0270-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="f0270-121">Jeśli zwróci ona kod zakończenia różny od 0, SetScript zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="f0270-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="f0270-122">Jeśli zwróci ona kod zakończenia 0, **SetScript** nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="f0270-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="f0270-123">**TestScript** również jest uruchamiany, gdy wywołujesz [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0270-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="f0270-124">Jednak w tym przypadku **SetScript** nie będzie działać niezależnie od tego, jaki kod zakończenia jest zwracana z **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="f0270-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="f0270-125">**TestScript** musi zwracać kod zakończenia 0, jeśli rzeczywistą konfigurację odpowiada bieżącej konfiguracji żądanego stanu, a wyjście kodu inne niż 0, jeśli nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="f0270-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="f0270-126">(Ostatnia konfiguracja wdrożonymi na węzeł, który używa DSC jest bieżąca konfiguracja żądanego stanu).</span><span class="sxs-lookup"><span data-stu-id="f0270-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="f0270-127">Skrypt musi zaczynać się od shebang, na przykład 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="f0270-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="f0270-128">Użytkownik</span><span class="sxs-lookup"><span data-stu-id="f0270-128">User</span></span>| <span data-ttu-id="f0270-129">Użytkownik do uruchomienia skryptu jako.</span><span class="sxs-lookup"><span data-stu-id="f0270-129">The user to run the script as.</span></span>|
| <span data-ttu-id="f0270-130">Grupa</span><span class="sxs-lookup"><span data-stu-id="f0270-130">Group</span></span>| <span data-ttu-id="f0270-131">Grupa, aby uruchomić skrypt jako.</span><span class="sxs-lookup"><span data-stu-id="f0270-131">The group to run the script as.</span></span>|
| <span data-ttu-id="f0270-132">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f0270-132">DependsOn</span></span> | <span data-ttu-id="f0270-133">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="f0270-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f0270-134">Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f0270-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="f0270-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0270-135">Example</span></span>

<span data-ttu-id="f0270-136">W poniższym przykładzie pokazano użycie **nxScript** zasobów do wykonania dodatkowych funkcji zarządzania konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="f0270-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

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