---
ms.date: 10/31/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zabezpieczanie pliku MOF
ms.openlocfilehash: 80ef37ef1bdcb0a8b0ad343b4eab99f1bc66e116
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="8c723-103">Zabezpieczanie pliku MOF</span><span class="sxs-lookup"><span data-stu-id="8c723-103">Securing the MOF File</span></span>

><span data-ttu-id="8c723-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8c723-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8c723-105">DSC zarządza konfiguracji węzłów serwera, stosując informacje przechowywane w pliku MOF, gdzie lokalnego Menedżera konfiguracji (LCM) implementuje stanu zakończenia żądanej.</span><span class="sxs-lookup"><span data-stu-id="8c723-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="8c723-106">Ponieważ ten plik zawiera szczegółowe informacje o konfiguracji, należy go chronić.</span><span class="sxs-lookup"><span data-stu-id="8c723-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="8c723-107">W tym temacie opisano sposób zapewnienia węzeł docelowy jest zaszyfrowany plik.</span><span class="sxs-lookup"><span data-stu-id="8c723-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="8c723-108">Począwszy od programu PowerShell w wersji 5.0, cały plik MOF jest domyślnie szyfrowane po zastosowaniu do węzła przy użyciu **Start DSCConfiguration** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c723-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the **Start-DSCConfiguration** cmdlet.</span></span>
<span data-ttu-id="8c723-109">Proces opisany w tym artykule jest wymagany tylko w przypadku wdrażania rozwiązania przy użyciu protokołu usługi ściągania, jeśli certyfikaty nie są zarządzane, aby upewnić się, można odszyfrować i odczytywane przez system, przed ich zastosowaniem konfiguracje pobrane przez węzeł docelowy (na przykład replikacji ściąganej usługi dostępne w systemie Windows Server).</span><span class="sxs-lookup"><span data-stu-id="8c723-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="8c723-110">Węzły w zarejestrowany [Konfiguracja DSC automatyzacji Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview) zostanie automatycznie certyfikaty zainstalowaniu i zarządzane przez usługę z nie koszty administracyjne wymagane.</span><span class="sxs-lookup"><span data-stu-id="8c723-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

><span data-ttu-id="8c723-111">**Uwaga:** w tym temacie omówiono certyfikaty używane do szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="8c723-111">**Note:** This topic discusses certificates used for encryption.</span></span>
><span data-ttu-id="8c723-112">Dla celów szyfrowania certyfikatu z podpisem własnym jest wystarczająca, ponieważ klucz prywatny jest zawsze mieć klucz tajny i szyfrowania nie oznacza zaufania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8c723-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
><span data-ttu-id="8c723-113">Certyfikaty z podpisem własnym należy *nie* można używać na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="8c723-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
><span data-ttu-id="8c723-114">Należy użyć certyfikatu z zaufanego urzędu certyfikacji (CA) dla celów uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="8c723-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c723-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8c723-115">Prerequisites</span></span>

<span data-ttu-id="8c723-116">Aby pomyślnie zaszyfrować poświadczenia używane do zabezpieczania konfiguracji DSC, upewnij się, że należy dysponować następującymi elementami:</span><span class="sxs-lookup"><span data-stu-id="8c723-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

