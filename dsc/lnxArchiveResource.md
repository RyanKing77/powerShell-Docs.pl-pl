---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "DSC dla systemu Linux nxArchive zasobów"
ms.openlocfilehash: da647432e14d2a4a3ceb2a36c7dee2dbfd350116
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="451d0-103">DSC dla systemu Linux nxArchive zasobów</span><span class="sxs-lookup"><span data-stu-id="451d0-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="451d0-104">**NxArchive** zasób w PowerShell żądanego stanu konfiguracji (DSC) zapewnia mechanizm do rozpakowywania plików archiwum (tar, .zip) w określonej ścieżce na węźle Linux.</span><span class="sxs-lookup"><span data-stu-id="451d0-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="451d0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="451d0-105">Syntax</span></span>

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="451d0-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="451d0-106">Properties</span></span>

|  <span data-ttu-id="451d0-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="451d0-107">Property</span></span> |  <span data-ttu-id="451d0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="451d0-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="451d0-109">Ścieżka_źródłowa</span><span class="sxs-lookup"><span data-stu-id="451d0-109">SourcePath</span></span>| <span data-ttu-id="451d0-110">Określa ścieżkę źródłową pliku archiwum.</span><span class="sxs-lookup"><span data-stu-id="451d0-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="451d0-111">To pole powinno być tar zip, lub. plik tar.gz.</span><span class="sxs-lookup"><span data-stu-id="451d0-111">This should be a .tar, .zip, or .tar.gz file.</span></span> | 
| <span data-ttu-id="451d0-112">Ścieżka_docelowa</span><span class="sxs-lookup"><span data-stu-id="451d0-112">DestinationPath</span></span>| <span data-ttu-id="451d0-113">Określa lokalizację, w której chcesz upewnij się, że są wyodrębniane zawartość archiwum.</span><span class="sxs-lookup"><span data-stu-id="451d0-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>| 
| <span data-ttu-id="451d0-114">Suma kontrolna</span><span class="sxs-lookup"><span data-stu-id="451d0-114">Checksum</span></span>| <span data-ttu-id="451d0-115">Definiuje typ używany do określenia, czy archiwum źródła został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="451d0-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="451d0-116">Wartości to: "ctime —", "mtime" lub "md5".</span><span class="sxs-lookup"><span data-stu-id="451d0-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="451d0-117">Wartość domyślna to "md5".</span><span class="sxs-lookup"><span data-stu-id="451d0-117">The default value is "md5".</span></span>| 
| <span data-ttu-id="451d0-118">Force</span><span class="sxs-lookup"><span data-stu-id="451d0-118">Force</span></span>| <span data-ttu-id="451d0-119">Niektóre operacje na plikach (takie jak zastąpienie pliku lub usuwanie katalogu, który nie jest pusty) spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="451d0-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="451d0-120">Przy użyciu **życie** właściwość zastępuje takie błędy.</span><span class="sxs-lookup"><span data-stu-id="451d0-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="451d0-121">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="451d0-121">The default value is **$false**.</span></span>| 
| <span data-ttu-id="451d0-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="451d0-122">DependsOn</span></span> | <span data-ttu-id="451d0-123">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="451d0-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="451d0-124">Na przykład jeśli **identyfikator** zasobu jest pierwszy blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** i jej typ jest **ResourceType**, za pomocą tej składni Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="451d0-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="451d0-125">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="451d0-125">Ensure</span></span>| <span data-ttu-id="451d0-126">Określa, czy należy sprawdzić, czy zawartość archiwum istnieje w **docelowego**.</span><span class="sxs-lookup"><span data-stu-id="451d0-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="451d0-127">Ustaw tę właściwość na "Brak", aby upewnić się, że istnieje zawartość.</span><span class="sxs-lookup"><span data-stu-id="451d0-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="451d0-128">Ustaw ją na "Brak", aby upewnić się, że nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="451d0-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="451d0-129">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="451d0-129">The default value is "Present".</span></span>| 

## <a name="example"></a><span data-ttu-id="451d0-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="451d0-130">Example</span></span>

<span data-ttu-id="451d0-131">Poniższy przykład przedstawia użycie **nxArchive** zasobów, aby upewnić się, że zawartość pliku archiwum o nazwie `website.tar` istnieją i są wyodrębniane w danej lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="451d0-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```
Import-DSCResource -Module nx 

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
} 
```

