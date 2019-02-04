---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Przy użyciu narzędzia Projektant zasobów
ms.openlocfilehash: 3fd2f06cf46602ee30dd34f8e7bd77d3c92b808f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686656"
---
# <a name="using-the-resource-designer-tool"></a>Przy użyciu narzędzia Projektant zasobów

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

Narzędzie Projektant zasobów to zbiór poleceń cmdlet udostępnianych przez **xDscResourceDesigner** moduł, który w ułatwienia tworzenia zasobów Windows PowerShell Desired State Configuration (DSC). Polecenia cmdlet w tym zasobie utworzenia schematu pliku MOF, moduł skryptu i struktury katalogów dla nowego zasobu. Aby uzyskać więcej informacji na temat zasobów DSC, zobacz [kompilacji Windows PowerShell Desired State Configuration zasobów niestandardowych](authoringResource.md).
W tym temacie utworzymy zasobu DSC, który zarządza użytkowników usługi Active Directory.
Użyj [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby zainstalować **xDscResourceDesigner** modułu.

>**Uwaga**: **Install-Module** znajduje się w **PowerShellGet** moduł, który znajduje się w programie PowerShell 5.0. Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [Podgląd modułów programu PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Utworzenie właściwości zasobów
Pierwszą rzeczą, jaką musimy jest, wybierz właściwości, które spowodują ujawnienie zasobu. W tym przykładzie definiujemy użytkownika usługi Active Directory, z następującymi właściwościami.

Nazwa parametru opis
* **Nazwa użytkownika**: Właściwość klucza, który unikatowo identyfikuje użytkownika.
* **Upewnij się,**: Określa, czy konto użytkownika powinno być obecne lub nieobecne. Ten parametr ma tylko dwa możliwe wartości.
* **DomainCredential**: Hasło użytkownika domeny.
* **Hasło**: Wymagane hasło dla użytkownika, które umożliwia konfigurację zmienić hasło użytkownika, jeśli to konieczne.

Aby utworzyć właściwości, użyjemy **New xDscResourceProperty** polecenia cmdlet. Następujące polecenia środowiska PowerShell Utwórz właściwości opisanych powyżej.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Utwórz zasób

Teraz, gdy zostały utworzone właściwości zasobów, możemy wywołać **New xDscResource** polecenia cmdlet, aby utworzyć zasób. **New xDscResource** polecenie cmdlet przyjmuje listę właściwości jako parametry. Zajmuje się także, ścieżka, gdzie można utworzyć modułu, Nazwa nowego zasobu i nazwę modułu, w którym znajduje się. Następujące polecenie programu PowerShell tworzy zasób.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

**New xDscResource** polecenie cmdlet tworzy schematu pliku MOF, skrypt zasobu szkielet, struktura katalogów wymagane dla nowego zasobu i manifestu modułu, który uwidacznia nowego zasobu.

Plik schematu pliku MOF wynosi **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, i jego zawartość jest w następujący sposób.

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

Skrypt zasobu wynosi **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Nie ma rzeczywisty logikę w celu zaimplementowania zasobu, którego musisz samodzielnie dodać. Poniżej znajdują się zawartość skryptu szkielet.

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

## <a name="updating-the-resource"></a>Aktualizowanie zasobu

Jeśli potrzebujesz dodać lub zmodyfikować listę parametrów zasobu, można wywołać **xDscResource aktualizacji** polecenia cmdlet. Polecenia cmdlet zasobów zostaje zaktualizowana o listę nowych parametrów. Jeśli masz już dodany logiki w skrypcie zasobów, pozostanie bez zmian.

Na przykład załóżmy, że mają zostać uwzględnione ostatni dziennik w czasie dla użytkownika w naszych zasobów. Zamiast pisania ponownie całkowicie zasobu, można wywołać **New xDscResourceProperty** Aby utworzyć nową właściwość, a następnie wywołaj **xDscResource aktualizacji** i dodać nowe właściwości Lista właściwości.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Testowanie schematu zasobów

Narzędzie Projektant zasobów przedstawia jeden więcej polecenia cmdlet, które mogą służyć do testowania poprawność schematu pliku MOF, który zostały napisane ręcznie. Wywołaj **xDscSchema testu** polecenia cmdlet, przekazując ścieżkę schematu zasobów MOF jako parametr. Polecenie cmdlet zwróci wszystkie błędy w schemacie.

### <a name="see-also"></a>Zobacz też

#### <a name="concepts"></a>Pojęcia
[Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów](authoringResource.md)

#### <a name="other-resources"></a>Inne zasoby
[xDscResourceDesigner Module](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
