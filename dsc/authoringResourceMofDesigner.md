---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Przy użyciu narzędzia Projektant zasobów
ms.openlocfilehash: e0282671861755a5f147de4d07783a4680024ec5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="5f8c3-103">Przy użyciu narzędzia Projektant zasobów</span><span class="sxs-lookup"><span data-stu-id="5f8c3-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="5f8c3-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5f8c3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5f8c3-105">Narzędzia projektanta zasobów to zbiór poleceń cmdlet udostępnianych przez **xDscResourceDesigner** moduł, który ułatwić tworzenie zasobów systemu Windows PowerShell Desired stan konfiguracji (DSC).</span><span class="sxs-lookup"><span data-stu-id="5f8c3-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="5f8c3-106">Poleceń cmdlet dla tego zasobu utworzenia schematu MOF, moduł skryptu i struktura katalogów dla nowego zasobu.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="5f8c3-107">Aby uzyskać więcej informacji o zasobach DSC, zobacz [kompilacji systemu Windows PowerShell Desired stan konfiguracji zasobów niestandardowych](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="5f8c3-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="5f8c3-108">W tym temacie utworzymy DSC zasobu, który zarządza użytkowników usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="5f8c3-109">Użyj [instalacji modułu](https://technet.microsoft.com/library/dn807162.aspx) polecenia cmdlet, aby zainstalować **xDscResourceDesigner** modułu.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-109">Use the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="5f8c3-110">**Uwaga**: **instalacji modułu** znajduje się w **PowerShellGet** moduł, który jest dostępny w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="5f8c3-111">Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [PackageManagement moduły programu PowerShell w wersji zapoznawczej](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="5f8c3-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="5f8c3-112">Utworzenie właściwości zasobów</span><span class="sxs-lookup"><span data-stu-id="5f8c3-112">Creating resource properties</span></span>
<span data-ttu-id="5f8c3-113">W pierwszej kolejności konieczne jest podejmowanie decyzji o właściwości, które powoduje to udostępnienie zasobu.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="5f8c3-114">Na przykład zdefiniujemy użytkownika usługi Active Directory z następującymi właściwościami.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="5f8c3-115">Nazwa parametru opis</span><span class="sxs-lookup"><span data-stu-id="5f8c3-115">Parameter name  Description</span></span>
* <span data-ttu-id="5f8c3-116">**Nazwa użytkownika**: Klucz właściwości, które jednoznacznie identyfikuje użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="5f8c3-117">**Upewnij się,**: Określa, czy konto użytkownika powinno być obecna nieobecne.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="5f8c3-118">Ten parametr ma tylko dwa możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="5f8c3-119">**DomainCredential**: domena hasło dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="5f8c3-120">**Hasło**: wymagane hasło dla użytkownika umożliwia konfigurację zmienić hasło użytkownika, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="5f8c3-121">Aby utworzyć właściwości, używamy **xDscResourceProperty nowy** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="5f8c3-122">Następujące polecenia programu PowerShell Utwórz właściwości opisanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="5f8c3-123">Utwórz zasób</span><span class="sxs-lookup"><span data-stu-id="5f8c3-123">Create the resource</span></span>

<span data-ttu-id="5f8c3-124">Teraz, gdy zostały utworzone właściwości zasobów, można nazywamy **xDscResource nowy** polecenia cmdlet do utworzenia zasobu.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="5f8c3-125">**XDscResource nowy** polecenia cmdlet przyjmuje listę właściwości parametry.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="5f8c3-126">Ma również ścieżki, w którym ma zostać utworzony moduł, nazwę nowego zasobu i nazwę modułu, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="5f8c3-127">Następujące polecenie programu PowerShell tworzy zasób.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="5f8c3-128">**XDscResource nowy** polecenie cmdlet tworzy schematu MOF, skrypt zasobu szkielet, struktura katalogów wymagane dla nowego zasobu i manifestu moduł, który udostępnia nowy zasób.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="5f8c3-129">Plik MOF schematu jest w **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, i jego zawartość jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="5f8c3-130">Skrypt zasobów znajduje się na **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="5f8c3-131">Nie ma rzeczywistego logikę do zaimplementowania zasób, który należy dodać samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="5f8c3-132">Poniżej znajdują się zawartość szkielet skryptu.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="5f8c3-133">Aktualizuje zasób</span><span class="sxs-lookup"><span data-stu-id="5f8c3-133">Updating the resource</span></span>

<span data-ttu-id="5f8c3-134">Jeśli musisz dodać lub zmodyfikować listy parametrów zasobu, należy wywołać **xDscResource aktualizacji** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="5f8c3-135">Polecenie cmdlet aktualizuje zasób z listą nowych parametrów.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="5f8c3-136">Jeśli logiki zostało już dodane do skryptu zasobu, jest pozostawiany bez zmian.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="5f8c3-137">Na przykład załóżmy, że mają zostać uwzględnione w dzienniku ostatniego w czasie dla użytkownika w naszym zasobów.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="5f8c3-138">Zamiast zapisywania ponownie całkowicie zasobu, należy wywołać **xDscResourceProperty nowy** do utworzenia nowej właściwości, a następnie wywołaj **xDscResource aktualizacji** i dodać nowe właściwości Lista właściwości.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="5f8c3-139">Testowanie schematu zasobów</span><span class="sxs-lookup"><span data-stu-id="5f8c3-139">Testing a resource schema</span></span>

<span data-ttu-id="5f8c3-140">Narzędzia projektanta zasobów przedstawia jedną więcej polecenia cmdlet, który może służyć do testowania ważności schematu MOF, który napisano ręcznie.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="5f8c3-141">Wywołanie **xDscSchema testu** polecenia cmdlet, przekazując ścieżkę schematu zasobów MOF jako parametr.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="5f8c3-142">Polecenie cmdlet dane wyjściowe obejmują wszelkie błędy w schemacie.</span><span class="sxs-lookup"><span data-stu-id="5f8c3-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="5f8c3-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f8c3-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="5f8c3-144">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="5f8c3-144">Concepts</span></span>
[<span data-ttu-id="5f8c3-145">Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów</span><span class="sxs-lookup"><span data-stu-id="5f8c3-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="5f8c3-146">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="5f8c3-146">Other Resources</span></span>
[<span data-ttu-id="5f8c3-147">xDscResourceDesigner modułu</span><span class="sxs-lookup"><span data-stu-id="5f8c3-147">xDscResourceDesigner Module</span></span>](https://powershellgallery.com/packages/xDscResourceDesigner)