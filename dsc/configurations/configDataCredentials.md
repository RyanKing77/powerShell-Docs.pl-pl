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
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="69039-103">Opcje poświadczeń w danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="69039-103">Credentials Options in Configuration Data</span></span>

><span data-ttu-id="69039-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="69039-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="69039-105">Hasła w postaci zwykłego tekstu, a użytkownicy domeny</span><span class="sxs-lookup"><span data-stu-id="69039-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="69039-106">Konfiguracje DSC zawierający poświadczenia bez szyfrowania wygeneruje komunikat o błędzie dotyczących haseł w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="69039-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="69039-107">Ponadto DSC wygeneruje ostrzeżenie, gdy przy użyciu poświadczeń domeny.</span><span class="sxs-lookup"><span data-stu-id="69039-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="69039-108">Aby pominąć tych błędów i komunikaty ostrzegawcze, użyj słowa kluczowe dane konfiguracji DSC:</span><span class="sxs-lookup"><span data-stu-id="69039-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="69039-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="69039-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="69039-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="69039-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="69039-111">Przechowywanie/przekazywania niezaszyfrowane hasła w postaci jawnej ogólnie nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="69039-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="69039-112">Zalecane jest zabezpieczanie poświadczenia za pomocą techniki omówione w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="69039-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="69039-113">Usługa Azure Automation DSC umożliwia centralne zarządzanie poświadczenia, aby być skompilowany w konfiguracji i bezpiecznie przechowywane.</span><span class="sxs-lookup"><span data-stu-id="69039-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="69039-114">Aby uzyskać informacje Zobacz: [Kompilowanie konfiguracji DSC / poświadczeń trwałych](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="69039-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="69039-115">Obsługa poświadczeń w DSC</span><span class="sxs-lookup"><span data-stu-id="69039-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="69039-116">Zasoby konfiguracji DSC Uruchom jako `Local System` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="69039-116">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="69039-117">Niektóre zasoby muszą mieć jednak poświadczenia, na przykład gdy `Package` zasobu należy zainstalować oprogramowanie w ramach określonego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="69039-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="69039-118">Wcześniejsze zasoby użyte, ustalone `Credential` nazwę właściwości, aby to obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="69039-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="69039-119">Program WMF 5.0 dodaje automatyczne `PsDscRunAsCredential` właściwości dla wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="69039-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="69039-120">Aby uzyskać informacje o używaniu `PsDscRunAsCredential`, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="69039-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="69039-121">Nowsze zasobów i zasobów niestandardowych można użyć tej właściwości automatyczne zamiast tworzyć własne właściwości dla poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="69039-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="69039-122">Projekt niektóre zasoby są używają wielu poświadczeń z określonego powodu i będą mieć własne właściwości poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="69039-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="69039-123">Aby znaleźć dostępne poświadczeń we właściwościach zasobu należy użyć `Get-DscResource -Name ResourceName -Syntax` i technologii Intellisense w środowisku ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="69039-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="69039-124">W tym przykładzie użyto [grupy](../resources/resources.md) zasób z `PSDesiredStateConfiguration` modułu wbudowanego zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="69039-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="69039-125">Można utworzyć grupy lokalne i dodać lub usunąć członków.</span><span class="sxs-lookup"><span data-stu-id="69039-125">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="69039-126">Akceptuje zarówno `Credential` właściwość i automatyczne `PsDscRunAsCredential` właściwości.</span><span class="sxs-lookup"><span data-stu-id="69039-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="69039-127">Jednak tylko używa zasobu `Credential` właściwości.</span><span class="sxs-lookup"><span data-stu-id="69039-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="69039-128">Aby uzyskać więcej informacji na temat `PsDscRunAsCredential` właściwości, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="69039-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="69039-129">Przykład: Zasób grupy właściwości Credential</span><span class="sxs-lookup"><span data-stu-id="69039-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="69039-130">DSC, o których uruchamiany `Local System`, więc jest już uprawnień do zmiany użytkowników i grup lokalnych.</span><span class="sxs-lookup"><span data-stu-id="69039-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="69039-131">Jeśli dodano element członkowski jest kontem lokalnym, poświadczenie nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="69039-131">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="69039-132">Jeśli `Group` zasobów doda konto domeny do lokalnej grupy, a następnie poświadczenie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="69039-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="69039-133">Nie są dozwolone anonimowe zapytania do usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="69039-133">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="69039-134">`Credential` Właściwość `Group` zasobów jest kontem domeny, używany do wykonywania zapytań w usłudze Active Directory.</span><span class="sxs-lookup"><span data-stu-id="69039-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="69039-135">W większości przypadków prawdopodobnie ogólne konto użytkownika, domyślnie użytkownicy mogą *odczytu* większości obiektów w usłudze Active Directory.</span><span class="sxs-lookup"><span data-stu-id="69039-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="69039-136">Przykładowa konfiguracja</span><span class="sxs-lookup"><span data-stu-id="69039-136">Example Configuration</span></span>

<span data-ttu-id="69039-137">Poniższy przykład kodu używa DSC do wypełniania grupy lokalnej o użytkownik domeny:</span><span class="sxs-lookup"><span data-stu-id="69039-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="69039-138">Ten kod generuje błąd i komunikat ostrzegawczy:</span><span class="sxs-lookup"><span data-stu-id="69039-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="69039-139">Ten przykład ma dwa problemy:</span><span class="sxs-lookup"><span data-stu-id="69039-139">This example has two issues:</span></span>

