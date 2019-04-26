---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Opcje poświadczeń w danych konfiguracji
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080156"
---
# <a name="credentials-options-in-configuration-data"></a>Opcje poświadczeń w danych konfiguracji

>Dotyczy: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Hasła w postaci zwykłego tekstu, a użytkownicy domeny

Konfiguracje DSC zawierający poświadczenia bez szyfrowania wygeneruje komunikat o błędzie dotyczących haseł w postaci zwykłego tekstu.
Ponadto DSC wygeneruje ostrzeżenie, gdy przy użyciu poświadczeń domeny.
Aby pominąć tych błędów i komunikaty ostrzegawcze, użyj słowa kluczowe dane konfiguracji DSC:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Przechowywanie/przekazywania niezaszyfrowane hasła w postaci jawnej ogólnie nie jest bezpieczne. Zalecane jest zabezpieczanie poświadczenia za pomocą techniki omówione w dalszej części tego tematu.
> Usługa Azure Automation DSC umożliwia centralne zarządzanie poświadczenia, aby być skompilowany w konfiguracji i bezpiecznie przechowywane.
> Aby uzyskać informacje Zobacz: [Kompilowanie konfiguracji DSC / poświadczeń trwałych](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Obsługa poświadczeń w DSC

Zasoby konfiguracji DSC Uruchom jako `Local System` domyślnie.
Niektóre zasoby muszą mieć jednak poświadczenia, na przykład gdy `Package` zasobu należy zainstalować oprogramowanie w ramach określonego konta użytkownika.

Wcześniejsze zasoby użyte, ustalone `Credential` nazwę właściwości, aby to obsłużyć.
Program WMF 5.0 dodaje automatyczne `PsDscRunAsCredential` właściwości dla wszystkich zasobów.
Aby uzyskać informacje o używaniu `PsDscRunAsCredential`, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](runAsUser.md).
Nowsze zasobów i zasobów niestandardowych można użyć tej właściwości automatyczne zamiast tworzyć własne właściwości dla poświadczenia.

> [!NOTE]
> Projekt niektóre zasoby są używają wielu poświadczeń z określonego powodu i będą mieć własne właściwości poświadczeń.

Aby znaleźć dostępne poświadczeń we właściwościach zasobu należy użyć `Get-DscResource -Name ResourceName -Syntax` i technologii Intellisense w środowisku ISE (`CTRL+SPACE`).

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

W tym przykładzie użyto [grupy](../resources/resources.md) zasób z `PSDesiredStateConfiguration` modułu wbudowanego zasobów DSC.
Można utworzyć grupy lokalne i dodać lub usunąć członków.
Akceptuje zarówno `Credential` właściwość i automatyczne `PsDscRunAsCredential` właściwości.
Jednak tylko używa zasobu `Credential` właściwości.

Aby uzyskać więcej informacji na temat `PsDscRunAsCredential` właściwości, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Przykład: Zasób grupy właściwości Credential

DSC, o których uruchamiany `Local System`, więc jest już uprawnień do zmiany użytkowników i grup lokalnych.
Jeśli dodano element członkowski jest kontem lokalnym, poświadczenie nie jest konieczne.
Jeśli `Group` zasobów doda konto domeny do lokalnej grupy, a następnie poświadczenie jest konieczne.

Nie są dozwolone anonimowe zapytania do usługi Active Directory.
`Credential` Właściwość `Group` zasobów jest kontem domeny, używany do wykonywania zapytań w usłudze Active Directory.
W większości przypadków prawdopodobnie ogólne konto użytkownika, domyślnie użytkownicy mogą *odczytu* większości obiektów w usłudze Active Directory.

## <a name="example-configuration"></a>Przykładowa konfiguracja

Poniższy przykład kodu używa DSC do wypełniania grupy lokalnej o użytkownik domeny:

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Ten kod generuje błąd i komunikat ostrzegawczy:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

Ten przykład ma dwa problemy:

1. Błąd wyjaśnia, czy hasła w postaci zwykłego tekstu nie są zalecane
2. Ostrzeżenie z informacją o tym względem przy użyciu poświadczeń domeny

