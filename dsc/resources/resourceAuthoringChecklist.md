---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Lista kontrolna tworzenia zasobu
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076586"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="f1f3c-103">Lista kontrolna tworzenia zasobu</span><span class="sxs-lookup"><span data-stu-id="f1f3c-103">Resource authoring checklist</span></span>

<span data-ttu-id="f1f3c-104">Ta lista kontrolna jest lista najlepszych rozwiązań, podczas tworzenia nowego zasobu DSC.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="f1f3c-105">Moduł zasobów zawiera plik psd1 i schema.mof dla każdego zasobu</span><span class="sxs-lookup"><span data-stu-id="f1f3c-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="f1f3c-106">Sprawdź, czy zasób ma poprawną strukturę i czy zawiera wszystkie wymagane pliki.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="f1f3c-107">Każdy moduł zasobów powinien zawierać plik psd1 i wszystkich zasobów innych niż złożone powinny mieć schema.mof pliku.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="f1f3c-108">Zasoby, które nie zawierają schematu, nie będą wyświetlane przez `Get-DscResource` i użytkownicy nie będą mogli korzystać z funkcji intellisense podczas pisania kodu dla tych modułów w środowisku ISE.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="f1f3c-109">Struktura katalogów xRemoteFile zasobu, który jest częścią programu [moduł zasobów xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="f1f3c-110">Zasób i schematu są poprawne</span><span class="sxs-lookup"><span data-stu-id="f1f3c-110">Resource and schema are correct</span></span>

<span data-ttu-id="f1f3c-111">Sprawdź schematu zasobów (\*. schema.mof) pliku.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="f1f3c-112">Możesz użyć [projektancie zasobów DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) ułatwiające tworzenie i testowanie schematu.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span>
<span data-ttu-id="f1f3c-113">Upewnij się, że:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-113">Make sure that:</span></span>

- <span data-ttu-id="f1f3c-114">Typy właściwości są prawidłowe (np. nie należy używać ciągu dla właściwości, które akceptuje wartości liczbowych, należy użyć UInt32 lub inne typy liczbowe zamiast)</span><span class="sxs-lookup"><span data-stu-id="f1f3c-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="f1f3c-115">Atrybuty właściwości są poprawnie określone jako: ([klucz], [wymagane], [napisać], [do odczytu])</span><span class="sxs-lookup"><span data-stu-id="f1f3c-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="f1f3c-116">Co najmniej jeden parametr w schemacie musi zostać oznaczone jako [klucz]</span><span class="sxs-lookup"><span data-stu-id="f1f3c-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="f1f3c-117">[do odczytu] właściwości nie współistnieć wraz z dowolnego z: [wymagane], [klucz], [zapisu]</span><span class="sxs-lookup"><span data-stu-id="f1f3c-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="f1f3c-118">Jeśli nie określono wiele kwalifikatory z wyjątkiem [do odczytu], następnie [klucz] ma pierwszeństwo przed</span><span class="sxs-lookup"><span data-stu-id="f1f3c-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="f1f3c-119">Jeśli [zapisu] i [wymagane] jest określony, a następnie pierwszeństwo [wymagane]</span><span class="sxs-lookup"><span data-stu-id="f1f3c-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="f1f3c-120">Określono ValueMap przykład zgodnie z wymaganiami:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="f1f3c-121">Przyjazna nazwa jest określona i potwierdza, konwencje nazewnictwa DSC</span><span class="sxs-lookup"><span data-stu-id="f1f3c-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="f1f3c-122">Przykład: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="f1f3c-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="f1f3c-123">Każde pole ma zrozumiały opis.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-123">Every field has meaningful description.</span></span> <span data-ttu-id="f1f3c-124">Repozytorium GitHub dla programu PowerShell ma dobre przykłady, takie jak [. schema.mof dla xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="f1f3c-124">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="f1f3c-125">Ponadto należy używać **xDscResource testu** i **xDscSchema testu** polecenia cmdlet z [projektancie zasobów DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) umożliwia automatyczne weryfikowanie zasobu i schematu:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-125">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="f1f3c-126">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="f1f3c-127">Zasób ładuje się bez błędów</span><span class="sxs-lookup"><span data-stu-id="f1f3c-127">Resource loads without errors</span></span>