* <span data-ttu-id="8c723-117">**Niektóre metody wystawiania i rozpowszechniania certyfikatów**.</span><span class="sxs-lookup"><span data-stu-id="8c723-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="8c723-118">Ten temat i jego przykłady przyjęto założenie, że używasz urzędu certyfikacji w usłudze Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8c723-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="8c723-119">Aby uzyskać więcej informacji o tła na usługi certyfikatów Active Directory, zobacz [usług certyfikatów Active Directory — omówienie](https://technet.microsoft.com/library/hh831740.aspx) i [usługi certyfikatów Active Directory w systemie Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="8c723-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
* <span data-ttu-id="8c723-120">**Dostęp administracyjny do węzła docelowego lub węzłów**.</span><span class="sxs-lookup"><span data-stu-id="8c723-120">**Administrative access to the target node or nodes**.</span></span>
* <span data-ttu-id="8c723-121">**Każdy węzeł docelowy ma certyfikat szyfrowania zapisany swojego osobistego magazynu**.</span><span class="sxs-lookup"><span data-stu-id="8c723-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="8c723-122">W programie Windows PowerShell ścieżka do magazynu jest Cert: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="8c723-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="8c723-123">Przykłady w tym temacie szablon "Uwierzytelnianie stacji roboczej", który można znaleźć (wraz z innych szablonów certyfikatów) w [domyślne szablony certyfikatów](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="8c723-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
* <span data-ttu-id="8c723-124">Jeśli będzie działać ta konfiguracja na komputerze innym niż węzeł docelowy **wyeksportować klucz publiczny certyfikatu**, a następnie zaimportuj go do komputera, należy uruchomić konfiguracji na podstawie.</span><span class="sxs-lookup"><span data-stu-id="8c723-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="8c723-125">Upewnij się, że wyeksportowane zostały tylko **publicznego** klucza; bezpieczeństwo klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="8c723-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="8c723-126">Ogólny proces</span><span class="sxs-lookup"><span data-stu-id="8c723-126">Overall process</span></span>

 1. <span data-ttu-id="8c723-127">Konfigurowanie certyfikatów, kluczy i odcisków palców, upewniając się, że każdy węzeł docelowy ma kopię certyfikatu, a komputer konfiguracji ma klucz publiczny i odcisk palca.</span><span class="sxs-lookup"><span data-stu-id="8c723-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="8c723-128">Tworzenie konfiguracji bloku danych, który zawiera ścieżkę i odcisku palca klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="8c723-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="8c723-129">Utwórz skrypt konfiguracji, który definiuje wymaganą konfigurację do węzła docelowego i konfiguruje odszyfrowywania na węzłach docelowych przez droższe lokalnej konfiguracji menedżera do odszyfrowania danych konfiguracji przy użyciu certyfikatu i jego odcisk palca.</span><span class="sxs-lookup"><span data-stu-id="8c723-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="8c723-130">Uruchom konfigurację, co spowoduje ustawienie lokalny program Configuration Manager i uruchom konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="8c723-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="8c723-132">Wymagania dotyczące certyfikatów</span><span class="sxs-lookup"><span data-stu-id="8c723-132">Certificate Requirements</span></span>

<span data-ttu-id="8c723-133">Wprowadzenie szyfrowania poświadczeń, certyfikat klucza publicznego musi być dostępny na _węzeł docelowy_ czyli **zaufanych** przez komputer używany do tworzenia konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="8c723-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="8c723-134">Ten certyfikat klucza publicznego ma określonych wymagań dotyczących on używanego do szyfrowania poświadczeń DSC:</span><span class="sxs-lookup"><span data-stu-id="8c723-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>
 1. <span data-ttu-id="8c723-135">**Użycie klucza**:</span><span class="sxs-lookup"><span data-stu-id="8c723-135">**Key Usage**:</span></span>
   - <span data-ttu-id="8c723-136">Musi zawierać: "KeyEncipherment" i "DataEncipherment".</span><span class="sxs-lookup"><span data-stu-id="8c723-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="8c723-137">Należy _nie_ zawierać: "Podpis cyfrowy".</span><span class="sxs-lookup"><span data-stu-id="8c723-137">Should _not_ contain: 'Digital Signature'.</span></span>
 2. <span data-ttu-id="8c723-138">**Ulepszone użycie klucza**:</span><span class="sxs-lookup"><span data-stu-id="8c723-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="8c723-139">Musi zawierać: szyfrowanie dokumentów (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="8c723-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="8c723-140">Należy _nie_ zawierać: uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2) i uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="8c723-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
 3. <span data-ttu-id="8c723-141">Klucz prywatny certyfikatu jest dostępna na \* Node_ docelowej.</span><span class="sxs-lookup"><span data-stu-id="8c723-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
 4. <span data-ttu-id="8c723-142">**Dostawcy** certyfikat musi być "Microsoft RSA SChannel Cryptographic Provider".</span><span class="sxs-lookup"><span data-stu-id="8c723-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