Flagi **PSDSCAllowPlainTextPassword** i **PSDSCAllowDomainUser** pomija błąd i ostrzeżenie informujące użytkownika zagrożenia.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Pierwszy komunikat o błędzie zawiera adres URL z dokumentacją.
Ten link wyjaśnia, jak zaszyfrować hasła, przy użyciu [ConfigurationData](./configData.md) struktury i certyfikatu.
Aby uzyskać więcej informacji o certyfikatach i DSC [przeczytaj ten wpis](http://aka.ms/certs4dsc).

Aby wymusić hasła w postaci zwykłego tekstu, wymaga zasób `PsDscAllowPlainTextPassword` — słowo kluczowe w danych konfiguracji sekcji w następujący sposób:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

**PSDSCAllowPlainTextPassword** Flaga wymaga, że użytkownik potwierdza ryzyko przechowywanie haseł w postaci zwykłego tekstu w pliku MOF. W wygenerowanym pliku MOF mimo że **PSCredential** obiekt zawierający **SecureString** użyto hasła wciąż będą wyświetlane jako zwykły tekst. Jest to jedyny raz, którego poświadczenia są widoczne. Uzyskiwanie dostępu do tego pliku MOF, daje każdy dostęp do konta administratora.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Poświadczenia przesyłanych i magazynowanych

- **PSDscAllowPlainTextPassword** Flaga umożliwia kompilacji pliki MOF zawierające hasła w postaci zwykłego tekstu.
  Należy zachować środki ostrożności podczas zapisywania pliki MOF zawierające hasła w postaci zwykłego tekstu.
- Dostarczenia pliku MOF do węzła w **wypychania** trybie WinRM szyfruje komunikację z usługą ochrony zwykłego tekstu, jeśli nie możesz zastąpić to ustawienie domyślne z **AllowUnencrypted** parametru.
  - Zaszyfrowanie pliku MOF przy użyciu certyfikatu chroni plik MOF w spoczynku, zanim zostały doliczone do węzła.
- W **ściągnięcia** trybu, można skonfigurować serwera ściągania Windows do używania protokołu HTTPS do szyfrowania ruchu przy użyciu protokołu określonego w Internet Information Server. Aby uzyskać więcej informacji, zobacz artykuły [Konfigurowanie klienta ściągania DSC](../pull-server/pullclient.md) i [MOF Zabezpieczanie plików przy użyciu certyfikatów](../pull-server/secureMOF.md).
  - W [konfiguracji stanu automatyzacji Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) usługi ściągania ruchu są zawsze szyfrowane.
- W węźle pliki MOF są szyfrowane, gdy w programie PowerShell 5.0.
  - W programie PowerShell 4.0 w pliku MOF pliki są niezaszyfrowane w spoczynku, chyba że są szyfrowane przy użyciu certyfikatu podczas wypychania lub pobierane do węzła.

**Microsoft informacją o tym, aby uniknąć hasła w formacie tekstowym ze względu na istotne zagrożenie bezpieczeństwa.**

## <a name="domain-credentials"></a>Poświadczenia domeny

Nadal uruchomione ponownie skrypt konfiguracji przykład (z lub bez szyfrowania), generuje ostrzeżenie, niezalecana korzystać z domeny, konto dla poświadczeń.
Za pomocą konta lokalnego pozwala wyeliminować ryzyko poświadczeń domeny, które mogłyby zostać użyte na innych serwerach.

**Korzystając z poświadczeń przy użyciu zasobów DSC, należy najpierw konta lokalnego za pośrednictwem konta domeny, jeśli jest to możliwe.**

W przypadku "\\"lub"\@" w `Username` właściwości poświadczeń, a następnie DSC będzie je traktować jako konto domeny.
Występuje wyjątek "localhost", "127.0.0.1" i ":: 1" w domenie część nazwy użytkownika.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

W DSC `Group` przykładu zasobów powyżej, wykonywanie zapytań do domeny usługi Active Directory *wymaga* konta domeny.
W takim przypadku Dodaj `PSDscAllowDomainUser` właściwość `ConfigurationData` blokowania w następujący sposób:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Teraz skryptu konfiguracji spowoduje wygenerowanie pliku MOF bez błędów i ostrzeżeń.
