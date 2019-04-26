---
ms.date: 08/24/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC skryptu
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076994"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="a89f9-103">Zasób DSC skryptu</span><span class="sxs-lookup"><span data-stu-id="a89f9-103">DSC Script Resource</span></span>

> <span data-ttu-id="a89f9-104">Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="a89f9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="a89f9-105">**Skryptu** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do uruchomienia Bloki skryptu programu Windows PowerShell w węzłach docelowych.</span><span class="sxs-lookup"><span data-stu-id="a89f9-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="a89f9-106">**Skryptu** używa zasobów `GetScript`, `SetScript`, i `TestScript` właściwości, które zawierają Bloki skryptu należy zdefiniować do wykonania odpowiednich DSC stanu operacji.</span><span class="sxs-lookup"><span data-stu-id="a89f9-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="a89f9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a89f9-107">Syntax</span></span>

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

> [!NOTE]
> <span data-ttu-id="a89f9-108">`GetScript`, `TestScript`, I `SetScript` bloki są przechowywane w postaci ciągów.</span><span class="sxs-lookup"><span data-stu-id="a89f9-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="a89f9-109">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a89f9-109">Properties</span></span>

|<span data-ttu-id="a89f9-110">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a89f9-110">Property</span></span>|<span data-ttu-id="a89f9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a89f9-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="a89f9-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="a89f9-112">GetScript</span></span>|<span data-ttu-id="a89f9-113">Blok skryptu, który zwraca bieżący stan węzła.</span><span class="sxs-lookup"><span data-stu-id="a89f9-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="a89f9-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="a89f9-114">SetScript</span></span>|<span data-ttu-id="a89f9-115">Blok skryptu DSC są używane do wymuszania zgodności, gdy węzeł nie jest w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="a89f9-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="a89f9-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="a89f9-116">TestScript</span></span>|<span data-ttu-id="a89f9-117">Blok skryptu, który określa, czy węzeł jest w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="a89f9-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="a89f9-118">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="a89f9-118">Credential</span></span>| <span data-ttu-id="a89f9-119">Określa poświadczenia do użycia dla tego skryptu, jeśli wymagane są poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="a89f9-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="a89f9-120">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a89f9-120">DependsOn</span></span>| <span data-ttu-id="a89f9-121">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="a89f9-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a89f9-122">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a89f9-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="a89f9-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="a89f9-123">GetScript</span></span>

<span data-ttu-id="a89f9-124">DSC nie używa danych wyjściowych `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="a89f9-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="a89f9-125">[Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) wykonuje polecenie cmdlet `GetScript` można pobrać stanu bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="a89f9-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="a89f9-126">Wartość zwracana nie jest wymagana od `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="a89f9-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="a89f9-127">Jeśli określisz wartość zwracana, musi on być `hashtable` zawierający **wynik** klucz, którego wartością jest `String`.</span><span class="sxs-lookup"><span data-stu-id="a89f9-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="a89f9-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="a89f9-128">TestScript</span></span>

<span data-ttu-id="a89f9-129">`TestScript` Jest wykonywana przez DSC, aby określić, czy `SetScript` powinien zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a89f9-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="a89f9-130">Jeśli `TestScript` zwraca `$false`, wykonuje DSC `SetScript` można przenieść węzeł z powrotem do żądanego stanu.</span><span class="sxs-lookup"><span data-stu-id="a89f9-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="a89f9-131">Aplikacja musi zwracać `boolean` wartość.</span><span class="sxs-lookup"><span data-stu-id="a89f9-131">It must return a `boolean` value.</span></span> <span data-ttu-id="a89f9-132">Wynikiem `$true` wskazuje, że węzeł jest zgodny i `SetScript` nie powinien wykonać.</span><span class="sxs-lookup"><span data-stu-id="a89f9-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="a89f9-133">[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) wykonuje polecenia cmdlet, `TestScript` można pobrać zgodności węzłów z **skryptu** zasobów.</span><span class="sxs-lookup"><span data-stu-id="a89f9-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="a89f9-134">Jednak w tym przypadku `SetScript` nie działa, niezależnie od tego, co `TestScript` block zwraca.</span><span class="sxs-lookup"><span data-stu-id="a89f9-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="a89f9-135">Wszystkie dane wyjściowe z Twojej `TestScript` jest częścią jego zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="a89f9-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="a89f9-136">Program PowerShell interpretuje unsuppressed danych wyjściowych w formacie różna od zera, co oznacza, że Twoje `TestScript` zwróci `$true` niezależnie od tego, stan tego węzła.</span><span class="sxs-lookup"><span data-stu-id="a89f9-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="a89f9-137">To powoduje produkuje nieoczekiwanych rezultatów, wyniki fałszywie dodatnie i powoduje trudności podczas rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="a89f9-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="a89f9-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="a89f9-138">SetScript</span></span>

<span data-ttu-id="a89f9-139">`SetScript` Modyfikuje węzła do wymuszenia żądanego stanu.</span><span class="sxs-lookup"><span data-stu-id="a89f9-139">The `SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="a89f9-140">Jest ona wywoływana przez DSC, jeśli `TestScript` skrypt zwraca blok `$false`.</span><span class="sxs-lookup"><span data-stu-id="a89f9-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="a89f9-141">`SetScript` Powinna posiadać wartości zwrotnej.</span><span class="sxs-lookup"><span data-stu-id="a89f9-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="a89f9-142">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a89f9-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="a89f9-143">Przykład 1: Zapisywanie tekstu próbki, przy użyciu skryptu zasobu</span><span class="sxs-lookup"><span data-stu-id="a89f9-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="a89f9-144">W tym przykładzie, sprawdza istnienie `C:\TempFolder\TestFile.txt` w każdym węźle.</span><span class="sxs-lookup"><span data-stu-id="a89f9-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="a89f9-145">Jeśli nie istnieje, tworzy go za pomocą `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="a89f9-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="a89f9-146">`GetScript` Zwraca zawartość pliku i jego wartość zwracana nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="a89f9-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="a89f9-147">Przykład 2: Porównywanie informacji dotyczących wersji przy użyciu skryptu zasobu</span><span class="sxs-lookup"><span data-stu-id="a89f9-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="a89f9-148">W tym przykładzie pobiera *zgodne* informacje o wersji z pliku tekstowego na komputerze, do tworzenia i zapisuje go w `$version` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a89f9-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="a89f9-149">Podczas generowania pliku MOF tego węzła, DSC zastępuje `$using:version` zmiennych w każdego skryptu blokowania z wartością `$version` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a89f9-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="a89f9-150">W czasie wykonywania *zgodne* wersji jest przechowywany w pliku tekstowym w każdym węźle w porównaniu i aktualizowane na kolejne wykonania.</span><span class="sxs-lookup"><span data-stu-id="a89f9-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

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
}
```