><span data-ttu-id="8c723-143">**Zalecane:** mimo że można użyć certyfikatu z zawierających użycie klucza 'Podpisu cyfrowego' lub jednej z EKU uwierzytelniania, umożliwi to klucz szyfrowania można łatwiej użyte i narażone na atak.</span><span class="sxs-lookup"><span data-stu-id="8c723-143">**Recommended Best Practice:** Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="8c723-144">Dlatego jest najlepszym rozwiązaniem jest użycie certyfikatu utworzony specjalnie na potrzeby zabezpieczania poświadczenia DSC pomija te użycie klucza i wartości EKU.</span><span class="sxs-lookup"><span data-stu-id="8c723-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="8c723-145">Każdego istniejącego certyfikatu na _węzeł docelowy_ czy spełnia te kryteria może służyć do bezpiecznych poświadczeń z usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="8c723-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="8c723-146">Tworzenie certyfikatu</span><span class="sxs-lookup"><span data-stu-id="8c723-146">Certificate creation</span></span>

<span data-ttu-id="8c723-147">Istnieją dwie metody, które należy wykonać w celu tworzenia i używania wymaganego certyfikatu szyfrowania (pary kluczy publiczno prywatnych).</span><span class="sxs-lookup"><span data-stu-id="8c723-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="8c723-148">Utwórz je na **węzeł docelowy** i wyeksportować tylko klucz publiczny do **tworzenia węzła**</span><span class="sxs-lookup"><span data-stu-id="8c723-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="8c723-149">Utwórz je na **tworzenia węzła** i wyeksportować całą pary kluczy do **węzeł docelowy.**</span><span class="sxs-lookup"><span data-stu-id="8c723-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="8c723-150">Metoda 1 jest zalecane, ponieważ klucz prywatny używany do odszyfrowywania poświadczeń w MOF pozostaje w docelowym węźle przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="8c723-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>


### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="8c723-151">Tworzenie certyfikatu w docelowym węźle</span><span class="sxs-lookup"><span data-stu-id="8c723-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="8c723-152">Klucz prywatny muszą być trzymane, ponieważ jest używany do odszyfrowywania MOF na **węzeł docelowy** Najprostszym sposobem, w tym celu jest utworzenie certyfikatu klucza prywatnego na **węzeł docelowy**i skopiuj  **Certyfikat klucza publicznego** do komputera, używanego do tworzenia konfiguracji DSC do pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="8c723-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="8c723-153">Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="8c723-153">The following example:</span></span>
 1. <span data-ttu-id="8c723-154">tworzy certyfikat na **węzeł docelowy.**</span><span class="sxs-lookup"><span data-stu-id="8c723-154">creates a certificate on the **Target node**</span></span>
 2. <span data-ttu-id="8c723-155">Eksportuje certyfikatu klucza publicznego na **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="8c723-155">exports the public key certificate on the **Target node**.</span></span>
 3. <span data-ttu-id="8c723-156">Importuje certyfikatu klucza publicznego do **Moje** magazynu certyfikatów na **Tworzenie węzła**.</span><span class="sxs-lookup"><span data-stu-id="8c723-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="8c723-157">W docelowym węźle: tworzenie i eksportowanie certyfikatu</span><span class="sxs-lookup"><span data-stu-id="8c723-157">On the Target Node: create and export the certificate</span></span>
><span data-ttu-id="8c723-158">Węzeł docelowy: Windows Server 2016 i Windows 10</span><span class="sxs-lookup"><span data-stu-id="8c723-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="8c723-159">Wyeksportowane raz, ```DscPublicKey.cer``` potrzebny do skopiowania na **tworzenia węzła**.</span><span class="sxs-lookup"><span data-stu-id="8c723-159">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

