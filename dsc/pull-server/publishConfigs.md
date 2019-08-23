---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguracja, instalacja
title: Publikowanie na serwerze ściągania przy użyciu identyfikatorów konfiguracji (V4/V5)
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986571"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="d569a-103">Publikowanie na serwerze ściągania przy użyciu identyfikatorów konfiguracji (V4/V5)</span><span class="sxs-lookup"><span data-stu-id="d569a-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="d569a-104">W poniższych sekcjach przyjęto założenie, że skonfigurowano już serwer ściągania.</span><span class="sxs-lookup"><span data-stu-id="d569a-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="d569a-105">Jeśli nie skonfigurowano serwera ściągania, można użyć następujących przewodników:</span><span class="sxs-lookup"><span data-stu-id="d569a-105">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="d569a-106">Konfigurowanie serwera ściągania SMB protokołu DSC</span><span class="sxs-lookup"><span data-stu-id="d569a-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d569a-107">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="d569a-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="d569a-108">Każdy węzeł docelowy można skonfigurować w taki sposób, aby pobierał konfiguracje, zasoby, a nawet raportuje jego stan.</span><span class="sxs-lookup"><span data-stu-id="d569a-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="d569a-109">W tym artykule pokazano, jak przekazywać zasoby, aby były dostępne do pobrania, i skonfigurować klientów do automatycznego pobierania zasobów.</span><span class="sxs-lookup"><span data-stu-id="d569a-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="d569a-110">Gdy węzeł otrzyma przypisaną konfigurację za pośrednictwem **ściągania** lub **wypychania** (V5), automatycznie pobiera wszystkie zasoby wymagane przez konfigurację z lokalizacji określonej w lokalnej Configuration Manager (LCM).</span><span class="sxs-lookup"><span data-stu-id="d569a-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="d569a-111">Kompiluj konfiguracje</span><span class="sxs-lookup"><span data-stu-id="d569a-111">Compile configurations</span></span>

<span data-ttu-id="d569a-112">Pierwszym krokiem do przechowywania [konfiguracji](../configurations/configurations.md) na serwerze ściągania jest skompilowanie ich do `.mof` plików.</span><span class="sxs-lookup"><span data-stu-id="d569a-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="d569a-113">Aby skonfigurować konfigurację ogólną i zastosować ją do większej liczby klientów, użyj `localhost` w bloku węzła.</span><span class="sxs-lookup"><span data-stu-id="d569a-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="d569a-114">W poniższym przykładzie przedstawiono powłokę konfiguracji używaną `localhost` zamiast określonej nazwy klienta.</span><span class="sxs-lookup"><span data-stu-id="d569a-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="d569a-115">Po skompilowaniu konfiguracji ogólnej należy mieć `localhost.mof` plik.</span><span class="sxs-lookup"><span data-stu-id="d569a-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="d569a-116">Zmiana nazwy pliku MOF</span><span class="sxs-lookup"><span data-stu-id="d569a-116">Renaming the MOF file</span></span>

<span data-ttu-id="d569a-117">Pliki konfiguracji `.mof` można przechowywać na serwerze ściągania za pomocą elementu **ConfigurationName** lub **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="d569a-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="d569a-118">W zależności od sposobu konfigurowania klientów ściągania można wybrać sekcję poniżej, aby poprawnie zmienić nazwy skompilowanych `.mof` plików.</span><span class="sxs-lookup"><span data-stu-id="d569a-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="d569a-119">Identyfikatory konfiguracji (GUID)</span><span class="sxs-lookup"><span data-stu-id="d569a-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="d569a-120">Musisz zmienić nazwę `localhost.mof` pliku na `<GUID>.mof` plik.</span><span class="sxs-lookup"><span data-stu-id="d569a-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="d569a-121">Można utworzyć losowy **Identyfikator GUID** przy użyciu poniższego przykładu lub przy użyciu polecenia cmdlet [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .</span><span class="sxs-lookup"><span data-stu-id="d569a-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="d569a-122">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d569a-122">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="d569a-123">Następnie można zmienić nazwę `.mof` pliku przy użyciu dowolnej akceptowalnej metody.</span><span class="sxs-lookup"><span data-stu-id="d569a-123">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="d569a-124">Poniższy przykład używa polecenia cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) .</span><span class="sxs-lookup"><span data-stu-id="d569a-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="d569a-125">Aby uzyskać więcej informacji na temat używania **identyfikatorów GUID** w środowisku, zobacz temat [Planowanie identyfikatorów GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="d569a-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="d569a-126">Nazwy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d569a-126">Configuration names</span></span>

