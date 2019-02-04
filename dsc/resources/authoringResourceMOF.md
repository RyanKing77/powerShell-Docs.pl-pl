---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Pisanie zasobu DSC niestandardowych z pliku MOF
ms.openlocfilehash: 5917e20769e750042a9855649ff5bec36ad14eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687566"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="85968-103">Pisanie zasobu DSC niestandardowych z pliku MOF</span><span class="sxs-lookup"><span data-stu-id="85968-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="85968-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="85968-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="85968-105">W tym temacie firma Microsoft będzie zdefiniowanie schematu w programie Windows PowerShell Desired State Configuration (DSC) zasobu niestandardowego pliku MOF i zaimplementować zasobu w pliku skryptu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="85968-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="85968-106">Ten zasób niestandardowy jest utworzenie i utrzymywanie witryny sieci web.</span><span class="sxs-lookup"><span data-stu-id="85968-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="85968-107">Trwa tworzenie schematu pliku MOF</span><span class="sxs-lookup"><span data-stu-id="85968-107">Creating the MOF schema</span></span>

<span data-ttu-id="85968-108">Schemat definiuje właściwości zasobu, które można skonfigurować za pomocą skryptu konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="85968-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="85968-109">Struktura folderów dla zasobów MOF</span><span class="sxs-lookup"><span data-stu-id="85968-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="85968-110">Aby zaimplementować zasób niestandardowy DSC przy użyciu schematu pliku MOF, utwórz następującą strukturę folderów.</span><span class="sxs-lookup"><span data-stu-id="85968-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="85968-111">Schemat pliku MOF jest zdefiniowana w pliku Demo_IISWebsite.schema.mof, a skrypt zasobu jest zdefiniowana w Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="85968-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="85968-112">Opcjonalnie można utworzyć plik manifestu (psd1) modułu.</span><span class="sxs-lookup"><span data-stu-id="85968-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="85968-113">Zwróć uwagę, że niezbędne do utworzenia folderu o nazwie DSCResources w folderze najwyższego poziomu jest i że folder dla każdego zasobu musi mieć taką samą nazwę jak zasób.</span><span class="sxs-lookup"><span data-stu-id="85968-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="85968-114">Zawartość pliku MOF</span><span class="sxs-lookup"><span data-stu-id="85968-114">The contents of the MOF file</span></span>

<span data-ttu-id="85968-115">Poniżej przedstawiono przykładowy plik MOF, który może służyć do zasobu niestandardowej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="85968-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="85968-116">Aby skorzystać z tego przykładu, Zapisz ten schemat do pliku, a następnie wywołaj pliku *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="85968-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

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

<span data-ttu-id="85968-117">Należy pamiętać o następujących dotyczących poprzedniego kodu:</span><span class="sxs-lookup"><span data-stu-id="85968-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="85968-118">`FriendlyName` Definiuje nazwę, które służy do odwoływania się do tego zasobu niestandardowych skryptów konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="85968-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="85968-119">W tym przykładzie `Website` jest odpowiednikiem przyjazną nazwę `Archive` dla wbudowanych zasób archiwum.</span><span class="sxs-lookup"><span data-stu-id="85968-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="85968-120">Klasy, należy zdefiniować dla niestandardowego zasobu musi pochodzić od klasy `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="85968-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="85968-121">Kwalifikator typu `[Key]`na właściwość wskazuje, że ta właściwość jednoznacznie identyfikują wystąpienie zasobu.</span><span class="sxs-lookup"><span data-stu-id="85968-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="85968-122">Co najmniej jeden `[Key]` właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="85968-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="85968-123">`[Required]` Kwalifikator wskazuje, że właściwość jest wymagana (wartość musi być określona w dowolnym skrypt konfiguracyjny, który korzysta z tego zasobu).</span><span class="sxs-lookup"><span data-stu-id="85968-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="85968-124">`[write]` Kwalifikator wskazuje, czy ta właściwość jest opcjonalna, korzystając z niestandardowego zasobu skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="85968-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="85968-125">`[read]` Kwalifikator wskazuje, że właściwość nie może ustawić konfigurację i jest tylko do celów raportowania.</span><span class="sxs-lookup"><span data-stu-id="85968-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="85968-126">`Values` ogranicza wartości, które mogą być przypisane do właściwości na listę wartości określonych w `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="85968-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="85968-127">Aby uzyskać więcej informacji, zobacz [ValueMap i kwalifikatory wartość](/windows/desktop/WmiSdk/value-map).</span><span class="sxs-lookup"><span data-stu-id="85968-127">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
* <span data-ttu-id="85968-128">W tym właściwości o nazwie `Ensure` wartościami `Present` i `Absent` w swoim zasobie jest zalecane jako sposób utrzymania jednolitego stylu przy użyciu wbudowanych zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="85968-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="85968-129">Nazwa pliku schematu niestandardowego zasobu bazy danych w następujący sposób: `classname.schema.mof`, gdzie `classname` jest identyfikatorem, który następuje po `class` — słowo kluczowe w definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="85968-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="85968-130">Zapisywanie skryptu zasobów</span><span class="sxs-lookup"><span data-stu-id="85968-130">Writing the resource script</span></span>

