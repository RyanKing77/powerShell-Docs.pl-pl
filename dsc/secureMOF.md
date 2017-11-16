---
ms.date: 2017-10-31
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Zabezpieczanie pliku MOF
ms.openlocfilehash: f4ef2962710c7458ac947bf33270175a09de643c
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="securing-the-mof-file"></a>Zabezpieczanie pliku MOF

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

DSC zarządza konfiguracji węzłów serwera, stosując informacje przechowywane w pliku MOF, gdzie lokalnego Menedżera konfiguracji (LCM) implementuje stanu zakończenia żądanej.
Ponieważ ten plik zawiera szczegółowe informacje o konfiguracji, należy go chronić.
W tym temacie opisano sposób zapewnienia węzeł docelowy jest zaszyfrowany plik.

Począwszy od programu PowerShell w wersji 5.0, cały plik MOF jest domyślnie szyfrowane po zastosowaniu do węzła przy użyciu **Start DSCConfiguration** polecenia cmdlet.
Proces opisany w tym artykule jest wymagany tylko w przypadku wdrażania rozwiązania przy użyciu protokołu usługi ściągania, jeśli certyfikaty nie są zarządzane, aby upewnić się, można odszyfrować i odczytywane przez system, przed ich zastosowaniem konfiguracje pobrane przez węzeł docelowy (na przykład replikacji ściąganej usługi dostępne w systemie Windows Server).
Węzły w zarejestrowany [Konfiguracja DSC automatyzacji Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) zostanie automatycznie certyfikaty zainstalowaniu i zarządzane przez usługę z nie koszty administracyjne wymagane.

>**Uwaga:** w tym temacie omówiono certyfikaty używane do szyfrowania.
>Dla celów szyfrowania certyfikatu z podpisem własnym jest wystarczająca, ponieważ klucz prywatny jest zawsze mieć klucz tajny i szyfrowania nie oznacza zaufania dokumentu.
>Certyfikaty z podpisem własnym należy *nie* można używać na potrzeby uwierzytelniania.
>Należy użyć certyfikatu z zaufanego urzędu certyfikacji (CA) dla celów uwierzytelniania.

## <a name="prerequisites"></a>Wymagania wstępne

Aby pomyślnie zaszyfrować poświadczenia używane do zabezpieczania konfiguracji DSC, upewnij się, że należy dysponować następującymi elementami:

* **Niektóre metody wystawiania i rozpowszechniania certyfikatów**. Ten temat i jego przykłady przyjęto założenie, że używasz urzędu certyfikacji w usłudze Active Directory. Aby uzyskać więcej informacji o tła na usługi certyfikatów Active Directory, zobacz [usług certyfikatów Active Directory — omówienie](https://technet.microsoft.com/library/hh831740.aspx) i [usługi certyfikatów Active Directory w systemie Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Dostęp administracyjny do węzła docelowego lub węzłów**.
* **Każdy węzeł docelowy ma certyfikat szyfrowania zapisany swojego osobistego magazynu**. W programie Windows PowerShell ścieżka do magazynu jest Cert: \LocalMachine\My. Przykłady w tym temacie szablon "Uwierzytelnianie stacji roboczej", który można znaleźć (wraz z innych szablonów certyfikatów) w [domyślne szablony certyfikatów](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
* Jeśli będzie działać ta konfiguracja na komputerze innym niż węzeł docelowy **wyeksportować klucz publiczny certyfikatu**, a następnie zaimportuj go do komputera, należy uruchomić konfiguracji na podstawie. Upewnij się, że wyeksportowane zostały tylko **publicznego** klucza; bezpieczeństwo klucza prywatnego.

## <a name="overall-process"></a>Ogólny proces

 1. Konfigurowanie certyfikatów, kluczy i odcisków palców, upewniając się, że każdy węzeł docelowy ma kopię certyfikatu, a komputer konfiguracji ma klucz publiczny i odcisk palca.
 2. Tworzenie konfiguracji bloku danych, który zawiera ścieżkę i odcisku palca klucza publicznego.
 3. Utwórz skrypt konfiguracji, który definiuje wymaganą konfigurację do węzła docelowego i konfiguruje odszyfrowywania na węzłach docelowych przez droższe lokalnej konfiguracji menedżera do odszyfrowania danych konfiguracji przy użyciu certyfikatu i jego odcisk palca.
 4. Uruchom konfigurację, co spowoduje ustawienie lokalny program Configuration Manager i uruchom konfiguracji DSC.

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Wymagania dotyczące certyfikatów

Wprowadzenie szyfrowania poświadczeń, certyfikat klucza publicznego musi być dostępny na _węzeł docelowy_ czyli **zaufanych** przez komputer używany do tworzenia konfiguracji DSC.
Ten certyfikat klucza publicznego ma określonych wymagań dotyczących on używanego do szyfrowania poświadczeń DSC:
 1. **Użycie klucza**:
   - Musi zawierać: "KeyEncipherment" i "DataEncipherment".
   - Należy _nie_ zawierać: "Podpis cyfrowy".
 2. **Ulepszone użycie klucza**:
   - Musi zawierać: szyfrowanie dokumentów (1.3.6.1.4.1.311.80.1).
   - Należy _nie_ zawierać: uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2) i uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1).
 3. Klucz prywatny certyfikatu jest dostępna na * Node_ docelowej.
 4. **Dostawcy** certyfikat musi być "Microsoft RSA SChannel Cryptographic Provider".
 
