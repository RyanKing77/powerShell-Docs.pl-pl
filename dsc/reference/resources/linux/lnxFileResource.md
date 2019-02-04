---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC for Linux nxFile Resource
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688651"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="1c48f-103">DSC for Linux nxFile Resource</span><span class="sxs-lookup"><span data-stu-id="1c48f-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="1c48f-104">**NxFile** zasób w programie PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania pliki i katalogi w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="1c48f-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c48f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c48f-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="1c48f-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1c48f-106">Properties</span></span>

|  <span data-ttu-id="1c48f-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1c48f-107">Property</span></span> |  <span data-ttu-id="1c48f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="1c48f-108">Description</span></span> |
|---|---|
| <span data-ttu-id="1c48f-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="1c48f-109">DestinationPath</span></span>| <span data-ttu-id="1c48f-110">Określa lokalizację, w którym chcesz upewnić się, stan dla pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="1c48f-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="1c48f-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="1c48f-111">SourcePath</span></span>| <span data-ttu-id="1c48f-112">Określa ścieżkę, z którego można skopiować zasobu pliku lub folderu.</span><span class="sxs-lookup"><span data-stu-id="1c48f-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="1c48f-113">Ta ścieżka może być ścieżką lokalną lub `http/https/ftp` adresu URL.</span><span class="sxs-lookup"><span data-stu-id="1c48f-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="1c48f-114">Zdalne `http/https/ftp` adresy URL są tylko obsługiwane w przypadku wartości **typu** właściwość jest plik.</span><span class="sxs-lookup"><span data-stu-id="1c48f-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="1c48f-115">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="1c48f-115">Ensure</span></span>| <span data-ttu-id="1c48f-116">Określa, czy należy sprawdzić, czy plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="1c48f-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="1c48f-117">Ustaw tę właściwość "Present", aby upewnić się, że plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="1c48f-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="1c48f-118">Ustaw ją na "Brak", aby upewnić się, że plik nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="1c48f-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="1c48f-119">Wartość domyślna to "Istnieje".</span><span class="sxs-lookup"><span data-stu-id="1c48f-119">The default value is "Present".</span></span>|
| <span data-ttu-id="1c48f-120">Typ</span><span class="sxs-lookup"><span data-stu-id="1c48f-120">Type</span></span>| <span data-ttu-id="1c48f-121">Określa, czy zasób konfigurowany jest katalog lub plik.</span><span class="sxs-lookup"><span data-stu-id="1c48f-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="1c48f-122">Ustaw tę właściwość na "directory", aby wskazać, czy zasób jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="1c48f-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="1c48f-123">Ustaw ją na "plik", aby wskazać, czy zasób jest plik.</span><span class="sxs-lookup"><span data-stu-id="1c48f-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="1c48f-124">Wartość domyślna to "file"</span><span class="sxs-lookup"><span data-stu-id="1c48f-124">The default value is "file"</span></span>|
| <span data-ttu-id="1c48f-125">Zawartość</span><span class="sxs-lookup"><span data-stu-id="1c48f-125">Contents</span></span>| <span data-ttu-id="1c48f-126">Określa zawartość pliku, na przykład określonego ciągu.</span><span class="sxs-lookup"><span data-stu-id="1c48f-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="1c48f-127">Suma kontrolna</span><span class="sxs-lookup"><span data-stu-id="1c48f-127">Checksum</span></span>| <span data-ttu-id="1c48f-128">Definiuje typ używany do określenia, czy dwa pliki są takie same.</span><span class="sxs-lookup"><span data-stu-id="1c48f-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="1c48f-129">Jeśli **sumy kontrolnej** nie jest określona, tylko nazwa pliku lub katalogu jest używana do porównania.</span><span class="sxs-lookup"><span data-stu-id="1c48f-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="1c48f-130">Wartości: "ctime", "mtime" lub "md5".</span><span class="sxs-lookup"><span data-stu-id="1c48f-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="1c48f-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="1c48f-131">Recurse</span></span>| <span data-ttu-id="1c48f-132">Wskazuje, czy podkatalogi są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="1c48f-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="1c48f-133">Ustaw tę właściwość na **$true** aby wskazać, że podkatalogi do uwzględnienia.</span><span class="sxs-lookup"><span data-stu-id="1c48f-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="1c48f-134">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="1c48f-134">The default is **$false**.</span></span> <span data-ttu-id="1c48f-135">**Uwaga:** Ta właściwość jest prawidłowa tylko kiedy **typu** ustawiono właściwość katalogu.</span><span class="sxs-lookup"><span data-stu-id="1c48f-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="1c48f-136">Force</span><span class="sxs-lookup"><span data-stu-id="1c48f-136">Force</span></span>| <span data-ttu-id="1c48f-137">Niektóre operacje na plikach (takich jak zastąpienie pliku lub usunięcie katalogu, który nie jest pusty) spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="1c48f-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="1c48f-138">Za pomocą **życie** właściwość zastępuje takie błędy.</span><span class="sxs-lookup"><span data-stu-id="1c48f-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="1c48f-139">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="1c48f-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="1c48f-140">Łącza</span><span class="sxs-lookup"><span data-stu-id="1c48f-140">Links</span></span>| <span data-ttu-id="1c48f-141">Określa zachowanie dla łącza symbolicznego.</span><span class="sxs-lookup"><span data-stu-id="1c48f-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="1c48f-142">Ustaw tę właściwość na "follow" stosować linki symboliczne i działania w elemencie docelowym łącza (na przykład.</span><span class="sxs-lookup"><span data-stu-id="1c48f-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="1c48f-143">Skopiuj plik zamiast łącza).</span><span class="sxs-lookup"><span data-stu-id="1c48f-143">copy the file instead of the link).</span></span> <span data-ttu-id="1c48f-144">Ustaw tę właściwość na "manage", które działają na link (np.</span><span class="sxs-lookup"><span data-stu-id="1c48f-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="1c48f-145">Skopiuj link, sam).</span><span class="sxs-lookup"><span data-stu-id="1c48f-145">copy the link itself).</span></span> <span data-ttu-id="1c48f-146">Ustaw tę właściwość na "ignorowania", aby zignorować łącza symbolicznego.</span><span class="sxs-lookup"><span data-stu-id="1c48f-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="1c48f-147">Grupa</span><span class="sxs-lookup"><span data-stu-id="1c48f-147">Group</span></span>| <span data-ttu-id="1c48f-148">Nazwa **grupy** być właścicielem pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="1c48f-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="1c48f-149">Tryb</span><span class="sxs-lookup"><span data-stu-id="1c48f-149">Mode</span></span>| <span data-ttu-id="1c48f-150">Określa odpowiednich uprawnień dla zasobu, w notacji ósemkowej lub symboliczne.</span><span class="sxs-lookup"><span data-stu-id="1c48f-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="1c48f-151">(na przykład 777 lub rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="1c48f-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="1c48f-152">Przy użyciu notacji symbolicznych, nie są oferowane pierwszy znak, który wskazuje katalog lub plik.</span><span class="sxs-lookup"><span data-stu-id="1c48f-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="1c48f-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1c48f-153">DependsOn</span></span> | <span data-ttu-id="1c48f-154">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="1c48f-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1c48f-155">Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1c48f-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="1c48f-156">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="1c48f-156">Additional Information</span></span>


