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
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="f6e54-103">Konfigurowanie serwera ściągania SMB platformy DSC</span><span class="sxs-lookup"><span data-stu-id="f6e54-103">Setting up a DSC SMB pull server</span></span>

><span data-ttu-id="f6e54-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f6e54-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f6e54-105">DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) serwera ściągania jest komputer obsługujący udziałów plików SMB, które udostępnia pliki konfiguracji DSC i zasoby DSC węzły docelowe podczas tych węzłów, poproś o ich.</span><span class="sxs-lookup"><span data-stu-id="f6e54-105">A DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="f6e54-106">Do korzystania z serwera ściągania SMB dla DSC, konieczne będzie:</span><span class="sxs-lookup"><span data-stu-id="f6e54-106">To use an SMB pull server for DSC, you have to:</span></span>
- <span data-ttu-id="f6e54-107">Konfigurowanie udziału plików SMB na serwerze programu PowerShell w wersji 4.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="f6e54-107">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="f6e54-108">Konfiguracja klienta programu PowerShell w wersji 4.0 lub nowszej ściąganie danych z tego udziału SMB</span><span class="sxs-lookup"><span data-stu-id="f6e54-108">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="f6e54-109">Tworzenie udziału plików SMB za pomocą zasobów xSmbShare</span><span class="sxs-lookup"><span data-stu-id="f6e54-109">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="f6e54-110">Istnieje wiele sposobów, aby skonfigurować udział plików SMB, ale Zobaczmy, jak to zrobić przy użyciu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="f6e54-110">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="f6e54-111">Instalowanie zasobów xSmbShare</span><span class="sxs-lookup"><span data-stu-id="f6e54-111">Install the xSmbShare resource</span></span>