>**Zalecane:** mimo że można użyć certyfikatu z zawierających użycie klucza 'Podpisu cyfrowego' lub jednej z EKU uwierzytelniania, umożliwi to klucz szyfrowania można łatwiej użyte i narażone na atak. Dlatego jest najlepszym rozwiązaniem jest użycie certyfikatu utworzony specjalnie na potrzeby zabezpieczania poświadczenia DSC pomija te użycie klucza i wartości EKU.
  
Każdego istniejącego certyfikatu na _węzeł docelowy_ czy spełnia te kryteria może służyć do bezpiecznych poświadczeń z usługi Konfiguracja DSC.

## <a name="certificate-creation"></a>Tworzenie certyfikatu

Istnieją dwie metody, które należy wykonać w celu tworzenia i używania wymaganego certyfikatu szyfrowania (pary kluczy publiczno prywatnych).

1. Utwórz je na **węzeł docelowy** i wyeksportować tylko klucz publiczny do **tworzenia węzła**
2. Utwórz je na **tworzenia węzła** i wyeksportować całą pary kluczy do **węzeł docelowy.**

Metoda 1 jest zalecane, ponieważ klucz prywatny używany do odszyfrowywania poświadczeń w MOF pozostaje w docelowym węźle przez cały czas.


### <a name="creating-the-certificate-on-the-target-node"></a>Tworzenie certyfikatu w docelowym węźle

Klucz prywatny muszą być trzymane, ponieważ jest używany do odszyfrowywania MOF na **węzeł docelowy** Najprostszym sposobem, w tym celu jest utworzenie certyfikatu klucza prywatnego na **węzeł docelowy**i skopiuj  **Certyfikat klucza publicznego** do komputera, używanego do tworzenia konfiguracji DSC do pliku MOF.
Poniższy przykład:
 1. tworzy certyfikat na **węzeł docelowy.**
 2. Eksportuje certyfikatu klucza publicznego na **węzeł docelowy**.
 3. Importuje certyfikatu klucza publicznego do **Moje** magazynu certyfikatów na **Tworzenie węzła**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>W docelowym węźle: tworzenie i eksportowanie certyfikatu
>Tworzenia węzła: Windows Server 2016 i Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
Wyeksportowane raz, ```DscPublicKey.cer``` potrzebny do skopiowania na **tworzenia węzła**.

>Węzeł autorstwa: Windows Server 2012 R2/Windows 8.1 i starszych wersji

Ponieważ nie obsługują polecenia cmdlet New-SelfSignedCertificate w systemach operacyjnych Windows starszych niż Windows 10 i Windows Server 2016 **typu** parametr, to alternatywna metoda tworzenia ten certyfikat jest wymagany na te systemy operacyjne.
W takim przypadku można użyć ```makecert.exe``` lub ```certutil.exe``` można utworzyć certyfikatu.

Jest to alternatywna metoda [pobrać skrypt SelfSignedCertificateEx.ps1 nowy Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) i przy jego użyciu zamiast tego Utwórz certyfikat:
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
    -StoreName 'My' `
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
Wyeksportowane raz, ```DscPublicKey.cer``` potrzebny do skopiowania na **tworzenia węzła**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>W węźle Autorstwo: Importowanie klucza publicznego certyfikatu
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Tworzenie certyfikatu w węźle tworzenia pakietów administracyjnych
Alternatywnie można utworzyć certyfikatu szyfrowania na **tworzenia węzła**, wyeksportowanej z **klucza prywatnego** jako PFX pliku, a następnie zaimportowane na **węzeł docelowy**.
Jest to metoda bieżącego wykonywania szyfrowania poświadczeń usługi Konfiguracja DSC w sprawie _Nano Server_.
Chociaż plik PFX jest zabezpieczony hasłem powinna być przechowywana bezpieczne podczas przesyłania.
Poniższy przykład:
 1. tworzy certyfikat na **Tworzenie węzła**.
 2. Eksportuje certyfikatu w tym klucza prywatnego na **Tworzenie węzła**.
 3. Usuwa klucz prywatny z **węzła tworzenie**, ale zachowuje certyfikatu klucza publicznego **Moje** przechowywania.
 4. Importuje prywatnego klucza certyfikatu do magazynu certyfikatów głównych na **węzeł docelowy**.
   - należy dodać go do magazynu certyfikatów głównych, dzięki czemu będą zaufane przez **węzeł docelowy**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>W węźle Autorstwo: tworzenie i eksportowanie certyfikatu
>Węzeł docelowy: Windows Server 2016 i Windows 10

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
Wyeksportowane raz, ```DscPrivateKey.pfx``` potrzebny do skopiowania na **węzeł docelowy**.

>Węzeł docelowy: Windows Server 2012 R2/Windows 8.1 i starszych wersji

Ponieważ nie obsługują polecenia cmdlet New-SelfSignedCertificate w systemach operacyjnych Windows starszych niż Windows 10 i Windows Server 2016 **typu** parametr, to alternatywna metoda tworzenia ten certyfikat jest wymagany na te systemy operacyjne.
W takim przypadku można użyć ```makecert.exe``` lub ```certutil.exe``` można utworzyć certyfikatu.

Jest to alternatywna metoda [pobrać skrypt SelfSignedCertificateEx.ps1 nowy Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) i przy jego użyciu zamiast tego Utwórz certyfikat:
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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>W docelowym węźle: Importowanie klucza prywatnego certyfikatu zaufanego głównego
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\Root -Password $mypwd > $null
```

