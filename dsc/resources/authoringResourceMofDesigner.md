---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Przy użyciu narzędzia Projektant zasobów
ms.openlocfilehash: 3fd2f06cf46602ee30dd34f8e7bd77d3c92b808f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076671"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="d3493-103">Przy użyciu narzędzia Projektant zasobów</span><span class="sxs-lookup"><span data-stu-id="d3493-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="d3493-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d3493-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d3493-105">Narzędzie Projektant zasobów to zbiór poleceń cmdlet udostępnianych przez **xDscResourceDesigner** moduł, który w ułatwienia tworzenia zasobów Windows PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="d3493-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="d3493-106">Polecenia cmdlet w tym zasobie utworzenia schematu pliku MOF, moduł skryptu i struktury katalogów dla nowego zasobu.</span><span class="sxs-lookup"><span data-stu-id="d3493-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="d3493-107">Aby uzyskać więcej informacji na temat zasobów DSC, zobacz [kompilacji Windows PowerShell Desired State Configuration zasobów niestandardowych](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="d3493-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="d3493-108">W tym temacie utworzymy zasobu DSC, który zarządza użytkowników usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d3493-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="d3493-109">Użyj [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby zainstalować **xDscResourceDesigner** modułu.</span><span class="sxs-lookup"><span data-stu-id="d3493-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="d3493-110">**Uwaga**: **Install-Module** znajduje się w **PowerShellGet** moduł, który znajduje się w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="d3493-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="d3493-111">Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [Podgląd modułów programu PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="d3493-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="d3493-112">Utworzenie właściwości zasobów</span><span class="sxs-lookup"><span data-stu-id="d3493-112">Creating resource properties</span></span>
<span data-ttu-id="d3493-113">Pierwszą rzeczą, jaką musimy jest, wybierz właściwości, które spowodują ujawnienie zasobu.</span><span class="sxs-lookup"><span data-stu-id="d3493-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="d3493-114">W tym przykładzie definiujemy użytkownika usługi Active Directory, z następującymi właściwościami.</span><span class="sxs-lookup"><span data-stu-id="d3493-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="d3493-115">Nazwa parametru opis</span><span class="sxs-lookup"><span data-stu-id="d3493-115">Parameter name  Description</span></span>
* <span data-ttu-id="d3493-116">**Nazwa użytkownika**: Właściwość klucza, który unikatowo identyfikuje użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d3493-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="d3493-117">**Upewnij się,**: Określa, czy konto użytkownika powinno być obecne lub nieobecne.</span><span class="sxs-lookup"><span data-stu-id="d3493-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="d3493-118">Ten parametr ma tylko dwa możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="d3493-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="d3493-119">**DomainCredential**: Hasło użytkownika domeny.</span><span class="sxs-lookup"><span data-stu-id="d3493-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="d3493-120">**hasło**: Wymagane hasło dla użytkownika, które umożliwia konfigurację zmienić hasło użytkownika, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="d3493-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="d3493-121">Aby utworzyć właściwości, użyjemy **New xDscResourceProperty** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d3493-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="d3493-122">Następujące polecenia środowiska PowerShell Utwórz właściwości opisanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="d3493-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="d3493-123">Utwórz zasób</span><span class="sxs-lookup"><span data-stu-id="d3493-123">Create the resource</span></span>

<span data-ttu-id="d3493-124">Teraz, gdy zostały utworzone właściwości zasobów, możemy wywołać **New xDscResource** polecenia cmdlet, aby utworzyć zasób.</span><span class="sxs-lookup"><span data-stu-id="d3493-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="d3493-125">**New xDscResource** polecenie cmdlet przyjmuje listę właściwości jako parametry.</span><span class="sxs-lookup"><span data-stu-id="d3493-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="d3493-126">Zajmuje się także, ścieżka, gdzie można utworzyć modułu, Nazwa nowego zasobu i nazwę modułu, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="d3493-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="d3493-127">Następujące polecenie programu PowerShell tworzy zasób.</span><span class="sxs-lookup"><span data-stu-id="d3493-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="d3493-128">**New xDscResource** polecenie cmdlet tworzy schematu pliku MOF, skrypt zasobu szkielet, struktura katalogów wymagane dla nowego zasobu i manifestu modułu, który uwidacznia nowego zasobu.</span><span class="sxs-lookup"><span data-stu-id="d3493-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="d3493-129">Plik schematu pliku MOF wynosi **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, i jego zawartość jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d3493-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

<span data-ttu-id="d3493-130">Skrypt zasobu wynosi **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="d3493-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="d3493-131">Nie ma rzeczywisty logikę w celu zaimplementowania zasobu, którego musisz samodzielnie dodać.</span><span class="sxs-lookup"><span data-stu-id="d3493-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="d3493-132">Poniżej znajdują się zawartość skryptu szkielet.</span><span class="sxs-lookup"><span data-stu-id="d3493-132">The contents of the skeleton script are as follows.</span></span>

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}


function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $result = [System.Boolean]

  $result
  #>
}


Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a><span data-ttu-id="d3493-133">Aktualizowanie zasobu</span><span class="sxs-lookup"><span data-stu-id="d3493-133">Updating the resource</span></span>

<span data-ttu-id="d3493-134">Jeśli potrzebujesz dodać lub zmodyfikować listę parametrów zasobu, można wywołać **xDscResource aktualizacji** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d3493-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="d3493-135">Polecenia cmdlet zasobów zostaje zaktualizowana o listę nowych parametrów.</span><span class="sxs-lookup"><span data-stu-id="d3493-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="d3493-136">Jeśli masz już dodany logiki w skrypcie zasobów, pozostanie bez zmian.</span><span class="sxs-lookup"><span data-stu-id="d3493-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="d3493-137">Na przykład załóżmy, że mają zostać uwzględnione ostatni dziennik w czasie dla użytkownika w naszych zasobów.</span><span class="sxs-lookup"><span data-stu-id="d3493-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="d3493-138">Zamiast pisania ponownie całkowicie zasobu, można wywołać **New xDscResourceProperty** Aby utworzyć nową właściwość, a następnie wywołaj **xDscResource aktualizacji** i dodać nowe właściwości Lista właściwości.</span><span class="sxs-lookup"><span data-stu-id="d3493-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="d3493-139">Testowanie schematu zasobów</span><span class="sxs-lookup"><span data-stu-id="d3493-139">Testing a resource schema</span></span>

<span data-ttu-id="d3493-140">Narzędzie Projektant zasobów przedstawia jeden więcej polecenia cmdlet, które mogą służyć do testowania poprawność schematu pliku MOF, który zostały napisane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="d3493-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="d3493-141">Wywołaj **xDscSchema testu** polecenia cmdlet, przekazując ścieżkę schematu zasobów MOF jako parametr.</span><span class="sxs-lookup"><span data-stu-id="d3493-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="d3493-142">Polecenie cmdlet zwróci wszystkie błędy w schemacie.</span><span class="sxs-lookup"><span data-stu-id="d3493-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="d3493-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3493-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="d3493-144">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="d3493-144">Concepts</span></span>
[<span data-ttu-id="d3493-145">Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów</span><span class="sxs-lookup"><span data-stu-id="d3493-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="d3493-146">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="d3493-146">Other Resources</span></span>
[<span data-ttu-id="d3493-147">xDscResourceDesigner Module</span><span class="sxs-lookup"><span data-stu-id="d3493-147">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
