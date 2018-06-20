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
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="25730-103">Pisanie niestandardowych zasobów DSC z MOF</span><span class="sxs-lookup"><span data-stu-id="25730-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="25730-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="25730-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="25730-105">W tym temacie firma Microsoft będzie zdefiniowanie schematu w programie Windows PowerShell Desired stan konfiguracji (DSC) zasobu niestandardowego pliku MOF i implementować zasobu w pliku skryptu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25730-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="25730-106">Ten zasób niestandardowy jest do tworzenia i obsługi witryny sieci web.</span><span class="sxs-lookup"><span data-stu-id="25730-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="25730-107">Trwa tworzenie schematu MOF</span><span class="sxs-lookup"><span data-stu-id="25730-107">Creating the MOF schema</span></span>

<span data-ttu-id="25730-108">Schemat definiuje właściwości z zasobem, który można skonfigurować za pomocą skryptu konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="25730-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="25730-109">Struktura folderów dla zasobu MOF</span><span class="sxs-lookup"><span data-stu-id="25730-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="25730-110">Aby zaimplementować DSC niestandardowego zasobu ze schematem MOF, utwórz następującą strukturę folderów.</span><span class="sxs-lookup"><span data-stu-id="25730-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="25730-111">Schemat MOF jest zdefiniowana w pliku Demo_IISWebsite.schema.mof, a skrypt zasobu jest zdefiniowany w Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="25730-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="25730-112">Opcjonalnie można utworzyć pliku manifestu (psd1) modułu.</span><span class="sxs-lookup"><span data-stu-id="25730-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="25730-113">Należy pamiętać, jest niezbędne utworzyć folder o nazwie DSCResources w folderze najwyższego poziomu oraz że folderu dla każdego zasobu musi mieć taką samą nazwę jak zasób.</span><span class="sxs-lookup"><span data-stu-id="25730-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="25730-114">Zawartość pliku MOF</span><span class="sxs-lookup"><span data-stu-id="25730-114">The contents of the MOF file</span></span>

<span data-ttu-id="25730-115">Poniżej znajduje się przykładowy plik MOF, który może służyć do zasobów niestandardowej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="25730-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="25730-116">Aby użyć tego przykładu, Zapisz ten schemat do pliku, a następnie wywołać plik *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="25730-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

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

