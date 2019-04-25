---
ms.date: 10/31/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zabezpieczanie pliku MOF
ms.openlocfilehash: 6c2aadb75ac617d9b845ef387f292b8156bb8889
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079337"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="80309-103">Zabezpieczanie pliku MOF</span><span class="sxs-lookup"><span data-stu-id="80309-103">Securing the MOF File</span></span>

> <span data-ttu-id="80309-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="80309-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="80309-105">DSC zarządza konfiguracją węzły serwera, stosując informacje przechowywane w pliku MOF, w przypadku, gdy lokalne Configuration Manager (LCM) wykonuje stanu końcowego żądaną.</span><span class="sxs-lookup"><span data-stu-id="80309-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="80309-106">Ponieważ ten plik zawiera szczegółowe informacje o konfiguracji, należy Przechowuj w bezpiecznym miejscu.</span><span class="sxs-lookup"><span data-stu-id="80309-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="80309-107">W tym temacie opisano sposób zapewnienia węzeł docelowy jest zaszyfrowany plik.</span><span class="sxs-lookup"><span data-stu-id="80309-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="80309-108">Począwszy od programu PowerShell w wersji 5.0, cały plik MOF jest domyślnie szyfrowane po zastosowaniu do węzła przy użyciu `Start-DSCConfiguration` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80309-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span>
<span data-ttu-id="80309-109">Proces opisany w tym artykule jest wymagany tylko wtedy, gdy wdrażanie rozwiązania przy użyciu protokołu usługi ściągania, jeśli certyfikaty nie są zarządzane, aby upewnić się, konfiguracje pobrane przez węzeł docelowy może być odszyfrowane i odczytywane przez system, przed ich zastosowaniem (na przykład usługi ściągania dostępne w systemie Windows Server).</span><span class="sxs-lookup"><span data-stu-id="80309-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="80309-110">Węzły zarejestrowane do [usługi Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) automatycznie mają certyfikaty zainstalowane i zarządzane przez usługę z nie czynności administracyjnych wymagane.</span><span class="sxs-lookup"><span data-stu-id="80309-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="80309-111">W tym temacie omówiono certyfikaty używane do szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="80309-111">This topic discusses certificates used for encryption.</span></span>
> <span data-ttu-id="80309-112">Dla celów szyfrowania certyfikat z podpisem własnym jest wystarczający, ponieważ klucz prywatny jest przechowywany zawsze, hasło i szyfrowanie nie oznacza zaufania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="80309-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
> <span data-ttu-id="80309-113">Certyfikaty z podpisem własnym należy *nie* można używać na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="80309-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
> <span data-ttu-id="80309-114">W żadnych celach uwierzytelniania należy używać certyfikatu z zaufanego urzędu certyfikacji (CA).</span><span class="sxs-lookup"><span data-stu-id="80309-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="80309-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="80309-115">Prerequisites</span></span>