<span data-ttu-id="85968-131">Skrypt zasobu implementuje logikę zasobu.</span><span class="sxs-lookup"><span data-stu-id="85968-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="85968-132">W tym module musi zawierać trzy funkcje wywoływane **Get TargetResource**, **TargetResource zestaw**, i **TargetResource testu**.</span><span class="sxs-lookup"><span data-stu-id="85968-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="85968-133">Wszystkie trzy funkcje należy przełączyć zestaw parametrów, która jest taka sama jak zestaw właściwości zdefiniowane w schemacie MOF, który został utworzony dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="85968-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="85968-134">W tym dokumencie to zbiór właściwości nazywa się "właściwości zasobów."</span><span class="sxs-lookup"><span data-stu-id="85968-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="85968-135">Te trzy funkcje w pliku o nazwie Store <ResourceName>psm1.</span><span class="sxs-lookup"><span data-stu-id="85968-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="85968-136">W poniższym przykładzie funkcje są przechowywane w pliku o nazwie Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="85968-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> <span data-ttu-id="85968-137">**Uwaga**: Po uruchomieniu tego samego skryptu konfiguracji zasobu więcej niż jeden raz, powinna pojawić się bez błędów i zasobu może pozostawać w tym samym stanie jako po uruchomieniu skryptu.</span><span class="sxs-lookup"><span data-stu-id="85968-137">**Note**: When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="85968-138">Aby to osiągnąć, upewnij się, że Twoje **Get TargetResource** i **TargetResource testu** funkcje Pozostaw bez zmian zasobu i wywoływanie tej **Set-TargetResource**działać więcej niż jeden raz w sekwencji z tego samego parametru wartości jest zawsze równoważne wywołanie go jeden raz.</span><span class="sxs-lookup"><span data-stu-id="85968-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="85968-139">W **Get TargetResource** funkcji implementacji, użyj wartości właściwości klucza zasobu, które są dostarczane jako parametry, aby sprawdzić stan wystąpienia określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="85968-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="85968-140">Ta funkcja musi zwracać tabelę mieszania, która zawiera wszystkie właściwości zasobu jako klucze i rzeczywiste wartości tych właściwości, jak odpowiadające im wartości.</span><span class="sxs-lookup"><span data-stu-id="85968-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="85968-141">Poniższy kod zawiera przykład.</span><span class="sxs-lookup"><span data-stu-id="85968-141">The following code provides an example.</span></span>

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

<span data-ttu-id="85968-142">W zależności od wartości, które są określone dla właściwości zasobu w skrypcie konfiguracji **TargetResource zestaw** należy wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="85968-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="85968-143">Utwórz nową witrynę sieci Web</span><span class="sxs-lookup"><span data-stu-id="85968-143">Create a new website</span></span>
* <span data-ttu-id="85968-144">Aktualizowanie istniejącej witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="85968-144">Update an existing website</span></span>
* <span data-ttu-id="85968-145">Usuń istniejącą witrynę sieci Web</span><span class="sxs-lookup"><span data-stu-id="85968-145">Delete an existing website</span></span>

<span data-ttu-id="85968-146">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="85968-146">The following example illustrates this.</span></span>

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

