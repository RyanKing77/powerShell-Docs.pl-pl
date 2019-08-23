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
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Pisanie zasobu DSC jednego wystąpienia (najlepsze rozwiązanie)

>**Uwaga:** W tym temacie opisano najlepsze rozwiązanie w zakresie definiowania zasobu DSC, który umożliwia tylko pojedyncze wystąpienie w konfiguracji. Obecnie nie istnieje Wbudowana funkcja DSC. Które mogą ulec zmianie w przyszłości.

Istnieją sytuacje, w których nie należy zezwalać na użycie zasobu wiele razy w konfiguracji. Na przykład w poprzedniej implementacji zasobu [xTimeZone](https://github.com/PowerShell/xTimeZone) konfiguracja może wywoływać zasób wiele razy, ustawiając strefę czasową na inne ustawienie w każdym bloku zasobów:

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

Wynika to z sposobu, w jaki działają klucze zasobów DSC. Zasób musi mieć co najmniej jedną właściwość klucza. Wystąpienie zasobu jest uznawane za unikatowe, jeśli kombinacja wartości wszystkich właściwości klucza jest unikatowa. W poprzedniej implementacji zasób [xTimeZone](https://github.com/PowerShell/xTimeZone) miał tylko jedną właściwość--**strefę czasową**, która była wymagana jako klucz. W związku z tym taka konfiguracja powinna zostać skompilowana i uruchomiona bez ostrzeżenia. Każdy z bloków zasobów **xTimeZone** jest uznawany za unikatowy. Może to spowodować, że konfiguracja zostanie wielokrotnie zastosowana do węzła, co spowoduje ponowne przetworzenie strefy czasowej.

Aby mieć pewność, że konfiguracja może ustawić strefę czasową dla węzła docelowego tylko raz, zasób został zaktualizowany tak, aby dodać drugą właściwość **IsSingleInstance**, która stała się właściwością klucza.
**IsSingleInstance** została ograniczona do pojedynczej wartości "tak" przy użyciu **ValueMap**. Stary schemat MOF dla zasobu to:

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

Skrypt zasobu został również zaktualizowany do korzystania z nowego parametru. W tym miejscu został zmieniony skrypt zasobów:

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

Zauważ, że właściwość **strefy czasowej** nie jest już kluczem. Teraz, jeśli konfiguracja próbuje dwukrotnie ustawić strefę czasową (przy użyciu dwóch różnych bloków **xTimeZone** z różnymi wartościami **strefy czasowej** ), Próba skompilowania konfiguracji spowoduje wystąpienie błędu:

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
