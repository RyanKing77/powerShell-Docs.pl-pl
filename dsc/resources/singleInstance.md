---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)
ms.openlocfilehash: 4d9e07c6aaa064f808a03d4252e8d352b82183ec
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986516"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="1cfc3-103">Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)</span><span class="sxs-lookup"><span data-stu-id="1cfc3-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="1cfc3-104">**Uwaga:** W tym temacie opisano najlepsze rozwiązanie w zakresie definiowania zasobu DSC, który umożliwia tylko pojedyncze wystąpienie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="1cfc3-105">Obecnie nie istnieje Wbudowana funkcja DSC.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="1cfc3-106">Które mogą ulec zmianie w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-106">That might change in the future.</span></span>

<span data-ttu-id="1cfc3-107">Istnieją sytuacje, w których nie należy zezwalać na użycie zasobu wiele razy w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="1cfc3-108">Na przykład w poprzedniej implementacji zasobu [xTimeZone](https://github.com/PowerShell/xTimeZone) konfiguracja może wywoływać zasób wiele razy, ustawiając strefę czasową na inne ustawienie w każdym bloku zasobów:</span><span class="sxs-lookup"><span data-stu-id="1cfc3-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

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

<span data-ttu-id="1cfc3-109">Wynika to z sposobu, w jaki działają klucze zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="1cfc3-110">Zasób musi mieć co najmniej jedną właściwość klucza.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-110">A resource must have at least one key property.</span></span> <span data-ttu-id="1cfc3-111">Wystąpienie zasobu jest uznawane za unikatowe, jeśli kombinacja wartości wszystkich właściwości klucza jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="1cfc3-112">W poprzedniej implementacji zasób [xTimeZone](https://github.com/PowerShell/xTimeZone) miał tylko jedną właściwość--**strefę czasową**, która była wymagana jako klucz.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="1cfc3-113">W związku z tym taka konfiguracja powinna zostać skompilowana i uruchomiona bez ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="1cfc3-114">Każdy z bloków zasobów **xTimeZone** jest uznawany za unikatowy.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="1cfc3-115">Może to spowodować, że konfiguracja zostanie wielokrotnie zastosowana do węzła, co spowoduje ponowne przetworzenie strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="1cfc3-116">Aby mieć pewność, że konfiguracja może ustawić strefę czasową dla węzła docelowego tylko raz, zasób został zaktualizowany tak, aby dodać drugą właściwość **IsSingleInstance**, która stała się właściwością klucza.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="1cfc3-117">**IsSingleInstance** została ograniczona do pojedynczej wartości "tak" przy użyciu **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="1cfc3-118">Stary schemat MOF dla zasobu to:</span><span class="sxs-lookup"><span data-stu-id="1cfc3-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="1cfc3-119">Zaktualizowany schemat MOF dla zasobu to:</span><span class="sxs-lookup"><span data-stu-id="1cfc3-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="1cfc3-120">Skrypt zasobu został również zaktualizowany do korzystania z nowego parametru.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="1cfc3-121">W tym miejscu został zmieniony skrypt zasobów:</span><span class="sxs-lookup"><span data-stu-id="1cfc3-121">Here how the resource script was changed:</span></span>

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
    [CmdletBinding()]
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

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"
    
    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
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

<span data-ttu-id="1cfc3-122">Zauważ, że właściwość **strefy czasowej** nie jest już kluczem.</span><span class="sxs-lookup"><span data-stu-id="1cfc3-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="1cfc3-123">Teraz, jeśli konfiguracja próbuje dwukrotnie ustawić strefę czasową (przy użyciu dwóch różnych bloków **xTimeZone** z różnymi wartościami **strefy czasowej** ), Próba skompilowania konfiguracji spowoduje wystąpienie błędu:</span><span class="sxs-lookup"><span data-stu-id="1cfc3-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

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