1. <span data-ttu-id="69039-140">Błąd wyjaśnia, czy hasła w postaci zwykłego tekstu nie są zalecane</span><span class="sxs-lookup"><span data-stu-id="69039-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="69039-141">Ostrzeżenie z informacją o tym względem przy użyciu poświadczeń domeny</span><span class="sxs-lookup"><span data-stu-id="69039-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="69039-142">Flagi **PSDSCAllowPlainTextPassword** i **PSDSCAllowDomainUser** pomija błąd i ostrzeżenie informujące użytkownika zagrożenia.</span><span class="sxs-lookup"><span data-stu-id="69039-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="69039-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="69039-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="69039-144">Pierwszy komunikat o błędzie zawiera adres URL z dokumentacją.</span><span class="sxs-lookup"><span data-stu-id="69039-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="69039-145">Ten link wyjaśnia, jak zaszyfrować hasła, przy użyciu [ConfigurationData](./configData.md) struktury i certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="69039-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="69039-146">Aby uzyskać więcej informacji o certyfikatach i DSC [przeczytaj ten wpis](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="69039-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="69039-147">Aby wymusić hasła w postaci zwykłego tekstu, wymaga zasób `PsDscAllowPlainTextPassword` — słowo kluczowe w danych konfiguracji sekcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="69039-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="69039-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="69039-148">localhost.mof</span></span>

<span data-ttu-id="69039-149">**PSDSCAllowPlainTextPassword** Flaga wymaga, że użytkownik potwierdza ryzyko przechowywanie haseł w postaci zwykłego tekstu w pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="69039-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="69039-150">W wygenerowanym pliku MOF mimo że **PSCredential** obiekt zawierający **SecureString** użyto hasła wciąż będą wyświetlane jako zwykły tekst.</span><span class="sxs-lookup"><span data-stu-id="69039-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="69039-151">Jest to jedyny raz, którego poświadczenia są widoczne.</span><span class="sxs-lookup"><span data-stu-id="69039-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="69039-152">Uzyskiwanie dostępu do tego pliku MOF, daje każdy dostęp do konta administratora.</span><span class="sxs-lookup"><span data-stu-id="69039-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="69039-153">Poświadczenia przesyłanych i magazynowanych</span><span class="sxs-lookup"><span data-stu-id="69039-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="69039-154">**PSDscAllowPlainTextPassword** Flaga umożliwia kompilacji pliki MOF zawierające hasła w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="69039-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span>
  <span data-ttu-id="69039-155">Należy zachować środki ostrożności podczas zapisywania pliki MOF zawierające hasła w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="69039-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="69039-156">Dostarczenia pliku MOF do węzła w **wypychania** trybie WinRM szyfruje komunikację z usługą ochrony zwykłego tekstu, jeśli nie możesz zastąpić to ustawienie domyślne z **AllowUnencrypted** parametru.</span><span class="sxs-lookup"><span data-stu-id="69039-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="69039-157">Zaszyfrowanie pliku MOF przy użyciu certyfikatu chroni plik MOF w spoczynku, zanim zostały doliczone do węzła.</span><span class="sxs-lookup"><span data-stu-id="69039-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="69039-158">W **ściągnięcia** trybu, można skonfigurować serwera ściągania Windows do używania protokołu HTTPS do szyfrowania ruchu przy użyciu protokołu określonego w Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="69039-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="69039-159">Aby uzyskać więcej informacji, zobacz artykuły [Konfigurowanie klienta ściągania DSC](../pull-server/pullclient.md) i [MOF Zabezpieczanie plików przy użyciu certyfikatów](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="69039-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="69039-160">W [konfiguracji stanu automatyzacji Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) usługi ściągania ruchu są zawsze szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="69039-160">In the [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="69039-161">W węźle pliki MOF są szyfrowane, gdy w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="69039-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="69039-162">W programie PowerShell 4.0 w pliku MOF pliki są niezaszyfrowane w spoczynku, chyba że są szyfrowane przy użyciu certyfikatu podczas wypychania lub pobierane do węzła.</span><span class="sxs-lookup"><span data-stu-id="69039-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="69039-163">**Microsoft informacją o tym, aby uniknąć hasła w formacie tekstowym ze względu na istotne zagrożenie bezpieczeństwa.**</span><span class="sxs-lookup"><span data-stu-id="69039-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="69039-164">Poświadczenia domeny</span><span class="sxs-lookup"><span data-stu-id="69039-164">Domain Credentials</span></span>

<span data-ttu-id="69039-165">Nadal uruchomione ponownie skrypt konfiguracji przykład (z lub bez szyfrowania), generuje ostrzeżenie, niezalecana korzystać z domeny, konto dla poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="69039-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="69039-166">Za pomocą konta lokalnego pozwala wyeliminować ryzyko poświadczeń domeny, które mogłyby zostać użyte na innych serwerach.</span><span class="sxs-lookup"><span data-stu-id="69039-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="69039-167">**Korzystając z poświadczeń przy użyciu zasobów DSC, należy najpierw konta lokalnego za pośrednictwem konta domeny, jeśli jest to możliwe.**</span><span class="sxs-lookup"><span data-stu-id="69039-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="69039-168">W przypadku "\\"lub"\@" w `Username` właściwości poświadczeń, a następnie DSC będzie je traktować jako konto domeny.</span><span class="sxs-lookup"><span data-stu-id="69039-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="69039-169">Występuje wyjątek "localhost", "127.0.0.1" i ":: 1" w domenie część nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="69039-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="69039-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="69039-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="69039-171">W DSC `Group` przykładu zasobów powyżej, wykonywanie zapytań do domeny usługi Active Directory *wymaga* konta domeny.</span><span class="sxs-lookup"><span data-stu-id="69039-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="69039-172">W takim przypadku Dodaj `PSDscAllowDomainUser` właściwość `ConfigurationData` blokowania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="69039-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="69039-173">Teraz skryptu konfiguracji spowoduje wygenerowanie pliku MOF bez błędów i ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="69039-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