<span data-ttu-id="85968-147">Na koniec **TargetResource testu** funkcji, należy wykonać ten sam parametr ustawiony jako **Get TargetResource** i **TargetResource zestaw**.</span><span class="sxs-lookup"><span data-stu-id="85968-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="85968-148">W danej implementacji **TargetResource testu**, sprawdź stan wystąpienia zasobu, który jest określony za pomocą parametrów klucza.</span><span class="sxs-lookup"><span data-stu-id="85968-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="85968-149">Jeśli rzeczywisty stan wystąpienia zasobu nie odpowiada wartości określone w zestaw parametrów, zwracają **$false**.</span><span class="sxs-lookup"><span data-stu-id="85968-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="85968-150">W przeciwnym razie Zwróć **$true**.</span><span class="sxs-lookup"><span data-stu-id="85968-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="85968-151">Poniższy kod implementuje **TargetResource testu** funkcji.</span><span class="sxs-lookup"><span data-stu-id="85968-151">The following code implements the **Test-TargetResource** function.</span></span>

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

<span data-ttu-id="85968-152">**Uwaga**: Łatwiejsze debugowanie użytku **Write-Verbose** polecenia cmdlet w danej implementacji poprzednie trzy funkcje.</span><span class="sxs-lookup"><span data-stu-id="85968-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="85968-153">To polecenie cmdlet zapisuje tekst w strumieniu komunikat trybu informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="85968-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="85968-154">Domyślnie strumień komunikatów pełnych nie jest wyświetlana, ale można je wyświetlić, zmieniając wartość **$VerbosePreference** zmiennej lub za pomocą **pełne** parametru w poleceniach cmdlet DSC = nowy.</span><span class="sxs-lookup"><span data-stu-id="85968-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="85968-155">Tworzenie manifestu modułu</span><span class="sxs-lookup"><span data-stu-id="85968-155">Creating the module manifest</span></span>

<span data-ttu-id="85968-156">Na koniec użyj **New ModuleManifest** polecenia cmdlet, aby zdefiniować <ResourceName>w pliku psd1 modułu zasobów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="85968-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="85968-157">Po wywołaniu tego polecenia cmdlet odwołanie pliku modułu (.psm1) skryptu, które są opisane w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="85968-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="85968-158">Obejmują **Get TargetResource**, **TargetResource zestaw**, i **TargetResource testu** na liście funkcji do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="85968-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="85968-159">Poniżej przedstawiono przykładowy plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="85968-159">Following is an example manifest file.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="85968-160">Obsługa PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="85968-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="85968-161">**Uwaga:** **PsDscRunAsCredential** jest obsługiwana w programie PowerShell 5.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="85968-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="85968-162">**PsDscRunAsCredential** właściwości mogą być używane w [konfiguracje DSC](../configurations/configurations.md) bloku zasobów, aby określić, że zasób powinien być wykonywany w ramach określonego zestawu poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="85968-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="85968-163">Aby uzyskać więcej informacji, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="85968-163">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="85968-164">Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć zmiennej automatyczne `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="85968-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="85968-165">Na przykład poniższy kod napisać kontekstu użytkownika, pod którym jest uruchamiany zasób w strumieniu pełne dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="85968-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="85968-166">Ponowny rozruch węzła</span><span class="sxs-lookup"><span data-stu-id="85968-166">Rebooting the Node</span></span>

<span data-ttu-id="85968-167">Jeśli akcje wykonywane w Twojej `Set-TargetResource` funkcja wymaga ponownego uruchomienia systemu, można użyć flagę globalną mówić LCM o ponownym uruchomieniu węzła.</span><span class="sxs-lookup"><span data-stu-id="85968-167">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="85968-168">Występuje, bezpośrednio po ponownym uruchomieniu `Set-TargetResource` zakończenie funkcji.</span><span class="sxs-lookup"><span data-stu-id="85968-168">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="85968-169">Wewnątrz swojej `Set-TargetResource` funkcji, Dodaj następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="85968-169">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="85968-170">Aby LCM wykonać ponowny rozruch węzła **RebootNodeIfNeeded** flagi musi być równa `$true`.</span><span class="sxs-lookup"><span data-stu-id="85968-170">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span> <span data-ttu-id="85968-171">**ActionAfterReboot** ustawienia należy także wybrać opcję **ContinueConfiguration**, co jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="85968-171">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration**, which is the default.</span></span> <span data-ttu-id="85968-172">Aby uzyskać więcej informacji na temat konfigurowania programu LCM, zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md), lub [Konfigurowanie programu Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="85968-172">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