<span data-ttu-id="f1f3c-128">Sprawdź, czy moduł zasobów może być załadowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-128">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="f1f3c-129">Można to osiągnąć ręcznie, uruchamiając `Import-Module <resource_module> -force` i potwierdzenie, że nie wystąpiły żadne błędy, lub przez zapisywanie Automatyzacja testów.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="f1f3c-130">W przypadku drugiego nagłówka tej struktury, można wykonać w przypadku testowym:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="f1f3c-131">Zasób jest idempotentna, w tym przypadku dodatnią</span><span class="sxs-lookup"><span data-stu-id="f1f3c-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="f1f3c-132">Jednym z podstawowych charakterystyk zasobów DSC jest idempotentność.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="f1f3c-133">Oznacza to, że trwa operacja zastosowania konfiguracji DSC, zawierająca ten zasób wielokrotnie będzie zawsze ten sam efekt.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="f1f3c-134">Jeśli na przykład możemy utworzyć konfigurację, która zawiera następujące zasoby pliku:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="f1f3c-135">Po zastosowaniu go po raz pierwszy, jako plik powinna zostać wyświetlona w `C:\test` folderu.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="f1f3c-136">Jednak kolejnych uruchomień taką samą konfigurację nie należy zmieniać stan maszyny (np. nie kopie `test.txt` można utworzyć pliku).</span><span class="sxs-lookup"><span data-stu-id="f1f3c-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span>
<span data-ttu-id="f1f3c-137">Aby upewnić się, zasób jest idempotentna, można wywoływać wielokrotnie `Set-TargetResource` podczas testowania zasobu bezpośrednio lub zadzwoń `Start-DscConfiguration` wiele razy podczas wykonywania pełnego testowania.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="f1f3c-138">Wynik powinien być taki sam, po każdym przebiegu.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="f1f3c-139">Scenariusz modyfikacji użytkownika testowego</span><span class="sxs-lookup"><span data-stu-id="f1f3c-139">Test user modification scenario</span></span>

<span data-ttu-id="f1f3c-140">Zmienianie stanu komputera, a następnie ponownemu uruchamianiu DSC, można sprawdzić, czy `Set-TargetResource` i `Test-TargetResource` działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="f1f3c-141">Poniżej przedstawiono kroki, które należy wykonać:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="f1f3c-142">Zacznij od zasobu nie jest w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-142">Start with the resource not in the desired state.</span></span>
2. <span data-ttu-id="f1f3c-143">Uruchom konfigurację z zasobem usługi</span><span class="sxs-lookup"><span data-stu-id="f1f3c-143">Run configuration with your resource</span></span>
3. <span data-ttu-id="f1f3c-144">Sprawdź `Test-DscConfiguration` zwraca wartość True</span><span class="sxs-lookup"><span data-stu-id="f1f3c-144">Verify `Test-DscConfiguration` returns True</span></span>
4. <span data-ttu-id="f1f3c-145">Modyfikowanie skonfigurowany element, aby brakować żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="f1f3c-145">Modify the configured item to be out of the desired state</span></span>
5. <span data-ttu-id="f1f3c-146">Sprawdź `Test-DscConfiguration` zwraca wartość false</span><span class="sxs-lookup"><span data-stu-id="f1f3c-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="f1f3c-147">Oto przykład bardziej konkretne, używając zasobu rejestru:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-147">Here’s a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="f1f3c-148">Uruchom za pomocą klucza rejestru nie jest w żądanym stanie</span><span class="sxs-lookup"><span data-stu-id="f1f3c-148">Start with registry key not in the desired state</span></span>
2. <span data-ttu-id="f1f3c-149">Uruchom `Start-DscConfiguration` przy użyciu konfiguracji, aby umieścić go w żądanym stanie i weryfikować ją przekazuje.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
3. <span data-ttu-id="f1f3c-150">Uruchom `Test-DscConfiguration` i sprawdź, funkcja zwraca wartość true</span><span class="sxs-lookup"><span data-stu-id="f1f3c-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
4. <span data-ttu-id="f1f3c-151">Zmodyfikuj wartość klucza, tak, aby nie jest w żądanym stanie</span><span class="sxs-lookup"><span data-stu-id="f1f3c-151">Modify the value of the key so that it is not in the desired state</span></span>
5. <span data-ttu-id="f1f3c-152">Uruchom `Test-DscConfiguration` i sprawdź, zwraca wartość false</span><span class="sxs-lookup"><span data-stu-id="f1f3c-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
6. <span data-ttu-id="f1f3c-153">`Get-TargetResource` funkcja została zweryfikowana przy użyciu `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="f1f3c-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="f1f3c-154">`Get-TargetResource` powinno zwrócić szczegółowe informacje o bieżącym stanem zasobu.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="f1f3c-155">Pamiętaj ją przetestować, wywołując `Get-DscConfiguration` po zastosowaniu konfiguracji i weryfikowanie, że dane wyjściowe poprawnie odzwierciedla bieżący stan maszyny.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="f1f3c-156">Ważne jest, aby przetestować go oddzielnie, ponieważ wszelkie problemy, w tym obszarze nie będą wyświetlane podczas wywoływania `Start-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="f1f3c-157">Wywołaj **Get/Set/Test-TargetResource** funkcje bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="f1f3c-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="f1f3c-158">Upewnij się, że testujesz **Get/Set/Test-TargetResource** funkcji realizowanych w swoim zasobie, bezpośrednie wywoływanie i weryfikowanie, czy działają one zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="f1f3c-159">Sprawdź przy użyciu typu End to End **Start-DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f1f3c-159">Verify End to End using **Start-DscConfiguration**</span></span>

