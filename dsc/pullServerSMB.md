---
ms.date: 04/11/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie serwera ściągania SMB platformy DSC
ms.openlocfilehash: 1eac6c51aeca3ed573ba8fa27188103436004920
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892869"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="0808d-103">Konfigurowanie serwera ściągania SMB platformy DSC</span><span class="sxs-lookup"><span data-stu-id="0808d-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="0808d-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0808d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0808d-105">Serwera ściągania (funkcja Windows *usługi DSC*) jest obsługiwanych składników systemu Windows Server jednak nie jest planowane oferują nowe funkcje lub możliwości osobno.</span><span class="sxs-lookup"><span data-stu-id="0808d-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="0808d-106">Zaleca się rozpocząć przechodzenie zarządzanych klientom [usługi Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (w tym funkcje poza serwera ściągania w systemie Windows Server) lub jeden z członków społeczności na liście [tutaj](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="0808d-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="0808d-107">DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) serwera ściągania jest komputer obsługujący udziałów plików SMB, które udostępnić pliki konfiguracji DSC i zasobów DSC węzły docelowe w przypadku tych węzłów, poproś o nich.</span><span class="sxs-lookup"><span data-stu-id="0808d-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="0808d-108">Aby użyć serwera ściągania SMB dla DSC, należy:</span><span class="sxs-lookup"><span data-stu-id="0808d-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="0808d-109">Konfigurowanie udziału plików SMB na serwerze z programem PowerShell 4.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="0808d-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="0808d-110">Konfigurowanie klienta programu PowerShell w wersji 4.0 lub nowszej na ściąganie z udziału SMB</span><span class="sxs-lookup"><span data-stu-id="0808d-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="0808d-111">Tworzenie udziału plików SMB przy użyciu zasobów xSmbShare</span><span class="sxs-lookup"><span data-stu-id="0808d-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="0808d-112">Istnieje kilka sposobów, aby skonfigurować udział plików SMB, ale Oto jak to zrobić za pomocą DSC.</span><span class="sxs-lookup"><span data-stu-id="0808d-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="0808d-113">Instalowanie zasobów xSmbShare</span><span class="sxs-lookup"><span data-stu-id="0808d-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="0808d-114">Wywołaj [Install-Module](/powershell/module/PowershellGet/Install-Module) polecenia cmdlet, aby zainstalować **xSmbShare** modułu.</span><span class="sxs-lookup"><span data-stu-id="0808d-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="0808d-115">`Install-Module` znajduje się w **PowerShellGet** moduł, który znajduje się w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="0808d-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="0808d-116">Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [Podgląd modułów programu PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="0808d-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="0808d-117">**XSmbShare** zawiera zasób DSC **xSmbShare**, który może służyć do tworzenia udziału plików SMB.</span><span class="sxs-lookup"><span data-stu-id="0808d-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="0808d-118">Tworzenie udziału plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="0808d-118">Create the directory and file share</span></span>

<span data-ttu-id="0808d-119">Używa następującej konfiguracji [pliku](fileResource.md) zasobu do utworzenia katalogu dla udziału i **xSmbShare** zasób, aby skonfigurować udział SMB:</span><span class="sxs-lookup"><span data-stu-id="0808d-119">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="0808d-120">Konfiguracja tworzy katalog `C:\DscSmbShare` Jeżeli tak nie jest już istnieje, a następnie używa tego katalogu jako udział plików SMB.</span><span class="sxs-lookup"><span data-stu-id="0808d-120">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="0808d-121">**FullAccess** należy zwrócić na konto, które trzeba zapisać lub usunąć z udziału plików i **dostęp do odczytu** muszą mieć do żadnego węzła klienta, który uzyskiwanie udziału (jest to ponieważ konfiguracji i zasobów DSC DSC działa jako konto systemowe domyślnie, więc sam komputer musi mieć dostęp do udziału).</span><span class="sxs-lookup"><span data-stu-id="0808d-121">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="0808d-122">Oferowanie dostępu do systemu plików klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="0808d-122">Give file system access to the pull client</span></span>

