---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Pisanie zasobu DSC niestandardowych z pliku MOF
ms.openlocfilehash: f243c3e3297711e6f6346a0f813a9c017fe227c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076739"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Pisanie zasobu DSC niestandardowych z pliku MOF

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

W tym temacie firma Microsoft będzie zdefiniowanie schematu w programie Windows PowerShell Desired State Configuration (DSC) zasobu niestandardowego pliku MOF i zaimplementować zasobu w pliku skryptu programu Windows PowerShell. Ten zasób niestandardowy jest utworzenie i utrzymywanie witryny sieci web.

## <a name="creating-the-mof-schema"></a>Trwa tworzenie schematu pliku MOF

Schemat definiuje właściwości zasobu, które można skonfigurować za pomocą skryptu konfiguracji DSC.

### <a name="folder-structure-for-a-mof-resource"></a>Struktura folderów dla zasobów MOF

Aby zaimplementować zasób niestandardowy DSC przy użyciu schematu pliku MOF, utwórz następującą strukturę folderów. Schemat pliku MOF jest zdefiniowana w pliku Demo_IISWebsite.schema.mof, a skrypt zasobu jest zdefiniowana w Demo_IISWebsite.psm1. Opcjonalnie można utworzyć plik manifestu (psd1) modułu.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Zwróć uwagę, że niezbędne do utworzenia folderu o nazwie DSCResources w folderze najwyższego poziomu jest i że folder dla każdego zasobu musi mieć taką samą nazwę jak zasób.

### <a name="the-contents-of-the-mof-file"></a>Zawartość pliku MOF

Poniżej przedstawiono przykładowy plik MOF, który może służyć do zasobu niestandardowej witryny sieci Web. Aby skorzystać z tego przykładu, Zapisz ten schemat do pliku, a następnie wywołaj pliku *Demo_IISWebsite.schema.mof*.

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

Należy pamiętać o następujących dotyczących poprzedniego kodu:

* `FriendlyName` Definiuje nazwę, które służy do odwoływania się do tego zasobu niestandardowych skryptów konfiguracji DSC. W tym przykładzie `Website` jest odpowiednikiem przyjazną nazwę `Archive` dla wbudowanych zasób archiwum.
* Klasy, należy zdefiniować dla niestandardowego zasobu musi pochodzić od klasy `OMI_BaseResource`.
* Kwalifikator typu `[Key]`na właściwość wskazuje, że ta właściwość jednoznacznie identyfikują wystąpienie zasobu. Co najmniej jeden `[Key]` właściwość jest wymagana.
* `[Required]` Kwalifikator wskazuje, że właściwość jest wymagana (wartość musi być określona w dowolnym skrypt konfiguracyjny, który korzysta z tego zasobu).
* `[write]` Kwalifikator wskazuje, czy ta właściwość jest opcjonalna, korzystając z niestandardowego zasobu skryptu konfiguracji. `[read]` Kwalifikator wskazuje, że właściwość nie może ustawić konfigurację i jest tylko do celów raportowania.
* `Values` ogranicza wartości, które mogą być przypisane do właściwości na listę wartości określonych w `ValueMap`. Aby uzyskać więcej informacji, zobacz [ValueMap i kwalifikatory wartość](/windows/desktop/WmiSdk/value-map).
* W tym właściwości o nazwie `Ensure` wartościami `Present` i `Absent` w swoim zasobie jest zalecane jako sposób utrzymania jednolitego stylu przy użyciu wbudowanych zasobów DSC.
* Nazwa pliku schematu niestandardowego zasobu bazy danych w następujący sposób: `classname.schema.mof`, gdzie `classname` jest identyfikatorem, który następuje po `class` — słowo kluczowe w definicji schematu.

### <a name="writing-the-resource-script"></a>Zapisywanie skryptu zasobów

Skrypt zasobu implementuje logikę zasobu. W tym module musi zawierać trzy funkcje wywoływane **Get TargetResource**, **TargetResource zestaw**, i **TargetResource testu**. Wszystkie trzy funkcje należy przełączyć zestaw parametrów, która jest taka sama jak zestaw właściwości zdefiniowane w schemacie MOF, który został utworzony dla zasobu. W tym dokumencie to zbiór właściwości nazywa się "właściwości zasobów." Te trzy funkcje w pliku o nazwie Store <ResourceName>psm1. W poniższym przykładzie funkcje są przechowywane w pliku o nazwie Demo_IISWebsite.psm1.