<span data-ttu-id="f6e54-112">Wywołanie [instalacji modułu](https://technet.microsoft.com/library/dn807162.aspx) polecenia cmdlet, aby zainstalować **xSmbShare** modułu.</span><span class="sxs-lookup"><span data-stu-id="f6e54-112">Call the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xSmbShare** module.</span></span>
><span data-ttu-id="f6e54-113">**Uwaga**: **instalacji modułu** znajduje się w **PowerShellGet** moduł, który jest dostępny w programie PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="f6e54-113">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="f6e54-114">Możesz pobrać **PowerShellGet** modułu PowerShell 3.0 i 4.0 w [PackageManagement moduły programu PowerShell w wersji zapoznawczej](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="f6e54-114">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> <span data-ttu-id="f6e54-115">**XSmbShare** zawiera zasób DSC **xSmbShare**, które mogą służyć do utworzenia udziału plików SMB.</span><span class="sxs-lookup"><span data-stu-id="f6e54-115">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="f6e54-116">Tworzenie udziału plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="f6e54-116">Create the directory and file share</span></span>

<span data-ttu-id="f6e54-117">Używa następującej konfiguracji [pliku](fileResource.md) zasobu do utworzenia katalogu dla udziału i **xSmbShare** zasobów, aby skonfigurować udział SMB:</span><span class="sxs-lookup"><span data-stu-id="f6e54-117">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="f6e54-118">Konfiguracja tworzy katalog `C:\DscSmbShare` Jeśli już nie istnieje, a następnie używa tego katalogu jako udziału plików SMB.</span><span class="sxs-lookup"><span data-stu-id="f6e54-118">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="f6e54-119">**FullAccess** należy nadać z żadnym kontem, które należy zapisać lub usunięcie z udziału plików i **dostęp do odczytu** należy przyznać węzły klienta z udziału (jest to ponieważ pobierające konfiguracje i/lub zasobów DSC DSC działa jako konto system domyślnie, komputer musi mieć dostęp do udziału).</span><span class="sxs-lookup"><span data-stu-id="f6e54-119">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>


### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="f6e54-120">Udzielić dostępu do systemu plików do klienta ściągania</span><span class="sxs-lookup"><span data-stu-id="f6e54-120">Give file system access to the pull client</span></span>

<span data-ttu-id="f6e54-121">Nadanie **dostęp do odczytu** klientowi węzeł umożliwia tym węźle, aby uzyskać dostępu do udziału SMB, ale nie do plików lub folderów w tym udostępnianie.</span><span class="sxs-lookup"><span data-stu-id="f6e54-121">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="f6e54-122">Należy jawnie udzielić klienta węzłów dostępu do folderu udostępnionego SMB i podfoldery.</span><span class="sxs-lookup"><span data-stu-id="f6e54-122">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="f6e54-123">Firma Microsoft można to zrobić z DSC przez dodawanie przy użyciu **cNtfsPermissionEntry** zasób, który jest zawarty w [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modułu.</span><span class="sxs-lookup"><span data-stu-id="f6e54-123">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="f6e54-124">Dodaje następującą konfigurację **cNtfsPermissionEntry** bloku, która udziela dostępu ReadAndExecute do ściągania klienta:</span><span class="sxs-lookup"><span data-stu-id="f6e54-124">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="f6e54-125">Wprowadzenie do konfiguracji i zasobów</span><span class="sxs-lookup"><span data-stu-id="f6e54-125">Placing configurations and resources</span></span>

<span data-ttu-id="f6e54-126">Zapisz pliki MOF konfiguracji i/lub DSC zasoby, które mają węzłów klienta może go umieścić w folderze udziału SMB.</span><span class="sxs-lookup"><span data-stu-id="f6e54-126">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="f6e54-127">Musi mieć nazwę pliku MOF wszystkie konfiguracji _ConfigurationID_MOF, gdzie _ConfigurationID_ jest wartością **ConfigurationID** właściwości LCM węzeł docelowy.</span><span class="sxs-lookup"><span data-stu-id="f6e54-127">Any configuration MOF file must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="f6e54-128">Aby uzyskać więcej informacji o konfigurowaniu klientów ściągania, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="f6e54-128">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="f6e54-129">**Uwaga:** identyfikatorów konfiguracji należy użyć, jeśli używasz serwera ściągania SMB.</span><span class="sxs-lookup"><span data-stu-id="f6e54-129">**Note:** You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="f6e54-130">Nazwy konfiguracji nie są obsługiwane dla protokołu SMB.</span><span class="sxs-lookup"><span data-stu-id="f6e54-130">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="f6e54-131">Każdy moduł zasobu musi być spakowane i o nazwie zgodnie z następującego wzorca `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="f6e54-131">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="f6e54-132">Na przykład moduł o nazwie xWebAdminstration z wersją modułu 3.1.2.0 będą miały postać "xWebAdministration_3.2.1.0.zip".</span><span class="sxs-lookup"><span data-stu-id="f6e54-132">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="f6e54-133">Każda wersja programu modułu muszą być zawarte w pliku zip pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="f6e54-133">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="f6e54-134">Ponieważ istnieje tylko jednej wersji zasobów w każdym pliku zip formatu modułu dodane w programie WMF 5.0 z obsługę wielu wersji modułu w jednym katalogu, nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="f6e54-134">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="f6e54-135">Oznacza to, czy przed grupowanie DSC modułów zasobów do użycia z serwera ściągania, należy wprowadzić niewielkie zmiany w strukturze katalogu.</span><span class="sxs-lookup"><span data-stu-id="f6e54-135">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="f6e54-136">Domyślny format modułów zawierających DSC zasobów w programie WMF 5.0 "{modułu Folder}\{wersji modułu} \DscResources\{Folder zasobów DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="f6e54-136">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="f6e54-137">Przed pakowania dla serwera ściągania po prostu usuń **{wersji modułu}** folderu, tak aby stał się ścieżka "{modułu Folder} \DscResources\{Folder zasobów DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="f6e54-137">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="f6e54-138">Dzięki tej zmianie folderu zip, zgodnie z powyższym opisem i umieścić w folderze udziału SMB te pliki zip.</span><span class="sxs-lookup"><span data-stu-id="f6e54-138">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="f6e54-139">Tworzenie sumy kontrolnej MOF</span><span class="sxs-lookup"><span data-stu-id="f6e54-139">Creating the MOF checksum</span></span>
<span data-ttu-id="f6e54-140">Plik MOF konfiguracji musi łączyć się z plikiem sumy kontrolnej, aby LCM w docelowym węźle można sprawdzić poprawność konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f6e54-140">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="f6e54-141">Aby utworzyć sumy kontrolnej, należy wywołać [DSCCheckSum nowy](https://technet.microsoft.com/en-us/library/dn521622.aspx) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6e54-141">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="f6e54-142">Polecenie cmdlet przyjmuje **ścieżki** parametr, który określa folder, w którym znajduje się konfiguracji MOF.</span><span class="sxs-lookup"><span data-stu-id="f6e54-142">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="f6e54-143">Polecenie cmdlet tworzy plik sumy kontrolnej o nazwie `ConfigurationMOFName.mof.checksum`, gdzie `ConfigurationMOFName` to nazwa pliku mof konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f6e54-143">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="f6e54-144">Jeśli istnieje więcej niż jedna konfiguracja pliki MOF we wskazanym folderze, suma kontrolna jest tworzony dla każdej konfiguracji w folderze.</span><span class="sxs-lookup"><span data-stu-id="f6e54-144">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="f6e54-145">Plik sumy kontrolnej musi znajdować się w tym samym katalogu co plik MOF konfiguracji (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` domyślnie), i mieć taką samą nazwę `.checksum` dodanym rozszerzeniem.</span><span class="sxs-lookup"><span data-stu-id="f6e54-145">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

><span data-ttu-id="f6e54-146">**Uwaga**: w przypadku zmiany pliku MOF konfiguracji w dowolny sposób, należy również ponownie utworzyć plik sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="f6e54-146">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="f6e54-147">Konfigurowanie klienta ściągania dla protokołu SMB</span><span class="sxs-lookup"><span data-stu-id="f6e54-147">Setting up a pull client for SMB</span></span>

<span data-ttu-id="f6e54-148">Aby skonfigurować klienta, który pobiera konfiguracje i/lub zasobów z udziału SMB, należy skonfigurować klienta lokalnego Configuration Manager (LCM) z **ConfigurationRepositoryShare** i **ResourceRepositoryShare** bloków określ udział, z którego ma zostać ściągania konfiguracje i zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="f6e54-148">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="f6e54-149">Aby uzyskać więcej informacji o konfigurowaniu LCM, zobacz [instalacji klienta ściągania za pomocą Identyfikatora konfiguracji](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="f6e54-149">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="f6e54-150">**Uwaga:** dla uproszczenia, w tym przykładzie użyto **PSDscAllowPlainTextPassword** umożliwia przekazywanie hasła w postaci zwykłego tekstu do **poświadczeń** parametru.</span><span class="sxs-lookup"><span data-stu-id="f6e54-150">**Note:** For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="f6e54-151">Aby dowiedzieć się, jak bardziej bezpieczny sposób przekazywania poświadczeń, zobacz [opcji poświadczeń w danych konfiguracji](configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="f6e54-151">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>

><span data-ttu-id="f6e54-152">**Uwaga:** należy określić **ConfigurationID** w **ustawienia** bloku metakonfigurację na serwerze ściągania SMB, nawet jeśli są tylko ściąganie zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e54-152">**Note:** You must specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="f6e54-153">Podziękowania</span><span class="sxs-lookup"><span data-stu-id="f6e54-153">Acknowledgements</span></span>

<span data-ttu-id="f6e54-154">Specjalne dzięki użyciu następujące:</span><span class="sxs-lookup"><span data-stu-id="f6e54-154">Special thanks to the following:</span></span>

- <span data-ttu-id="f6e54-155">Jan F. Robbins, którego ogłoszenia na za pomocą protokołu SMB dla DSC pomogła informuje zawartości w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f6e54-155">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="f6e54-156">Jest jego blog [Robbins F Jan](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="f6e54-156">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="f6e54-157">Nikalaichyk serge, który utworzone **cNtfsAccessControl** modułu.</span><span class="sxs-lookup"><span data-stu-id="f6e54-157">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="f6e54-158">Źródło dla tego modułu jest w https://github.com/SNikalaichyk/cNtfsAccessControl.</span><span class="sxs-lookup"><span data-stu-id="f6e54-158">The source for this module is at https://github.com/SNikalaichyk/cNtfsAccessControl.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6e54-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6e54-159">See also</span></span>
- [<span data-ttu-id="f6e54-160">Omówienie stanu konfiguracji żądanego programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6e54-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="f6e54-161">Realizacja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f6e54-161">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="f6e54-162">Konfigurowanie klienta ściągania przy użyciu identyfikatora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f6e54-162">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)