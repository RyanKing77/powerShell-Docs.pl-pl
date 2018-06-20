---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)
ms.openlocfilehash: 9494964b1b13eaa082ad5cbc279b4586bb7211cc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218369"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)

>**Uwaga:** w tym temacie opisano najlepszym rozwiązaniem do definiowania zasobów DSC, który umożliwia tylko jedno wystąpienie w konfiguracji. Obecnie nie są ma wbudowanej funkcji DSC w tym celu. Który mogą ulec zmianie w przyszłości.

Istnieją sytuacje, w których nie chcesz zezwolić zasobu jest używana wiele razy w konfiguracji. Na przykład w poprzedniej implementacji [xTimeZone](https://github.com/PowerShell/xTimeZone) zasobów, konfiguracji można wywołać zasobu wielokrotnie, ustawienie strefy czasowej na inne ustawienie w każdym bloku zasobów:

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

Jest to spowodowane sposób pracy klucze zasobów usługi Konfiguracja DSC. Zasób musi mieć co najmniej jedną właściwość klucza. Wystąpienie zasobu jest traktowany jako unikatowy, jeśli kombinacja wartości wszystkich właściwości klucza są unikatowe. W jego poprzedniej implementacji [xTimeZone](https://github.com/PowerShell/xTimeZone) zasobów ma tylko jedną właściwość--**strefy czasowej**, który został musi być kluczem. W związku z tym konfiguracji, takie jak powyżej czy kompilowanie i uruchamianie bez ostrzeżenia. Każdy z **xTimeZone** bloki zasobów jest uznawany za unikatowy. To spowoduje konfiguracji wielokrotnie stosowane do tego węzła, cyklicznie strefa czasowa i z powrotem.

Zapewnienie konfiguracji można ustawić strefę czasową dla węzła docelowego tylko raz, zasób został zaktualizowano w celu dodania drugiej właściwości **IsSingleInstance**, które stały się właściwości klucza.
**IsSingleInstance** został ograniczony do pojedynczą wartość "Tak" przy użyciu **ValueMap**. Stary schematu MOF dla zasobu to:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Zaktualizowany schemat MOF dla zasobu to:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Skrypt zasobu Zaktualizowano również, aby użyć nowego parametru. Oto starego skryptu zasobu:

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

Zwróć uwagę, że **strefy czasowej** właściwość nie jest już klucz. Teraz, jeśli konfiguracja podejmuje próbę ustawienia strefy czasowej dwukrotnie (przy użyciu dwóch różnych **xTimeZone** bloków z różnymi **strefy czasowej** wartości), próby skompilowania konfiguracji spowoduje błąd:

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