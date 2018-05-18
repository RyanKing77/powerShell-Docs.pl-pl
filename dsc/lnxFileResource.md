---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: DSC dla systemu Linux nxFile zasobów
ms.openlocfilehash: f1eb98092049ae837d144ccf99a84fe5614144e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="06aec-103">DSC dla systemu Linux nxFile zasobów</span><span class="sxs-lookup"><span data-stu-id="06aec-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="06aec-104">**NxFile** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do zarządzania plików i katalogów w węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="06aec-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="06aec-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="06aec-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="06aec-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="06aec-106">Properties</span></span>

|  <span data-ttu-id="06aec-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="06aec-107">Property</span></span> |  <span data-ttu-id="06aec-108">Opis</span><span class="sxs-lookup"><span data-stu-id="06aec-108">Description</span></span> |
|---|---|
| <span data-ttu-id="06aec-109">Ścieżka_docelowa</span><span class="sxs-lookup"><span data-stu-id="06aec-109">DestinationPath</span></span>| <span data-ttu-id="06aec-110">Określa lokalizację, w której chcesz zapewnić stan pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="06aec-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="06aec-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="06aec-111">SourcePath</span></span>| <span data-ttu-id="06aec-112">Określa ścieżkę, z którego można skopiować pliku lub folderu zasobów.</span><span class="sxs-lookup"><span data-stu-id="06aec-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="06aec-113">Ta ścieżka może być ścieżką lokalną lub `http/https/ftp` adresu URL.</span><span class="sxs-lookup"><span data-stu-id="06aec-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="06aec-114">Zdalne `http/https/ftp` adresy URL są tylko obsługiwane, gdy wartość **typu** właściwość jest plik.</span><span class="sxs-lookup"><span data-stu-id="06aec-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="06aec-115">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="06aec-115">Ensure</span></span>| <span data-ttu-id="06aec-116">Określa, czy należy sprawdzić, czy plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="06aec-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="06aec-117">Ustaw tę właściwość na "Brak", aby upewnić się, że plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="06aec-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="06aec-118">Ustaw ją na "Brak", aby upewnić się, że plik nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="06aec-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="06aec-119">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="06aec-119">The default value is "Present".</span></span>|
| <span data-ttu-id="06aec-120">Typ</span><span class="sxs-lookup"><span data-stu-id="06aec-120">Type</span></span>| <span data-ttu-id="06aec-121">Określa, czy zasób konfigurowany jest katalog lub plik.</span><span class="sxs-lookup"><span data-stu-id="06aec-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="06aec-122">Ustaw tę właściwość na "directory", aby wskazać, czy zasób jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="06aec-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="06aec-123">Ustaw go na "plik", aby wskazać, czy zasób jest plik.</span><span class="sxs-lookup"><span data-stu-id="06aec-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="06aec-124">Wartość domyślna to "plik"</span><span class="sxs-lookup"><span data-stu-id="06aec-124">The default value is "file"</span></span>|
| <span data-ttu-id="06aec-125">Zawartość</span><span class="sxs-lookup"><span data-stu-id="06aec-125">Contents</span></span>| <span data-ttu-id="06aec-126">Określa zawartość pliku, takie jak określony ciąg.</span><span class="sxs-lookup"><span data-stu-id="06aec-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="06aec-127">Suma kontrolna</span><span class="sxs-lookup"><span data-stu-id="06aec-127">Checksum</span></span>| <span data-ttu-id="06aec-128">Definiuje typ używany do określenia, czy dwa pliki są takie same.</span><span class="sxs-lookup"><span data-stu-id="06aec-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="06aec-129">Jeśli **sumy kontrolnej** nie zostanie określona, tylko nazwa pliku lub katalogu jest używana do porównania.</span><span class="sxs-lookup"><span data-stu-id="06aec-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="06aec-130">Wartości to: "ctime —", "mtime" lub "md5".</span><span class="sxs-lookup"><span data-stu-id="06aec-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="06aec-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="06aec-131">Recurse</span></span>| <span data-ttu-id="06aec-132">Wskazuje, czy podkatalogi są dołączone.</span><span class="sxs-lookup"><span data-stu-id="06aec-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="06aec-133">Ta właściwość jest ustawiana **$true** aby wskazać, że chcesz podkatalogów, które zostaną uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="06aec-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="06aec-134">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="06aec-134">The default is **$false**.</span></span> <span data-ttu-id="06aec-135">**Uwaga:** ta właściwość jest prawidłowa tylko gdy **typu** właściwość jest ustawiona na katalogu.</span><span class="sxs-lookup"><span data-stu-id="06aec-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="06aec-136">Force</span><span class="sxs-lookup"><span data-stu-id="06aec-136">Force</span></span>| <span data-ttu-id="06aec-137">Niektóre operacje na plikach (takie jak zastąpienie pliku lub usuwanie katalogu, który nie jest pusty) spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="06aec-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="06aec-138">Przy użyciu **życie** właściwość zastępuje takie błędy.</span><span class="sxs-lookup"><span data-stu-id="06aec-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="06aec-139">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="06aec-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="06aec-140">Łącza</span><span class="sxs-lookup"><span data-stu-id="06aec-140">Links</span></span>| <span data-ttu-id="06aec-141">Określa zachowanie dla łącza symbolicznego.</span><span class="sxs-lookup"><span data-stu-id="06aec-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="06aec-142">Ustaw tę właściwość na "podążać" wykonaj łącza symbolicznego i działa w systemie docelowym łącza (np.</span><span class="sxs-lookup"><span data-stu-id="06aec-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="06aec-143">Skopiuj plik zamiast łącza).</span><span class="sxs-lookup"><span data-stu-id="06aec-143">copy the file instead of the link).</span></span> <span data-ttu-id="06aec-144">Ustaw tę właściwość na "manage", które działają na link (np.</span><span class="sxs-lookup"><span data-stu-id="06aec-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="06aec-145">Skopiuj link, sam).</span><span class="sxs-lookup"><span data-stu-id="06aec-145">copy the link itself).</span></span> <span data-ttu-id="06aec-146">Ustaw tę właściwość na "Ignoruj", aby zignorować łącza symbolicznego.</span><span class="sxs-lookup"><span data-stu-id="06aec-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="06aec-147">Grupa</span><span class="sxs-lookup"><span data-stu-id="06aec-147">Group</span></span>| <span data-ttu-id="06aec-148">Nazwa **grupy** do pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="06aec-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="06aec-149">Tryb</span><span class="sxs-lookup"><span data-stu-id="06aec-149">Mode</span></span>| <span data-ttu-id="06aec-150">Określa odpowiednie uprawnienia do zasobów, w notacji ósemkowe lub symbolicznych.</span><span class="sxs-lookup"><span data-stu-id="06aec-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="06aec-151">(na przykład 777 lub rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="06aec-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="06aec-152">Jeśli przy użyciu notacji symbolicznych, nie zapewniają pierwszego znaku, który wskazuje katalog lub plik.</span><span class="sxs-lookup"><span data-stu-id="06aec-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="06aec-153">dependsOn</span><span class="sxs-lookup"><span data-stu-id="06aec-153">DependsOn</span></span> | <span data-ttu-id="06aec-154">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="06aec-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="06aec-155">Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="06aec-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="06aec-156">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="06aec-156">Additional Information</span></span>


