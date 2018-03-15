---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Opcje poświadczeń w danych konfiguracji"
ms.openlocfilehash: 6ddf82c2b63309255ec3187d650677a6c3c2afb0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="credentials-options-in-configuration-data"></a>Opcje poświadczeń w danych konfiguracji
>Dotyczy: Środowiska Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Haseł w postaci zwykłego tekstu, a użytkownicy domeny

Konfiguracji DSC zawierający poświadczenia bez szyfrowania wygeneruje komunikat o błędzie dotyczący haseł w postaci zwykłego tekstu.
Ponadto DSC wygeneruje ostrzeżenie, gdy przy użyciu poświadczeń domeny.
Aby pominąć tych błędów i ostrzeżeń, użyj słowa kluczowe dane konfiguracji DSC:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> Przechowywanie/przesyła niezaszyfrowane hasła w postaci zwykłego tekstu zwykle nie jest bezpieczne. Zaleca się zabezpieczenie poświadczeń przy użyciu techniki omówione w dalszej części tego tematu.
> Usługi Konfiguracja DSC automatyzacji Azure umożliwia centralne zarządzanie poświadczenia, aby być skompilowany w konfiguracji i bezpiecznie przechowywane.
> Aby uzyskać informacje, zobacz: [kompilowania konfiguracji DSC / zasoby poświadczeń](/azure/automation/automation-dsc-compile#credential-assets)

Poniżej przedstawiono przykład przekazywania poświadczeń w postaci zwykłego tekstu:

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
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a>Obsługa poświadczeń w konfiguracji DSC

Zasoby konfiguracji DSC Uruchom jako `Local System` domyślnie.
Jednak niektóre zasoby potrzebne poświadczenia, na przykład gdy `Package` zasobów, należy zainstalować oprogramowanie w ramach określonego konta użytkownika.

Używane wcześniej zasoby ustalony `Credential` nazwę właściwości, aby rozwiązać.
Automatyczne dodany WMF 5.0 `PsDscRunAsCredential` właściwości dla wszystkich zasobów.
Aby uzyskać informacje o korzystaniu z `PsDscRunAsCredential`, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).
Nowsze zasobów i zasobów niestandardowych można użyć tej właściwości automatyczne zamiast tworzenia własnych właściwości dla poświadczenia.

> [!NOTE]
> Projekt niektórych zasobów są używają wielu poświadczeń z określonego powodu i mają one właściwości własne poświadczenia.

Aby odnaleźć dostępne poświadczeń właściwości w zasobie użyj jednej `Get-DscResource -Name ResourceName -Syntax` i technologii Intellisense w ISE (`CTRL+SPACE`).

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

W tym przykładzie użyto [grupy](https://msdn.microsoft.com/powershell/dsc/groupresource) zasób z `PSDesiredStateConfiguration` wbudowany moduł zasobów usługi Konfiguracja DSC.
Możesz tworzyć grupy lokalne i dodać lub usunąć członków.
Akceptuje zarówno `Credential` właściwości i automatyczne `PsDscRunAsCredential` właściwości.
Jednak używa tylko zasób `Credential` właściwości.

Aby uzyskać więcej informacji na temat `PsDscRunAsCredential` właściwości, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Przykład: Grupy zasobów właściwości poświadczeń

DSC jest uruchamiana `Local System`, więc jest już uprawnień do zmiany użytkowników i grup lokalnych.
Jeśli dodano element członkowski jest kontem lokalnym, niezbędne jest nie ma poświadczeń.
Jeśli `Group` zasobów dodaje konto domeny do lokalnej grupy, a następnie konieczne jest podanie poświadczeń.

Nie są dozwolone anonimowe zapytania do usługi Active Directory.
`Credential` Właściwość `Group` zasób jest konto domeny używane do zapytania usługi Active Directory.
W większości przypadków może to być konto użytkownika ogólnego, ponieważ domyślnie użytkownicy mogą *odczytu* większość obiektów w usłudze Active Directory.

## <a name="example-configuration"></a>Przykładowa konfiguracja

Poniższy przykład kodu wykorzystuje DSC do wypełniania grupy lokalnej z użytkownikiem domeny:

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

Ten kod generuje zarówno błędu i ostrzeżenia:

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

W tym przykładzie występują dwa problemy:
1. Wystąpił błąd wyjaśniono, że haseł w postaci zwykłego tekstu nie są zalecane
2. Ostrzeżenia z informacją o tym przed przy użyciu poświadczeń domeny

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

Pierwszy komunikat o błędzie zawiera adres URL z dokumentacją.
To łącze wyjaśniono, jak do szyfrowania haseł przy użyciu [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) struktury i certyfikatu.
Aby uzyskać więcej informacji o certyfikatach i DSC [odczytać ten wpis](http://aka.ms/certs4dsc).

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
> `NodeName` nie może być równa gwiazdka nazwę określonego węzła jest wymagana.

**Microsoft informacją o tym, aby uniknąć hasła w formacie tekstowym z powodu znaczące zagrożenie bezpieczeństwa.**

Wystąpił wyjątek może być podczas korzystania z usługi Konfiguracja DSC automatyzacji Azure tylko dane zawsze jest przechowywany jako zaszyfrowany (podczas przesyłania, przechowywane w usłudze i magazynowane w węźle).

## <a name="domain-credentials"></a>Domain Credentials

Nadal uruchomiona ponownie skryptu konfiguracji przykład (z lub bez szyfrowania), generuje ostrzeżenie, że, przy użyciu domeny konto dla poświadczeń nie jest zalecane.
Za pomocą konta lokalnego eliminuje ryzyko poświadczeń domeny, które mogłyby zostać użyte na innych serwerach.

**Korzystając z poświadczeń z usługi Konfiguracja DSC zasobów, preferowane jest kontem lokalnym za pośrednictwem konta domeny, jeśli to możliwe.**

W przypadku "\' lub" @ "w `Username` właściwość credential, a następnie DSC będzie je traktować jako konto domeny.
Brak wyjątek dla "localhost", "127.0.0.1" i ":: 1" w domenie część nazwy użytkownika.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

W konfiguracji DSC `Group` zasobów przykładzie przedstawionym powyżej zapytań domeny usługi Active Directory *wymaga* konta domeny.
W takim przypadku Dodaj `PSDscAllowDomainUser` właściwości `ConfigurationData` zablokować w następujący sposób:

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

Teraz skryptu konfiguracji spowoduje wygenerowanie pliku MOF bez błędów lub ostrzeżeń.
