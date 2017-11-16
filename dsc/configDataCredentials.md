---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Opcje poświadczeń w danych konfiguracji"
ms.openlocfilehash: 94ff541fc517254ef2876c424307513eaf1d362a
ms.sourcegitcommit: 28e71b0ae868014523631fec3f5417de751944f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2017
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="442a2-103">Opcje poświadczeń w danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="442a2-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="442a2-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="442a2-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="442a2-105">Haseł w postaci zwykłego tekstu, a użytkownicy domeny</span><span class="sxs-lookup"><span data-stu-id="442a2-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="442a2-106">Konfiguracji DSC zawierający poświadczenia bez szyfrowania wygeneruje komunikat o błędzie dotyczący haseł w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="442a2-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="442a2-107">Ponadto DSC wygeneruje ostrzeżenie, gdy przy użyciu poświadczeń domeny.</span><span class="sxs-lookup"><span data-stu-id="442a2-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="442a2-108">Aby pominąć tych błędów i ostrzeżeń, użyj słowa kluczowe dane konfiguracji DSC:</span><span class="sxs-lookup"><span data-stu-id="442a2-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="442a2-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="442a2-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="442a2-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="442a2-110">**PsDscAllowDomainUser**</span></span>

><span data-ttu-id="442a2-111">**Uwagi:**</span><span class="sxs-lookup"><span data-stu-id="442a2-111">**Notes:**</span></span> <p><span data-ttu-id="442a2-112">Przechowywanie/przesyła niezaszyfrowane hasła w postaci zwykłego tekstu zwykle nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="442a2-112">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="442a2-113">Zaleca się zabezpieczenie poświadczeń przy użyciu techniki omówione w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="442a2-113">Securing credentials by using the techniques covered later in this topic is recommended.</span></span></p> <p><span data-ttu-id="442a2-114">Usługi Konfiguracja DSC automatyzacji Azure umożliwia centralne zarządzanie poświadczenia, aby być skompilowany w konfiguracji i bezpiecznie przechowywane.</span><span class="sxs-lookup"><span data-stu-id="442a2-114">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>  <span data-ttu-id="442a2-115">Aby uzyskać informacje, zobacz: [kompilowania konfiguracji DSC / zasoby poświadczeń](https://docs.microsoft.com/en-in/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="442a2-115">For information, see: [Compiling DSC Configurations / Credential Assets](https://docs.microsoft.com/en-in/azure/automation/automation-dsc-compile#credential-assets)</span></span></p>

<span data-ttu-id="442a2-116">Poniżej przedstawiono przykład przekazywania poświadczeń w postaci zwykłego tekstu:</span><span class="sxs-lookup"><span data-stu-id="442a2-116">The following is an example of passing plain text credentials:</span></span>

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

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="442a2-117">Obsługa poświadczeń w konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="442a2-117">Handling Credentials in DSC</span></span>

<span data-ttu-id="442a2-118">Zasoby konfiguracji DSC Uruchom jako `Local System` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="442a2-118">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="442a2-119">Jednak niektóre zasoby potrzebne poświadczenia, na przykład gdy `Package` zasobów, należy zainstalować oprogramowanie w ramach określonego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="442a2-119">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="442a2-120">Używane wcześniej zasoby ustalony `Credential` nazwę właściwości, aby rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="442a2-120">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="442a2-121">Automatyczne dodany WMF 5.0 `PsDscRunAsCredential` właściwości dla wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="442a2-121">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="442a2-122">Aby uzyskać informacje o korzystaniu z `PsDscRunAsCredential`, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="442a2-122">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="442a2-123">Nowsze zasobów i zasobów niestandardowych można użyć tej właściwości automatyczne zamiast tworzenia własnych właściwości dla poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="442a2-123">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

><span data-ttu-id="442a2-124">**Uwaga:** projektu niektórych zasobów są używają wielu poświadczeń z określonego powodu i mają własne właściwości poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="442a2-124">**Note:** the design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="442a2-125">Aby odnaleźć dostępne poświadczeń właściwości w zasobie użyj jednej `Get-DscResource -Name ResourceName -Syntax` i technologii Intellisense w ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="442a2-125">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="442a2-126">W tym przykładzie użyto [grupy](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) zasób z `PSDesiredStateConfiguration` wbudowany moduł zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="442a2-126">This example uses a [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="442a2-127">Możesz tworzyć grupy lokalne i dodać lub usunąć członków.</span><span class="sxs-lookup"><span data-stu-id="442a2-127">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="442a2-128">Akceptuje zarówno `Credential` właściwości i automatyczne `PsDscRunAsCredential` właściwości.</span><span class="sxs-lookup"><span data-stu-id="442a2-128">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="442a2-129">Jednak używa tylko zasób `Credential` właściwości.</span><span class="sxs-lookup"><span data-stu-id="442a2-129">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="442a2-130">Aby uzyskać więcej informacji na temat `PsDscRunAsCredential` właściwości, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="442a2-130">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="442a2-131">Przykład: Grupy zasobów właściwości poświadczeń</span><span class="sxs-lookup"><span data-stu-id="442a2-131">Example: The Group resource Credential property</span></span>

<span data-ttu-id="442a2-132">DSC jest uruchamiana `Local System`, więc jest już uprawnień do zmiany użytkowników i grup lokalnych.</span><span class="sxs-lookup"><span data-stu-id="442a2-132">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="442a2-133">Jeśli dodano element członkowski jest kontem lokalnym, niezbędne jest nie ma poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="442a2-133">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="442a2-134">Jeśli `Group` zasobów dodaje konto domeny do lokalnej grupy, a następnie konieczne jest podanie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="442a2-134">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="442a2-135">Nie są dozwolone anonimowe zapytania do usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="442a2-135">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="442a2-136">`Credential` Właściwość `Group` zasób jest konto domeny używane do zapytania usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="442a2-136">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="442a2-137">W większości przypadków może to być konto użytkownika ogólnego, ponieważ domyślnie użytkownicy mogą *odczytu* większość obiektów w usłudze Active Directory.</span><span class="sxs-lookup"><span data-stu-id="442a2-137">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="442a2-138">Przykładowa konfiguracja</span><span class="sxs-lookup"><span data-stu-id="442a2-138">Example Configuration</span></span>

<span data-ttu-id="442a2-139">Poniższy przykład kodu wykorzystuje DSC do wypełniania grupy lokalnej z użytkownikiem domeny:</span><span class="sxs-lookup"><span data-stu-id="442a2-139">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="442a2-140">Ten kod generuje zarówno błędu i ostrzeżenia:</span><span class="sxs-lookup"><span data-stu-id="442a2-140">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="442a2-141">W tym przykładzie występują dwa problemy:</span><span class="sxs-lookup"><span data-stu-id="442a2-141">This example has two issues:</span></span>
1.  <span data-ttu-id="442a2-142">Wystąpił błąd wyjaśniono, że haseł w postaci zwykłego tekstu nie są zalecane</span><span class="sxs-lookup"><span data-stu-id="442a2-142">An error explains that plain text passwords are not recommended</span></span>
2.  <span data-ttu-id="442a2-143">Ostrzeżenia z informacją o tym przed przy użyciu poświadczeń domeny</span><span class="sxs-lookup"><span data-stu-id="442a2-143">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="442a2-144">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="442a2-144">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="442a2-145">Pierwszy komunikat o błędzie zawiera adres URL z dokumentacją.</span><span class="sxs-lookup"><span data-stu-id="442a2-145">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="442a2-146">To łącze wyjaśniono, jak do szyfrowania haseł przy użyciu [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) struktury i certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="442a2-146">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="442a2-147">Aby uzyskać więcej informacji o certyfikatach i DSC [odczytać ten wpis](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="442a2-147">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="442a2-148">Aby wymusić hasła w postaci zwykłego tekstu, wymaga zasób `PsDscAllowPlainTextPassword` — słowo kluczowe w danych konfiguracji sekcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="442a2-148">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

><span data-ttu-id="442a2-149">**Uwaga:** `NodeName` nie może być równa gwiazdka nazwę określonego węzła jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="442a2-149">**Note:** `NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="442a2-150">**Microsoft informacją o tym, aby uniknąć hasła w formacie tekstowym z powodu znaczące zagrożenie bezpieczeństwa.**</span><span class="sxs-lookup"><span data-stu-id="442a2-150">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>
<span data-ttu-id="442a2-151">Wystąpił wyjątek może być podczas korzystania z usługi Konfiguracja DSC automatyzacji Azure tylko dane zawsze jest przechowywany jako zaszyfrowany (podczas przesyłania, przechowywane w usłudze i magazynowane w węźle).</span><span class="sxs-lookup"><span data-stu-id="442a2-151">An exception would be when using the Azure Automation DSC service, only because the data is always stored encrypted (in transit, at rest in the service, and at rest on the node).</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="442a2-152">Poświadczenia domeny</span><span class="sxs-lookup"><span data-stu-id="442a2-152">Domain Credentials</span></span>

<span data-ttu-id="442a2-153">Nadal uruchomiona ponownie skryptu konfiguracji przykład (z lub bez szyfrowania), generuje ostrzeżenie, że, przy użyciu domeny konto dla poświadczeń nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="442a2-153">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="442a2-154">Za pomocą konta lokalnego eliminuje ryzyko poświadczeń domeny, które mogłyby zostać użyte na innych serwerach.</span><span class="sxs-lookup"><span data-stu-id="442a2-154">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="442a2-155">**Korzystając z poświadczeń z usługi Konfiguracja DSC zasobów, preferowane jest kontem lokalnym za pośrednictwem konta domeny, jeśli to możliwe.**</span><span class="sxs-lookup"><span data-stu-id="442a2-155">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="442a2-156">W przypadku "\' lub" @ "w `Username` właściwość credential, a następnie DSC będzie je traktować jako konto domeny.</span><span class="sxs-lookup"><span data-stu-id="442a2-156">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="442a2-157">Brak wyjątek dla "localhost", "127.0.0.1" i ":: 1" w domenie część nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="442a2-157">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="442a2-158">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="442a2-158">PSDscAllowDomainUser</span></span>

<span data-ttu-id="442a2-159">W konfiguracji DSC `Group` zasobów przykładzie przedstawionym powyżej zapytań domeny usługi Active Directory *wymaga* konta domeny.</span><span class="sxs-lookup"><span data-stu-id="442a2-159">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="442a2-160">W takim przypadku Dodaj `PSDscAllowDomainUser` właściwości `ConfigurationData` zablokować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="442a2-160">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="442a2-161">Teraz skryptu konfiguracji spowoduje wygenerowanie pliku MOF bez błędów lub ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="442a2-161">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