><span data-ttu-id="8c723-160">Węzeł docelowy: Windows Server 2012 R2/Windows 8.1 i starszych wersji</span><span class="sxs-lookup"><span data-stu-id="8c723-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="8c723-161">Ponieważ nie obsługują polecenia cmdlet New-SelfSignedCertificate w systemach operacyjnych Windows starszych niż Windows 10 i Windows Server 2016 **typu** parametr, to alternatywna metoda tworzenia ten certyfikat jest wymagany na te systemy operacyjne.</span><span class="sxs-lookup"><span data-stu-id="8c723-161">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="8c723-162">W takim przypadku można użyć ```makecert.exe``` lub ```certutil.exe``` można utworzyć certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8c723-162">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="8c723-163">Jest to alternatywna metoda [pobrać skrypt SelfSignedCertificateEx.ps1 nowy Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) i przy jego użyciu zamiast tego Utwórz certyfikat:</span><span class="sxs-lookup"><span data-stu-id="8c723-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="8c723-164">Wyeksportowane raz, ```DscPublicKey.cer``` potrzebny do skopiowania na **tworzenia węzła**.</span><span class="sxs-lookup"><span data-stu-id="8c723-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="8c723-165">W węźle Autorstwo: Importowanie klucza publicznego certyfikatu</span><span class="sxs-lookup"><span data-stu-id="8c723-165">On the Authoring Node: import the cert’s public key</span></span>
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="8c723-166">Tworzenie certyfikatu w węźle tworzenia pakietów administracyjnych</span><span class="sxs-lookup"><span data-stu-id="8c723-166">Creating the Certificate on the Authoring Node</span></span>
<span data-ttu-id="8c723-167">Alternatywnie można utworzyć certyfikatu szyfrowania na **tworzenia węzła**, wyeksportowanej z **klucza prywatnego** jako PFX pliku, a następnie zaimportowane na **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="8c723-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="8c723-168">Jest to metoda bieżącego wykonywania szyfrowania poświadczeń usługi Konfiguracja DSC w sprawie _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="8c723-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="8c723-169">Chociaż plik PFX jest zabezpieczony hasłem powinna być przechowywana bezpieczne podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="8c723-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="8c723-170">Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="8c723-170">The following example:</span></span>
 1. <span data-ttu-id="8c723-171">tworzy certyfikat na **Tworzenie węzła**.</span><span class="sxs-lookup"><span data-stu-id="8c723-171">creates a certificate on the **Authoring node**.</span></span>
 2. <span data-ttu-id="8c723-172">Eksportuje certyfikatu w tym klucza prywatnego na **Tworzenie węzła**.</span><span class="sxs-lookup"><span data-stu-id="8c723-172">exports the certificate including the private key on the **Authoring node**.</span></span>
 3. <span data-ttu-id="8c723-173">Usuwa klucz prywatny z **węzła tworzenie**, ale zachowuje certyfikatu klucza publicznego **Moje** przechowywania.</span><span class="sxs-lookup"><span data-stu-id="8c723-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
 4. <span data-ttu-id="8c723-174">Importuje prywatnego klucza certyfikatu do magazynu certyfikatów głównych na **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="8c723-174">imports the private key certificate into the root certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="8c723-175">należy dodać go do magazynu certyfikatów głównych, dzięki czemu będą zaufane przez **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="8c723-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="8c723-176">W węźle Autorstwo: tworzenie i eksportowanie certyfikatu</span><span class="sxs-lookup"><span data-stu-id="8c723-176">On the Authoring Node: create and export the certificate</span></span>
><span data-ttu-id="8c723-177">Węzeł docelowy: Windows Server 2016 i Windows 10</span><span class="sxs-lookup"><span data-stu-id="8c723-177">Target Node: Windows Server 2016 and Windows 10</span></span>

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
<span data-ttu-id="8c723-178">Wyeksportowane raz, ```DscPrivateKey.pfx``` potrzebny do skopiowania na **węzeł docelowy**.</span><span class="sxs-lookup"><span data-stu-id="8c723-178">Once exported, the ```DscPrivateKey.pfx``` would need to be copied to the **Target Node**.</span></span>

