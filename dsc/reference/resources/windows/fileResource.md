---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC plików
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077334"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="f3f5e-103">Zasób DSC plików</span><span class="sxs-lookup"><span data-stu-id="f3f5e-103">DSC File Resource</span></span>

> <span data-ttu-id="f3f5e-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f3f5e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f3f5e-105">Zasób pliku w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania plikami i folderami w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="f3f5e-106">**Ścieżka_docelowa** i **Ścieżka_źródłowa** muszą być dostępne w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-106">The **DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3f5e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3f5e-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f3f5e-108">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f3f5e-108">Properties</span></span>

|<span data-ttu-id="f3f5e-109">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f3f5e-109">Property</span></span>       |<span data-ttu-id="f3f5e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f3f5e-110">Description</span></span>                                                                   |<span data-ttu-id="f3f5e-111">Wymagana</span><span class="sxs-lookup"><span data-stu-id="f3f5e-111">Required</span></span>|<span data-ttu-id="f3f5e-112">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="f3f5e-112">Default</span></span>|
|---------------|------------------------------------------------------------------------------|--------|-------|
|<span data-ttu-id="f3f5e-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="f3f5e-113">DestinationPath</span></span>|<span data-ttu-id="f3f5e-114">Lokalizacja, w węźle docelowym, aby mieć pewność, jest `Present` lub `Absent`.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-114">The location, on the target node, you want to ensure is `Present` or `Absent`.</span></span>|<span data-ttu-id="f3f5e-115">Tak</span><span class="sxs-lookup"><span data-stu-id="f3f5e-115">Yes</span></span>|<span data-ttu-id="f3f5e-116">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-116">No</span></span>|
|<span data-ttu-id="f3f5e-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f3f5e-117">Attributes</span></span>     |<span data-ttu-id="f3f5e-118">Żądany stan atrybutów dla pliku docelowego lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-118">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="f3f5e-119">Prawidłowe wartości to **archiwum**, **ukryty**, **tylko do odczytu**, i **systemu**.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-119">Valid values are **Archive**, **Hidden**, **ReadOnly**, and **System**.</span></span>|<span data-ttu-id="f3f5e-120">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-120">No</span></span>|<span data-ttu-id="f3f5e-121">Brak</span><span class="sxs-lookup"><span data-stu-id="f3f5e-121">None</span></span>|
|<span data-ttu-id="f3f5e-122">Sumy kontrolnej</span><span class="sxs-lookup"><span data-stu-id="f3f5e-122">Checksum</span></span>      |<span data-ttu-id="f3f5e-123">Typ sumy kontrolnej używany do określenia, czy dwa pliki są takie same.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-123">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="f3f5e-124">Prawidłowe wartości to: SHA-1, SHA-256, SHA-512, createdDate, Data modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-124">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|<span data-ttu-id="f3f5e-125">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-125">No</span></span>|<span data-ttu-id="f3f5e-126">Tylko nazwę pliku lub katalogu jest porównywany.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-126">Only the file or directory name is compared.</span></span>|
|<span data-ttu-id="f3f5e-127">Zawartość</span><span class="sxs-lookup"><span data-stu-id="f3f5e-127">Contents</span></span>       |<span data-ttu-id="f3f5e-128">Prawidłowa tylko w przypadku korzystania z `File` typu.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-128">Only valid when used with `File` type.</span></span> <span data-ttu-id="f3f5e-129">Wskazuje zawartość, aby upewnij się, że są `Present` lub `Absent` z pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-129">Indicates the contents to Ensure are `Present` or `Absent` from the targeted file.</span></span> |<span data-ttu-id="f3f5e-130">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-130">No</span></span>|<span data-ttu-id="f3f5e-131">Brak</span><span class="sxs-lookup"><span data-stu-id="f3f5e-131">None</span></span>|
|<span data-ttu-id="f3f5e-132">Poświadczenie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-132">Credential</span></span>     |<span data-ttu-id="f3f5e-133">Poświadczenia, które są wymagane do dostępu do zasobów, takich jak pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-133">The credentials that are required to access resources, such as source files.</span></span>|<span data-ttu-id="f3f5e-134">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-134">No</span></span>|<span data-ttu-id="f3f5e-135">Konto komputera węzła docelowego.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-135">The target node's Computer Account.</span></span> <span data-ttu-id="f3f5e-136">(*patrz Uwaga*)</span><span class="sxs-lookup"><span data-stu-id="f3f5e-136">(*see note*)</span></span>|
|<span data-ttu-id="f3f5e-137">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="f3f5e-137">Ensure</span></span>         |<span data-ttu-id="f3f5e-138">Żądany stan docelowego pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-138">The desired state of the target file or directory.</span></span> |<span data-ttu-id="f3f5e-139">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-139">No</span></span>|<span data-ttu-id="f3f5e-140">**Obecna**</span><span class="sxs-lookup"><span data-stu-id="f3f5e-140">**Present**</span></span>|
|<span data-ttu-id="f3f5e-141">Force</span><span class="sxs-lookup"><span data-stu-id="f3f5e-141">Force</span></span>          |<span data-ttu-id="f3f5e-142">Zastępuje operacji dostępu, które mogłyby spowodować błąd (np. zastąpienie pliku lub usunięcie katalogu, który nie jest pusty).</span><span class="sxs-lookup"><span data-stu-id="f3f5e-142">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span>|<span data-ttu-id="f3f5e-143">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-143">No</span></span>|`$false`|
|<span data-ttu-id="f3f5e-144">Recurse</span><span class="sxs-lookup"><span data-stu-id="f3f5e-144">Recurse</span></span>        |<span data-ttu-id="f3f5e-145">Prawidłowa tylko w przypadku korzystania z `Directory` typu.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-145">Only valid when used with `Directory` type.</span></span> <span data-ttu-id="f3f5e-146">Wykonuje rekursywnego operacji stan do wszystkich podkatalogów.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-146">Performs the state operation recursively to all subdirectories.</span></span>|<span data-ttu-id="f3f5e-147">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-147">No</span></span>|`$false`|
|<span data-ttu-id="f3f5e-148">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f3f5e-148">DependsOn</span></span>      |<span data-ttu-id="f3f5e-149">Ustawia zależność określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-149">Sets a dependency on specified resource(s).</span></span> <span data-ttu-id="f3f5e-150">Ten zasób będzie wykonywane tylko wtedy po pomyślnym wykonaniu wszystkich zasobów zależnych.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-150">This resource will only execute after successful execution of any dependent resources.</span></span> <span data-ttu-id="f3f5e-151">Można określić zasoby zależne, używając składni `"[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-151">You can specify dependent resources using the syntax `"[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="f3f5e-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="f3f5e-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span></span>|<span data-ttu-id="f3f5e-153">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-153">No</span></span>|<span data-ttu-id="f3f5e-154">Brak</span><span class="sxs-lookup"><span data-stu-id="f3f5e-154">None</span></span>|
|<span data-ttu-id="f3f5e-155">SourcePath</span><span class="sxs-lookup"><span data-stu-id="f3f5e-155">SourcePath</span></span>     |<span data-ttu-id="f3f5e-156">Ścieżka, z którego można skopiować zasobu pliku lub folderu.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-156">The path from which to copy the file or folder resource.</span></span>|<span data-ttu-id="f3f5e-157">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-157">No</span></span>|<span data-ttu-id="f3f5e-158">Brak</span><span class="sxs-lookup"><span data-stu-id="f3f5e-158">None</span></span>|
|<span data-ttu-id="f3f5e-159">Typ</span><span class="sxs-lookup"><span data-stu-id="f3f5e-159">Type</span></span>           |<span data-ttu-id="f3f5e-160">Typ zasobu jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-160">The type of resource being configured.</span></span> <span data-ttu-id="f3f5e-161">Prawidłowe wartości to `Directory` i `File`.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-161">Valid values are `Directory` and `File`.</span></span>|<span data-ttu-id="f3f5e-162">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-162">No</span></span>|`File`|
|<span data-ttu-id="f3f5e-163">MatchSource</span><span class="sxs-lookup"><span data-stu-id="f3f5e-163">MatchSource</span></span>    |<span data-ttu-id="f3f5e-164">Określa, jeśli zasób powinien monitorować nowe pliki dodane do katalogu źródłowego po kopii początkowej.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-164">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="f3f5e-165">Wartość `$true` wskazuje, że po kopii początkowej, wszystkie nowe pliki źródłowe zostaną skopiowane do lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-165">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="f3f5e-166">Jeśli ustawiono `$False`, zasób buforuje zawartość katalogu źródłowego i ignoruje wszelkie pliki dodane po kopii początkowej.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-166">If set to `$False`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span>|<span data-ttu-id="f3f5e-167">Nie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-167">No</span></span>|`$false`|

> [!WARNING]
> <span data-ttu-id="f3f5e-168">Jeśli nie określisz wartości `Credential` lub `PSRunAsCredential` (PS V.5), zasób będzie używał konta komputera węzła docelowego w dostęp do `SourcePath`.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-168">If you do not specify a value for `Credential` or `PSRunAsCredential` (PS V.5), the resource will use the computer account of the target node to access the `SourcePath`.</span></span>  <span data-ttu-id="f3f5e-169">Gdy `SourcePath` jest udziału UNC, może to spowodować błąd "Odmowa dostępu".</span><span class="sxs-lookup"><span data-stu-id="f3f5e-169">When the `SourcePath` is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="f3f5e-170">Upewnij się, Twoje uprawnienia są odpowiednio ustawiane lub użyj `Credential` lub `PSRunAsCredential` właściwości, aby określić konto, które mają być używane.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-170">Please ensure your permissions are set accordingly, or use the `Credential` or `PSRunAsCredential` properties to specify the account that should be used.</span></span>

## <a name="present-vs-absent"></a><span data-ttu-id="f3f5e-171">Przedstawia programu vs. Nieobecny</span><span class="sxs-lookup"><span data-stu-id="f3f5e-171">Present vs. Absent</span></span>

<span data-ttu-id="f3f5e-172">Każdy zasób DSC wykonuje różne operacje, w oparciu o wartość określona dla `Ensure` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-172">Each DSC resource performs different operations based on the value you specify for the `Ensure` property.</span></span> <span data-ttu-id="f3f5e-173">Wartości, które określisz dla powyższych właściwości określa operacji stanu wykonywane.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-173">The values you specify for the above properties determines the state operation performed.</span></span>

### <a name="existence"></a><span data-ttu-id="f3f5e-174">Istnienie</span><span class="sxs-lookup"><span data-stu-id="f3f5e-174">Existence</span></span>

<span data-ttu-id="f3f5e-175">Kiedy należy określić tylko `DestinationPath`, zasób zapewnia, że ścieżka istnieje (`Present`) lub nie istnieje (`Absent`).</span><span class="sxs-lookup"><span data-stu-id="f3f5e-175">When you only specify a `DestinationPath`, the resource ensures that the path exists (`Present`) or does not exist (`Absent`).</span></span>

### <a name="copy-operations"></a><span data-ttu-id="f3f5e-176">Operacje kopiowania</span><span class="sxs-lookup"><span data-stu-id="f3f5e-176">Copy Operations</span></span>

<span data-ttu-id="f3f5e-177">Po określeniu `SourcePath` i `DestinationPath` z `Type` wartość **katalogu**, katalog zasobów kopii źródłowej w ścieżce docelowej.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-177">When you specify a `SourcePath` and a `DestinationPath` with a `Type` value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="f3f5e-178">Właściwości `Recurse`, `Force`, i `MatchSource` Zmień typ operacji kopiowania wykonywania, podczas gdy `Credential` Określa konto, które umożliwia uzyskanie dostępu do katalogu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-178">The properties `Recurse`, `Force`, and `MatchSource` change the type of copy operation performed, while `Credential` determines which account to use to access the source directory.</span></span>

### <a name="limitations"></a><span data-ttu-id="f3f5e-179">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="f3f5e-179">Limitations</span></span>

<span data-ttu-id="f3f5e-180">Jeśli określona wartość `ReadOnly` dla `Attributes` właściwości wraz z `DestinationPath`, `Ensure = "Present"` utworzyłoby podanej ścieżki, podczas gdy `Contents` ustawiał zawartość pliku.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-180">If you specified a value of `ReadOnly` for the `Attributes` property alongside a `DestinationPath`, `Ensure = "Present"` would create the path specified, while `Contents` would set the contents of the file.</span></span>  <span data-ttu-id="f3f5e-181">`Absent` Będzie ignorować stan operacji `Attributes` właściwość całkowicie i Usuń każdy plik w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-181">An `Absent` state operation would ignore the `Attributes` property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="f3f5e-182">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3f5e-182">Example</span></span>

<span data-ttu-id="f3f5e-183">Poniższy przykład kopiuje katalog i jego podkatalogach z serwera ściągania z węzłem docelowym przy użyciu pliku zasobu.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-183">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="f3f5e-184">Jeśli operacja się powiedzie, zasób dziennika zapisuje komunikat z potwierdzeniem w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-184">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="f3f5e-185">Katalog źródłowy jest ścieżką UNC (`\\PullServer\DemoSource`) udostępnionych z serwera ściągania.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-185">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="f3f5e-186">`Recurse` Właściwości gwarantuje, że wszystkie podkatalogi są również kopiowane.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-186">The `Recurse` property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3f5e-187">LCM w docelowym węźle wykonuje w kontekście lokalnego konta systemowego, domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-187">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="f3f5e-188">Aby udzielić dostępu do **Ścieżka_źródłowa**, nadać kontu komputera węzła docelowego odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-188">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="f3f5e-189">**Poświadczeń** i **PSDSCRunAsCredential** (v5) zarówno zmienić używa kontekstu LCM, aby uzyskać dostęp do **Ścieżka_źródłowa**.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-189">The **Credential** and **PSDSCRunAsCredential** (v5) both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="f3f5e-190">Nadal musisz udzielić dostępu do konta, które będą używane do dostępu **Ścieżka_źródłowa**.</span><span class="sxs-lookup"><span data-stu-id="f3f5e-190">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="f3f5e-191">Więcej używania na **poświadczenia** Zobacz DSC [Uruchom jako użytkownik](../../../configurations/runAsUser.md) lub [poświadczenia dostępu do danych konfiguracji](../../../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="f3f5e-191">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