<span data-ttu-id="f1f3c-160">Testowanie **Get/Set/Test-TargetResource** funkcji przez bezpośrednie wywoływanie jest ważne, ale nie wszystkie problemy zostaną odnalezione w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="f1f3c-161">Należy skoncentrować się znaczna część testowania przy użyciu `Start-DscConfiguration` lub serwerze ściągania.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="f1f3c-162">W rzeczywistości jest to, jak użytkownicy będą używać zasobów, dzięki czemu nie uwzględniać znaczenie tego rodzaju testy.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="f1f3c-163">Możliwe typy problemów:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-163">Possible types of issues:</span></span>

- <span data-ttu-id="f1f3c-164">Poświadczenie/sesji może zachowywać się inaczej agenta DSC jest uruchamiana jako usługa.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="f1f3c-165">Należy przetestować każdej funkcji, w tym miejscu typu end to end.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="f1f3c-166">Błędy generowane przez `Start-DscConfiguration` mogą być inne niż te wyświetlane podczas wywoływania `Set-TargetResource` funkcji bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="f1f3c-167">Platformy obsługiwane przez test zgodności na wszystkich DSC</span><span class="sxs-lookup"><span data-stu-id="f1f3c-167">Test compatability on all DSC supported platforms</span></span>

<span data-ttu-id="f1f3c-168">Zasób powinny działać na wszystkich platformach DSC obsługiwane (Windows Server 2008 R2 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="f1f3c-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="f1f3c-169">Instalowanie najnowszej wersji platformy WMF (Windows Management Framework) dla Twojego systemu operacyjnego, aby pobrać najnowszą wersję DSC.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="f1f3c-170">Jeśli zasób nie działa na niektórych z tych platform zgodnie z projektem, powinny być zwrócone określony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="f1f3c-171">Ponadto upewnij się, że zasób sprawdza, czy polecenia cmdlet wywoływanego są obecne na określonym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="f1f3c-172">Windows Server 2012 dodano dużą liczbą nowych poleceń cmdlet, które nie są dostępne w systemie Windows Server 2008 R2, nawet w przypadku programu WMF zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="f1f3c-173">Sprawdź na kliencie Windows (jeśli dotyczy)</span><span class="sxs-lookup"><span data-stu-id="f1f3c-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="f1f3c-174">Jednym bardzo często przerwy testu jest sprawdzanie zasobów tylko w wersjach server systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="f1f3c-175">Wiele zasobów również zostały zaprojektowane do pracy na jednostki SKU klienta, więc jeśli jest to istotne w Twoim przypadku, nie zapomnij go przetestować na tych platformach, a także.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="f1f3c-176">Get-DSCResource zawiera listę zasobów</span><span class="sxs-lookup"><span data-stu-id="f1f3c-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="f1f3c-177">Po wdrożeniu modułu wywoływania `Get-DscResource` w wyniku pomysłem jest wystawienie zasobu m.in.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="f1f3c-178">Jeśli nie można odnaleźć zasób na liście, upewnij się, ten plik schema.mof dla tego zasobu istnieje.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="f1f3c-179">Moduł zasobów zawiera przykłady</span><span class="sxs-lookup"><span data-stu-id="f1f3c-179">Resource module contains examples</span></span>

<span data-ttu-id="f1f3c-180">Tworzenie przykładów jakości, które ułatwiają innym osobom dowiedzieć się, jak z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="f1f3c-181">Jest to niezwykle istotne, szczególnie w przypadku, ponieważ wielu użytkowników traktować przykładowego kodu jako dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="f1f3c-182">Po pierwsze należy ustalić, przykłady, które zostaną dołączone za pomocą modułu — co najmniej, powinny obejmować najważniejszych przypadków użycia dla zasobu:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="f1f3c-183">Jeśli modułu zawiera kilka zasobów, które wymagają pracy zespołowej, scenariusz end-to-end, w idealnym przypadku będzie istnieć pierwszy przykład podstawowy end-to-end.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="f1f3c-184">Przykłady początkowe powinny być bardzo proste — jak rozpocząć pracę z zasobami w małych partiach łatwych do zarządzania (np. tworzenia nowego wirtualnego dysku twardego)</span><span class="sxs-lookup"><span data-stu-id="f1f3c-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="f1f3c-185">Przykłady kolejnych powinien rozwijać tych przykładów (np. Tworzenie maszyny Wirtualnej z dysku VHD, usunięcie maszyny Wirtualnej, modyfikując maszyn wirtualnych) i wyświetlania informacji dotyczących zaawansowanych funkcji (np. Tworzenie maszyny Wirtualnej z pamięcią dynamiczną)</span><span class="sxs-lookup"><span data-stu-id="f1f3c-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="f1f3c-186">Przykładowe konfiguracje należy ustawiać parametry (wszystkie wartości mają być przekazywane do konfiguracji jako parametry i powinno być żadnych wartości zapisane na stałe):</span><span class="sxs-lookup"><span data-stu-id="f1f3c-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- <span data-ttu-id="f1f3c-187">Jest dobrym rozwiązaniem, aby uwzględnić (out) komentarzami przykładem wywołania konfiguracji przy użyciu rzeczywistych wartości na końcu przykładowy skrypt.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
  <span data-ttu-id="f1f3c-188">Na przykład w powyższej konfiguracji nie jest koniecznie oczywiste, że najlepszym sposobem, aby określić UserAgent jest:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="f1f3c-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` W tym przypadku komentarz może wyjaśnić zamierzony wykonanie konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- <span data-ttu-id="f1f3c-190">W każdym przykładzie krótki opis, który wyjaśnia, co robi i zapisywać znaczenie parametrów.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="f1f3c-191">Upewnij się, przykłady obejmują większość ważnych scenariuszy zasobu bazy danych i jeśli nic nie brakuje, sprawdź, czy wszystkie wykonania i przełączyć maszynę w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="f1f3c-192">Komunikaty o błędach są łatwe do zrozumienia i pomaganie użytkownikom w rozwiązywaniu problemów</span><span class="sxs-lookup"><span data-stu-id="f1f3c-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="f1f3c-193">Komunikaty o błędach dobre powinny być następujące:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-193">Good error messages should be:</span></span>

- <span data-ttu-id="f1f3c-194">Brak: Największy problem z komunikatami o błędach jest często nie istnieje, dlatego upewnij się, że są one dostępne.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="f1f3c-195">Łatwe do zrozumienia: Kody błędów ludzkich możliwy do odczytu, nie zasłoniętej</span><span class="sxs-lookup"><span data-stu-id="f1f3c-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="f1f3c-196">Dokładny: Opisano, jakie dokładnie problem</span><span class="sxs-lookup"><span data-stu-id="f1f3c-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="f1f3c-197">Konstruktywnych informacji: Porady dotyczące sposobu rozwiązania problemu</span><span class="sxs-lookup"><span data-stu-id="f1f3c-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="f1f3c-198">Proces łagodnego: Nie blame użytkownika lub stały się, że nieprawidłowe</span><span class="sxs-lookup"><span data-stu-id="f1f3c-198">Polite: Don’t blame user or make them feel bad</span></span>

<span data-ttu-id="f1f3c-199">Upewnij się, sprawdź błędy w scenariuszach typu End to End (przy użyciu `Start-DscConfiguration`), ponieważ one mogą się różnić od tych zwracane po uruchomieniu funkcji zasobów bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="f1f3c-200">Komunikaty dziennika są łatwe do zrozumienia i informacyjnej (w tym — pełne, — debugowania, jak i dzienniki zdarzeń systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="f1f3c-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="f1f3c-201">Upewnij się, że dzienniki zwrócone przez zasób są łatwe do zrozumienia i podać wartość dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="f1f3c-202">Zasoby ma produkt wyjściowy wszystkie informacje, które mogą być pomocne dla użytkowników, ale nie więcej dzienników zawsze jest lepiej.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="f1f3c-203">Należy unikać nadmiarowości i wyprowadzanie danych, które nie zapewniają dodatkową wartość — nie należy ktoś przechodzą przez setki wpisy dziennika, aby można było znaleźć, czego szukają.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-203">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="f1f3c-204">Oczywiście żadne dzienniki nie jest to dopuszczalne rozwiązanie tego problemu albo.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="f1f3c-205">Podczas testowania, należy również analizować pełne i debugowania dzienniki (uruchamiając `Start-DscConfiguration` z `–Verbose` i `–Debug` zmienia odpowiednio), jak również jako dzienniki zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="f1f3c-206">Aby wyświetlić dzienniki DSC ETW, przejdź do podglądu zdarzeń, a następnie otwórz następujący folder: Aplikacje i usługi firmy Microsoft - Windows - Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="f1f3c-207">Domyślnie zostanie kanał operacyjny, ale upewnij się, możesz włączyć analityczne i debugowania kanały przed uruchomieniem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="f1f3c-208">Aby włączyć kanały analityczne/Debug, można wykonać poniższy skrypt:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="f1f3c-209">Implementacja zasób nie zawiera ścieżki zapisane na stałe</span><span class="sxs-lookup"><span data-stu-id="f1f3c-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="f1f3c-210">Upewnij się w implementacji zasobów istnieje nie ścieżek zapisane na stałe, zwłaszcza w przypadku, gdy zakładają też języka (en-us), lub gdy występują zmiennych systemowych, które mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="f1f3c-211">Jeśli dostęp do określonej ścieżki, użyj zmiennych środowiskowych zamiast hardcoding zasobu ścieżki, ponieważ mogą się różnić na innych komputerach.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="f1f3c-212">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-212">Example:</span></span>

<span data-ttu-id="f1f3c-213">Zamiast:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="f1f3c-214">można napisać:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="f1f3c-215">Implementacja zasobów nie zawiera informacji o użytkowniku</span><span class="sxs-lookup"><span data-stu-id="f1f3c-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="f1f3c-216">Upewnij się, że nie ma żadnych wiadomości e-mail, informacje o koncie, nazwiska lub nazwy osoby w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="f1f3c-217">Zasób został przetestowany z prawidłową nieprawidłowe poświadczenia</span><span class="sxs-lookup"><span data-stu-id="f1f3c-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="f1f3c-218">Jeśli zasób przyjmuje poświadczenia, jako parametr:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="f1f3c-219">Sprawdź, czy zasób działa, gdy System lokalny (lub konto komputera dla zasobów zdalnych) nie ma dostępu.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="f1f3c-220">Sprawdź działa zasobów przy użyciu poświadczeń, określony dla pobierania ustawiania i testowanie</span><span class="sxs-lookup"><span data-stu-id="f1f3c-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="f1f3c-221">Jeśli zasób uzyskuje dostęp do udziałów, przetestuj wszystkich wariantów, czego potrzebujesz do obsługi, takie jak:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="f1f3c-222">Standardowy system windows udziałów.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-222">Standard windows shares.</span></span>
  - <span data-ttu-id="f1f3c-223">Udziały systemu plików DFS.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-223">DFS shares.</span></span>
  - <span data-ttu-id="f1f3c-224">Udziały SAMBA (jeśli mają być obsługiwane systemu Linux.)</span><span class="sxs-lookup"><span data-stu-id="f1f3c-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="f1f3c-225">Zasób nie wymaga wprowadzania interaktywne</span><span class="sxs-lookup"><span data-stu-id="f1f3c-225">Resource does not require interactive input</span></span>

<span data-ttu-id="f1f3c-226">**Get/Set/Test-TargetResource** funkcje mają zostać wykonane automatycznie i nie należy czekać do wejściowych użytkownika na każdym etapie cyklu wykonywania (np. nie należy używać `Get-Credential` wewnątrz tych funkcji).</span><span class="sxs-lookup"><span data-stu-id="f1f3c-226">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="f1f3c-227">Jeśli musisz podać dane wejściowe użytkownika, należy przekazać go do konfiguracji jako parametr w fazie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-227">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="f1f3c-228">Funkcje zasobów została dokładnie przetestowana.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="f1f3c-229">Ta lista kontrolna zawiera elementy, które są ważne do zbadania i/lub często zostaną pominięte.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="f1f3c-230">Będzie istnieć wiele testów, głównie funkcjonalności te, które są specyficzne dla zasobu, testowania i nie są tutaj wymienione.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="f1f3c-231">Nie zapomnij o ujemna przypadków testowych.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-231">Don’t forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="f1f3c-232">Najlepszym rozwiązaniem jest: Moduł zasobów zawiera folder testy za pomocą skryptu ResourceDesignerTests.ps1</span><span class="sxs-lookup"><span data-stu-id="f1f3c-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="f1f3c-233">Jest dobrą praktyką jest tworzenie folderu "testy" wewnątrz modułu zasobów, tworzenie `ResourceDesignerTests.ps1` pliku i Dodaj testy przy użyciu **xDscResource testu** i **xDscSchema testu** dla wszystkich zasobów w danych modułu.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-233">It’s a good practice to create folder “Tests” inside resource module, create `ResourceDesignerTests.ps1` file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="f1f3c-234">Dzięki temu można szybko sprawdzić poprawność schematów wszystkie zasoby z danym modułów i nie wykonuje sprawdzanie przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="f1f3c-235">Aby uzyskać xRemoteFile `ResourceTests.ps1` mogłoby wyglądać tak proste, jak:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="f1f3c-236">Najlepszym rozwiązaniem jest: Folder zasobów zawiera zasób skryptu projektanta do generowania schematu</span><span class="sxs-lookup"><span data-stu-id="f1f3c-236">Best practice: Resource folder contains resource designer script for generating schema</span></span>

<span data-ttu-id="f1f3c-237">Każdy zasób może zawierać zasobu skryptu projektanta, które generuje schemat mof zasobu.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-237">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="f1f3c-238">Ten plik należy umieścić w `<ResourceName>\ResourceDesignerScripts` i będzie nosić nazwę Generuj `<ResourceName>Schema.ps1` dla zasobu xRemoteFile ten plik będzie nazywany `GenerateXRemoteFileSchema.ps1` i zawierać:</span><span class="sxs-lookup"><span data-stu-id="f1f3c-238">This file should be placed in `<ResourceName>\ResourceDesignerScripts` and be named Generate `<ResourceName>Schema.ps1` For xRemoteFile resource this file would be called `GenerateXRemoteFileSchema.ps1` and contain:</span></span>

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="f1f3c-239">Najlepszym rozwiązaniem jest: Zasób obsługuje - WhatIf</span><span class="sxs-lookup"><span data-stu-id="f1f3c-239">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="f1f3c-240">Jeśli zasób jest wykonywanie operacji "niebezpiecznych", jest dobrym rozwiązaniem, aby zaimplementować `-WhatIf` funkcji.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-240">If your resource is performing “dangerous” operations, it’s a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="f1f3c-241">Po zakończeniu upewnij się, że `-WhatIf` dane wyjściowe poprawnie opisuje operacje, co się stanie, jeśli polecenie zostało wykonane bez `-WhatIf` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-241">After it’s done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span>
<span data-ttu-id="f1f3c-242">Sprawdź także, czy nie jest wykonywane operacje (nie do stanu węzła zmian) podczas `–WhatIf` przełącznik jest obecny.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-242">Also, verify that operations does not execute (no changes to the node’s state are made) when `–WhatIf` switch is present.</span></span>
<span data-ttu-id="f1f3c-243">Załóżmy na przykład, że testujemy pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-243">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="f1f3c-244">Poniżej znajduje się prostej konfiguracji, co powoduje utworzenie pliku `test.txt` z zawartością "test":</span><span class="sxs-lookup"><span data-stu-id="f1f3c-244">Below is simple configuration which creates file `test.txt` with contents “test”:</span></span>

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

<span data-ttu-id="f1f3c-245">Jeśli firma Microsoft kompilacji, a następnie wykonanie konfiguracji z `-WhatIf` przełącznika, dane wyjściowe informuje NAS, dokładnie co się stanie, gdy Uruchamiamy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-245">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="f1f3c-246">Konfiguracja samego jednak nie zostało wykonane (`test.txt` nie utworzono pliku).</span><span class="sxs-lookup"><span data-stu-id="f1f3c-246">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="f1f3c-247">Ta lista nie jest wyczerpująca, ale obejmuje wiele ważnych kwestii, które można napotkać podczas projektowania, opracowywania i testowania zasoby DSC.</span><span class="sxs-lookup"><span data-stu-id="f1f3c-247">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
