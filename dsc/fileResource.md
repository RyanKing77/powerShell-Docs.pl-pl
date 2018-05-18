---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób plików konfiguracji DSC
ms.openlocfilehash: 86a5dcd97b4163b3780038c815d3de5a523ce4bf
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-file-resource"></a><span data-ttu-id="8d813-103">Zasób plików konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="8d813-103">DSC File Resource</span></span>

> <span data-ttu-id="8d813-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8d813-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8d813-105">Plik zasobów w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania plikami i folderami w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="8d813-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="8d813-106">**Uwaga:** Jeśli **MatchSource** właściwość jest ustawiona na **$false** (która jest wartością domyślną), zawartość do skopiowania są buforowane konfiguracja zostanie zastosowana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="8d813-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="8d813-107">Kolejne aplikacji konfiguracji nie będzie sprawdzać dostępność zaktualizowane pliki lub foldery w ścieżce określonej przez **Ścieżka_źródłowa**.</span><span class="sxs-lookup"><span data-stu-id="8d813-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="8d813-108">Jeśli chcesz wyszukać aktualizacje do plików i/lub folderów w **Ścieżka_źródłowa** za każdym razem, gdy konfiguracja zostanie zastosowana, ustaw **MatchSource** do **$true**.</span><span class="sxs-lookup"><span data-stu-id="8d813-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d813-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d813-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="8d813-110">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8d813-110">Properties</span></span>