## <a name="configuration-data"></a>Dane konfiguracji

Blok danych konfiguracji definiuje węzły docelowe, których działanie od tego, czy lub nie, aby zaszyfrować poświadczenia, środki szyfrowania i inne informacje. Aby uzyskać więcej informacji na blok danych konfiguracji, zobacz [oddzielając konfigurację i dane środowiska](configData.md).

Dostępne są następujące elementy, które można skonfigurować dla każdego węzła związanych z szyfrowania poświadczeń:
* **NodeName** — nazwa konfigurowanego szyfrowania poświadczeń do węzła docelowego.
* **PsDscAllowPlainTextPassword** — czy niezaszyfrowane poświadczeń będzie mogła zostać przekazany do tego węzła. Jest to **niezalecane**.
* **Odcisk palca** — odcisk palca certyfikatu, który będzie używany do odszyfrowywania poświadczeń w konfiguracji DSC na _węzeł docelowy_. **Ten certyfikat musi istnieć w magazynie certyfikatów komputera lokalnego w docelowym węźle.**
* **CertificateFile** — plik certyfikatu (zawierającą tylko klucz publiczny) która powinna być używana do szyfrowania poświadczeń dla _węzeł docelowy_. Musi to być albo x.509 szyfrowany binarnie algorytmem DER lub plik certyfikatu format x.509 szyfrowany algorytmem Base-64.

Ten przykład przedstawia blok danych konfiguracji określający węzła docelowego do działania o nazwie targetNode, ścieżka do pliku certyfikatu klucza publicznego (o nazwie targetNode.cer) i odcisku palca klucza publicznego.

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


## <a name="configuration-script"></a>Skrypt konfiguracji

W skrypcie programu configuration użyj `PsCredential` parametr, aby upewnić się, że poświadczenia są przechowywane dla najkrótszym czasie. Po uruchomieniu podany przykład DSC monit o wprowadzenie poświadczeń, a następnie szyfrować pliku MOF przy użyciu CertificateFile, który jest skojarzony z węzła docelowego w bloku danych konfiguracji. Ten przykładowy kod kopiuje plik z udziału, który jest zabezpieczony przez użytkownika.

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

## <a name="setting-up-decryption"></a>Konfigurowanie odszyfrowywania

Przed [ `Start-DscConfiguration` ](https://technet.microsoft.com/en-us/library/dn521623.aspx) można pracować, trzeba sprawdzić lokalny program Configuration Manager na każdym węźle docelowym o certyfikacie używanym do odszyfrowywania poświadczeń, Sprawdź odcisk palca certyfikatu przy użyciu zasobów CertificateID. Ta funkcja przykład znajdziesz odpowiedni certyfikat lokalny (trzeba będzie dostosować go tak znajdzie dokładnie certyfikat, którego chcesz użyć):

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

Przy użyciu identyfikowana na podstawie jego odcisk palca certyfikatu Aby użyć wartości można zaktualizować skryptu konfiguracji:

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

## <a name="running-the-configuration"></a>Uruchomiony w konfiguracji

W tym momencie możesz uruchomić konfiguracja, w którym dane wyjściowe obejmują dwa pliki:

 * A *. meta.mof pliku, który konfiguruje lokalny program Configuration Manager można odszyfrować poświadczeń przy użyciu certyfikatu, który jest przechowywany w magazynie komputera lokalnego i identyfikowana na podstawie jego odcisk palca. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx)stosuje *. meta.mof pliku.
 * Plik MOF, który faktycznie ma zastosowanie do konfiguracji. Początek DscConfiguration ma zastosowanie do konfiguracji.

Te polecenia będzie wykonywać te kroki:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

W tym przykładzie wypycha konfiguracji DSC do węzła docelowego.
Konfiguracja DSC można również będą stosowane przy użyciu serwera ściągania usługi Konfiguracja DSC, jeśli jest dostępny.

Zobacz [konfigurowania klienta ściągania usługi Konfiguracja DSC](pullClient.md) Aby uzyskać więcej informacji na temat stosowania konfiguracji DSC przy użyciu serwera ściągania usługi Konfiguracja DSC.

## <a name="credential-encryption-module-example"></a>Przykład modułu szyfrowania poświadczeń

Oto przykład pełna, która będzie zawierała wszystkie te kroki, oraz pomocnika polecenie cmdlet eksportuje i kopiuje kluczy publicznych:

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

