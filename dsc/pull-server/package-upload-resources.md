---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Pakiet i przekazywanie zasobów do serwera ściągania
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404759"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="e2ab0-103">Pakiet i przekazywanie zasobów do serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="e2ab0-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="e2ab0-104">W poniższych sekcjach przyjęto założenie, że już zdefiniowano serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="e2ab0-105">Jeśli nie zdefiniowano z serwera ściągania, można użyć następujących przewodników:</span><span class="sxs-lookup"><span data-stu-id="e2ab0-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="e2ab0-106">Konfigurowanie serwera ściągania SMB DSC</span><span class="sxs-lookup"><span data-stu-id="e2ab0-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="e2ab0-107">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="e2ab0-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="e2ab0-108">Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="e2ab0-109">W tym artykule pokazano sposób przekazywania zasobów, dzięki czemu są one dostępne do pobrania, a następnie skonfigurować klientów, aby pobrać zasoby automatycznie.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="e2ab0-110">Gdy węzeł odbiera przypisanej konfiguracji, za pośrednictwem **ściągnięcia** lub **wypychania** (v5), automatycznie pobiera wszystkie zasoby wymagane przez tę konfigurację w lokalizacji określonej w LCM.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="e2ab0-111">Pakiet zasobów modułów</span><span class="sxs-lookup"><span data-stu-id="e2ab0-111">Package Resource Modules</span></span>

<span data-ttu-id="e2ab0-112">Każdy zasób jest dostępny dla klienta pobrać muszą być przechowywane w pliku ".zip".</span><span class="sxs-lookup"><span data-stu-id="e2ab0-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="e2ab0-113">W poniższym przykładzie opisano kroki wymagane przy użyciu [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) zasobów.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="e2ab0-114">W przypadku wszystkich klientów przy użyciu programu PowerShell 4.0 będzie konieczne flaten strukturę folderów zasobów i Usuń wszystkie foldery wersji.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="e2ab0-115">Aby uzyskać więcej informacji, zobacz [wielu wersji zasobu](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="e2ab0-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="e2ab0-116">Można kompresować katalog zasobów przy użyciu dowolnego narzędzia, skryptu lub metoda, którego chcesz używać.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="e2ab0-117">W Windows, możesz *kliknij prawym przyciskiem myszy* w katalogu "xPSDesiredStateConfiguration" i wybierz pozycję "Wyślij", a następnie "Skompresowany Folder".</span><span class="sxs-lookup"><span data-stu-id="e2ab0-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Kliknij prawym przyciskiem myszy](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="e2ab0-119">Nazewnictwo archiwum zasobów</span><span class="sxs-lookup"><span data-stu-id="e2ab0-119">Naming the Resource Archive</span></span>

<span data-ttu-id="e2ab0-120">Archiwum zasobu musi mieć nazwę w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="e2ab0-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="e2ab0-121">W powyższym przykładzie "xPSDesiredStateConfiguration.zip" powinien być zmieniono nazwę "xPSDesiredStateConfiguration_8.4.4.0.zip".</span><span class="sxs-lookup"><span data-stu-id="e2ab0-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="e2ab0-122">Tworzenie sumy kontrolne</span><span class="sxs-lookup"><span data-stu-id="e2ab0-122">Create CheckSums</span></span>

<span data-ttu-id="e2ab0-123">Gdy moduł zasobów zostanie skompresowany i zmieniono jego nazwę, należy utworzyć **sumy kontrolnej**.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="e2ab0-124">**Sumy kontrolnej** jest używany przez LCM na kliencie, aby ustalić, czy zasób został zmieniony i muszą zostać pobrane ponownie.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="e2ab0-125">Możesz utworzyć **sumy kontrolnej** z [New DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) polecenia cmdlet, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="e2ab0-126">Żadne dane wyjściowe będą wyświetlane, ale powinien zostać wyświetlony "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span><span class="sxs-lookup"><span data-stu-id="e2ab0-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="e2ab0-127">Można również uruchomić `New-DSCCheckSum` względem katalogu plików, używając `-Path` parametru.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="e2ab0-128">Jeśli istnieje już sumy kontrolnej, aby wymusić można ponownie utworzyć za pomocą `-Force` parametru.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="e2ab0-129">Miejsce przechowywania zasobów archiwa</span><span class="sxs-lookup"><span data-stu-id="e2ab0-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="e2ab0-130">Na serwerze ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="e2ab0-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="e2ab0-131">Po skonfigurowaniu serwera ściągania HTTP, jak wyjaśniono w [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md), określ katalogi dla **ModulePath** i **ConfigurationPath** kluczy.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="e2ab0-132">**ConfigurationPath** klucz wskazuje, gdzie powinny być przechowywane pliki "MOF".</span><span class="sxs-lookup"><span data-stu-id="e2ab0-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="e2ab0-133">**ModulePath** wskazuje przechowywania wszystkich modułów zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="e2ab0-134">W udziale SMB</span><span class="sxs-lookup"><span data-stu-id="e2ab0-134">On an SMB Share</span></span>

<span data-ttu-id="e2ab0-135">Jeśli określono **ResourceRepositoryShare**, gdy Konfigurowanie klienta ściągania, przechowywane archiwa i sumy kontrolne w **Ścieżka_źródłowa** katalogu z **ResourceRepositoryShare** bloku.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="e2ab0-136">Jeśli określono tylko **ConfigurationRepositoryShare**, gdy Konfigurowanie klienta ściągania, przechowywane archiwa i sumy kontrolne w **Ścieżka_źródłowa** katalogu z  **ConfigurationRepositoryShare** bloku.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="e2ab0-137">Aktualizowanie zasobów</span><span class="sxs-lookup"><span data-stu-id="e2ab0-137">Updating resources</span></span>

<span data-ttu-id="e2ab0-138">Można wymusić węzeł, aby zaktualizować swoje zasoby, zmieniając numer wersji w nazwie archiwum lub tworząc nowe sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="e2ab0-139">Klienta ściągania będzie sprawdzać dostępność nowych wersji z wymaganych zasobów, a także zaktualizować sumy kontrolne, podczas jego LCM odświeżania.</span><span class="sxs-lookup"><span data-stu-id="e2ab0-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2ab0-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2ab0-140">See also</span></span>

- [<span data-ttu-id="e2ab0-141">Konfigurowanie serwera ściągania SMB DSC</span><span class="sxs-lookup"><span data-stu-id="e2ab0-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="e2ab0-142">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="e2ab0-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