<span data-ttu-id="80309-116">Aby pomyślnie zaszyfrować poświadczenia używane do zabezpieczania konfiguracji DSC, upewnij się, że dysponujesz następującymi elementami:</span><span class="sxs-lookup"><span data-stu-id="80309-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="80309-117">**Niektóre środki wystawiania i rozpowszechniania certyfikatów**.</span><span class="sxs-lookup"><span data-stu-id="80309-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="80309-118">Ten temat i jego przykładów przyjęto założenie, że w przypadku korzystania z urzędu certyfikacji w usłudze Active Directory.</span><span class="sxs-lookup"><span data-stu-id="80309-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="80309-119">Aby uzyskać więcej informacji o tła w usługach certyfikatów Active Directory, zobacz [Omówienie usług certyfikatów w usłudze Active Directory](https://technet.microsoft.com/library/hh831740.aspx) i [usług certyfikatów Active Directory w systemie Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="80309-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="80309-120">**Dostęp administracyjny do węzła docelowego lub węzły**.</span><span class="sxs-lookup"><span data-stu-id="80309-120">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="80309-121">**Każdy węzeł docelowy ma certyfikat szyfrowania zapisane jego Store osobiste**.</span><span class="sxs-lookup"><span data-stu-id="80309-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="80309-122">W programie Windows PowerShell ścieżkę do magazynu jest Cert: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="80309-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="80309-123">Przykłady w tym temacie używania szablonu "Uwierzytelnianie stacji roboczej", który można znaleźć (wraz z innych szablonów certyfikatów) w [domyślne szablony certyfikatów](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="80309-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="80309-124">Jeśli będzie działać tej konfiguracji na komputerze innym niż węzeł docelowy **wyeksportować klucz publiczny certyfikatu**, a następnie zaimportuj go do komputera, Uruchom konfigurację przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="80309-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="80309-125">Upewnij się, który chcesz eksportować tylko **publicznych** klucza; bezpieczeństwo klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="80309-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="80309-126">Ogólny proces</span><span class="sxs-lookup"><span data-stu-id="80309-126">Overall process</span></span>

 1. <span data-ttu-id="80309-127">Konfigurowanie certyfikatów, kluczy i odciski palców, upewniając się, że każdy węzeł docelowy ma kopii certyfikatu, a konfiguracja komputer ma klucza publicznego i odcisk palca.</span><span class="sxs-lookup"><span data-stu-id="80309-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="80309-128">Tworzenie bloku danych konfiguracji, który zawiera ścieżkę i odcisk palca klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="80309-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="80309-129">Utwórz skrypt konfiguracyjny, który definiuje żądaną konfigurację dla węzła docelowego i konfiguruje odszyfrowywania na węzłach docelowych przez polecenia lokalnego konfiguracji menedżera do odszyfrowania danych konfiguracji, za pomocą certyfikatu i jego odcisk palca.</span><span class="sxs-lookup"><span data-stu-id="80309-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="80309-130">Uruchom konfigurację, co spowoduje ustawienie Local Configuration Manager i konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="80309-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](../images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="80309-132">Wymagania dotyczące certyfikatów</span><span class="sxs-lookup"><span data-stu-id="80309-132">Certificate Requirements</span></span>

<span data-ttu-id="80309-133">Wprowadzenie szyfrowania poświadczeń, certyfikat klucza publicznego musi być dostępny na _węzeł docelowy_ czyli **zaufanych** przez komputer używany do tworzenia konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="80309-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="80309-134">Ten certyfikat klucza publicznego ma określonych wymagań dotyczących może być ona używana do szyfrowania poświadczeń DSC:</span><span class="sxs-lookup"><span data-stu-id="80309-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="80309-135">**Użycie klucza**:</span><span class="sxs-lookup"><span data-stu-id="80309-135">**Key Usage**:</span></span>
   - <span data-ttu-id="80309-136">Musi zawierać: "KeyEncipherment" i "DataEncipherment".</span><span class="sxs-lookup"><span data-stu-id="80309-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="80309-137">Należy _nie_ zawierają: "Podpis cyfrowy".</span><span class="sxs-lookup"><span data-stu-id="80309-137">Should _not_ contain: 'Digital Signature'.</span></span>
2. <span data-ttu-id="80309-138">**Ulepszone użycie klucza**:</span><span class="sxs-lookup"><span data-stu-id="80309-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="80309-139">Musi zawierać: Szyfrowanie dokumentów (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="80309-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="80309-140">Należy _nie_ zawierają: Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2) i uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="80309-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
3. <span data-ttu-id="80309-141">Klucz prywatny certyfikatu jest dostępna na \* Node_ docelowej.</span><span class="sxs-lookup"><span data-stu-id="80309-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
4. <span data-ttu-id="80309-142">**Dostawcy** dla certyfikatu musi być "Microsoft RSA SChannel Cryptographic Provider".</span><span class="sxs-lookup"><span data-stu-id="80309-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80309-143">Mimo że można użyć certyfikatu z zawierających użycie klucza, 'Podpis cyfrowy' lub jedną wartość EKU uwierzytelniania, umożliwi to klucz szyfrowania, można łatwiej użyte i podatne na atak.</span><span class="sxs-lookup"><span data-stu-id="80309-143">Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="80309-144">Dlatego jest najlepszym rozwiązaniem jest użycie certyfikatów utworzonych specjalnie na potrzeby zabezpieczania poświadczenia DSC pomija te użycie klucza i wartości EKU.</span><span class="sxs-lookup"><span data-stu-id="80309-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="80309-145">Dowolnego istniejącego certyfikatu na _węzeł docelowy_ czy spełnia te kryteria może służyć do bezpiecznych poświadczeń DSC.</span><span class="sxs-lookup"><span data-stu-id="80309-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="80309-146">Tworzenie certyfikatu</span><span class="sxs-lookup"><span data-stu-id="80309-146">Certificate creation</span></span>

