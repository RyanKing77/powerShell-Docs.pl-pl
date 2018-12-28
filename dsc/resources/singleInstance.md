---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)
ms.openlocfilehash: 9494964b1b13eaa082ad5cbc279b4586bb7211cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405330"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)

>**Uwaga:** W tym temacie opisano najlepsze rozwiązanie dla Definiowanie zasobów DSC, umożliwiającą tylko jedno wystąpienie w konfiguracji. Obecnie nie ma żadnych wbudowanej funkcji DSC, aby to zrobić. Które mogą ulec zmianie w przyszłości.

Istnieją sytuacje, w których nie chcesz zezwolić na zasób, który ma być używany wielokrotnie w konfiguracji. Na przykład w poprzedniej implementacji [xTimeZone](https://github.com/PowerShell/xTimeZone) zasobów, konfiguracji można nazwać zasobu wielokrotnie, ustawienie strefy czasowej na inne ustawienie w każdym bloku zasobów:

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

Jest to ze względu na sposób pracy klucze zasobu DSC. Zasób musi mieć co najmniej jedną właściwość klucza. Wystąpienie zasobu jest traktowany jako unikatowe, jeśli kombinacja wartości wszystkich właściwości klucza jest unikatowa. W jego poprzedniej implementacji [xTimeZone](https://github.com/PowerShell/xTimeZone) zasobu ma tylko jedną właściwość —**strefa czasowa**, który został musi być kluczem. W związku z tym konfiguracji, takiego jak pokazano powyżej może skompilować i uruchomić bez ostrzeżenia. Każdy z **xTimeZone** bloków zasobów jest traktowane jako unikatowe. To spowoduje, że konfigurację można wielokrotnie zastosować do węzła, cykliczny strefę czasową i z powrotem.

Aby upewnij się, że konfiguracja może strefę czasową dla węzła docelowego tylko raz, zasób został zaktualizowany do Dodaj drugą właściwość **IsSingleInstance**, które stały się właściwość klucza.
**IsSingleInstance** zostało ograniczone do pojedynczej wartości "Yes" przy użyciu **ValueMap**. Stary schematu pliku MOF dla zasobu to:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Zaktualizowano schemat MOF dla zasobu to:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Skrypt zasobów został także zaktualizowany do użycia nowego parametru. Oto starego skryptu zasobu:

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

Należy zauważyć, że **strefa czasowa** właściwość nie jest już klucz. Teraz, jeśli konfiguracja próbuje Ustaw strefę czasową dwa razy (przy użyciu dwóch różnych **xTimeZone** bloków z różnymi **strefa czasowa** wartości), próba skompilowania konfiguracji spowoduje błąd:

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