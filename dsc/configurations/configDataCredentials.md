---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Opcje poświadczeń w danych konfiguracji
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "55686376"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="21ad5-103">Opcje poświadczeń w danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="21ad5-103">Credentials Options in Configuration Data</span></span>

><span data-ttu-id="21ad5-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="21ad5-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="21ad5-105">Haseł w postaci zwykłego tekstu, a użytkownicy domeny</span><span class="sxs-lookup"><span data-stu-id="21ad5-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="21ad5-106">Konfiguracji DSC zawierający poświadczenia bez szyfrowania wygeneruje komunikat o błędzie dotyczący haseł w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="21ad5-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="21ad5-107">Ponadto DSC wygeneruje ostrzeżenie, gdy przy użyciu poświadczeń domeny.</span><span class="sxs-lookup"><span data-stu-id="21ad5-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="21ad5-108">Aby pominąć tych błędów i ostrzeżeń, użyj słowa kluczowe dane konfiguracji DSC:</span><span class="sxs-lookup"><span data-stu-id="21ad5-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="21ad5-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="21ad5-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="21ad5-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="21ad5-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="21ad5-111">Przechowywanie/przesyła niezaszyfrowane hasła w postaci zwykłego tekstu zwykle nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="21ad5-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="21ad5-112">Zaleca się zabezpieczenie poświadczeń przy użyciu techniki omówione w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="21ad5-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="21ad5-113">Usługi Konfiguracja DSC automatyzacji Azure umożliwia centralne zarządzanie poświadczenia, aby być skompilowany w konfiguracji i bezpiecznie przechowywane.</span><span class="sxs-lookup"><span data-stu-id="21ad5-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="21ad5-114">Aby uzyskać informacje Zobacz: [Kompilowanie konfiguracji DSC / poświadczeń zasoby](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="21ad5-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="21ad5-115">Obsługa poświadczeń w konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="21ad5-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="21ad5-116">Zasoby konfiguracji DSC Uruchom jako `Local System` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="21ad5-116">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="21ad5-117">Jednak niektóre zasoby potrzebne poświadczenia, na przykład gdy `Package` zasobów, należy zainstalować oprogramowanie w ramach określonego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="21ad5-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="21ad5-118">Używane wcześniej zasoby ustalony `Credential` nazwę właściwości, aby rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="21ad5-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="21ad5-119">Automatyczne dodany WMF 5.0 `PsDscRunAsCredential` właściwości dla wszystkich zasobów.</span><span class="sxs-lookup"><span data-stu-id="21ad5-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="21ad5-120">Aby uzyskać informacje o korzystaniu z `PsDscRunAsCredential`, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="21ad5-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="21ad5-121">Nowsze zasobów i zasobów niestandardowych można użyć tej właściwości automatyczne zamiast tworzenia własnych właściwości dla poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="21ad5-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="21ad5-122">Projekt niektórych zasobów są używają wielu poświadczeń z określonego powodu i mają one właściwości własne poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="21ad5-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="21ad5-123">Aby odnaleźć dostępne poświadczeń właściwości w zasobie użyj jednej `Get-DscResource -Name ResourceName -Syntax` i technologii Intellisense w ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="21ad5-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="21ad5-124">W tym przykładzie użyto [grupy](../resources/resources.md) zasób z `PSDesiredStateConfiguration` wbudowany moduł zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="21ad5-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="21ad5-125">Możesz tworzyć grupy lokalne i dodać lub usunąć członków.</span><span class="sxs-lookup"><span data-stu-id="21ad5-125">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="21ad5-126">Akceptuje zarówno `Credential` właściwości i automatyczne `PsDscRunAsCredential` właściwości.</span><span class="sxs-lookup"><span data-stu-id="21ad5-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="21ad5-127">Jednak używa tylko zasób `Credential` właściwości.</span><span class="sxs-lookup"><span data-stu-id="21ad5-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="21ad5-128">Aby uzyskać więcej informacji na temat `PsDscRunAsCredential` właściwości, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="21ad5-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="21ad5-129">Przykład: Zasób grupy właściwości poświadczeń</span><span class="sxs-lookup"><span data-stu-id="21ad5-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="21ad5-130">DSC jest uruchamiana `Local System`, więc jest już uprawnień do zmiany użytkowników i grup lokalnych.</span><span class="sxs-lookup"><span data-stu-id="21ad5-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="21ad5-131">Jeśli dodano element członkowski jest kontem lokalnym, niezbędne jest nie ma poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="21ad5-131">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="21ad5-132">Jeśli `Group` zasobów dodaje konto domeny do lokalnej grupy, a następnie konieczne jest podanie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="21ad5-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="21ad5-133">Nie są dozwolone anonimowe zapytania do usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="21ad5-133">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="21ad5-134">`Credential` Właściwość `Group` zasób jest konto domeny używane do zapytania usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="21ad5-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="21ad5-135">W większości przypadków może to być konto użytkownika ogólnego, ponieważ domyślnie użytkownicy mogą *odczytu* większość obiektów w usłudze Active Directory.</span><span class="sxs-lookup"><span data-stu-id="21ad5-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="21ad5-136">Przykładowa konfiguracja</span><span class="sxs-lookup"><span data-stu-id="21ad5-136">Example Configuration</span></span>