><span data-ttu-id="8c723-179">Węzeł docelowy: Windows Server 2012 R2/Windows 8.1 i starszych wersji</span><span class="sxs-lookup"><span data-stu-id="8c723-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="8c723-180">Ponieważ nie obsługują polecenia cmdlet New-SelfSignedCertificate w systemach operacyjnych Windows starszych niż Windows 10 i Windows Server 2016 **typu** parametr, to alternatywna metoda tworzenia ten certyfikat jest wymagany na te systemy operacyjne.</span><span class="sxs-lookup"><span data-stu-id="8c723-180">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="8c723-181">W takim przypadku można użyć ```makecert.exe``` lub ```certutil.exe``` można utworzyć certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8c723-181">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="8c723-182">Jest to alternatywna metoda [pobrać skrypt SelfSignedCertificateEx.ps1 nowy Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) i przy jego użyciu zamiast tego Utwórz certyfikat:</span><span class="sxs-lookup"><span data-stu-id="8c723-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="8c723-183">W docelowym węźle: Importowanie klucza prywatnego certyfikatu zaufanego głównego</span><span class="sxs-lookup"><span data-stu-id="8c723-183">On the Target Node: import the cert’s private key as a trusted root</span></span>
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="8c723-184">Dane konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8c723-184">Configuration data</span></span>

<span data-ttu-id="8c723-185">Blok danych konfiguracji definiuje węzły docelowe, których działanie od tego, czy lub nie, aby zaszyfrować poświadczenia, środki szyfrowania i inne informacje.</span><span class="sxs-lookup"><span data-stu-id="8c723-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="8c723-186">Aby uzyskać więcej informacji na blok danych konfiguracji, zobacz [oddzielając konfigurację i dane środowiska](configData.md).</span><span class="sxs-lookup"><span data-stu-id="8c723-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="8c723-187">Dostępne są następujące elementy, które można skonfigurować dla każdego węzła związanych z szyfrowania poświadczeń:</span><span class="sxs-lookup"><span data-stu-id="8c723-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>
* <span data-ttu-id="8c723-188">**NodeName** — nazwa konfigurowanego szyfrowania poświadczeń do węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="8c723-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
* <span data-ttu-id="8c723-189">**PsDscAllowPlainTextPassword** — czy niezaszyfrowane poświadczeń będzie mogła zostać przekazany do tego węzła.</span><span class="sxs-lookup"><span data-stu-id="8c723-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="8c723-190">Jest to **niezalecane**.</span><span class="sxs-lookup"><span data-stu-id="8c723-190">This is **not recommended**.</span></span>
* <span data-ttu-id="8c723-191">**Odcisk palca** — odcisk palca certyfikatu, który będzie używany do odszyfrowywania poświadczeń w konfiguracji DSC na _węzeł docelowy_.</span><span class="sxs-lookup"><span data-stu-id="8c723-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="8c723-192">**Ten certyfikat musi istnieć w magazynie certyfikatów komputera lokalnego w docelowym węźle.**</span><span class="sxs-lookup"><span data-stu-id="8c723-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
* <span data-ttu-id="8c723-193">**CertificateFile** — plik certyfikatu (zawierającą tylko klucz publiczny) która powinna być używana do szyfrowania poświadczeń dla _węzeł docelowy_.</span><span class="sxs-lookup"><span data-stu-id="8c723-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="8c723-194">Musi to być albo x.509 szyfrowany binarnie algorytmem DER lub plik certyfikatu format x.509 szyfrowany algorytmem Base-64.</span><span class="sxs-lookup"><span data-stu-id="8c723-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="8c723-195">Ten przykład przedstawia blok danych konfiguracji określający węzła docelowego do działania o nazwie targetNode, ścieżka do pliku certyfikatu klucza publicznego (o nazwie targetNode.cer) i odcisku palca klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="8c723-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

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


