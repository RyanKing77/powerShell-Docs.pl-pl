---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: DSC dla systemu Linux zasób nxArchive
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048475"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="0c19b-103">DSC dla systemu Linux zasób nxArchive</span><span class="sxs-lookup"><span data-stu-id="0c19b-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="0c19b-104">**NxArchive** zasobów w programie PowerShell Desired State Configuration (DSC) udostępnia mechanizm do rozpakowywania plików archiwum (tar, .zip) w określonej ścieżce na węźle systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="0c19b-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c19b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c19b-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="0c19b-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0c19b-106">Properties</span></span>

|  <span data-ttu-id="0c19b-107">Właściwość</span><span class="sxs-lookup"><span data-stu-id="0c19b-107">Property</span></span> |  <span data-ttu-id="0c19b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="0c19b-108">Description</span></span> |
|---|---|
| <span data-ttu-id="0c19b-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="0c19b-109">SourcePath</span></span>| <span data-ttu-id="0c19b-110">Określa ścieżkę źródłową pliku archiwum.</span><span class="sxs-lookup"><span data-stu-id="0c19b-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="0c19b-111">Powinno to być tar .zip, lub. plik tar.gz.</span><span class="sxs-lookup"><span data-stu-id="0c19b-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="0c19b-112">Ścieżka_docelowa</span><span class="sxs-lookup"><span data-stu-id="0c19b-112">DestinationPath</span></span>| <span data-ttu-id="0c19b-113">Określa lokalizację, w której chcesz upewnić się, że zawartość archiwum zostały wyodrębnione.</span><span class="sxs-lookup"><span data-stu-id="0c19b-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="0c19b-114">Suma kontrolna</span><span class="sxs-lookup"><span data-stu-id="0c19b-114">Checksum</span></span>| <span data-ttu-id="0c19b-115">Definiuje typ używany do określenia, czy archiwum źródła został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="0c19b-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="0c19b-116">Wartości: "ctime", "mtime" lub "md5".</span><span class="sxs-lookup"><span data-stu-id="0c19b-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="0c19b-117">Wartość domyślna to "md5".</span><span class="sxs-lookup"><span data-stu-id="0c19b-117">The default value is "md5".</span></span>|
| <span data-ttu-id="0c19b-118">Force</span><span class="sxs-lookup"><span data-stu-id="0c19b-118">Force</span></span>| <span data-ttu-id="0c19b-119">Niektóre operacje na plikach (takich jak zastąpienie pliku lub usunięcie katalogu, który nie jest pusty) spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="0c19b-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="0c19b-120">Za pomocą **życie** właściwość zastępuje takie błędy.</span><span class="sxs-lookup"><span data-stu-id="0c19b-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="0c19b-121">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="0c19b-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="0c19b-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0c19b-122">DependsOn</span></span> | <span data-ttu-id="0c19b-123">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="0c19b-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0c19b-124">Na przykład jeśli **identyfikator** zasobu jest najpierw blok skryptu konfiguracji, który chcesz uruchomić **ResourceName** a jej typ jest **ResourceType**, składnia za pomocą tego Właściwość jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0c19b-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="0c19b-125">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="0c19b-125">Ensure</span></span>| <span data-ttu-id="0c19b-126">Określa, czy należy sprawdzić, czy zawartość archiwum istnieje w **docelowy**.</span><span class="sxs-lookup"><span data-stu-id="0c19b-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="0c19b-127">Ustaw tę właściwość "Present", aby upewnić się, że zawartość istnieje.</span><span class="sxs-lookup"><span data-stu-id="0c19b-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="0c19b-128">Ustaw ją na "Brak", aby upewnić się, że nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="0c19b-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="0c19b-129">Wartość domyślna to "Istnieje".</span><span class="sxs-lookup"><span data-stu-id="0c19b-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="0c19b-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c19b-130">Example</span></span>

<span data-ttu-id="0c19b-131">Poniższy przykład pokazuje, jak używać **nxArchive** zasobów, aby upewnić się, że zawartość pliku archiwum o nazwie `website.tar` istnieją i są wyodrębniane w danej lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="0c19b-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

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