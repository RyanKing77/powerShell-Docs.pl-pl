---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)
ms.openlocfilehash: fc118fd8b0d91d2001030769ac7e3c6321972905
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="758b5-103">Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)</span><span class="sxs-lookup"><span data-stu-id="758b5-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="758b5-104">**Uwaga:** w tym temacie opisano najlepszym rozwiązaniem do definiowania zasobów DSC, który umożliwia tylko jedno wystąpienie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="758b5-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="758b5-105">Obecnie nie są ma wbudowanej funkcji DSC w tym celu.</span><span class="sxs-lookup"><span data-stu-id="758b5-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="758b5-106">Który mogą ulec zmianie w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="758b5-106">That might change in the future.</span></span>

<span data-ttu-id="758b5-107">Istnieją sytuacje, w których nie chcesz zezwolić zasobu jest używana wiele razy w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="758b5-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="758b5-108">Na przykład w poprzedniej implementacji [xTimeZone](https://github.com/PowerShell/xTimeZone) zasobów, konfiguracji można wywołać zasobu wielokrotnie, ustawienie strefy czasowej na inne ustawienie w każdym bloku zasobów:</span><span class="sxs-lookup"><span data-stu-id="758b5-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

<span data-ttu-id="758b5-109">Jest to spowodowane sposób pracy klucze zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="758b5-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="758b5-110">Zasób musi mieć co najmniej jedną właściwość klucza.</span><span class="sxs-lookup"><span data-stu-id="758b5-110">A resource must have at least one key property.</span></span> <span data-ttu-id="758b5-111">Wystąpienie zasobu jest traktowany jako unikatowy, jeśli kombinacja wartości wszystkich właściwości klucza są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="758b5-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="758b5-112">W jego poprzedniej implementacji [xTimeZone](https://github.com/PowerShell/xTimeZone) zasobów ma tylko jedną właściwość--**strefy czasowej**, który został musi być kluczem.</span><span class="sxs-lookup"><span data-stu-id="758b5-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="758b5-113">W związku z tym konfiguracji, takie jak powyżej czy kompilowanie i uruchamianie bez ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="758b5-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="758b5-114">Każdy z **xTimeZone** bloki zasobów jest uznawany za unikatowy.</span><span class="sxs-lookup"><span data-stu-id="758b5-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="758b5-115">To spowoduje konfiguracji wielokrotnie stosowane do tego węzła, cyklicznie strefa czasowa i z powrotem.</span><span class="sxs-lookup"><span data-stu-id="758b5-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="758b5-116">Zapewnienie konfiguracji można ustawić strefę czasową dla węzła docelowego tylko raz, zasób został zaktualizowano w celu dodania drugiej właściwości **IsSingleInstance**, które stały się właściwości klucza.</span><span class="sxs-lookup"><span data-stu-id="758b5-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="758b5-117">**IsSingleInstance** został ograniczony do pojedynczą wartość "Tak" przy użyciu **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="758b5-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="758b5-118">Stary schematu MOF dla zasobu to:</span><span class="sxs-lookup"><span data-stu-id="758b5-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="758b5-119">Zaktualizowany schemat MOF dla zasobu to:</span><span class="sxs-lookup"><span data-stu-id="758b5-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="758b5-120">Skrypt zasobu Zaktualizowano również, aby użyć nowego parametru.</span><span class="sxs-lookup"><span data-stu-id="758b5-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="758b5-121">Oto starego skryptu zasobu:</span><span class="sxs-lookup"><span data-stu-id="758b5-121">Here is the old resource script:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}


function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
            else
            {
                Write-Verbose -Verbose "TimeZone already set to $TimeZone"
            }
        }
        catch
        {
            $ErrorMsg = $_.Exception.Message
            Write-Verbose -Verbose $ErrorMsg
        }
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="758b5-122">Zwróć uwagę, że **strefy czasowej** właściwość nie jest już klucz.</span><span class="sxs-lookup"><span data-stu-id="758b5-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="758b5-123">Teraz, jeśli konfiguracja podejmuje próbę ustawienia strefy czasowej dwukrotnie (przy użyciu dwóch różnych **xTimeZone** bloków z różnymi **strefy czasowej** wartości), próby skompilowania konfiguracji spowoduje błąd:</span><span class="sxs-lookup"><span data-stu-id="758b5-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```