<span data-ttu-id="0808d-123">Zapewniając **dostęp do odczytu** klienta węzeł zezwala na tym węźle, aby uzyskać dostęp do udziału SMB, ale nie do plików lub folderów w ramach którego są współdzielone.</span><span class="sxs-lookup"><span data-stu-id="0808d-123">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="0808d-124">Należy jawnie udzielić klienta węzłów dostęp do folderu w udziale SMB i podfoldery.</span><span class="sxs-lookup"><span data-stu-id="0808d-124">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="0808d-125">Możemy to zrobić za pomocą DSC, dodając za pomocą **cNtfsPermissionEntry** zasób, który jest zawarty w [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modułu.</span><span class="sxs-lookup"><span data-stu-id="0808d-125">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="0808d-126">Dodaje następującą konfigurację **cNtfsPermissionEntry** bloku, która udziela dostępu ReadAndExecute klientowi ściągnięcia:</span><span class="sxs-lookup"><span data-stu-id="0808d-126">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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
            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="0808d-127">Wprowadzenie do konfiguracji i zasobów</span><span class="sxs-lookup"><span data-stu-id="0808d-127">Placing configurations and resources</span></span>

<span data-ttu-id="0808d-128">Zapisz pliki MOF konfiguracji i/lub zasobów DSC, które chcesz, aby węzły klienta w celu ściągania w folderze udziału SMB.</span><span class="sxs-lookup"><span data-stu-id="0808d-128">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="0808d-129">Musi mieć nazwę dowolnego pliku MOF konfiguracji *ConfigurationID*MOF, gdzie *ConfigurationID* jest wartością **ConfigurationID** właściwość LCM węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="0808d-129">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="0808d-130">Aby uzyskać więcej informacji o konfigurowaniu ściągnięcia klientów, zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="0808d-130">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0808d-131">Jeśli używasz serwera ściągania SMB, należy użyć identyfikatorów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0808d-131">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="0808d-132">Nazwy konfiguracji nie są obsługiwane dla protokołu SMB.</span><span class="sxs-lookup"><span data-stu-id="0808d-132">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="0808d-133">Każdy moduł zasobów musi być spakowane i o nazwie, zgodnie z następującym wzorcem `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="0808d-133">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="0808d-134">Na przykład moduł o nazwie xWebAdminstration przy użyciu wersji modułu 3.1.2.0 będzie można o nazwie "xWebAdministration_3.2.1.0.zip".</span><span class="sxs-lookup"><span data-stu-id="0808d-134">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="0808d-135">Każda wersja modułu musi być zawarty w pliku zip jednego.</span><span class="sxs-lookup"><span data-stu-id="0808d-135">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="0808d-136">Ponieważ ma tylko jedną wersję zasobu w każdym pliku zip, dodać formatu modułu w programie WMF 5.0 z obsługę wielu wersji modułu w pojedynczym katalogu nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0808d-136">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="0808d-137">Oznacza to, że przed pakowaniu modułów zasoby DSC do użytku z serwera ściągania należy wprowadź niewielką zmianę do struktury katalogu.</span><span class="sxs-lookup"><span data-stu-id="0808d-137">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="0808d-138">Domyślny format modułów zawierających zasobów DSC w programie WMF 5.0 jest `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="0808d-138">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="0808d-139">Przed pakowania dla serwera ściągania po prostu usunąć `{Module version}` folderu, tak aby stał się ścieżkę `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="0808d-139">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="0808d-140">Dzięki tej zmianie folderu zip, zgodnie z powyższym opisem i umieścić te pliki zip w folderze udziału SMB.</span><span class="sxs-lookup"><span data-stu-id="0808d-140">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="0808d-141">Tworzenie sumy kontrolnej pliku MOF</span><span class="sxs-lookup"><span data-stu-id="0808d-141">Creating the MOF checksum</span></span>

<span data-ttu-id="0808d-142">Pliku MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w węźle docelowym można zweryfikować jej konfigurację.</span><span class="sxs-lookup"><span data-stu-id="0808d-142">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="0808d-143">Aby utworzyć sumy kontrolnej, wywołaj [New DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0808d-143">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="0808d-144">Polecenie cmdlet pobiera `Path` parametr, który określa folder, w którym znajduje się plik MOF konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0808d-144">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="0808d-145">Polecenie cmdlet tworzy sumy kontrolnej pliku o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0808d-145">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="0808d-146">Jeśli istnieje więcej niż jedną konfigurację pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.</span><span class="sxs-lookup"><span data-stu-id="0808d-146">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="0808d-147">Plik sumy kontrolnej musi znajdować się w tym samym katalogu co plik MOF konfiguracji (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` domyślnie), i ma taką samą nazwę `.checksum` dodanym rozszerzeniem.</span><span class="sxs-lookup"><span data-stu-id="0808d-147">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="0808d-148">Jeśli zmienisz pliku MOF konfiguracji w jakikolwiek sposób, należy odtworzyć pliku sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="0808d-148">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="0808d-149">Konfigurowanie klienta ściągania dla protokołu SMB</span><span class="sxs-lookup"><span data-stu-id="0808d-149">Setting up a pull client for SMB</span></span>