<span data-ttu-id="21ad5-137">Poniższy przykład kodu wykorzystuje DSC do wypełniania grupy lokalnej z użytkownikiem domeny:</span><span class="sxs-lookup"><span data-stu-id="21ad5-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="21ad5-138">Ten kod generuje zarówno błędu i ostrzeżenia:</span><span class="sxs-lookup"><span data-stu-id="21ad5-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="21ad5-139">W tym przykładzie występują dwa problemy:</span><span class="sxs-lookup"><span data-stu-id="21ad5-139">This example has two issues:</span></span>

1. <span data-ttu-id="21ad5-140">Wystąpił błąd wyjaśniono, że haseł w postaci zwykłego tekstu nie są zalecane</span><span class="sxs-lookup"><span data-stu-id="21ad5-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="21ad5-141">Ostrzeżenia z informacją o tym przed przy użyciu poświadczeń domeny</span><span class="sxs-lookup"><span data-stu-id="21ad5-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="21ad5-142">Flagi **PSDSCAllowPlainTextPassword** i **PSDSCAllowDomainUser** pomija błąd i ostrzeżenie informujące użytkownika zagrożenia.</span><span class="sxs-lookup"><span data-stu-id="21ad5-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="21ad5-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="21ad5-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="21ad5-144">Pierwszy komunikat o błędzie zawiera adres URL z dokumentacją.</span><span class="sxs-lookup"><span data-stu-id="21ad5-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="21ad5-145">To łącze wyjaśniono, jak do szyfrowania haseł przy użyciu [ConfigurationData](./configData.md) struktury i certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="21ad5-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="21ad5-146">Aby uzyskać więcej informacji o certyfikatach i DSC [odczytać ten wpis](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="21ad5-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="21ad5-147">Aby wymusić hasła w postaci zwykłego tekstu, wymaga zasób `PsDscAllowPlainTextPassword` — słowo kluczowe w danych konfiguracji sekcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="21ad5-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="21ad5-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="21ad5-148">localhost.mof</span></span>

