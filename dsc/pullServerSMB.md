---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Konfigurowanie serwera ściągania SMB platformy DSC
ms.openlocfilehash: e9228c050d6f496e30e94404a564ed2e425a5412
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Konfigurowanie serwera ściągania SMB platformy DSC

>Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) serwera ściągania jest komputer obsługujący udziałów plików SMB, które udostępnia pliki konfiguracji DSC i zasoby DSC węzły docelowe podczas tych węzłów, poproś o ich.

Do korzystania z serwera ściągania SMB dla DSC, konieczne będzie:
- Konfigurowanie udziału plików SMB na serwerze programu PowerShell w wersji 4.0 lub nowszej
- Konfiguracja klienta programu PowerShell w wersji 4.0 lub nowszej ściąganie danych z tego udziału SMB

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Tworzenie udziału plików SMB za pomocą zasobów xSmbShare

Istnieje wiele sposobów, aby skonfigurować udział plików SMB, ale Zobaczmy, jak to zrobić przy użyciu usługi Konfiguracja DSC.

### <a name="install-the-xsmbshare-resource"></a>Instalowanie zasobów xSmbShare

Wywołanie [instalacji modułu](https://technet.microsoft.com/library/dn807162.aspx) polecenia cmdlet, aby zainstalować **xSmbShare** modułu.
>**Uwaga**: **instalacji modułu** znajduje się w **PowerShellGet** moduł, który jest dostępny w programie PowerShell 5.0. Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [PackageManagement moduły programu PowerShell w wersji zapoznawczej](https://www.microsoft.com/en-us/download/details.aspx?id=49186). **XSmbShare** zawiera zasób DSC **xSmbShare**, które mogą służyć do utworzenia udziału plików SMB.

### <a name="create-the-directory-and-file-share"></a>Tworzenie udziału plików i katalogów

Używa następującej konfiguracji [pliku](fileResource.md) zasobu do utworzenia katalogu dla udziału i **xSmbShare** zasobów, aby skonfigurować udział SMB:

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare

    Node localhost {

        File CreateFolder {

            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

    }

}
```

Konfiguracja tworzy katalog `C:\DscSmbShare` Jeśli już nie istnieje, a następnie używa tego katalogu jako udziału plików SMB. **FullAccess** należy nadać z żadnym kontem, które należy zapisać lub usunięcie z udziału plików i **dostęp do odczytu** należy przyznać węzły klienta z udziału (jest to ponieważ pobierające konfiguracje i/lub zasobów DSC DSC działa jako konto system domyślnie, komputer musi mieć dostęp do udziału).


### <a name="give-file-system-access-to-the-pull-client"></a>Udzielić dostępu do systemu plików do klienta ściągania

Nadanie **dostęp do odczytu** klientowi węzeł umożliwia tym węźle, aby uzyskać dostępu do udziału SMB, ale nie do plików lub folderów w tym udostępnianie. Należy jawnie udzielić klienta węzłów dostępu do folderu udostępnionego SMB i podfoldery. Firma Microsoft można to zrobić z DSC przez dodawanie przy użyciu **cNtfsPermissionEntry** zasób, który jest zawarty w [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modułu. Dodaje następującą konfigurację **cNtfsPermissionEntry** bloku, która udziela dostępu ReadAndExecute do ściągania klienta:

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost {

        File CreateFolder {

            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

        cNtfsPermissionEntry PermissionSet1 {

        Ensure = 'Present'
        Path = 'C:\DSCSMB'
        Principal = 'myDomain\Contoso-Server$'
        AccessControlInformation = @(
            cNtfsAccessControlInformation
            {
                AccessControlType = 'Allow'
                FileSystemRights = 'ReadAndExecute'
                Inheritance = 'ThisFolderSubfoldersAndFiles'
                NoPropagateInherit = $false
            }
        )
        DependsOn = '[File]CreateFolder'

        }


    }

}
```

## <a name="placing-configurations-and-resources"></a>Wprowadzenie do konfiguracji i zasobów

Zapisz pliki MOF konfiguracji i/lub DSC zasoby, które mają węzłów klienta może go umieścić w folderze udziału SMB.

Musi mieć nazwę pliku MOF wszystkie konfiguracji _ConfigurationID_MOF, gdzie _ConfigurationID_ jest wartością **ConfigurationID** właściwości LCM węzeł docelowy. Aby uzyskać więcej informacji o konfigurowaniu klientów ściągania, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji](pullClientConfigID.md).

>**Uwaga:** identyfikatorów konfiguracji należy użyć, jeśli używasz serwera ściągania SMB. Nazwy konfiguracji nie są obsługiwane dla protokołu SMB.

Każdy moduł zasobu musi być spakowane i o nazwie zgodnie z następującego wzorca `{Module Name}_{Module Version}.zip`. Na przykład moduł o nazwie xWebAdminstration z wersją modułu 3.1.2.0 będą miały postać "xWebAdministration_3.2.1.0.zip". Każda wersja programu modułu muszą być zawarte w pliku zip pojedynczego. Ponieważ istnieje tylko jednej wersji zasobów w każdym pliku zip formatu modułu dodane w programie WMF 5.0 z obsługę wielu wersji modułu w jednym katalogu, nie jest obsługiwana. Oznacza to, czy przed grupowanie DSC modułów zasobów do użycia z serwera ściągania, należy wprowadzić niewielkie zmiany w strukturze katalogu. Domyślny format modułów zawierających DSC zasobów w programie WMF 5.0 "{modułu Folder}\{wersji modułu} \DscResources\{Folder zasobów DSC}\'. Przed pakowania dla serwera ściągania po prostu usuń **{wersji modułu}** folderu, tak aby stał się ścieżka "{modułu Folder} \DscResources\{Folder zasobów DSC}\'. Dzięki tej zmianie folderu zip, zgodnie z powyższym opisem i umieścić w folderze udziału SMB te pliki zip.

## <a name="creating-the-mof-checksum"></a>Tworzenie sumy kontrolnej MOF
Plik MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w docelowym węźle można sprawdzić poprawność konfiguracji.
Aby utworzyć sumy kontrolnej, należy wywołać [DSCCheckSum nowy](https://technet.microsoft.com/en-us/library/dn521622.aspx) polecenia cmdlet. Polecenie cmdlet przyjmuje **ścieżki** parametr, który określa folder, w którym znajduje się konfiguracji MOF. Polecenie cmdlet tworzy plik sumy kontrolnej o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.
Jeśli istnieje więcej niż jedna konfiguracja pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.

Plik sumy kontrolnej musi znajdować się w tym samym katalogu co plik MOF konfiguracji (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` domyślnie), i mieć taką samą nazwę `.checksum` dodanym rozszerzeniem.

>**Uwaga**: w przypadku zmiany pliku MOF konfiguracji w dowolny sposób, należy również ponownie utworzyć plik sumy kontrolnej.

## <a name="setting-up-a-pull-client-for-smb"></a>Konfigurowanie klienta ściągania dla protokołu SMB

Aby skonfigurować klienta, który pobiera konfiguracje i/lub zasobów z udziału SMB, należy skonfigurować klienta lokalnego Configuration Manager (LCM) z **ConfigurationRepositoryShare** i **ResourceRepositoryShare** bloków określ udział, z którego ma zostać ściągania konfiguracje i zasobów usługi Konfiguracja DSC.

Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji](pullClientConfigID.md).

>**Uwaga:** dla uproszczenia, w tym przykładzie użyto **PSDscAllowPlainTextPassword** umożliwia przekazywanie hasła w postaci zwykłego tekstu do **poświadczeń** parametru. Aby dowiedzieć się, jak bardziej bezpieczny sposób przekazywania poświadczeń, zobacz [opcji poświadczeń w danych konfiguracji](configDataCredentials.md).

>**Uwaga:** należy określić **ConfigurationID** w **ustawienia** bloku metakonfigurację na serwerze ściągania SMB, nawet jeśli są tylko ściąganie zasobów.

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{

    AllNodes = @(

        @{

            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves

            NodeName="localhost"

            PSDscAllowPlainTextPassword = $true

        })



}
```

## <a name="acknowledgements"></a>Podziękowania

Specjalne dzięki użyciu następujące:

- Jan F. Robbins, którego ogłoszenia na za pomocą protokołu SMB dla DSC pomogła informuje zawartości w tym temacie. Jest jego blog [Robbins F Jan](http://mikefrobbins.com/).
- Nikalaichyk serge, który utworzone **cNtfsAccessControl** modułu. Źródło dla tego modułu jest w https://github.com/SNikalaichyk/cNtfsAccessControl.

## <a name="see-also"></a>Zobacz też
- [Omówienie stanu konfiguracji żądanego programu Windows PowerShell](overview.md)
- [Realizacja konfiguracji](enactingConfigurations.md)
- [Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji](pullClientConfigID.md)