|  <span data-ttu-id="8d813-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8d813-111">Property</span></span>  |  <span data-ttu-id="8d813-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8d813-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="8d813-113">Ścieżka_docelowa</span><span class="sxs-lookup"><span data-stu-id="8d813-113">DestinationPath</span></span>| <span data-ttu-id="8d813-114">Wskazuje lokalizację, do której chcesz zapewnić stan pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="8d813-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="8d813-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8d813-115">Attributes</span></span>| <span data-ttu-id="8d813-116">Określa stan odpowiednie atrybuty docelowego pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="8d813-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="8d813-117">Suma kontrolna</span><span class="sxs-lookup"><span data-stu-id="8d813-117">Checksum</span></span>| <span data-ttu-id="8d813-118">Wskazuje typ sumy kontrolnej używany do określenia, czy dwa pliki są takie same.</span><span class="sxs-lookup"><span data-stu-id="8d813-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="8d813-119">Jeśli __sumy kontrolnej__ nie zostanie określona, tylko nazwa pliku lub katalogu jest używana do porównania.</span><span class="sxs-lookup"><span data-stu-id="8d813-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="8d813-120">Prawidłowe wartości to: algorytmu SHA-1, SHA-256, SHA-512, createdDate, Data modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="8d813-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="8d813-121">Zawartość</span><span class="sxs-lookup"><span data-stu-id="8d813-121">Contents</span></span>| <span data-ttu-id="8d813-122">Określa zawartość pliku, takie jak określony ciąg.</span><span class="sxs-lookup"><span data-stu-id="8d813-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="8d813-123">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="8d813-123">Credential</span></span>| <span data-ttu-id="8d813-124">Określa poświadczenia, które są wymagane do dostępu do zasobów, takich jak pliki źródłowe, jeśli taki dostęp jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="8d813-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="8d813-125">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="8d813-125">Ensure</span></span>| <span data-ttu-id="8d813-126">Wskazuje, czy istnieje plik lub katalog.</span><span class="sxs-lookup"><span data-stu-id="8d813-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="8d813-127">Ustaw tę właściwość na "Brak", aby upewnić się, że plik lub katalog nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="8d813-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="8d813-128">Ustaw ją na "Brak", aby upewnić się, że istnieje plik lub katalog.</span><span class="sxs-lookup"><span data-stu-id="8d813-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="8d813-129">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="8d813-129">The default is "Present".</span></span>|
| <span data-ttu-id="8d813-130">Force</span><span class="sxs-lookup"><span data-stu-id="8d813-130">Force</span></span>| <span data-ttu-id="8d813-131">Niektóre operacje na plikach (takie jak zastąpienie pliku lub usuwanie katalogu, który nie jest pusty) spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="8d813-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="8d813-132">Za pomocą właściwości Force zastępuje takie błędy.</span><span class="sxs-lookup"><span data-stu-id="8d813-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="8d813-133">Wartość domyślna to __$false__.</span><span class="sxs-lookup"><span data-stu-id="8d813-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="8d813-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="8d813-134">Recurse</span></span>| <span data-ttu-id="8d813-135">Wskazuje, czy podkatalogi są dołączone.</span><span class="sxs-lookup"><span data-stu-id="8d813-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="8d813-136">Ta właściwość jest ustawiana __$true__ aby wskazać, że chcesz podkatalogów, które zostaną uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="8d813-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="8d813-137">Wartość domyślna to __$false__.</span><span class="sxs-lookup"><span data-stu-id="8d813-137">The default is __$false__.</span></span> <span data-ttu-id="8d813-138">**Uwaga**: Ta właściwość jest prawidłowy tylko, gdy właściwość Type ma ustawioną w katalogu.</span><span class="sxs-lookup"><span data-stu-id="8d813-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="8d813-139">dependsOn</span><span class="sxs-lookup"><span data-stu-id="8d813-139">DependsOn</span></span> | <span data-ttu-id="8d813-140">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="8d813-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8d813-141">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8d813-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="8d813-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="8d813-142">SourcePath</span></span>| <span data-ttu-id="8d813-143">Określa ścieżkę do skopiowania zasobów pliku lub folderu.</span><span class="sxs-lookup"><span data-stu-id="8d813-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="8d813-144">Typ</span><span class="sxs-lookup"><span data-stu-id="8d813-144">Type</span></span>| <span data-ttu-id="8d813-145">Wskazuje, czy zasób konfigurowany jest katalog lub plik.</span><span class="sxs-lookup"><span data-stu-id="8d813-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="8d813-146">Ustaw tę właściwość na "Directory", aby wskazać, czy zasób jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="8d813-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="8d813-147">Ustaw ją na "Plik", aby wskazać, czy zasób jest plik.</span><span class="sxs-lookup"><span data-stu-id="8d813-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="8d813-148">Wartość domyślna to "Plik".</span><span class="sxs-lookup"><span data-stu-id="8d813-148">The default value is “File”.</span></span>|
| <span data-ttu-id="8d813-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="8d813-149">MatchSource</span></span>| <span data-ttu-id="8d813-150">Jeśli ustawiono wartość domyślną __$false__, a następnie wszystkie pliki w źródle (, że pliki A, B i C) zostanie dodany do miejsca docelowego konfiguracja zostanie zastosowana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="8d813-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="8d813-151">Jeśli nowy plik (D) jest dodawany do źródła, jego nie zostanie dodany do miejsca docelowego, nawet wtedy, gdy konfiguracja zostanie zastosowana ponownie później.</span><span class="sxs-lookup"><span data-stu-id="8d813-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="8d813-152">Jeśli wartość jest __$true__, a następnie każdorazowo konfiguracja zostanie zastosowana, nowe pliki później znaleziono w źródle (na przykład plik D, w tym przykładzie) są dodawane do miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="8d813-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="8d813-153">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="8d813-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="8d813-154">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d813-154">Example</span></span>

<span data-ttu-id="8d813-155">Poniższy przykład przedstawia użycie pliku zasobu do upewnij się, że katalog o tej ścieżce `C:\Users\Public\Documents\DSCDemo\DemoSource` w źródle komputera (na przykład serwer "ściągania") występuje również (wraz z wszystkie podkatalogi) w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="8d813-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="8d813-156">Również zapisuje komunikat potwierdzający dziennika po ukończeniu i zawiera instrukcję, aby upewnić się, że operację sprawdzania plików jest uruchamiana przed operację rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="8d813-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```