---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Publikowanie na serwerze ściągania przy użyciu identyfikatorów konfiguracji (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686369"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="112f8-103">Publikowanie na serwerze ściągania przy użyciu identyfikatorów konfiguracji (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="112f8-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="112f8-104">W poniższych sekcjach przyjęto założenie, że już zdefiniowano serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="112f8-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="112f8-105">Jeśli nie zdefiniowano z serwera ściągania, można użyć następujących przewodników:</span><span class="sxs-lookup"><span data-stu-id="112f8-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="112f8-106">Konfigurowanie serwera ściągania SMB DSC</span><span class="sxs-lookup"><span data-stu-id="112f8-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="112f8-107">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="112f8-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="112f8-108">Każdy węzeł docelowy można skonfigurować do pobrania konfiguracji, zasobów i nawet raportować jej stanu.</span><span class="sxs-lookup"><span data-stu-id="112f8-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="112f8-109">W tym artykule pokazano sposób przekazywania zasobów, dzięki czemu są one dostępne do pobrania, a następnie skonfigurować klientów, aby pobrać zasoby automatycznie.</span><span class="sxs-lookup"><span data-stu-id="112f8-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="112f8-110">Gdy węzeł odbiera przypisanej konfiguracji, za pośrednictwem **ściągnięcia** lub **wypychania** (v5), automatycznie pobiera wszystkie zasoby wymagane przez tę konfigurację w lokalizacji określonej w LCM.</span><span class="sxs-lookup"><span data-stu-id="112f8-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="112f8-111">Konfiguracje kompilacji</span><span class="sxs-lookup"><span data-stu-id="112f8-111">Compile Configurations</span></span>

<span data-ttu-id="112f8-112">Pierwszym krokiem do przechowywania [konfiguracje](../configurations/configurations.md) na serwerze ściągania, to aby skompilować je do plików "MOF".</span><span class="sxs-lookup"><span data-stu-id="112f8-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="112f8-113">Aby konfiguracja ogólny i mające zastosowanie do większej liczby klientów, należy użyć `localhost` w bloku Twojej węzła.</span><span class="sxs-lookup"><span data-stu-id="112f8-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="112f8-114">W poniższym przykładzie pokazano powłoki konfiguracji, który używa `localhost` zamiast nazwy określonego klienta.</span><span class="sxs-lookup"><span data-stu-id="112f8-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="112f8-115">Po skompilowałeś konfiguracji ogólnych powinny mieć plik "localhost.mof".</span><span class="sxs-lookup"><span data-stu-id="112f8-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="112f8-116">Zmiana nazwy pliku MOF</span><span class="sxs-lookup"><span data-stu-id="112f8-116">Renaming the MOF file</span></span>

<span data-ttu-id="112f8-117">Można przechowywać pliki "MOF" konfiguracji na serwerze ściągania przez **ConfigurationName** lub **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="112f8-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="112f8-118">W zależności od tego, jak zamierzasz skonfigurować klientów ściągania możesz wybrać sekcję poniżej, aby odpowiednio zmienić nazwy plików skompilowanych "MOF".</span><span class="sxs-lookup"><span data-stu-id="112f8-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="112f8-119">Konfiguracja identyfikatory (GUID)</span><span class="sxs-lookup"><span data-stu-id="112f8-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="112f8-120">Musisz zmienić nazwę pliku "localhost.mof" do "<GUID>MOF" pliku.</span><span class="sxs-lookup"><span data-stu-id="112f8-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="112f8-121">Można utworzyć losowej **Guid** w przykładzie poniżej lub za pomocą [nowy Guid](/powershell/module/microsoft.powershell.utility/new-guid) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="112f8-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="112f8-122">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="112f8-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="112f8-123">Następnie można zmienić nazwę pliku "MOF" przy użyciu dowolnej metody dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="112f8-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="112f8-124">W poniższym przykładzie użyto [Zmień nazwę elementu](/powershell/module/microsoft.powershell.management/rename-item) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="112f8-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="112f8-125">Aby uzyskać więcej informacji o korzystaniu z **identyfikatorów GUID** w danym środowisku, zobacz [planowanie identyfikatorów GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="112f8-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="112f8-126">Nazwy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="112f8-126">Configuration Names</span></span>

<span data-ttu-id="112f8-127">Musisz zmienić nazwę pliku "localhost.mof" do "<Configuration Name>MOF" pliku.</span><span class="sxs-lookup"><span data-stu-id="112f8-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="112f8-128">W poniższym przykładzie jest używana nazwa konfiguracji z poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="112f8-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="112f8-129">Następnie można zmienić nazwę pliku "MOF" przy użyciu dowolnej metody dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="112f8-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="112f8-130">W poniższym przykładzie użyto [Zmień nazwę elementu](/powershell/module/microsoft.powershell.management/rename-item) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="112f8-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="112f8-131">Utwórz sumę kontrolną</span><span class="sxs-lookup"><span data-stu-id="112f8-131">Create the CheckSum</span></span>

<span data-ttu-id="112f8-132">Każdy plik "MOF" w udziale serwera ściągania lub udział SMB musi mieć plik skojarzony ".checksum".</span><span class="sxs-lookup"><span data-stu-id="112f8-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="112f8-133">Ten plik umożliwia klientom, o których wiadomo, kiedy plik skojarzony "MOF" został zmieniony i powinny być pobierane ponownie.</span><span class="sxs-lookup"><span data-stu-id="112f8-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="112f8-134">Możesz utworzyć **sumy kontrolnej** z [New DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="112f8-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="112f8-135">Można również uruchomić `New-DSCCheckSum` względem katalogu plików, używając `-Path` parametru.</span><span class="sxs-lookup"><span data-stu-id="112f8-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="112f8-136">Jeśli istnieje już sumy kontrolnej, aby wymusić można ponownie utworzyć za pomocą `-Force` parametru.</span><span class="sxs-lookup"><span data-stu-id="112f8-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="112f8-137">W poniższym przykładzie określono katalogu zawierającego plik "MOF" w poprzedniej sekcji i używa `-Force` parametru.</span><span class="sxs-lookup"><span data-stu-id="112f8-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="112f8-138">Żadne dane wyjściowe będą wyświetlane, ale powinien zostać wyświetlony "<GUID or Configuration Name>. mof.checksum" pliku.</span><span class="sxs-lookup"><span data-stu-id="112f8-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="112f8-139">Gdzie można przechowywać pliki MOF i sumy kontrolne</span><span class="sxs-lookup"><span data-stu-id="112f8-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="112f8-140">Na serwerze ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="112f8-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="112f8-141">Po skonfigurowaniu serwera ściągania HTTP, jak wyjaśniono w [Konfigurowanie serwera ściągania HTTP DSC](pullServer.md), określ katalogi dla **ModulePath** i **ConfigurationPath** kluczy.</span><span class="sxs-lookup"><span data-stu-id="112f8-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="112f8-142">**ConfigurationPath** klucz wskazuje, gdzie powinny być przechowywane pliki "MOF".</span><span class="sxs-lookup"><span data-stu-id="112f8-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="112f8-143">**ConfigurationPath** wskazuje, gdzie wszystkie pliki "MOF" i ".checksum" pliki powinny być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="112f8-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="112f8-144">W udziale SMB</span><span class="sxs-lookup"><span data-stu-id="112f8-144">On an SMB Share</span></span>

<span data-ttu-id="112f8-145">Po skonfigurowaniu używać udziału SMB klienta ściągania należy określić **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="112f8-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="112f8-146">Wszystkie pliki "MOF" i ".checksum" pliki następnie powinny być przechowywane w **Ścieżka_źródłowa** katalogu z **ConfigurationRepositoryShare** bloku.</span><span class="sxs-lookup"><span data-stu-id="112f8-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="112f8-147">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="112f8-147">Next Steps</span></span>

<span data-ttu-id="112f8-148">Następnie należy skonfigurować klientów ściągnięcia w celu ściągnięcia określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="112f8-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="112f8-149">Aby uzyskać więcej informacji zobacz jeden z następujących przewodników:</span><span class="sxs-lookup"><span data-stu-id="112f8-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="112f8-150">Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji (v4)</span><span class="sxs-lookup"><span data-stu-id="112f8-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="112f8-151">Konfigurowanie klienta ściągania przy użyciu identyfikatorów konfiguracji (v5)</span><span class="sxs-lookup"><span data-stu-id="112f8-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="112f8-152">Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji (v5)</span><span class="sxs-lookup"><span data-stu-id="112f8-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="112f8-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="112f8-153">See also</span></span>

- [<span data-ttu-id="112f8-154">Konfigurowanie serwera ściągania SMB DSC</span><span class="sxs-lookup"><span data-stu-id="112f8-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="112f8-155">Konfigurowanie serwera ściągania HTTP DSC</span><span class="sxs-lookup"><span data-stu-id="112f8-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="112f8-156">Pakiet i przekazywanie zasobów do serwera ściągania</span><span class="sxs-lookup"><span data-stu-id="112f8-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
