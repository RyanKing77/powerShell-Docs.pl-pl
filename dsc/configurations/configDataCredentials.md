---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Opcje poświadczeń w danych konfiguracji
ms.openlocfilehash: c4057457bf6beb2c5fc9dffef9122cd488ccdcd7
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012436"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="e6d97-103">Opcje poświadczeń w danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e6d97-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="e6d97-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e6d97-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="e6d97-105">Hasła w postaci zwykłego tekstu, a użytkownicy domeny</span><span class="sxs-lookup"><span data-stu-id="e6d97-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="e6d97-106">Konfiguracje DSC zawierający poświadczenia bez szyfrowania wygeneruje komunikat o błędzie dotyczących haseł w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="e6d97-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="e6d97-107">Ponadto DSC wygeneruje ostrzeżenie, gdy przy użyciu poświadczeń domeny.</span><span class="sxs-lookup"><span data-stu-id="e6d97-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="e6d97-108">Aby pominąć tych błędów i komunikaty ostrzegawcze, użyj słowa kluczowe dane konfiguracji DSC:</span><span class="sxs-lookup"><span data-stu-id="e6d97-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="e6d97-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="e6d97-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="e6d97-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="e6d97-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="e6d97-111">Przechowywanie/przekazywania niezaszyfrowane hasła w postaci jawnej ogólnie nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="e6d97-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="e6d97-112">Zalecane jest zabezpieczanie poświadczenia za pomocą techniki omówione w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e6d97-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="e6d97-113">Usługa Azure Automation DSC umożliwia centralne zarządzanie poświadczenia, aby być skompilowany w konfiguracji i bezpiecznie przechowywane.</span><span class="sxs-lookup"><span data-stu-id="e6d97-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="e6d97-114">Aby uzyskać informacje Zobacz: [Kompilowanie konfiguracji DSC / poświadczeń trwałych](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="e6d97-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="e6d97-115">Oto przykład przekazywania poświadczeń w postaci zwykłego tekstu:</span><span class="sxs-lookup"><span data-stu-id="e6d97-115">The following is an example of passing plain text credentials:</span></span>

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

<span data-ttu-id="e6d97-116">Jest to fragment pliku "MOF", wygenerowanego przez konfigurację "TestMachine1".</span><span class="sxs-lookup"><span data-stu-id="e6d97-116">This is an excerpt from the ".mof" file generated by the configuration for "TestMachine1".</span></span> <span data-ttu-id="e6d97-117">`System.Security.SecureString` Używanych w konfiguracji został przekonwertowany na zwykły tekst i przechowywane w pliku "MOF" jako `MSF_Credential`.</span><span class="sxs-lookup"><span data-stu-id="e6d97-117">The `System.Security.SecureString` used in the configuration was converted to plain text and stored in the ".mof" file as a `MSF_Credential`.</span></span> <span data-ttu-id="e6d97-118">Element `SecureString` jest szyfrowana za pomocą bieżącego profilu użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e6d97-118">A `SecureString` is encrypted with the current users profile.</span></span> <span data-ttu-id="e6d97-119">Działa to dobrze z wszystkie formularze zarządzania zdalnego programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6d97-119">This works well with all forms of PowerShell remote management.</span></span> <span data-ttu-id="e6d97-120">Plik "MOF" została zaprojektowana jako mechanizm autonomicznej konfiguracji autonomicznej.</span><span class="sxs-lookup"><span data-stu-id="e6d97-120">A ".mof" file is designed to be a stand alone configuration mechanism.</span></span> <span data-ttu-id="e6d97-121">Począwszy od programu PowerShell w wersji 5.0 "pliki"MOF w węźle są szyfrowane w stanie spoczynku, ale nie przesyłanych do węzła.</span><span class="sxs-lookup"><span data-stu-id="e6d97-121">Beginning in PowerShell 5.0, ".mof" files on a Node are encrypted at rest, but not in transit to the Node.</span></span> <span data-ttu-id="e6d97-122">Oznacza to, czy w pliku "MOF" hasła są widoczne jako zwykłego tekstu, po zastosowaniu do węzła.</span><span class="sxs-lookup"><span data-stu-id="e6d97-122">This means that passwords in a ".mof" file are exposed as clear text when you apply them to a Node.</span></span> <span data-ttu-id="e6d97-123">Aby zaszyfrować poświadczenia, należy użyć **serwera ściągania**.</span><span class="sxs-lookup"><span data-stu-id="e6d97-123">To encrypt credentials, you need to use a **Pull Server**.</span></span> <span data-ttu-id="e6d97-124">Aby uzyskać więcej informacji, zobacz [MOF Zabezpieczanie plików przy użyciu certyfikatów](./pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="e6d97-124">For more information, see [Securing MOF files with Certificates](./pull-server/secureMOF.md).</span></span>

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

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="e6d97-125">Obsługa poświadczeń w DSC</span><span class="sxs-lookup"><span data-stu-id="e6d97-125">Handling Credentials in DSC</span></span>

<span data-ttu-id="e6d97-126">Zasoby konfiguracji DSC Uruchom jako `Local System` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e6d97-126">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="e6d97-127">Niektóre zasoby muszą mieć jednak poświadczenia, na przykład gdy `Package` zasobu należy zainstalować oprogramowanie w ramach określonego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e6d97-127">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="e6d97-128">Wcześniejsze zasoby użyte, ustalone `Credential` nazwę właściwości, aby to obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="e6d97-128">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="e6d97-129">Program WMF 5.0 dodaje automatyczne `PsDscRunAsCredential` właściwości dla wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="e6d97-129">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="e6d97-130">Aby uzyskać informacje o używaniu `PsDscRunAsCredential`, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="e6d97-130">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="e6d97-131">Nowsze zasobów i zasobów niestandardowych można użyć tej właściwości automatyczne zamiast tworzyć własne właściwości dla poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="e6d97-131">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="e6d97-132">Projekt niektóre zasoby są używają wielu poświadczeń z określonego powodu i będą mieć własne właściwości poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="e6d97-132">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="e6d97-133">Aby znaleźć dostępne poświadczeń we właściwościach zasobu należy użyć `Get-DscResource -Name ResourceName -Syntax` i technologii Intellisense w środowisku ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="e6d97-133">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="e6d97-134">W tym przykładzie użyto [grupy](../resources/resources.md) zasób z `PSDesiredStateConfiguration` modułu wbudowanego zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="e6d97-134">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="e6d97-135">Można utworzyć grupy lokalne i dodać lub usunąć członków.</span><span class="sxs-lookup"><span data-stu-id="e6d97-135">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="e6d97-136">Akceptuje zarówno `Credential` właściwość i automatyczne `PsDscRunAsCredential` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e6d97-136">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="e6d97-137">Jednak tylko używa zasobu `Credential` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e6d97-137">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="e6d97-138">Aby uzyskać więcej informacji na temat `PsDscRunAsCredential` właściwości, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="e6d97-138">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="e6d97-139">Przykład: Zasób grupy właściwości Credential</span><span class="sxs-lookup"><span data-stu-id="e6d97-139">Example: The Group resource Credential property</span></span>

<span data-ttu-id="e6d97-140">DSC, o których uruchamiany `Local System`, więc jest już uprawnień do zmiany użytkowników i grup lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e6d97-140">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="e6d97-141">Jeśli dodano element członkowski jest kontem lokalnym, poświadczenie nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="e6d97-141">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="e6d97-142">Jeśli `Group` zasobów doda konto domeny do lokalnej grupy, a następnie poświadczenie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="e6d97-142">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="e6d97-143">Nie są dozwolone anonimowe zapytania do usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e6d97-143">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="e6d97-144">`Credential` Właściwość `Group` zasobów jest kontem domeny, używany do wykonywania zapytań w usłudze Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e6d97-144">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="e6d97-145">W większości przypadków prawdopodobnie ogólne konto użytkownika, domyślnie użytkownicy mogą *odczytu* większości obiektów w usłudze Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e6d97-145">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="e6d97-146">Przykładowa konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e6d97-146">Example Configuration</span></span>

<span data-ttu-id="e6d97-147">Poniższy przykład kodu używa DSC do wypełniania grupy lokalnej o użytkownik domeny:</span><span class="sxs-lookup"><span data-stu-id="e6d97-147">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="e6d97-148">Ten kod generuje błąd i komunikat ostrzegawczy:</span><span class="sxs-lookup"><span data-stu-id="e6d97-148">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="e6d97-149">Ten przykład ma dwa problemy:</span><span class="sxs-lookup"><span data-stu-id="e6d97-149">This example has two issues:</span></span>
1. <span data-ttu-id="e6d97-150">Błąd wyjaśnia, czy hasła w postaci zwykłego tekstu nie są zalecane</span><span class="sxs-lookup"><span data-stu-id="e6d97-150">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="e6d97-151">Ostrzeżenie z informacją o tym względem przy użyciu poświadczeń domeny</span><span class="sxs-lookup"><span data-stu-id="e6d97-151">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="e6d97-152">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="e6d97-152">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="e6d97-153">Pierwszy komunikat o błędzie zawiera adres URL z dokumentacją.</span><span class="sxs-lookup"><span data-stu-id="e6d97-153">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="e6d97-154">Ten link wyjaśnia, jak zaszyfrować hasła, przy użyciu [ConfigurationData](./configData.md) struktury i certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e6d97-154">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="e6d97-155">Aby uzyskać więcej informacji o certyfikatach i DSC [przeczytaj ten wpis](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="e6d97-155">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="e6d97-156">Aby wymusić hasła w postaci zwykłego tekstu, wymaga zasób `PsDscAllowPlainTextPassword` — słowo kluczowe w danych konfiguracji sekcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e6d97-156">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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
> <span data-ttu-id="e6d97-157">`NodeName` nie może być równa gwiazdka obowiązkowa jest tylko nazwa określonego węzła.</span><span class="sxs-lookup"><span data-stu-id="e6d97-157">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="e6d97-158">**Microsoft informacją o tym, aby uniknąć hasła w formacie tekstowym ze względu na istotne zagrożenie bezpieczeństwa.**</span><span class="sxs-lookup"><span data-stu-id="e6d97-158">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="e6d97-159">Poświadczenia domeny</span><span class="sxs-lookup"><span data-stu-id="e6d97-159">Domain Credentials</span></span>

<span data-ttu-id="e6d97-160">Nadal uruchomione ponownie skrypt konfiguracji przykład (z lub bez szyfrowania), generuje ostrzeżenie, niezalecana korzystać z domeny, konto dla poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="e6d97-160">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="e6d97-161">Za pomocą konta lokalnego pozwala wyeliminować ryzyko poświadczeń domeny, które mogłyby zostać użyte na innych serwerach.</span><span class="sxs-lookup"><span data-stu-id="e6d97-161">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="e6d97-162">**Korzystając z poświadczeń przy użyciu zasobów DSC, należy najpierw konta lokalnego za pośrednictwem konta domeny, jeśli jest to możliwe.**</span><span class="sxs-lookup"><span data-stu-id="e6d97-162">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="e6d97-163">W przypadku "\' lub" @ "w `Username` właściwości poświadczeń, a następnie DSC będzie je traktować jako konto domeny.</span><span class="sxs-lookup"><span data-stu-id="e6d97-163">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="e6d97-164">Występuje wyjątek "localhost", "127.0.0.1" i ":: 1" w domenie część nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e6d97-164">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="e6d97-165">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="e6d97-165">PSDscAllowDomainUser</span></span>

<span data-ttu-id="e6d97-166">W DSC `Group` przykładu zasobów powyżej, wykonywanie zapytań do domeny usługi Active Directory *wymaga* konta domeny.</span><span class="sxs-lookup"><span data-stu-id="e6d97-166">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="e6d97-167">W takim przypadku Dodaj `PSDscAllowDomainUser` właściwość `ConfigurationData` blokowania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e6d97-167">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="e6d97-168">Teraz skryptu konfiguracji spowoduje wygenerowanie pliku MOF bez błędów i ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="e6d97-168">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