## <a name="configuration-script"></a><span data-ttu-id="8c723-196">Skrypt konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8c723-196">Configuration script</span></span>

<span data-ttu-id="8c723-197">W skrypcie programu configuration użyj `PsCredential` parametr, aby upewnić się, że poświadczenia są przechowywane dla najkrótszym czasie.</span><span class="sxs-lookup"><span data-stu-id="8c723-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="8c723-198">Po uruchomieniu podany przykład DSC monit o wprowadzenie poświadczeń, a następnie szyfrować pliku MOF przy użyciu CertificateFile, który jest skojarzony z węzła docelowego w bloku danych konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8c723-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="8c723-199">Ten przykładowy kod kopiuje plik z udziału, który jest zabezpieczony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8c723-199">This code example copies a file from a share that is secured to a user.</span></span>

```
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

## <a name="setting-up-decryption"></a><span data-ttu-id="8c723-200">Konfigurowanie odszyfrowywania</span><span class="sxs-lookup"><span data-stu-id="8c723-200">Setting up decryption</span></span>

<span data-ttu-id="8c723-201">Przed [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) można pracować, trzeba sprawdzić lokalny program Configuration Manager na każdym węźle docelowym o certyfikacie używanym do odszyfrowywania poświadczeń, Sprawdź odcisk palca certyfikatu przy użyciu zasobów CertificateID.</span><span class="sxs-lookup"><span data-stu-id="8c723-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="8c723-202">Ta funkcja przykład znajdziesz odpowiedni certyfikat lokalny (trzeba będzie dostosować go tak znajdzie dokładnie certyfikat, którego chcesz użyć):</span><span class="sxs-lookup"><span data-stu-id="8c723-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

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

<span data-ttu-id="8c723-203">Przy użyciu identyfikowana na podstawie jego odcisk palca certyfikatu Aby użyć wartości można zaktualizować skryptu konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="8c723-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

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

## <a name="running-the-configuration"></a><span data-ttu-id="8c723-204">Uruchomiony w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8c723-204">Running the configuration</span></span>

<span data-ttu-id="8c723-205">W tym momencie możesz uruchomić konfiguracja, w którym dane wyjściowe obejmują dwa pliki:</span><span class="sxs-lookup"><span data-stu-id="8c723-205">At this point, you can run the configuration, which will output two files:</span></span>

 * <span data-ttu-id="8c723-206">A \*. meta.mof pliku, który konfiguruje lokalny program Configuration Manager można odszyfrować poświadczeń przy użyciu certyfikatu, który jest przechowywany w magazynie komputera lokalnego i identyfikowana na podstawie jego odcisk palca.</span><span class="sxs-lookup"><span data-stu-id="8c723-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="8c723-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) stosuje \*. meta.mof pliku.</span><span class="sxs-lookup"><span data-stu-id="8c723-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
 * <span data-ttu-id="8c723-208">Plik MOF, który faktycznie ma zastosowanie do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8c723-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="8c723-209">Początek DscConfiguration ma zastosowanie do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8c723-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="8c723-210">Te polecenia będzie wykonywać te kroki:</span><span class="sxs-lookup"><span data-stu-id="8c723-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="8c723-211">W tym przykładzie wypycha konfiguracji DSC do węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="8c723-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="8c723-212">Konfiguracja DSC można również będą stosowane przy użyciu serwera ściągania usługi Konfiguracja DSC, jeśli jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="8c723-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="8c723-213">Zobacz [konfigurowania klienta ściągania usługi Konfiguracja DSC](pullClient.md) Aby uzyskać więcej informacji na temat stosowania konfiguracji DSC przy użyciu serwera ściągania usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="8c723-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="8c723-214">Przykład modułu szyfrowania poświadczeń</span><span class="sxs-lookup"><span data-stu-id="8c723-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="8c723-215">Oto przykład pełna, która będzie zawierała wszystkie te kroki, oraz pomocnika polecenie cmdlet eksportuje i kopiuje kluczy publicznych:</span><span class="sxs-lookup"><span data-stu-id="8c723-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

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