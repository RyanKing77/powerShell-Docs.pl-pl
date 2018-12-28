---
ms.date: 04/11/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie serwera ściągania SMB platformy DSC
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404729"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Konfigurowanie serwera ściągania SMB platformy DSC

Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno. Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).

DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) serwera ściągania jest komputer obsługujący udziałów plików SMB, które udostępnić pliki konfiguracji DSC i zasobów DSC węzły docelowe w przypadku tych węzłów, poproś o nich.

Aby użyć serwera ściągania SMB dla DSC, należy:

- Konfigurowanie udziału plików SMB na serwerze z programem PowerShell 4.0 lub nowszy
- Konfigurowanie klienta programu PowerShell w wersji 4.0 lub nowszej na ściąganie z udziału SMB

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Tworzenie udziału plików SMB przy użyciu zasobów xSmbShare

Istnieje kilka sposobów, aby skonfigurować udział plików SMB, ale Oto jak to zrobić za pomocą DSC.

### <a name="install-the-xsmbshare-resource"></a>Instalowanie zasobów xSmbShare

Wywołaj [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby zainstalować **xSmbShare** modułu.

> [!NOTE]
> `Install-Module` znajduje się w **PowerShellGet** moduł, który znajduje się w programie PowerShell 5.0. Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [Podgląd modułów programu PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
> **XSmbShare** zawiera zasób DSC **xSmbShare**, który może służyć do tworzenia udziału plików SMB.

### <a name="create-the-directory-and-file-share"></a>Tworzenie udziału plików i katalogów

Używa następującej konfiguracji **pliku** zasobu do utworzenia katalogu dla udziału i **xSmbShare** zasób, aby skonfigurować udział SMB:

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
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

Konfiguracja tworzy katalog `C:\DscSmbShare`, jeśli jeszcze nie istnieje, a następnie używa tego katalogu jako udział plików SMB. **FullAccess** należy zwrócić na konto, które trzeba zapisać lub usunąć z udziału plików. **Dostęp do odczytu** należy przyznać wszystkie węzły klienta, które pobierają konfiguracji i zasobów DSC z udziału.

> [!NOTE]
> Za pomocą konta system domyślnie działa DSC, więc sam komputer musi mieć dostęp do udziału.

### <a name="give-file-system-access-to-the-pull-client"></a>Oferowanie dostępu do systemu plików klienta ściągania

Zapewniając **dostęp do odczytu** klienta węzeł zezwala na tym węźle, aby uzyskać dostęp do udziału SMB, ale nie do plików lub folderów w ramach którego są współdzielone. Należy jawnie udzielić klienta węzłów dostęp do folderu w udziale SMB i podfoldery. Możemy to zrobić za pomocą DSC, dodając za pomocą **cNtfsPermissionEntry** zasób, który jest zawarty w [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modułu. Dodaje następującą konfigurację **cNtfsPermissionEntry** bloku, która udziela dostępu ReadAndExecute klientowi ściągnięcia:

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
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

Zapisz pliki MOF konfiguracji i/lub zasobów DSC, które chcesz, aby węzły klienta w celu ściągania w folderze udziału SMB.

Musi mieć nazwę dowolnego pliku MOF konfiguracji *ConfigurationID*MOF, gdzie *ConfigurationID* jest wartością **ConfigurationID** właściwość LCM węzeł docelowy. Aby uzyskać więcej informacji o konfigurowaniu ściągnięcia klientów, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji](pullClientConfigID.md).

> [!NOTE]
> Jeśli używasz serwera ściągania SMB, należy użyć identyfikatorów konfiguracji. Nazwy konfiguracji nie są obsługiwane dla protokołu SMB.

Każdy moduł zasobów musi być spakowane i nazwanych zgodnie z następującym wzorcem `{Module Name}_{Module Version}.zip`. Na przykład moduł o nazwie xWebAdminstration przy użyciu wersji modułu 3.1.2.0 będzie można o nazwie "xWebAdministration_3.2.1.0.zip". Każda wersja modułu musi być zawarty w pliku zip jednego. Różne wersje modułu w pliku zip nie są obsługiwane. Przed pakowaniu modułów zasoby DSC do użytku z serwera ściągania, należy wprowadzić niewielkie zmiany do struktury katalogu.

Domyślny format modułów zawierających zasobów DSC w programie WMF 5.0 jest `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.

Przed pakowania dla serwera ściągania po prostu usunąć `{Module version}` folderu, tak aby stał się ścieżkę `{Module Folder}\DscResources\{DSC Resource Folder}\`. Dzięki tej zmianie folderu zip, zgodnie z powyższym opisem i umieścić te pliki zip w folderze udziału SMB.

## <a name="creating-the-mof-checksum"></a>Tworzenie sumy kontrolnej pliku MOF

Pliku MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w węźle docelowym można zweryfikować jej konfigurację.
Aby utworzyć sumy kontrolnej, wywołaj [New DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) polecenia cmdlet. Polecenie cmdlet pobiera `Path` parametr, który określa folder, w którym znajduje się plik MOF konfiguracji. Polecenie cmdlet tworzy sumy kontrolnej pliku o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.
Jeśli istnieje więcej niż jedną konfigurację pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.

Plik sumy kontrolnej musi znajdować się w tym samym katalogu co plik MOF konfiguracji (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` domyślnie), i ma taką samą nazwę `.checksum` dodanym rozszerzeniem.

> [!NOTE]
> Jeśli zmienisz pliku MOF konfiguracji w jakikolwiek sposób, należy odtworzyć pliku sumy kontrolnej.

## <a name="setting-up-a-pull-client-for-smb"></a>Konfigurowanie klienta ściągania dla protokołu SMB

Aby skonfigurować klienta, który pobiera dane konfiguracji i/lub zasobów z udziału SMB, należy skonfigurować klienta lokalnego Configuration Manager (LCM) przy użyciu **ConfigurationRepositoryShare** i **ResourceRepositoryShare** bloków, które określają udziału, z którego ma zostać ściągania konfiguracji i zasobów DSC.

Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji](pullClientConfigID.md).

> [!NOTE]
> Dla uproszczenia w tym przykładzie użyto **PSDscAllowPlainTextPassword** umożliwia przekazanie przechowywała hasła w celu **poświadczeń** parametru. Aby dowiedzieć się, jak bardziej bezpieczne przekazywanie poświadczeń, zobacz [opcje poświadczeń w danych konfiguracji](../configurations/configDataCredentials.md).
>
> Możesz **musi** określ **ConfigurationID** w **ustawienia** bloku metaconfiguration dla serwera ściągania SMB, nawet jeśli tylko ściągają zasobów.

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

Specjalne dzięki następujących osób:

- Mike F. Robbins, którego wpisów dotyczących przy użyciu protokołu SMB dla DSC pomogła informuje zawartości w tym temacie. Jego blog znajduje się na [Mike F Robbins](http://mikefrobbins.com/).
- Nikalaichyk serge, kto utworzone **cNtfsAccessControl** modułu. Źródło dla tego modułu wynosi [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Zobacz też

[Program Windows PowerShell Desired State Configuration — omówienie](../overview/overview.md)

[Realizacja konfiguracji](enactingConfigurations.md)

[Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji](pullClientConfigID.md)