<span data-ttu-id="21ad5-149">**PSDSCAllowPlainTextPassword** Flaga wymaga, aby użytkownik potwierdzić ryzyka przechowywania haseł w postaci zwykłego tekstu w pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="21ad5-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="21ad5-150">W wygenerowanym pliku MOF nawet jeśli **PSCredential** obiekt zawierający **SecureString** użyto hasła nadal wyświetlane jako zwykły tekst.</span><span class="sxs-lookup"><span data-stu-id="21ad5-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="21ad5-151">Jest to czas tylko poświadczenia są widoczne.</span><span class="sxs-lookup"><span data-stu-id="21ad5-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="21ad5-152">Aby uzyskać dostęp do tego zapewnia pliku MOF każdy dostęp do konta administratora.</span><span class="sxs-lookup"><span data-stu-id="21ad5-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="21ad5-153">Poświadczenia przesyłanych i przechowywanych</span><span class="sxs-lookup"><span data-stu-id="21ad5-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="21ad5-154">**PSDscAllowPlainTextPassword** Flaga umożliwia kompilacji pliki MOF zawierające hasła w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="21ad5-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span>
  <span data-ttu-id="21ad5-155">Doszło przechowywanie plików MOF zawierający haseł w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="21ad5-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="21ad5-156">Dostarczenia pliku MOF do węzła w **Push** trybie WinRM szyfruje komunikacji chronić hasła zwykłego tekstu, chyba że zastąpić domyślną z **AllowUnencrypted** parametru.</span><span class="sxs-lookup"><span data-stu-id="21ad5-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="21ad5-157">MOF przy użyciu certyfikatu szyfrowania chroni plik MOF magazynowane przed zastosowano do węzła.</span><span class="sxs-lookup"><span data-stu-id="21ad5-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="21ad5-158">W **ściągania** tryb, można skonfigurować systemu Windows server ściągnięcia do używania protokołu HTTPS do szyfrowania ruchu przy użyciu protokołu określonego w polu serwera Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="21ad5-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="21ad5-159">Aby uzyskać więcej informacji, zobacz artykuły [konfigurowania klienta ściągania usługi Konfiguracja DSC](../pull-server/pullclient.md) i [pliki MOF zabezpieczanie z certyfikatami](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="21ad5-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="21ad5-160">W [konfiguracji stanu usługi Automatyzacja Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) usługi ściągania ruchu są zawsze szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="21ad5-160">In the [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="21ad5-161">W węźle pliki MOF są szyfrowane, gdy w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="21ad5-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="21ad5-162">W programie PowerShell MOF 4.0 pliki są magazynowane niezaszyfrowane, chyba że są szyfrowane przy użyciu certyfikatu podczas naciśnięty, czy pobierane do węzła.</span><span class="sxs-lookup"><span data-stu-id="21ad5-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="21ad5-163">**Microsoft informacją o tym, aby uniknąć hasła w formacie tekstowym z powodu znaczące zagrożenie bezpieczeństwa.**</span><span class="sxs-lookup"><span data-stu-id="21ad5-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="21ad5-164">Poświadczenia domeny</span><span class="sxs-lookup"><span data-stu-id="21ad5-164">Domain Credentials</span></span>

<span data-ttu-id="21ad5-165">Nadal uruchomiona ponownie skryptu konfiguracji przykład (z lub bez szyfrowania), generuje ostrzeżenie, że, przy użyciu domeny konto dla poświadczeń nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="21ad5-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="21ad5-166">Za pomocą konta lokalnego eliminuje ryzyko poświadczeń domeny, które mogłyby zostać użyte na innych serwerach.</span><span class="sxs-lookup"><span data-stu-id="21ad5-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="21ad5-167">**Korzystając z poświadczeń z usługi Konfiguracja DSC zasobów, preferowane jest kontem lokalnym za pośrednictwem konta domeny, jeśli to możliwe.**</span><span class="sxs-lookup"><span data-stu-id="21ad5-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="21ad5-168">W przypadku "\\"lub"\@" w `Username` właściwość credential, a następnie DSC będzie je traktować jako konto domeny.</span><span class="sxs-lookup"><span data-stu-id="21ad5-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="21ad5-169">Brak wyjątek dla "localhost", "127.0.0.1" i ":: 1" w domenie część nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="21ad5-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="21ad5-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="21ad5-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="21ad5-171">W konfiguracji DSC `Group` zasobów przykładzie przedstawionym powyżej zapytań domeny usługi Active Directory *wymaga* konta domeny.</span><span class="sxs-lookup"><span data-stu-id="21ad5-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="21ad5-172">W takim przypadku Dodaj `PSDscAllowDomainUser` właściwości `ConfigurationData` zablokować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="21ad5-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="21ad5-173">Teraz skryptu konfiguracji spowoduje wygenerowanie pliku MOF bez błędów lub ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="21ad5-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
