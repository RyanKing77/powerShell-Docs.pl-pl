---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Pisanie niestandardowych zasobów DSC z MOF
ms.openlocfilehash: 50b5f2eddbac4571f5351b32648d45c54ded167e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189639"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Pisanie niestandardowych zasobów DSC z MOF

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

W tym temacie firma Microsoft będzie zdefiniowanie schematu w programie Windows PowerShell Desired stan konfiguracji (DSC) zasobu niestandardowego pliku MOF i implementować zasobu w pliku skryptu programu Windows PowerShell. Ten zasób niestandardowy jest do tworzenia i obsługi witryny sieci web.

## <a name="creating-the-mof-schema"></a>Trwa tworzenie schematu MOF

Schemat definiuje właściwości z zasobem, który można skonfigurować za pomocą skryptu konfiguracji DSC.

### <a name="folder-structure-for-a-mof-resource"></a>Struktura folderów dla zasobu MOF

Aby zaimplementować DSC niestandardowego zasobu ze schematem MOF, utwórz następującą strukturę folderów. Schemat MOF jest zdefiniowana w pliku Demo_IISWebsite.schema.mof, a skrypt zasobu jest zdefiniowany w Demo_IISWebsite.psm1. Opcjonalnie można utworzyć pliku manifestu (psd1) modułu.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Należy pamiętać, jest niezbędne utworzyć folder o nazwie DSCResources w folderze najwyższego poziomu oraz że folderu dla każdego zasobu musi mieć taką samą nazwę jak zasób.

### <a name="the-contents-of-the-mof-file"></a>Zawartość pliku MOF

Poniżej znajduje się przykładowy plik MOF, który może służyć do zasobów niestandardowej witryny sieci Web. Aby użyć tego przykładu, Zapisz ten schemat do pliku, a następnie wywołać plik *Demo_IISWebsite.schema.mof*.

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Należy zwrócić uwagę na poniższe kwestie poprzedni kod:

* `FriendlyName` Określa nazwę, którą można odwoływać się do tego zasobu niestandardowego w skryptach konfiguracji DSC. W tym przykładzie `Website` jest odpowiednikiem przyjazną nazwę `Archive` wbudowanych zasobu archiwum.
* Definiowanie dla niestandardowego zasobu musi pochodzić od klasy `OMI_BaseResource`.
* Kwalifikator typu `[Key]`na właściwość wskazuje, że ta właściwość pozwolą jednoznacznie zidentyfikować wystąpienia zasobu. Co najmniej jeden `[Key]` właściwość jest wymagana.
* `[Required]` Kwalifikator wskazuje, że właściwość jest wymagana (w przypadku dowolnego skryptu konfiguracji, który używa tego zasobu musi być określona wartość).
* `[write]` Kwalifikator wskazuje, że ta właściwość jest opcjonalna, korzystając z zasobów niestandardowych za pomocą skryptów konfiguracji. `[read]` Kwalifikator wskazuje, że właściwości nie można ustawić konfiguracji i jest wyłącznie dla celów raportowania.
* `Values` ogranicza wartości, które można przypisać do właściwości do listy wartości zdefiniowanych w `ValueMap`. Aby uzyskać więcej informacji, zobacz [ValueMap i kwalifikatory wartość](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).
* W tym właściwości o nazwie `Ensure` z wartościami `Present` i `Absent` w zasobie zaleca się jako sposób Obsługa stylu spójne z wbudowanych zasobów usługi Konfiguracja DSC.
* Nazwa pliku schematu niestandardowego zasobu w następujący sposób: `classname.schema.mof`, gdzie `classname` jest identyfikatorem, który następuje `class` — słowo kluczowe w definicji schematu.

### <a name="writing-the-resource-script"></a>Pisanie skryptów zasobów

