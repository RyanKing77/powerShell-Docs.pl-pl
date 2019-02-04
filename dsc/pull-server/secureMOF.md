---
ms.date: 10/31/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zabezpieczanie pliku MOF
ms.openlocfilehash: 6c2aadb75ac617d9b845ef387f292b8156bb8889
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688329"
---
# <a name="securing-the-mof-file"></a>Zabezpieczanie pliku MOF

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC zarządza konfiguracją węzły serwera, stosując informacje przechowywane w pliku MOF, w przypadku, gdy lokalne Configuration Manager (LCM) wykonuje stanu końcowego żądaną.
Ponieważ ten plik zawiera szczegółowe informacje o konfiguracji, należy Przechowuj w bezpiecznym miejscu.
W tym temacie opisano sposób zapewnienia węzeł docelowy jest zaszyfrowany plik.

Począwszy od programu PowerShell w wersji 5.0, cały plik MOF jest domyślnie szyfrowane po zastosowaniu do węzła przy użyciu `Start-DSCConfiguration` polecenia cmdlet.
Proces opisany w tym artykule jest wymagany tylko wtedy, gdy wdrażanie rozwiązania przy użyciu protokołu usługi ściągania, jeśli certyfikaty nie są zarządzane, aby upewnić się, konfiguracje pobrane przez węzeł docelowy może być odszyfrowane i odczytywane przez system, przed ich zastosowaniem (na przykład usługi ściągania dostępne w systemie Windows Server).
Węzły zarejestrowane do [usługi Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) automatycznie mają certyfikaty zainstalowane i zarządzane przez usługę z nie czynności administracyjnych wymagane.

> [!NOTE]
> W tym temacie omówiono certyfikaty używane do szyfrowania.
> Dla celów szyfrowania certyfikat z podpisem własnym jest wystarczający, ponieważ klucz prywatny jest przechowywany zawsze, hasło i szyfrowanie nie oznacza zaufania dokumentu.
> Certyfikaty z podpisem własnym należy *nie* można używać na potrzeby uwierzytelniania.
> W żadnych celach uwierzytelniania należy używać certyfikatu z zaufanego urzędu certyfikacji (CA).

## <a name="prerequisites"></a>Wymagania wstępne

Aby pomyślnie zaszyfrować poświadczenia używane do zabezpieczania konfiguracji DSC, upewnij się, że dysponujesz następującymi elementami:

- **Niektóre środki wystawiania i rozpowszechniania certyfikatów**. Ten temat i jego przykładów przyjęto założenie, że w przypadku korzystania z urzędu certyfikacji w usłudze Active Directory. Aby uzyskać więcej informacji o tła w usługach certyfikatów Active Directory, zobacz [Omówienie usług certyfikatów w usłudze Active Directory](https://technet.microsoft.com/library/hh831740.aspx) i [usług certyfikatów Active Directory w systemie Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
- **Dostęp administracyjny do węzła docelowego lub węzły**.
- **Każdy węzeł docelowy ma certyfikat szyfrowania zapisane jego Store osobiste**. W programie Windows PowerShell ścieżkę do magazynu jest Cert: \LocalMachine\My. Przykłady w tym temacie używania szablonu "Uwierzytelnianie stacji roboczej", który można znaleźć (wraz z innych szablonów certyfikatów) w [domyślne szablony certyfikatów](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
- Jeśli będzie działać tej konfiguracji na komputerze innym niż węzeł docelowy **wyeksportować klucz publiczny certyfikatu**, a następnie zaimportuj go do komputera, Uruchom konfigurację przy użyciu. Upewnij się, który chcesz eksportować tylko **publicznych** klucza; bezpieczeństwo klucza prywatnego.

## <a name="overall-process"></a>Ogólny proces

 1. Konfigurowanie certyfikatów, kluczy i odciski palców, upewniając się, że każdy węzeł docelowy ma kopii certyfikatu, a konfiguracja komputer ma klucza publicznego i odcisk palca.
 2. Tworzenie bloku danych konfiguracji, który zawiera ścieżkę i odcisk palca klucza publicznego.
 3. Utwórz skrypt konfiguracyjny, który definiuje żądaną konfigurację dla węzła docelowego i konfiguruje odszyfrowywania na węzłach docelowych przez polecenia lokalnego konfiguracji menedżera do odszyfrowania danych konfiguracji, za pomocą certyfikatu i jego odcisk palca.
 4. Uruchom konfigurację, co spowoduje ustawienie Local Configuration Manager i konfiguracji DSC.

![Diagram1](../images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Wymagania dotyczące certyfikatów

Wprowadzenie szyfrowania poświadczeń, certyfikat klucza publicznego musi być dostępny na _węzeł docelowy_ czyli **zaufanych** przez komputer używany do tworzenia konfiguracji DSC.
Ten certyfikat klucza publicznego ma określonych wymagań dotyczących może być ona używana do szyfrowania poświadczeń DSC:

1. **Użycie klucza**:
   - Musi zawierać: "KeyEncipherment" i "DataEncipherment".
   - Należy _nie_ zawierają: "Podpis cyfrowy".
2. **Ulepszone użycie klucza**:
   - Musi zawierać: Szyfrowanie dokumentów (1.3.6.1.4.1.311.80.1).
   - Należy _nie_ zawierają: Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2) i uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1).
3. Klucz prywatny certyfikatu jest dostępna na * Node_ docelowej.
4. **Dostawcy** dla certyfikatu musi być "Microsoft RSA SChannel Cryptographic Provider".

> [!IMPORTANT]
> Mimo że można użyć certyfikatu z zawierających użycie klucza, 'Podpis cyfrowy' lub jedną wartość EKU uwierzytelniania, umożliwi to klucz szyfrowania, można łatwiej użyte i podatne na atak. Dlatego jest najlepszym rozwiązaniem jest użycie certyfikatów utworzonych specjalnie na potrzeby zabezpieczania poświadczenia DSC pomija te użycie klucza i wartości EKU.

Dowolnego istniejącego certyfikatu na _węzeł docelowy_ czy spełnia te kryteria może służyć do bezpiecznych poświadczeń DSC.

## <a name="certificate-creation"></a>Tworzenie certyfikatu

Istnieją dwie metody, które można wykonać w celu tworzenia i używania wymaganego certyfikatu szyfrowania (pary kluczy publiczny prywatny).

1. Utwórz je na **węzeł docelowy** i wyeksportować tylko klucz publiczny, który **tworzenia węzła**
2. Utwórz je na **tworzenia węzła** i eksportować całą pary kluczy do **węzeł docelowy**

Metoda 1 jest zalecane, ponieważ klucz prywatny używany do odszyfrowywania poświadczeń w pliku MOF pozostaje w docelowym węźle przez cały czas.

### <a name="creating-the-certificate-on-the-target-node"></a>Tworzenie certyfikatu na węzeł docelowy

Klucz prywatny musi znajdować się wpisu tajnego, ponieważ jest używany do odszyfrowywania pliku MOF w **węzeł docelowy** Najprostszym sposobem wykonania tego zadania jest utworzenie certyfikatu klucza prywatnego na **węzeł docelowy**, a następnie skopiuj  **Certyfikat klucza publicznego** komputer używany do tworzenia konfiguracji DSC w pliku MOF.
Poniższy przykład:

1. tworzy certyfikat na **węzeł docelowy**
2. Eksportuje certyfikat klucza publicznego na **węzeł docelowy**.
3. importuje certyfikat klucza publicznego do **Moje** magazynu certyfikatów na **węzeł tworzenie**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>W węźle docelowym: tworzenie i eksportowanie certyfikatu

> Węzeł docelowy: System Windows Server 2016 i Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

Po wyeksportowaniu `DscPublicKey.cer` musi być skopiowane do **tworzenia węzła**.

> Węzeł docelowy: Windows Server 2012 R2/Windows 8.1 i starszych wersji
> [!WARNING]
> Ponieważ `New-SelfSignedCertificate` nie obsługują polecenia cmdlet w systemie operacyjnym Windows przed systemem Windows 10 i Windows Server 2016 **typu** parametr, alternatywną metodę tworzenia ten certyfikat jest wymagany w tych systemach operacyjnych.
>
> W takim przypadku można użyć `makecert.exe` lub `certutil.exe` do utworzenia certyfikatu.
>
>Alternatywna metoda jest [Pobierz skrypt New SelfSignedCertificateEx.ps1 z Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) i użyć go do utworzenia certyfikatu zamiast tego:

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

Po wyeksportowaniu ```DscPublicKey.cer``` musi być skopiowane do **tworzenia węzła**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>W węźle Autorstwo: importowanie certyfikatu klucza publicznego

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Tworzenie certyfikatu w węźle tworzenia pakietów administracyjnych

Alternatywnie można utworzyć certyfikatu szyfrowania na **tworzenia węzła**, wyeksportowane z **klucza prywatnego** jako plik PFX pliku, a następnie zaimportowane na **węzeł docelowy**.
Jest to bieżąca metoda implementowania szyfrowania poświadczeń DSC na _serwera Nano Server_.
Mimo, że plik PFX jest zabezpieczony za pomocą hasła powinna być przechowywana bezpieczne podczas przesyłania.
Poniższy przykład:

1. tworzy certyfikat na **węzeł tworzenie**.
2. Umożliwia wyeksportowanie certyfikatu w tym klucza prywatnego na **węzeł tworzenie**.
3. Usuwa klucz prywatny z **węzeł tworzenie**, ale zachowuje certyfikatu klucza publicznego **Moje** przechowywania.
4. importuje certyfikat klucza prywatnego do magazynu certyfikatów My(Personal) na **węzeł docelowy**.
   - należy dodać do magazynu certyfikatów głównych, dzięki czemu będą zaufane przez **węzeł docelowy**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>W węźle tworzenie: tworzenie i eksportowanie certyfikatu

> Węzeł docelowy: System Windows Server 2016 i Windows 10

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

Po wyeksportowaniu `DscPrivateKey.pfx` musi być skopiowane do **węzeł docelowy**.

> Węzeł docelowy: Windows Server 2012 R2/Windows 8.1 i starszych wersji
> [!WARNING]
> Ponieważ `New-SelfSignedCertificate` nie obsługują polecenia cmdlet w systemie operacyjnym Windows przed systemem Windows 10 i Windows Server 2016 **typu** parametr, alternatywną metodę tworzenia ten certyfikat jest wymagany w tych systemach operacyjnych.
>
> W takim przypadku można użyć `makecert.exe` lub `certutil.exe` do utworzenia certyfikatu.
>
> Alternatywna metoda jest [Pobierz skrypt New SelfSignedCertificateEx.ps1 z Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) i użyć go do utworzenia certyfikatu zamiast tego:

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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>W węźle docelowym: Importowanie klucza prywatnego certyfikatu jako zaufany główny urząd certyfikacji

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Dane konfiguracji

Blok danych konfiguracyjnych definiuje węzły docelowe, których działanie od tego, czy lub nie, aby zaszyfrować poświadczenia, oznacza, że szyfrowania i inne informacje. Aby uzyskać więcej informacji na temat konfiguracji bloku danych, zobacz [oddzielając konfigurację i dane środowiska](../configurations/configData.md).

Dostępne są następujące elementy, które można skonfigurować dla każdego węzła i that are related to poświadczenie szyfrowania:

- **NodeName** — nazwa węzeł docelowy jest skonfigurowany do szyfrowania poświadczeń.
- **PsDscAllowPlainTextPassword** — czy poświadczeń nieszyfrowanych będzie mogła być przekazana do tego węzła. Jest to **niezalecane**.
- **Odcisk palca** — odcisk palca certyfikatu, który będzie używany do odszyfrowywania poświadczeń w konfiguracji DSC na _węzeł docelowy_. **Ten certyfikat musi istnieć w magazynie certyfikatów komputera lokalnego w docelowym węźle.**
- **CertificateFile** — plik certyfikatu (zawierający tylko klucz publiczny), powinny być używane do szyfrowania poświadczeń dla _węzeł docelowy_. Musi to być certyfikat x.509 szyfrowany binarnie algorytmem DER lub plik certyfikatu format X.509 szyfrowany algorytmem Base-64.

W tym przykładzie przedstawiono bloku danych konfiguracji, który określa węzeł docelowy, która będzie działać targetNode nazwanych, ścieżka do pliku certyfikatu klucza publicznego (o nazwie targetNode.cer) i odcisk palca klucza publicznego.

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

W sam skrypt konfiguracji za pomocą `PsCredential` parametru, aby upewnić się, że poświadczenia są przechowywane na możliwie najkrótszym czasie. Po uruchomieniu podany przykład, DSC monit o poświadczenia, a następnie szyfrować pliku MOF przy użyciu CertificateFile, który jest skojarzony z węzłem docelowym w bloku danych konfiguracji. Ten przykładowy kod kopiuje plik z udziału, która jest zabezpieczony przez użytkownika.

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

## <a name="setting-up-decryption"></a>Konfigurowanie odszyfrowywania

Przed [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) pracować, trzeba poinformować programu Local Configuration Manager na każdym węźle docelowym o certyfikacie używanym do odszyfrowywania poświadczeń w przy użyciu zasobów CertificateID, aby zweryfikować odcisk palca certyfikatu. Ta funkcja przykład znajdzie odpowiedni certyfikat lokalny (może być konieczne go dostosować, zatem zostanie odnaleziony dokładnie certyfikat, którego chcesz użyć):

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

Za pomocą certyfikatu identyfikowane przez jego odcisk palca skryptu konfiguracji mogą być aktualizowane, aby użyć wartości:

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

## <a name="running-the-configuration"></a>Uruchamianie konfiguracji

W tym momencie możesz uruchomić konfigurację, która zwróci dwa pliki:

- A *. plik meta.mof, który umożliwia skonfigurowanie programu Local Configuration Manager można odszyfrować poświadczeń przy użyciu certyfikatu, który jest przechowywany w magazynie komputera lokalnego i identyfikowane przez jego odcisk palca. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) stosuje *. meta.mof pliku.
- Plik MOF, który faktycznie ma zastosowanie do konfiguracji. Start-DscConfiguration ma zastosowanie do konfiguracji.

Te polecenia spowoduje wykonanie tych kroków:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

W tym przykładzie wypycha konfigurację DSC do węzła docelowego.
Konfiguracja DSC mogą być stosowane również za pomocą serwera ściągania DSC, jeśli jest dostępny.

Zobacz [Konfigurowanie klienta ściągania DSC](pullClient.md) Aby uzyskać więcej informacji na temat stosowania konfiguracji DSC przy użyciu serwera ściągania DSC.

## <a name="credential-encryption-module-example"></a>Przykład modułu szyfrowania poświadczeń

Oto pełny przykład, który zawiera wszystkie te kroki, a także polecenia cmdlet pomocnika, która eksportuje i kopiuje je kluczy publicznych:

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