<span data-ttu-id="80309-147">Istnieją dwie metody, które można wykonać w celu tworzenia i używania wymaganego certyfikatu szyfrowania (pary kluczy publiczny prywatny).</span><span class="sxs-lookup"><span data-stu-id="80309-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="80309-148">Utwórz je na **węzeł docelowy** i wyeksportować tylko klucz publiczny, który **tworzenia węzła**</span><span class="sxs-lookup"><span data-stu-id="80309-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="80309-149">Utwórz je na **tworzenia węzła** i eksportować całą pary kluczy do **węzeł docelowy**</span><span class="sxs-lookup"><span data-stu-id="80309-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="80309-150">Metoda 1 jest zalecane, ponieważ klucz prywatny używany do odszyfrowywania poświadczeń w pliku MOF pozostaje w docelowym węźle przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="80309-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="80309-151">Tworzenie certyfikatu na węzeł docelowy</span><span class="sxs-lookup"><span data-stu-id="80309-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="80309-152">Klucz prywatny musi znajdować się wpisu tajnego, ponieważ jest używany do odszyfrowywania pliku MOF w **węzeł docelowy** Najprostszym sposobem wykonania tego zadania jest utworzenie certyfikatu klucza prywatnego na **węzeł docelowy**, a następnie skopiuj  **Certyfikat klucza publicznego** komputer używany do tworzenia konfiguracji DSC w pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="80309-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="80309-153">Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="80309-153">The following example:</span></span>

1. <span data-ttu-id="80309-154">tworzy certyfikat na **węzeł docelowy**</span><span class="sxs-lookup"><span data-stu-id="80309-154">creates a certificate on the **Target node**</span></span>
2. <span data-ttu-id="80309-155">Eksportuje certyfikat klucza publicznego na **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="80309-155">exports the public key certificate on the **Target node**.</span></span>
3. <span data-ttu-id="80309-156">importuje certyfikat klucza publicznego do **Moje** magazynu certyfikatów na **węzeł tworzenie**.</span><span class="sxs-lookup"><span data-stu-id="80309-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="80309-157">W węźle docelowym: tworzenie i eksportowanie certyfikatu</span><span class="sxs-lookup"><span data-stu-id="80309-157">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="80309-158">Węzeł docelowy: Windows Server 2016 i Windows 10</span><span class="sxs-lookup"><span data-stu-id="80309-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="80309-159">Po wyeksportowaniu `DscPublicKey.cer` musi być skopiowane do **tworzenia węzła**.</span><span class="sxs-lookup"><span data-stu-id="80309-159">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="80309-160">Węzeł docelowy: Windows Server 2012 R2/Windows 8.1 i starszych wersji</span><span class="sxs-lookup"><span data-stu-id="80309-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="80309-161">Ponieważ `New-SelfSignedCertificate` nie obsługują polecenia cmdlet w systemie operacyjnym Windows przed systemem Windows 10 i Windows Server 2016 **typu** parametr, alternatywną metodę tworzenia ten certyfikat jest wymagany w tych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="80309-161">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="80309-162">W takim przypadku można użyć `makecert.exe` lub `certutil.exe` do utworzenia certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="80309-162">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
><span data-ttu-id="80309-163">Alternatywna metoda jest [Pobierz skrypt New SelfSignedCertificateEx.ps1 z Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) i użyć go do utworzenia certyfikatu zamiast tego:</span><span class="sxs-lookup"><span data-stu-id="80309-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="80309-164">Po wyeksportowaniu ```DscPublicKey.cer``` musi być skopiowane do **tworzenia węzła**.</span><span class="sxs-lookup"><span data-stu-id="80309-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="80309-165">W węźle Autorstwo: importowanie certyfikatu klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="80309-165">On the Authoring Node: import the cert’s public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="80309-166">Tworzenie certyfikatu w węźle tworzenia pakietów administracyjnych</span><span class="sxs-lookup"><span data-stu-id="80309-166">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="80309-167">Alternatywnie można utworzyć certyfikatu szyfrowania na **tworzenia węzła**, wyeksportowane z **klucza prywatnego** jako plik PFX pliku, a następnie zaimportowane na **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="80309-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="80309-168">Jest to bieżąca metoda implementowania szyfrowania poświadczeń DSC na _serwera Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="80309-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="80309-169">Mimo, że plik PFX jest zabezpieczony za pomocą hasła powinna być przechowywana bezpieczne podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="80309-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="80309-170">Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="80309-170">The following example:</span></span>