Skrypt zasobu implementuje logiki zasobu. W tym module musi zawierać trzy funkcje wywołane **Get-TargetResource**, **TargetResource zestaw**, i **TargetResource testu**. Wszystkie trzy funkcje należy przełączyć zestaw parametrów, który jest taki sam jak zbiór właściwości zdefiniowane w schemacie MOF, który został utworzony dla zasobu. W tym dokumencie to zbiór właściwości nazywa się "właściwości zasobów." Te trzy funkcje w pliku o nazwie magazynu <ResourceName>.psm1. W poniższym przykładzie funkcje są przechowywane w pliku o nazwie Demo_IISWebsite.psm1.

> **Uwaga**: po uruchomieniu tego samego skryptu konfiguracji na zasobie więcej niż raz, powinien zostać wyświetlony bez błędów i zasobu może pozostawać w takim samym stanie jako raz uruchamiania skryptu. Aby to zrobić, upewnij się, że Twoje **Get-TargetResource** i **TargetResource testu** funkcje Pozostaw bez zmian zasobu i że wywoływanie **Set-TargetResource**działać więcej niż raz w sekwencji z tego samego parametru wartości jest zawsze równoważne wywoływanie jej raz.

W **Get TargetResource** funkcji implementacji, należy użyć wartości właściwości klucza zasobu, które znajdują się jako parametry do sprawdzania stanu wystąpienia określonego zasobu. Ta funkcja musi zwracać tabelę wyznaczania wartości skrótu, która zawiera wszystkie właściwości zasobu jako klucze i rzeczywiste wartości tych właściwości jako odpowiednie wartości. Poniższy kod stanowi przykład.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

W zależności od wartości, które są określone dla właściwości zasobów w skrypcie konfiguracji **TargetResource zestaw** należy wykonać jedną z następujących czynności:

* Utwórz nową witrynę sieci Web
* Aktualizowanie istniejącej witryny sieci Web
* Usuń istniejącej witryny sieci Web

Poniższy przykład przedstawia to.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

Na koniec **TargetResource testu** funkcji musi mieć tego samego zestawu jako parametrów **Get-TargetResource** i **TargetResource zestawu**. W implementacji **TargetResource testu**, sprawdź stan wystąpienia zasobu, który określono w parametrach klucza. W przypadku rzeczywisty stan wystąpienia zasobu nie odpowiada wartości podanych w zestaw parametrów, zwraca **$false**. W przeciwnym razie zwraca **$true**.

Poniższy kod implementuje **TargetResource testu** funkcji.

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

**Uwaga**: ułatwiają debugowanie, użyj **Write-Verbose** polecenia cmdlet w implementacji poprzednie trzy funkcje.
>To polecenie cmdlet zapisuje tekst w strumieniu komunikat trybu informacji pełnej.
>Domyślnie nie jest wyświetlany komunikat trybu informacji pełnej strumienia, ale można je wyświetlić, zmieniając wartość **$VerbosePreference** zmiennej lub za pomocą **pełne** parametru w poleceniach cmdlet DSC = new.

### <a name="creating-the-module-manifest"></a>Tworzenie manifestu modułu

Na koniec użyj **ModuleManifest nowy** polecenia cmdlet, aby zdefiniować <ResourceName>plik psd1 dla modułu zasobów niestandardowych. Po wywołaniu tego polecenia cmdlet, odwołanie pliku modułu (.psm1) skrypt, które są opisane w poprzedniej sekcji. Obejmują **Get-TargetResource**, **TargetResource zestaw**, i **TargetResource testu** na liście funkcji do wyeksportowania. Poniżej znajduje się przykładowy plik manifestu.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a>Obsługa PsDscRunAsCredential

>**Uwaga:** **PsDscRunAsCredential** jest obsługiwana w programie PowerShell 5.0 i nowszych.

**PsDscRunAsCredential** właściwość może być używana w [konfiguracji DSC](configurations.md) bloku zasobów, aby określić, że zasób powinny być uruchamiane w określonym zestawie poświadczeń.
Aby uzyskać więcej informacji, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).

Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć automatycznego zmiennej `$PsDscContext`.

Na przykład następujący kod zapisać kontekstu użytkownika, na którym uruchomiono zasobu w strumieniu pełne dane wyjściowe:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```