<span data-ttu-id="d569a-127">Musisz zmienić nazwę `localhost.mof` pliku na `<Configuration Name>.mof` plik.</span><span class="sxs-lookup"><span data-stu-id="d569a-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="d569a-128">W poniższym przykładzie użyto nazwy konfiguracji z poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d569a-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="d569a-129">Następnie można zmienić nazwę `.mof` pliku przy użyciu dowolnej akceptowalnej metody.</span><span class="sxs-lookup"><span data-stu-id="d569a-129">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="d569a-130">Poniższy przykład używa polecenia cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) .</span><span class="sxs-lookup"><span data-stu-id="d569a-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="d569a-131">Utwórz sumę kontrolną</span><span class="sxs-lookup"><span data-stu-id="d569a-131">Create the checkSum</span></span>

<span data-ttu-id="d569a-132">Każdy `.mof` plik przechowywany na serwerze ściągania lub udział SMB musi mieć skojarzony `.checksum` plik.</span><span class="sxs-lookup"><span data-stu-id="d569a-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="d569a-133">Ten plik umożliwia klientom znać, kiedy skojarzony `.mof` plik został zmieniony i powinien zostać pobrany ponownie.</span><span class="sxs-lookup"><span data-stu-id="d569a-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="d569a-134">Można utworzyć **sumę kontrolną** za pomocą polecenia cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) .</span><span class="sxs-lookup"><span data-stu-id="d569a-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="d569a-135">Można również uruchomić `New-DSCCheckSum` dla katalogu plików `-Path` przy użyciu parametru.</span><span class="sxs-lookup"><span data-stu-id="d569a-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="d569a-136">Jeśli suma kontrolna już istnieje, można wymusić jej ponowne utworzenie za pomocą `-Force` parametru.</span><span class="sxs-lookup"><span data-stu-id="d569a-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="d569a-137">Poniższy przykład określa katalog zawierający `.mof` plik z poprzedniej sekcji i `-Force` używa parametru.</span><span class="sxs-lookup"><span data-stu-id="d569a-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="d569a-138">Nie będą wyświetlane żadne dane wyjściowe, ale powinien `<GUID or Configuration Name>.mof.checksum` pojawić się plik.</span><span class="sxs-lookup"><span data-stu-id="d569a-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="d569a-139">Miejsce przechowywania plików MOF i sum kontrolnych</span><span class="sxs-lookup"><span data-stu-id="d569a-139">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="d569a-140">Na serwerze ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="d569a-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="d569a-141">Podczas konfigurowania serwera ściągania HTTP, zgodnie z opisem w temacie [Konfigurowanie serwera ściągania http DSC](pullServer.md), należy określić katalogi dla kluczy **ModulePath** i **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="d569a-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="d569a-142">Klucz **ModulePath** wskazuje, gdzie mają być przechowywane spakowane `.zip` pliki modułu.</span><span class="sxs-lookup"><span data-stu-id="d569a-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="d569a-143">**ConfigurationPath** wskazuje, gdzie mają `.mof` być przechowywane `.checksum` wszystkie pliki i pliki.</span><span class="sxs-lookup"><span data-stu-id="d569a-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="d569a-144">W udziale SMB</span><span class="sxs-lookup"><span data-stu-id="d569a-144">On an SMB share</span></span>

<span data-ttu-id="d569a-145">Po skonfigurowaniu klienta ściągania do korzystania z udziału SMB należy określić **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="d569a-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="d569a-146">Wszystkie `.mof` pliki i `.checksum` pliki powinny być przechowywane w katalogu **SourcePath** z bloku **ConfigurationRepositoryShare** .</span><span class="sxs-lookup"><span data-stu-id="d569a-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="d569a-147">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d569a-147">Next steps</span></span>

<span data-ttu-id="d569a-148">Następnie należy skonfigurować klientów ściągania w celu ściągnięcia określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d569a-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="d569a-149">Aby uzyskać więcej informacji, zobacz jedną z następujących przewodników:</span><span class="sxs-lookup"><span data-stu-id="d569a-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="d569a-150">Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji (v4)</span><span class="sxs-lookup"><span data-stu-id="d569a-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="d569a-151">Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji (V5)</span><span class="sxs-lookup"><span data-stu-id="d569a-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="d569a-152">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji (V5)</span><span class="sxs-lookup"><span data-stu-id="d569a-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="d569a-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d569a-153">See also</span></span>

- [<span data-ttu-id="d569a-154">Konfigurowanie serwera ściągania SMB protokołu DSC</span><span class="sxs-lookup"><span data-stu-id="d569a-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d569a-155">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="d569a-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="d569a-156">Pakowanie i przekazywanie zasobów do serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="d569a-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