1. <span data-ttu-id="80309-171">tworzy certyfikat na **węzeł tworzenie**.</span><span class="sxs-lookup"><span data-stu-id="80309-171">creates a certificate on the **Authoring node**.</span></span>
2. <span data-ttu-id="80309-172">Umożliwia wyeksportowanie certyfikatu w tym klucza prywatnego na **węzeł tworzenie**.</span><span class="sxs-lookup"><span data-stu-id="80309-172">exports the certificate including the private key on the **Authoring node**.</span></span>
3. <span data-ttu-id="80309-173">Usuwa klucz prywatny z **węzeł tworzenie**, ale zachowuje certyfikatu klucza publicznego **Moje** przechowywania.</span><span class="sxs-lookup"><span data-stu-id="80309-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
4. <span data-ttu-id="80309-174">importuje certyfikat klucza prywatnego do magazynu certyfikatów My(Personal) na **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="80309-174">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="80309-175">należy dodać do magazynu certyfikatów głównych, dzięki czemu będą zaufane przez **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="80309-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="80309-176">W węźle tworzenie: tworzenie i eksportowanie certyfikatu</span><span class="sxs-lookup"><span data-stu-id="80309-176">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="80309-177">Węzeł docelowy: Windows Server 2016 i Windows 10</span><span class="sxs-lookup"><span data-stu-id="80309-177">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

<span data-ttu-id="80309-178">Po wyeksportowaniu `DscPrivateKey.pfx` musi być skopiowane do **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="80309-178">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="80309-179">Węzeł docelowy: Windows Server 2012 R2/Windows 8.1 i starszych wersji</span><span class="sxs-lookup"><span data-stu-id="80309-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="80309-180">Ponieważ `New-SelfSignedCertificate` nie obsługują polecenia cmdlet w systemie operacyjnym Windows przed systemem Windows 10 i Windows Server 2016 **typu** parametr, alternatywną metodę tworzenia ten certyfikat jest wymagany w tych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="80309-180">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="80309-181">W takim przypadku można użyć `makecert.exe` lub `certutil.exe` do utworzenia certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="80309-181">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
> <span data-ttu-id="80309-182">Alternatywna metoda jest [Pobierz skrypt New SelfSignedCertificateEx.ps1 z Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) i użyć go do utworzenia certyfikatu zamiast tego:</span><span class="sxs-lookup"><span data-stu-id="80309-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="80309-183">W węźle docelowym: Importowanie klucza prywatnego certyfikatu jako zaufany główny urząd certyfikacji</span><span class="sxs-lookup"><span data-stu-id="80309-183">On the Target Node: import the cert’s private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="80309-184">Dane konfiguracji</span><span class="sxs-lookup"><span data-stu-id="80309-184">Configuration data</span></span>

<span data-ttu-id="80309-185">Blok danych konfiguracyjnych definiuje węzły docelowe, których działanie od tego, czy lub nie, aby zaszyfrować poświadczenia, oznacza, że szyfrowania i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="80309-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="80309-186">Aby uzyskać więcej informacji na temat konfiguracji bloku danych, zobacz [oddzielając konfigurację i dane środowiska](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="80309-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](../configurations/configData.md).</span></span>

<span data-ttu-id="80309-187">Dostępne są następujące elementy, które można skonfigurować dla każdego węzła i that are related to poświadczenie szyfrowania:</span><span class="sxs-lookup"><span data-stu-id="80309-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="80309-188">**NodeName** — nazwa węzeł docelowy jest skonfigurowany do szyfrowania poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="80309-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="80309-189">**PsDscAllowPlainTextPassword** — czy poświadczeń nieszyfrowanych będzie mogła być przekazana do tego węzła.</span><span class="sxs-lookup"><span data-stu-id="80309-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="80309-190">Jest to **niezalecane**.</span><span class="sxs-lookup"><span data-stu-id="80309-190">This is **not recommended**.</span></span>
- <span data-ttu-id="80309-191">**Odcisk palca** — odcisk palca certyfikatu, który będzie używany do odszyfrowywania poświadczeń w konfiguracji DSC na _węzeł docelowy_.</span><span class="sxs-lookup"><span data-stu-id="80309-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="80309-192">**Ten certyfikat musi istnieć w magazynie certyfikatów komputera lokalnego w docelowym węźle.**</span><span class="sxs-lookup"><span data-stu-id="80309-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="80309-193">**CertificateFile** — plik certyfikatu (zawierający tylko klucz publiczny), powinny być używane do szyfrowania poświadczeń dla _węzeł docelowy_.</span><span class="sxs-lookup"><span data-stu-id="80309-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="80309-194">Musi to być certyfikat x.509 szyfrowany binarnie algorytmem DER lub plik certyfikatu format X.509 szyfrowany algorytmem Base-64.</span><span class="sxs-lookup"><span data-stu-id="80309-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="80309-195">W tym przykładzie przedstawiono bloku danych konfiguracji, który określa węzeł docelowy, która będzie działać targetNode nazwanych, ścieżka do pliku certyfikatu klucza publicznego (o nazwie targetNode.cer) i odcisk palca klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="80309-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```