<span data-ttu-id="1c48f-157">Z systemami Linux i Windows znaki podziału wiersza różnych w plikach tekstowych domyślnie używają i może to spowodować nieoczekiwane wyniki, podczas konfigurowania niektórych plików na komputerze z systemem Linux przy użyciu __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="1c48f-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="1c48f-158">Istnieje wiele sposobów, aby zarządzać zawartość pliku systemu Linux, unikając problemy spowodowane przez znaki podziału wiersza nieoczekiwany:</span><span class="sxs-lookup"><span data-stu-id="1c48f-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="1c48f-159">Krok 1. Skopiuj plik ze źródła zdalnego (http, https lub ftp): Utwórz plik w systemie Linux z żądaną zawartość i przygotowania na serwerze sieci web lub ftp dostępne węzły skonfigurujesz.</span><span class="sxs-lookup"><span data-stu-id="1c48f-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="1c48f-160">Zdefiniuj __Ścieżka_źródłowa__ właściwość __nxFile__ zasobów za pomocą adresu URL sieci web lub ftp do pliku.</span><span class="sxs-lookup"><span data-stu-id="1c48f-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


<span data-ttu-id="1c48f-161">Krok 2. Odczytać zawartość pliku w skrypcie programu PowerShell przy użyciu [pobrania zawartości](https://technet.microsoft.com/library/hh849787.aspx) po ustawieniu __$OFS__ właściwości, aby znak podziału wiersza systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="1c48f-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


<span data-ttu-id="1c48f-162">Krok 3. Użyj funkcji programu PowerShell, aby zamienić Windows podziały wierszy przy użyciu systemu Linux, znaki podziału wiersza.</span><span class="sxs-lookup"><span data-stu-id="1c48f-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a><span data-ttu-id="1c48f-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c48f-163">Example</span></span>

<span data-ttu-id="1c48f-164">Poniższy przykład zapewnia, że katalog `/opt/mydir` istnieje, i czy plik z określoną zawartość istnieje tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="1c48f-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```