<span data-ttu-id="06aec-157">Linux i Windows przy użyciu znaki końca wiersza różnych w plikach tekstowych domyślnie, a to może spowodować nieoczekiwane wyniki podczas konfigurowania niektóre pliki z komputera z systemem Linux __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="06aec-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="06aec-158">Istnieje wiele sposobów zarządzania zawartością pliku Linux, unikając problemów spowodowanych znaki końca wiersza nieoczekiwany:</span><span class="sxs-lookup"><span data-stu-id="06aec-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="06aec-159">Krok 1: Skopiuj plik ze źródła zdalnego (http, https lub ftp): Utwórz plik w systemie Linux z żądaną zawartość i przemieszczanie go na serwerze sieci web lub ftp dostępny węzłów skonfigurujesz.</span><span class="sxs-lookup"><span data-stu-id="06aec-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="06aec-160">Zdefiniuj __Ścieżka_źródłowa__ właściwości w __nxFile__ zasobów z adresem URL sieci web lub ftp do pliku.</span><span class="sxs-lookup"><span data-stu-id="06aec-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

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


<span data-ttu-id="06aec-161">Krok 2: Odczytać zawartości pliku skryptu programu PowerShell z [pobrania zawartości](https://technet.microsoft.com/library/hh849787.aspx) po ustawieniu __$OFS__ właściwości można użyć znaku podział wiersza systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="06aec-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


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


<span data-ttu-id="06aec-162">Krok 3: Użyj funkcji programu PowerShell należy zastąpić Windows podziałów Linux, znaki podziału wiersza.</span><span class="sxs-lookup"><span data-stu-id="06aec-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

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

## <a name="example"></a><span data-ttu-id="06aec-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="06aec-163">Example</span></span>

<span data-ttu-id="06aec-164">Poniższy przykład zapewnia, że katalog `/opt/mydir` istnieje, i istnieje plik z określoną zawartość tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="06aec-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

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