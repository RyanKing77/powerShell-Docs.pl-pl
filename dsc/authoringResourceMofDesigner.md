---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Przy użyciu narzędzia Projektant zasobów"
ms.openlocfilehash: 5a034547d0850682513e9a80367ce148bfcf0bdc
ms.sourcegitcommit: a775e4788616490980123e8e6ea78594ffeb6f7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2017
---
# <a name="using-the-resource-designer-tool"></a>Przy użyciu narzędzia Projektant zasobów

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Narzędzia projektanta zasobów to zbiór poleceń cmdlet udostępnianych przez **xDscResourceDesigner** moduł, który ułatwić tworzenie zasobów systemu Windows PowerShell Desired stan konfiguracji (DSC). Poleceń cmdlet dla tego zasobu utworzenia schematu MOF, moduł skryptu i struktura katalogów dla nowego zasobu. Aby uzyskać więcej informacji o zasobach DSC, zobacz [kompilacji systemu Windows PowerShell Desired stan konfiguracji zasobów niestandardowych](authoringResource.md).
W tym temacie utworzymy DSC zasobu, który zarządza użytkowników usługi Active Directory.
Użyj [instalacji modułu](https://technet.microsoft.com/en-us/library/dn807162.aspx) polecenia cmdlet, aby zainstalować **xDscResourceDesigner** modułu.

>**Uwaga**: **instalacji modułu** znajduje się w **PowerShellGet** moduł, który jest dostępny w programie PowerShell 5.0. Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [PackageManagement moduły programu PowerShell w wersji zapoznawczej](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Utworzenie właściwości zasobów
W pierwszej kolejności konieczne jest podejmowanie decyzji o właściwości, które powoduje to udostępnienie zasobu. Na przykład zdefiniujemy użytkownika usługi Active Directory z następującymi właściwościami.
 
Nazwa parametru opis
* **Nazwa użytkownika**: Klucz właściwości, które jednoznacznie identyfikuje użytkownika.
* **Upewnij się,**: Określa, czy konto użytkownika powinno być obecna nieobecne. Ten parametr ma tylko dwa możliwe wartości.
* **DomainCredential**: domena hasło dla użytkownika.
* **Hasło**: wymagane hasło dla użytkownika umożliwia konfigurację zmienić hasło użytkownika, w razie potrzeby.

Aby utworzyć właściwości, używamy **xDscResourceProperty nowy** polecenia cmdlet. Następujące polecenia programu PowerShell Utwórz właściwości opisanych powyżej.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Utwórz zasób

Teraz, gdy zostały utworzone właściwości zasobów, można nazywamy **xDscResource nowy** polecenia cmdlet do utworzenia zasobu. **XDscResource nowy** polecenia cmdlet przyjmuje listę właściwości parametry. Ma również ścieżki, w którym ma zostać utworzony moduł, nazwę nowego zasobu i nazwę modułu, w którym znajduje się. Następujące polecenie programu PowerShell tworzy zasób.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

**XDscResource nowy** polecenie cmdlet tworzy schematu MOF, skrypt zasobu szkielet, struktura katalogów wymagane dla nowego zasobu i manifestu moduł, który udostępnia nowy zasób.

Plik MOF schematu jest w **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, i jego zawartość jest w następujący sposób.

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

Skrypt zasobów znajduje się na **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Nie ma rzeczywistego logikę do zaimplementowania zasób, który należy dodać samodzielnie. Poniżej znajdują się zawartość szkielet skryptu.

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

## <a name="updating-the-resource"></a>Aktualizuje zasób

Jeśli musisz dodać lub zmodyfikować listy parametrów zasobu, należy wywołać **xDscResource aktualizacji** polecenia cmdlet. Polecenie cmdlet aktualizuje zasób z listą nowych parametrów. Jeśli logiki zostało już dodane do skryptu zasobu, jest pozostawiany bez zmian.

Na przykład załóżmy, że mają zostać uwzględnione w dzienniku ostatniego w czasie dla użytkownika w naszym zasobów. Zamiast zapisywania ponownie całkowicie zasobu, należy wywołać **xDscResourceProperty nowy** do utworzenia nowej właściwości, a następnie wywołaj **xDscResource aktualizacji** i dodać nowe właściwości Lista właściwości.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Testowanie schematu zasobów

Narzędzia projektanta zasobów przedstawia jedną więcej polecenia cmdlet, który może służyć do testowania ważności schematu MOF, który napisano ręcznie. Wywołanie **xDscSchema testu** polecenia cmdlet, przekazując ścieżkę schematu zasobów MOF jako parametr. Polecenie cmdlet dane wyjściowe obejmują wszelkie błędy w schemacie.

### <a name="see-also"></a>Zobacz też

#### <a name="concepts"></a>Pojęcia
[Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów](authoringResource.md)

#### <a name="other-resources"></a>Inne zasoby
[xDscResourceDesigner modułu](https://powershellgallery.com/packages/xDscResourceDesigner)