---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób skryptu konfiguracji DSC"
ms.openlocfilehash: d3e231d33a04fd8a018ffe2f3d51a15360e0d312
ms.sourcegitcommit: 60f06a06c2fce63024f3f4cbd7657b1dfe7fcb1a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="dsc-script-resource"></a><span data-ttu-id="7b6b9-103">Zasób skryptu konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="7b6b9-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="7b6b9-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7b6b9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7b6b9-105">**Skryptu** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający uruchamianie blokach skryptu programu Windows PowerShell w węzłach docelowych.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="7b6b9-106">`Script` Zasób ma `GetScript`, `SetScript`, i `TestScript` właściwości.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="7b6b9-107">Te właściwości powinien mieć ustawioną w blokach skryptu, które będą uruchamiane w każdym węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="7b6b9-108">`GetScript` Bloku skryptu ma zwracać obiektu hashtable reprezentujący stan bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="7b6b9-109">Hashtable musi zawierać tylko jeden klucz `Result` i wartość musi być typu `String`.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="7b6b9-110">Zwraca niczego nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-110">It is not required to return anything.</span></span> <span data-ttu-id="7b6b9-111">DSC nie ma wpływu na dane wyjściowe tego bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="7b6b9-112">`TestScript` Bloku skryptu należy określić, czy bieżący węzeł ma zostać zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="7b6b9-113">Powinien on zwrócić `$true` Jeśli węzeł jest aktualny.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="7b6b9-114">Powinien on zwrócić `$false` Jeśli konfiguracji węzła jest przestarzały i powinien zostać zaktualizowany przez `SetScript` blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="7b6b9-115">`TestScript` Bloku skryptu jest wywoływana przez DSC.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="7b6b9-116">`SetScript` Bloku skryptu należy modyfikować węzła.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="7b6b9-117">Jeśli jest wywoływana przez DSC `TestScript` zablokować powrotu `$false`.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="7b6b9-118">Jeśli musisz używać zmiennych z skrypt konfiguracji w `GetScript`, `TestScript`, lub `SetScript` blokach skryptu, użyj `$using:` zakresu (patrz poniżej przedstawiono przykład).</span><span class="sxs-lookup"><span data-stu-id="7b6b9-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="7b6b9-119">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b6b9-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="7b6b9-120">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7b6b9-120">Properties</span></span>

|  <span data-ttu-id="7b6b9-121">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7b6b9-121">Property</span></span>  |  <span data-ttu-id="7b6b9-122">Opis</span><span class="sxs-lookup"><span data-stu-id="7b6b9-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="7b6b9-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="7b6b9-123">GetScript</span></span>| <span data-ttu-id="7b6b9-124">Zawiera blok skryptu programu Windows PowerShell, który uruchamia po wywołaniu [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="7b6b9-125">Ten blok musi zwracać obiektu hashtable.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-125">This block must return a hashtable.</span></span> <span data-ttu-id="7b6b9-126">Hashtable musi zawierać tylko jeden klucz **wynik** i wartość musi być typu **ciąg**.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="7b6b9-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="7b6b9-127">SetScript</span></span>| <span data-ttu-id="7b6b9-128">Zawiera blok skryptu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="7b6b9-129">Gdy wywołanie [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) polecenia cmdlet, **TestScript** bloku jest uruchamiany pierwszy.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="7b6b9-130">Jeśli **TestScript** zablokować zwraca **$false**, **SetScript** bloku zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="7b6b9-131">Jeśli **TestScript** zablokować zwraca **$true**, **SetScript** bloku nie zostaną uruchomione.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="7b6b9-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="7b6b9-132">TestScript</span></span>| <span data-ttu-id="7b6b9-133">Zawiera blok skryptu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="7b6b9-134">Podczas wywołania [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) działa ten blok polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="7b6b9-135">Jeśli zmienna zwraca **$false**, blok SetScript zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="7b6b9-136">Jeśli zmienna zwraca **$true**, SetScript będzie blok, nie działać.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="7b6b9-137">**TestScript** bloku również uruchamiane przy wywołaniu [DscConfiguration testu](https://technet.microsoft.com/en-us/library/dn407382.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="7b6b9-138">Jednak w tym przypadku **SetScript** nie Uruchom, niezależnie od tego, jaka wartość TestScript zablokować zwraca bloku.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="7b6b9-139">**TestScript** bloku musi zwracać wartość True, jeśli rzeczywista konfiguracja zgodny z bieżącej konfiguracji żądanego stanu i wartość False, jeśli nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="7b6b9-140">(W bieżącej konfiguracji żądanego stanu jest ostatniej konfiguracji wdrożonymi na węźle, który używa DSC).</span><span class="sxs-lookup"><span data-stu-id="7b6b9-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="7b6b9-141">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="7b6b9-141">Credential</span></span>| <span data-ttu-id="7b6b9-142">Określa poświadczenia na potrzeby uruchomienie tego skryptu, jeśli są wymagane poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="7b6b9-143">dependsOn</span><span class="sxs-lookup"><span data-stu-id="7b6b9-143">DependsOn</span></span>| <span data-ttu-id="7b6b9-144">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7b6b9-145">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest **ResourceName** i jej typ jest **ResourceType**, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="7b6b9-146">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="7b6b9-146">Example 1</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="7b6b9-147">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="7b6b9-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Result'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = { 
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="7b6b9-148">Ten zasób jest zapisywania wersji konfiguracji do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="7b6b9-149">Ta wersja jest dostępna na komputerze klienckim, ale nie znajduje się w dowolny z węzłów, więc musi zostać przekazane do każdego z `Script` blokach skryptu zasobu przy użyciu programu PowerShell w `using` zakresu.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="7b6b9-150">Podczas generowania MOF węzła pliku, wartość `$version` zmiennej jest do odczytu z pliku tekstowego na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="7b6b9-151">Zamienia DSC `$using:version` zablokować zmiennych w każdego skryptu z wartością `$version` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7b6b9-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

