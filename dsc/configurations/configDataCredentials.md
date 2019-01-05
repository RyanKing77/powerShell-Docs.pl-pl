---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Opcje poświadczeń w danych konfiguracji
ms.openlocfilehash: 10cf3456fcc7104b7dd779db30aebace54ba087a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046645"
---
# <a name="credentials-options-in-configuration-data"></a>Opcje poświadczeń w danych konfiguracji
>Dotyczy: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Hasła w postaci zwykłego tekstu, a użytkownicy domeny

Konfiguracje DSC zawierający poświadczenia bez szyfrowania wygeneruje komunikat o błędzie dotyczących haseł w postaci zwykłego tekstu.
Ponadto DSC wygeneruje ostrzeżenie, gdy przy użyciu poświadczeń domeny.
Aby pominąć tych błędów i komunikaty ostrzegawcze, użyj słowa kluczowe dane konfiguracji DSC:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> Przechowywanie/przekazywania niezaszyfrowane hasła w postaci jawnej ogólnie nie jest bezpieczne. Zalecane jest zabezpieczanie poświadczenia za pomocą techniki omówione w dalszej części tego tematu.
> Usługa Azure Automation DSC umożliwia centralne zarządzanie poświadczenia, aby być skompilowany w konfiguracji i bezpiecznie przechowywane.
> Aby uzyskać informacje Zobacz: [Kompilowanie konfiguracji DSC / poświadczeń trwałych](/azure/automation/automation-dsc-compile#credential-assets)

Oto przykład przekazywania poświadczeń w postaci zwykłego tekstu:

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
            @{
                # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
                NodeName="*"
                PSDscAllowPlainTextPassword = $true
            },
            #however, each node still needs to be explicitly defined for "*" to have meaning
            @{
                NodeName = "TestMachine1"
            },
            #we can also use a property to define node-specific passwords, although this is no more secure
            @{
                NodeName = "TestMachine2";
                UserName = "User2"
                LocalPassword = "ThisIsYetAnotherPlaintextPassword"
            }
        )
}

configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $promptedCreds
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }
}

# We declared the ConfigurationData in a local variable, but we need to pass it
# in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData

# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

Jest to fragment pliku "MOF", wygenerowanego przez konfigurację "TestMachine1". `System.Security.SecureString` Używanych w konfiguracji został przekonwertowany na zwykły tekst i przechowywane w pliku "MOF" jako `MSF_Credential`. Element `SecureString` jest szyfrowana za pomocą bieżącego profilu użytkowników. Działa to dobrze z wszystkie formularze zarządzania zdalnego programu PowerShell. Plik "MOF" została zaprojektowana jako mechanizm autonomicznej konfiguracji autonomicznej. Począwszy od programu PowerShell w wersji 5.0 "pliki"MOF w węźle są szyfrowane w stanie spoczynku, ale nie przesyłanych do węzła. Oznacza to, czy w pliku "MOF" hasła są widoczne jako zwykłego tekstu, po zastosowaniu do węzła. Aby zaszyfrować poświadczenia, należy użyć **serwera ściągania**. Aby uzyskać więcej informacji, zobacz [MOF Zabezpieczanie plików przy użyciu certyfikatów](../pull-server/secureMOF.md).

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

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
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

Ten przykład ma dwa problemy:
1. Błąd wyjaśnia, czy hasła w postaci zwykłego tekstu nie są zalecane
2. Ostrzeżenie z informacją o tym względem przy użyciu poświadczeń domeny

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

Pierwszy komunikat o błędzie zawiera adres URL z dokumentacją.
Ten link wyjaśnia, jak zaszyfrować hasła, przy użyciu [ConfigurationData](./configData.md) struktury i certyfikatu.
Aby uzyskać więcej informacji o certyfikatach i DSC [przeczytaj ten wpis](http://aka.ms/certs4dsc).

Aby wymusić hasła w postaci zwykłego tekstu, wymaga zasób `PsDscAllowPlainTextPassword` — słowo kluczowe w danych konfiguracji sekcji w następujący sposób:

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

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> `NodeName` nie może być równa gwiazdka obowiązkowa jest tylko nazwa określonego węzła.

**Microsoft informacją o tym, aby uniknąć hasła w formacie tekstowym ze względu na istotne zagrożenie bezpieczeństwa.**

## <a name="domain-credentials"></a>Poświadczenia domeny

Nadal uruchomione ponownie skrypt konfiguracji przykład (z lub bez szyfrowania), generuje ostrzeżenie, niezalecana korzystać z domeny, konto dla poświadczeń.
Za pomocą konta lokalnego pozwala wyeliminować ryzyko poświadczeń domeny, które mogłyby zostać użyte na innych serwerach.

**Korzystając z poświadczeń przy użyciu zasobów DSC, należy najpierw konta lokalnego za pośrednictwem konta domeny, jeśli jest to możliwe.**

W przypadku "\' lub" @ "w `Username` właściwości poświadczeń, a następnie DSC będzie je traktować jako konto domeny.
Występuje wyjątek "localhost", "127.0.0.1" i ":: 1" w domenie część nazwy użytkownika.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

W DSC `Group` przykładu zasobów powyżej, wykonywanie zapytań do domeny usługi Active Directory *wymaga* konta domeny.
W takim przypadku Dodaj `PSDscAllowDomainUser` właściwość `ConfigurationData` blokowania w następujący sposób:

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

Teraz skryptu konfiguracji spowoduje wygenerowanie pliku MOF bez błędów i ostrzeżeń.