<span data-ttu-id="0808d-150">Aby skonfigurować klienta, który pobiera dane konfiguracji i/lub zasobów z udziału SMB, należy skonfigurować klienta lokalnego Configuration Manager (LCM) przy użyciu **ConfigurationRepositoryShare** i **ResourceRepositoryShare** bloków, które określają udziału, z którego ma zostać ściągania konfiguracji i zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="0808d-150">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="0808d-151">Aby uzyskać więcej informacji na temat Konfigurowanie programu LCM zobacz [Konfigurowanie klienta ściągania przy użyciu Identyfikatora konfiguracji](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="0808d-151">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0808d-152">Dla uproszczenia w tym przykładzie użyto **PSDscAllowPlainTextPassword** umożliwia przekazanie przechowywała hasła w celu **poświadczeń** parametru.</span><span class="sxs-lookup"><span data-stu-id="0808d-152">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="0808d-153">Aby dowiedzieć się, jak bardziej bezpieczne przekazywanie poświadczeń, zobacz [opcje poświadczeń w danych konfiguracji](configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="0808d-153">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>
>
> <span data-ttu-id="0808d-154">Możesz **musi** określ **ConfigurationID** w **ustawienia** bloku metaconfiguration dla serwera ściągania SMB, nawet jeśli tylko ściągają zasobów.</span><span class="sxs-lookup"><span data-stu-id="0808d-154">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="0808d-155">Podziękowania</span><span class="sxs-lookup"><span data-stu-id="0808d-155">Acknowledgements</span></span>

<span data-ttu-id="0808d-156">Specjalne dzięki gotowej do następujących:</span><span class="sxs-lookup"><span data-stu-id="0808d-156">Special thanks to the following:</span></span>

- <span data-ttu-id="0808d-157">Mike F. Robbins, którego wpisów dotyczących przy użyciu protokołu SMB dla DSC pomogła informuje zawartości w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="0808d-157">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="0808d-158">Jego blog znajduje się na [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="0808d-158">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="0808d-159">Nikalaichyk serge, kto utworzone **cNtfsAccessControl** modułu.</span><span class="sxs-lookup"><span data-stu-id="0808d-159">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="0808d-160">Źródło dla tego modułu wynosi [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="0808d-160">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="0808d-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0808d-161">See also</span></span>

[<span data-ttu-id="0808d-162">Program Windows PowerShell Desired State Configuration — omówienie</span><span class="sxs-lookup"><span data-stu-id="0808d-162">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)

[<span data-ttu-id="0808d-163">Realizacja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0808d-163">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="0808d-164">Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0808d-164">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)