## <a name="configuration-script"></a><span data-ttu-id="80309-196">Skrypt konfiguracji</span><span class="sxs-lookup"><span data-stu-id="80309-196">Configuration script</span></span>

<span data-ttu-id="80309-197">W sam skrypt konfiguracji za pomocą `PsCredential` parametru, aby upewnić się, że poświadczenia są przechowywane na możliwie najkrótszym czasie.</span><span class="sxs-lookup"><span data-stu-id="80309-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="80309-198">Po uruchomieniu podany przykład, DSC monit o poświadczenia, a następnie szyfrować pliku MOF przy użyciu CertificateFile, który jest skojarzony z węzłem docelowym w bloku danych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="80309-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="80309-199">Ten przykładowy kod kopiuje plik z udziału, która jest zabezpieczony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="80309-199">This code example copies a file from a share that is secured to a user.</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="80309-200">Konfigurowanie odszyfrowywania</span><span class="sxs-lookup"><span data-stu-id="80309-200">Setting up decryption</span></span>

<span data-ttu-id="80309-201">Przed [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) pracować, trzeba poinformować programu Local Configuration Manager na każdym węźle docelowym o certyfikacie używanym do odszyfrowywania poświadczeń w przy użyciu zasobów CertificateID, aby zweryfikować odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="80309-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="80309-202">Ta funkcja przykład znajdzie odpowiedni certyfikat lokalny (może być konieczne go dostosować, zatem zostanie odnaleziony dokładnie certyfikat, którego chcesz użyć):</span><span class="sxs-lookup"><span data-stu-id="80309-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

<span data-ttu-id="80309-203">Za pomocą certyfikatu identyfikowane przez jego odcisk palca skryptu konfiguracji mogą być aktualizowane, aby użyć wartości:</span><span class="sxs-lookup"><span data-stu-id="80309-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="80309-204">Uruchamianie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="80309-204">Running the configuration</span></span>

<span data-ttu-id="80309-205">W tym momencie możesz uruchomić konfigurację, która zwróci dwa pliki:</span><span class="sxs-lookup"><span data-stu-id="80309-205">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="80309-206">A \*. plik meta.mof, który umożliwia skonfigurowanie programu Local Configuration Manager można odszyfrować poświadczeń przy użyciu certyfikatu, który jest przechowywany w magazynie komputera lokalnego i identyfikowane przez jego odcisk palca.</span><span class="sxs-lookup"><span data-stu-id="80309-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="80309-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) stosuje \*. meta.mof pliku.</span><span class="sxs-lookup"><span data-stu-id="80309-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
- <span data-ttu-id="80309-208">Plik MOF, który faktycznie ma zastosowanie do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="80309-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="80309-209">Start-DscConfiguration ma zastosowanie do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="80309-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="80309-210">Te polecenia spowoduje wykonanie tych kroków:</span><span class="sxs-lookup"><span data-stu-id="80309-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="80309-211">W tym przykładzie wypycha konfigurację DSC do węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="80309-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="80309-212">Konfiguracja DSC mogą być stosowane również za pomocą serwera ściągania DSC, jeśli jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="80309-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="80309-213">Zobacz [Konfigurowanie klienta ściągania DSC](pullClient.md) Aby uzyskać więcej informacji na temat stosowania konfiguracji DSC przy użyciu serwera ściągania DSC.</span><span class="sxs-lookup"><span data-stu-id="80309-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="80309-214">Przykład modułu szyfrowania poświadczeń</span><span class="sxs-lookup"><span data-stu-id="80309-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="80309-215">Oto pełny przykład, który zawiera wszystkie te kroki, a także polecenia cmdlet pomocnika, która eksportuje i kopiuje je kluczy publicznych:</span><span class="sxs-lookup"><span data-stu-id="80309-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