<span data-ttu-id="25730-117">Należy zwrócić uwagę na poniższe kwestie poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="25730-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="25730-118">`FriendlyName` Określa nazwę, którą można odwoływać się do tego zasobu niestandardowego w skryptach konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="25730-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="25730-119">W tym przykładzie `Website` jest odpowiednikiem przyjazną nazwę `Archive` wbudowanych zasobu archiwum.</span><span class="sxs-lookup"><span data-stu-id="25730-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="25730-120">Definiowanie dla niestandardowego zasobu musi pochodzić od klasy `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="25730-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="25730-121">Kwalifikator typu `[Key]`na właściwość wskazuje, że ta właściwość pozwolą jednoznacznie zidentyfikować wystąpienia zasobu.</span><span class="sxs-lookup"><span data-stu-id="25730-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="25730-122">Co najmniej jeden `[Key]` właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="25730-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="25730-123">`[Required]` Kwalifikator wskazuje, że właściwość jest wymagana (w przypadku dowolnego skryptu konfiguracji, który używa tego zasobu musi być określona wartość).</span><span class="sxs-lookup"><span data-stu-id="25730-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="25730-124">`[write]` Kwalifikator wskazuje, że ta właściwość jest opcjonalna, korzystając z zasobów niestandardowych za pomocą skryptów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="25730-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="25730-125">`[read]` Kwalifikator wskazuje, że właściwości nie można ustawić konfiguracji i jest wyłącznie dla celów raportowania.</span><span class="sxs-lookup"><span data-stu-id="25730-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="25730-126">`Values` ogranicza wartości, które można przypisać do właściwości do listy wartości zdefiniowanych w `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="25730-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="25730-127">Aby uzyskać więcej informacji, zobacz [ValueMap i kwalifikatory wartość](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span><span class="sxs-lookup"><span data-stu-id="25730-127">For more information, see [ValueMap and Value Qualifiers](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span></span>
* <span data-ttu-id="25730-128">W tym właściwości o nazwie `Ensure` z wartościami `Present` i `Absent` w zasobie zaleca się jako sposób Obsługa stylu spójne z wbudowanych zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="25730-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="25730-129">Nazwa pliku schematu niestandardowego zasobu w następujący sposób: `classname.schema.mof`, gdzie `classname` jest identyfikatorem, który następuje `class` — słowo kluczowe w definicji schematu.</span><span class="sxs-lookup"><span data-stu-id="25730-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="25730-130">Pisanie skryptów zasobów</span><span class="sxs-lookup"><span data-stu-id="25730-130">Writing the resource script</span></span>

<span data-ttu-id="25730-131">Skrypt zasobu implementuje logiki zasobu.</span><span class="sxs-lookup"><span data-stu-id="25730-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="25730-132">W tym module musi zawierać trzy funkcje wywołane **Get-TargetResource**, **TargetResource zestaw**, i **TargetResource testu**.</span><span class="sxs-lookup"><span data-stu-id="25730-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="25730-133">Wszystkie trzy funkcje należy przełączyć zestaw parametrów, który jest taki sam jak zbiór właściwości zdefiniowane w schemacie MOF, który został utworzony dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="25730-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="25730-134">W tym dokumencie to zbiór właściwości nazywa się "właściwości zasobów."</span><span class="sxs-lookup"><span data-stu-id="25730-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="25730-135">Te trzy funkcje w pliku o nazwie magazynu <ResourceName>.psm1.</span><span class="sxs-lookup"><span data-stu-id="25730-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="25730-136">W poniższym przykładzie funkcje są przechowywane w pliku o nazwie Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="25730-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> <span data-ttu-id="25730-137">**Uwaga**: po uruchomieniu tego samego skryptu konfiguracji na zasobie więcej niż raz, powinien zostać wyświetlony bez błędów i zasobu może pozostawać w takim samym stanie jako raz uruchamiania skryptu.</span><span class="sxs-lookup"><span data-stu-id="25730-137">**Note**: When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="25730-138">Aby to zrobić, upewnij się, że Twoje **Get-TargetResource** i **TargetResource testu** funkcje Pozostaw bez zmian zasobu i że wywoływanie **Set-TargetResource**działać więcej niż raz w sekwencji z tego samego parametru wartości jest zawsze równoważne wywoływanie jej raz.</span><span class="sxs-lookup"><span data-stu-id="25730-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="25730-139">W **Get TargetResource** funkcji implementacji, należy użyć wartości właściwości klucza zasobu, które znajdują się jako parametry do sprawdzania stanu wystąpienia określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="25730-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="25730-140">Ta funkcja musi zwracać tabelę wyznaczania wartości skrótu, która zawiera wszystkie właściwości zasobu jako klucze i rzeczywiste wartości tych właściwości jako odpowiednie wartości.</span><span class="sxs-lookup"><span data-stu-id="25730-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="25730-141">Poniższy kod stanowi przykład.</span><span class="sxs-lookup"><span data-stu-id="25730-141">The following code provides an example.</span></span>

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

<span data-ttu-id="25730-142">W zależności od wartości, które są określone dla właściwości zasobów w skrypcie konfiguracji **TargetResource zestaw** należy wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="25730-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="25730-143">Utwórz nową witrynę sieci Web</span><span class="sxs-lookup"><span data-stu-id="25730-143">Create a new website</span></span>
* <span data-ttu-id="25730-144">Aktualizowanie istniejącej witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="25730-144">Update an existing website</span></span>
* <span data-ttu-id="25730-145">Usuń istniejącej witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="25730-145">Delete an existing website</span></span>

<span data-ttu-id="25730-146">Poniższy przykład przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="25730-146">The following example illustrates this.</span></span>

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

<span data-ttu-id="25730-147">Na koniec **TargetResource testu** funkcji musi mieć tego samego zestawu jako parametrów **Get-TargetResource** i **TargetResource zestawu**.</span><span class="sxs-lookup"><span data-stu-id="25730-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="25730-148">W implementacji **TargetResource testu**, sprawdź stan wystąpienia zasobu, który określono w parametrach klucza.</span><span class="sxs-lookup"><span data-stu-id="25730-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="25730-149">W przypadku rzeczywisty stan wystąpienia zasobu nie odpowiada wartości podanych w zestaw parametrów, zwraca **$false**.</span><span class="sxs-lookup"><span data-stu-id="25730-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="25730-150">W przeciwnym razie zwraca **$true**.</span><span class="sxs-lookup"><span data-stu-id="25730-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="25730-151">Poniższy kod implementuje **TargetResource testu** funkcji.</span><span class="sxs-lookup"><span data-stu-id="25730-151">The following code implements the **Test-TargetResource** function.</span></span>

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

<span data-ttu-id="25730-152">**Uwaga**: ułatwiają debugowanie, użyj **Write-Verbose** polecenia cmdlet w implementacji poprzednie trzy funkcje.</span><span class="sxs-lookup"><span data-stu-id="25730-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="25730-153">To polecenie cmdlet zapisuje tekst w strumieniu komunikat trybu informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="25730-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="25730-154">Domyślnie nie jest wyświetlany komunikat trybu informacji pełnej strumienia, ale można je wyświetlić, zmieniając wartość **$VerbosePreference** zmiennej lub za pomocą **pełne** parametru w poleceniach cmdlet DSC = new.</span><span class="sxs-lookup"><span data-stu-id="25730-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="25730-155">Tworzenie manifestu modułu</span><span class="sxs-lookup"><span data-stu-id="25730-155">Creating the module manifest</span></span>

<span data-ttu-id="25730-156">Na koniec użyj **ModuleManifest nowy** polecenia cmdlet, aby zdefiniować <ResourceName>plik psd1 dla modułu zasobów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="25730-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="25730-157">Po wywołaniu tego polecenia cmdlet, odwołanie pliku modułu (.psm1) skrypt, które są opisane w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="25730-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="25730-158">Obejmują **Get-TargetResource**, **TargetResource zestaw**, i **TargetResource testu** na liście funkcji do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="25730-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="25730-159">Poniżej znajduje się przykładowy plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="25730-159">Following is an example manifest file.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="25730-160">Obsługa PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="25730-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="25730-161">**Uwaga:** **PsDscRunAsCredential** jest obsługiwana w programie PowerShell 5.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="25730-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="25730-162">**PsDscRunAsCredential** właściwość może być używana w [konfiguracji DSC](configurations.md) bloku zasobów, aby określić, że zasób powinny być uruchamiane w określonym zestawie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="25730-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="25730-163">Aby uzyskać więcej informacji, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="25730-163">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="25730-164">Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć automatycznego zmiennej `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="25730-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="25730-165">Na przykład następujący kod zapisać kontekstu użytkownika, na którym uruchomiono zasobu w strumieniu pełne dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="25730-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```