> [!NOTE]
> Po uruchomieniu tego samego skryptu konfiguracji zasobu więcej niż jeden raz, powinna pojawić się bez błędów i zasobu może pozostawać w tym samym stanie jako po uruchomieniu skryptu. Aby to osiągnąć, upewnij się, że Twoje **Get TargetResource** i **TargetResource testu** funkcje Pozostaw bez zmian zasobu i wywoływanie tej **Set-TargetResource**działać więcej niż jeden raz w sekwencji z tego samego parametru wartości jest zawsze równoważne wywołanie go jeden raz.

W **Get TargetResource** funkcji implementacji, użyj wartości właściwości klucza zasobu, które są dostarczane jako parametry, aby sprawdzić stan wystąpienia określonego zasobu. Ta funkcja musi zwracać tabelę mieszania, która zawiera wszystkie właściwości zasobu jako klucze i rzeczywiste wartości tych właściwości, jak odpowiadające im wartości. Poniższy kod zawiera przykład.

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

W zależności od wartości, które są określone dla właściwości zasobu w skrypcie konfiguracji **TargetResource zestaw** należy wykonać jedną z następujących czynności:

* Utwórz nową witrynę sieci Web
* Aktualizowanie istniejącej witryny sieci Web
* Usuń istniejącą witrynę sieci Web

Ilustruje to poniższy przykład.

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

Na koniec **TargetResource testu** funkcji, należy wykonać ten sam parametr ustawiony jako **Get TargetResource** i **TargetResource zestaw**. W danej implementacji **TargetResource testu**, sprawdź stan wystąpienia zasobu, który jest określony za pomocą parametrów klucza. Jeśli rzeczywisty stan wystąpienia zasobu nie odpowiada wartości określone w zestaw parametrów, zwracają **$false**. W przeciwnym razie Zwróć **$true**.

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

**Uwaga**: Łatwiejsze debugowanie użytku **Write-Verbose** polecenia cmdlet w danej implementacji poprzednie trzy funkcje.
>To polecenie cmdlet zapisuje tekst w strumieniu komunikat trybu informacji pełnej.
>Domyślnie strumień komunikatów pełnych nie jest wyświetlana, ale można je wyświetlić, zmieniając wartość **$VerbosePreference** zmiennej lub za pomocą **pełne** parametru w poleceniach cmdlet DSC = nowy.

### <a name="creating-the-module-manifest"></a>Tworzenie manifestu modułu

Na koniec użyj **New ModuleManifest** polecenia cmdlet, aby zdefiniować <ResourceName>w pliku psd1 modułu zasobów niestandardowych. Po wywołaniu tego polecenia cmdlet odwołanie pliku modułu (.psm1) skryptu, które są opisane w poprzedniej sekcji. Obejmują **Get TargetResource**, **TargetResource zestaw**, i **TargetResource testu** na liście funkcji do wyeksportowania. Poniżej przedstawiono przykładowy plik manifestu.

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

**PsDscRunAsCredential** właściwości mogą być używane w [konfiguracje DSC](../configurations/configurations.md) bloku zasobów, aby określić, że zasób powinien być wykonywany w ramach określonego zestawu poświadczeń.
Aby uzyskać więcej informacji, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](../configurations/runAsUser.md).

Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć zmiennej automatyczne `$PsDscContext`.

Na przykład poniższy kod napisać kontekstu użytkownika, pod którym jest uruchamiany zasób w strumieniu pełne dane wyjściowe:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a>Ponowny rozruch węzła

Jeśli akcje wykonywane w Twojej `Set-TargetResource` funkcja wymaga ponownego uruchomienia systemu, można użyć flagę globalną mówić LCM o ponownym uruchomieniu węzła. Występuje, bezpośrednio po ponownym uruchomieniu `Set-TargetResource` zakończenie funkcji.

Wewnątrz swojej `Set-TargetResource` funkcji, Dodaj następujący wiersz kodu.

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

Aby LCM wykonać ponowny rozruch węzła **RebootNodeIfNeeded** flagi musi być równa `$true`. **ActionAfterReboot** ustawienia należy także wybrać opcję **ContinueConfiguration**, co jest ustawieniem domyślnym. Aby uzyskać więcej informacji na temat konfigurowania programu LCM, zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md), lub [Konfigurowanie programu Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).
