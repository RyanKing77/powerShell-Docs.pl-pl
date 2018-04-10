---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Lista kontrolna tworzenia zasobu
ms.openlocfilehash: 39f652b458702dc7e815ab4b2f965e6728fa1b51
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="211e2-103">Lista kontrolna tworzenia zasobu</span><span class="sxs-lookup"><span data-stu-id="211e2-103">Resource authoring checklist</span></span>
<span data-ttu-id="211e2-104">Ta lista kontrolna znajduje się lista najlepszych praktyk podczas tworzenia nowego zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="211e2-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="211e2-105">Moduł zasobu zawiera plik psd1 i schema.mof dla każdego zasobu</span><span class="sxs-lookup"><span data-stu-id="211e2-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>
<span data-ttu-id="211e2-106">Sprawdź, czy zasób ma poprawną strukturę i czy zawiera wszystkie wymagane pliki.</span><span class="sxs-lookup"><span data-stu-id="211e2-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="211e2-107">Każdy moduł zasobów musi zawierać plik psd1 i każdy zasób złożone z systemem innym niż powinien mieć schema.mof pliku.</span><span class="sxs-lookup"><span data-stu-id="211e2-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="211e2-108">Zasoby, które nie zawierają schematu nie są wyświetlane przez **Get-DscResource** i użytkownicy nie będą mogły używać funkcji intellisense podczas pisania kodu dla tych modułów w ISE.</span><span class="sxs-lookup"><span data-stu-id="211e2-108">Resources that do not contain schema will not be listed by **Get-DscResource** and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="211e2-109">Struktura katalogów xRemoteFile zasobu, który jest częścią programu [moduł zasobów xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="211e2-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>


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

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="211e2-110">Zasób i schematu są prawidłowe ##</span><span class="sxs-lookup"><span data-stu-id="211e2-110">Resource and schema are correct##</span></span>
<span data-ttu-id="211e2-111">Sprawdź schemat zasobów (\*. schema.mof) pliku.</span><span class="sxs-lookup"><span data-stu-id="211e2-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="211e2-112">Można użyć [projektanta zasobów DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) ułatwiające opracowanie i przetestowanie schematu.</span><span class="sxs-lookup"><span data-stu-id="211e2-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to help develop and test your schema.</span></span>
<span data-ttu-id="211e2-113">Upewnij się, że:</span><span class="sxs-lookup"><span data-stu-id="211e2-113">Make sure that:</span></span>
- <span data-ttu-id="211e2-114">Typy właściwości są prawidłowe (np. nie używaj ciąg dla właściwości, które akceptuje wartości liczbowe, należy użyć UInt32 lub inne typy liczbowe zamiast tego)</span><span class="sxs-lookup"><span data-stu-id="211e2-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="211e2-115">Atrybuty właściwości są określone poprawnie jako: ([klucz], [wymagane], [zapisu], [read])</span><span class="sxs-lookup"><span data-stu-id="211e2-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="211e2-116">Co najmniej jeden parametr w schemacie musi być oznaczony jako [klucz]</span><span class="sxs-lookup"><span data-stu-id="211e2-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="211e2-117">[read] właściwości nie współistnieć wraz z dowolną z: [wymagane], [klucz], [zapisu]</span><span class="sxs-lookup"><span data-stu-id="211e2-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="211e2-118">Jeśli określonych jest wiele kwalifikatory z wyjątkiem [odczytu], następnie [klucz] ma pierwszeństwo przed</span><span class="sxs-lookup"><span data-stu-id="211e2-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="211e2-119">Jeśli [zapisu] i [wymagane] jest określona, a następnie pierwszeństwo będzie miała [wymagane]</span><span class="sxs-lookup"><span data-stu-id="211e2-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="211e2-120">ValueMap jest określony w miarę potrzeb</span><span class="sxs-lookup"><span data-stu-id="211e2-120">ValueMap is specified where appropriate</span></span>

<span data-ttu-id="211e2-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="211e2-121">Example:</span></span>
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- <span data-ttu-id="211e2-122">Przyjazna nazwa jest określona i potwierdza, DSC konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="211e2-122">Friendly name is specified and confirms to DSC naming conventions</span></span>

<span data-ttu-id="211e2-123">Przykład: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span><span class="sxs-lookup"><span data-stu-id="211e2-123">Example: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span></span>

- <span data-ttu-id="211e2-124">Każde pole ma zrozumiały opis.</span><span class="sxs-lookup"><span data-stu-id="211e2-124">Every field has meaningful description.</span></span> <span data-ttu-id="211e2-125">Repozytorium PowerShell GitHub ma dobre przykłady, takich jak [. schema.mof dla xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="211e2-125">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="211e2-126">Ponadto należy używać **xDscResource testu** i **xDscSchema testu** poleceń cmdlet z [projektanta zasobów DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) automatycznie sprawdzić zasobów i schematu:</span><span class="sxs-lookup"><span data-stu-id="211e2-126">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to automatically verify the resource and schema:</span></span>
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
<span data-ttu-id="211e2-127">Przykład:</span><span class="sxs-lookup"><span data-stu-id="211e2-127">For example:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="211e2-128">Obciążenia zasobów bez błędów</span><span class="sxs-lookup"><span data-stu-id="211e2-128">Resource loads without errors</span></span> ##
<span data-ttu-id="211e2-129">Sprawdź, czy moduł zasobów można pomyślnie załadować.</span><span class="sxs-lookup"><span data-stu-id="211e2-129">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="211e2-130">Można to osiągnąć ręcznie, uruchamiając `Import-Module <resource_module> -force ` i potwierdzenie, że nie wystąpiły żadne błędy, lub przez zapisywanie automatyzacji testów.</span><span class="sxs-lookup"><span data-stu-id="211e2-130">This can be achieved manually, by running `Import-Module <resource_module> -force ` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="211e2-131">W przypadku drugiego nagłówka tej struktury można wykonać w przypadku testowego:</span><span class="sxs-lookup"><span data-stu-id="211e2-131">In case of the latter, you can follow this structure in your test case:</span></span>
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="211e2-132">Zasób jest idempotentności w przypadku dodatnią</span><span class="sxs-lookup"><span data-stu-id="211e2-132">Resource is idempotent in the positive case</span></span>
<span data-ttu-id="211e2-133">Jeden z podstawowych właściwości zasobów DSC jest projektu.</span><span class="sxs-lookup"><span data-stu-id="211e2-133">One of the fundamental characteristics of DSC resources is be idempotence.</span></span> <span data-ttu-id="211e2-134">Oznacza to, że stosowania konfiguracji DSC, zawierający wiele razy ten zasób będzie zawsze osiągnąć ten sam rezultat.</span><span class="sxs-lookup"><span data-stu-id="211e2-134">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="211e2-135">Jeśli na przykład utworzymy konfigurację, która zawiera zasób następujących plików:</span><span class="sxs-lookup"><span data-stu-id="211e2-135">For example, if we create a configuration which contains the following File resource:</span></span>
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```
<span data-ttu-id="211e2-136">Po zastosowaniu go po raz pierwszy, test.txt pliku powinna pojawić się w folderze C:\test.</span><span class="sxs-lookup"><span data-stu-id="211e2-136">After applying it for the first time, file test.txt should appear in C:\test folder.</span></span> <span data-ttu-id="211e2-137">Jednak kolejnych uruchomieniach taką samą konfigurację, nie należy zmieniać stan maszyny (np. Brak kopii pliku test.txt należy utworzyć).</span><span class="sxs-lookup"><span data-stu-id="211e2-137">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the test.txt file should be created).</span></span>
<span data-ttu-id="211e2-138">Zapewnienie zasób jest idempotentności można wywoływać wielokrotnie **TargetResource zestaw** podczas testowania zasobu bezpośrednio, lub zadzwoń **Start DscConfiguration** wiele razy w przypadku przeprowadzania pełnego testowania.</span><span class="sxs-lookup"><span data-stu-id="211e2-138">To ensure a resource is idempotent you can repeatedly call **Set-TargetResource** when testing the resource directly, or call **Start-DscConfiguration** multiple times when doing end to end testing.</span></span> <span data-ttu-id="211e2-139">Wynik powinien być taki sam po każdym Uruchom.</span><span class="sxs-lookup"><span data-stu-id="211e2-139">The result should be the same after every run.</span></span>


## <a name="test-user-modification-scenario"></a><span data-ttu-id="211e2-140">Scenariusz modyfikacji użytkownika testowego</span><span class="sxs-lookup"><span data-stu-id="211e2-140">Test user modification scenario</span></span> ##
<span data-ttu-id="211e2-141">Zmienianie stanu urządzenia i ponowne uruchomienie usługi Konfiguracja DSC, można sprawdzić, czy **TargetResource zestaw** i **TargetResource testu** działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="211e2-141">By changing the state of the machine and then rerunning DSC, you can verify that **Set-TargetResource** and **Test-TargetResource** function properly.</span></span> <span data-ttu-id="211e2-142">Poniżej przedstawiono kroki, które należy wykonać:</span><span class="sxs-lookup"><span data-stu-id="211e2-142">Here are steps you should take:</span></span>
1.  <span data-ttu-id="211e2-143">Rozpocznij od zasobu nie jest w stanie żądany.</span><span class="sxs-lookup"><span data-stu-id="211e2-143">Start with the resource not in the desired state.</span></span>
2.  <span data-ttu-id="211e2-144">Konfiguracja uruchomieniowa o zasobie</span><span class="sxs-lookup"><span data-stu-id="211e2-144">Run configuration with your resource</span></span>
3.  <span data-ttu-id="211e2-145">Sprawdź **DscConfiguration testu** zwraca wartość True</span><span class="sxs-lookup"><span data-stu-id="211e2-145">Verify **Test-DscConfiguration** returns True</span></span>
4.  <span data-ttu-id="211e2-146">Zmodyfikuj element skonfigurowanych poza żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="211e2-146">Modify the configured item to be out of the desired state</span></span>
5.  <span data-ttu-id="211e2-147">Sprawdź **DscConfiguration testu** zwraca wartość false, w tym miejscu jest bardziej konkretny przykład przy użyciu zasobów rejestru:</span><span class="sxs-lookup"><span data-stu-id="211e2-147">Verify **Test-DscConfiguration** returns false Here’s a more concrete example using Registry resource:</span></span>
1.  <span data-ttu-id="211e2-148">Uruchom z kluczem rejestru nie jest w stanie żądaną</span><span class="sxs-lookup"><span data-stu-id="211e2-148">Start with registry key not in the desired state</span></span>
2.  <span data-ttu-id="211e2-149">Uruchom **Start DscConfiguration** konfiguracji umieszcza je w żądanym stanie i sprawdź jej przekazuje.</span><span class="sxs-lookup"><span data-stu-id="211e2-149">Run **Start-DscConfiguration** with a configuration to put it in the desired state and verify it passes.</span></span>
3.  <span data-ttu-id="211e2-150">Uruchom **DscConfiguration testu** i sprawdź, zwraca wartość true</span><span class="sxs-lookup"><span data-stu-id="211e2-150">Run **Test-DscConfiguration** and verify it returns true</span></span>
4.  <span data-ttu-id="211e2-151">Zmodyfikuj wartość klucza, dzięki czemu nie jest żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="211e2-151">Modify the value of the key so that it is not in the desired state</span></span>
5.  <span data-ttu-id="211e2-152">Uruchom **DscConfiguration testu** i sprawdź, zwraca wartość false</span><span class="sxs-lookup"><span data-stu-id="211e2-152">Run **Test-DscConfiguration** and verify it returns false</span></span>
6.  <span data-ttu-id="211e2-153">Get-TargetResource funkcji została zweryfikowana przy użyciu Get DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="211e2-153">Get-TargetResource functionality was verified using Get-DscConfiguration</span></span>

<span data-ttu-id="211e2-154">Get-TargetResource powinien zwrócić szczegółowe informacje o bieżącym stanem zasobu.</span><span class="sxs-lookup"><span data-stu-id="211e2-154">Get-TargetResource should return details of the current state of the resource.</span></span> <span data-ttu-id="211e2-155">Upewnij się przetestować go przez wywołanie Get-DscConfiguration, po zastosowaniu konfiguracji i sprawdzanie, czy dane wyjściowe poprawnie odzwierciedla bieżący stan maszyny.</span><span class="sxs-lookup"><span data-stu-id="211e2-155">Make sure to test it by calling Get-DscConfiguration after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="211e2-156">Należy przetestować go oddzielnie, ponieważ wszelkie problemy w tym zakresie nie będzie dłużej wyświetlane podczas wywoływania metody Start DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="211e2-156">It's important to test it separately, since any issues in this area won't appear when calling Start-DscConfiguration.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="211e2-157">Wywołanie **Get/Set/Test-TargetResource** funkcje bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="211e2-157">Call **Get/Set/Test-TargetResource** functions directly</span></span> ##

<span data-ttu-id="211e2-158">Upewnij się, że należy przetestować **Get/Set/Test-TargetResource** funkcje implementowana w zasobie przez bezpośrednie wywoływanie i sprawdzanie, czy działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="211e2-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="211e2-159">Sprawdź przy użyciu pełnego **Start DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="211e2-159">Verify End to End using **Start-DscConfiguration**</span></span> ##

<span data-ttu-id="211e2-160">Testowanie **Get/Set/Test-TargetResource** funkcje przez bezpośrednie wywoływanie jest ważne, ale nie wszystkie problemy nie zostaną odnalezione w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="211e2-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="211e2-161">Należy skoncentrować znaczną część testowania przy użyciu **Start DscConfiguration** lub z serwerem ściągania.</span><span class="sxs-lookup"><span data-stu-id="211e2-161">You should focus significant part of your testing on using **Start-DscConfiguration** or the pull server.</span></span> <span data-ttu-id="211e2-162">W rzeczywistości jest to, jak użytkownicy będą używać zasobów, dlatego nie przypadku licznik nie uwzględniać znaczenia tego typu testy.</span><span class="sxs-lookup"><span data-stu-id="211e2-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="211e2-163">Możliwe typy problemy:</span><span class="sxs-lookup"><span data-stu-id="211e2-163">Possible types of issues:</span></span>
- <span data-ttu-id="211e2-164">Poświadczenie/sesji może zachowywać się inaczej, ponieważ DSC agent działa jako usługa.</span><span class="sxs-lookup"><span data-stu-id="211e2-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="211e2-165">Należy sprawdzić wszystkie funkcje tutaj pełnego.</span><span class="sxs-lookup"><span data-stu-id="211e2-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="211e2-166">Błędy danych wyjściowych przez **Start DscConfiguration** mogą być inne niż wyświetlone podczas wywoływania metody **TargetResource zestaw** funkcji bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="211e2-166">Errors output by **Start-DscConfiguration** may be different than those displayed when calling the **Set-TargetResource** function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="211e2-167">Test zgodności DSC wszystkie obsługiwane platformy</span><span class="sxs-lookup"><span data-stu-id="211e2-167">Test compatability on all DSC supported platforms</span></span> ##
<span data-ttu-id="211e2-168">Zasobu powinny działać na wszystkich platformach DSC obsługiwane (z systemem Windows Server 2008 R2 lub nowszym).</span><span class="sxs-lookup"><span data-stu-id="211e2-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="211e2-169">Zainstaluj najnowsze WMF (Windows Management Framework) w systemie operacyjnym, aby pobrać najnowszą wersję usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="211e2-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="211e2-170">Jeśli zasób nie działa na niektórych z tych platform zgodnie z projektem, ma zostać zwrócony komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="211e2-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="211e2-171">Ponadto upewnij się, że zasobu sprawdza, czy polecenia cmdlet, wywoływana znajdują się na określonym komputerze.</span><span class="sxs-lookup"><span data-stu-id="211e2-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="211e2-172">Windows Server 2012 dodano dużą liczbą nowych poleceń cmdlet, które nie są dostępne w systemie Windows Server 2008 R2, nawet w przypadku WMF zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="211e2-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="211e2-173">Sprawdź w kliencie systemu Windows (jeśli dotyczy)</span><span class="sxs-lookup"><span data-stu-id="211e2-173">Verify on Windows Client (if applicable)</span></span> ##
<span data-ttu-id="211e2-174">Jeden często przerwę testu jest sprawdzanie zasobów tylko w wersjach systemu Windows server.</span><span class="sxs-lookup"><span data-stu-id="211e2-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="211e2-175">Wiele zasobów są również przeznaczona do pracy w SKU klienta, jeśli jest to istotne w przypadku sieci, nie zapomnij przetestować go także tych platform.</span><span class="sxs-lookup"><span data-stu-id="211e2-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>
## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="211e2-176">Get-DSCResource zawiera listę zasobów</span><span class="sxs-lookup"><span data-stu-id="211e2-176">Get-DSCResource lists the resource</span></span> ##
<span data-ttu-id="211e2-177">Po wdrożeniu modułu, wywołanie Get-DscResource powinny zawierać zasobu między innymi w wyniku.</span><span class="sxs-lookup"><span data-stu-id="211e2-177">After deploying the module, calling Get-DscResource should list your resource among others as a result.</span></span> <span data-ttu-id="211e2-178">Jeśli na liście, nie można odnaleźć zasobu, upewnij się, czy plik schema.mof dla tego zasobu istnieje.</span><span class="sxs-lookup"><span data-stu-id="211e2-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>
## <a name="resource-module-contains-examples"></a><span data-ttu-id="211e2-179">Moduł zasobu zawiera przykłady</span><span class="sxs-lookup"><span data-stu-id="211e2-179">Resource module contains examples</span></span> ##
<span data-ttu-id="211e2-180">Tworzenie przykłady jakości, które będzie ułatwiała innym zrozumieć, jak z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="211e2-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="211e2-181">Jest to ważne, szczególnie, ponieważ w przypadku wielu użytkowników zaliczenie dokumentacji przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="211e2-181">This is crucial, especially since many users treat sample code as documentation.</span></span>
- <span data-ttu-id="211e2-182">Najpierw należy określić przykłady, które zostanie uwzględniony w module — co najmniej, powinno obejmować najważniejszych przypadków użycia dla zasobu:</span><span class="sxs-lookup"><span data-stu-id="211e2-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="211e2-183">Modułu zawiera kilka zasobów, które wymagają współdziałają ze sobą scenariusz end-to-end, prosty przykład end-to-end w idealnym przypadku będzie pierwszy.</span><span class="sxs-lookup"><span data-stu-id="211e2-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="211e2-184">Przykłady początkowej powinny być bardzo prosty — jak rozpocząć pracę z zasobami w małych partiach łatwych do (np. utworzenie nowego wirtualnego dysku twardego)</span><span class="sxs-lookup"><span data-stu-id="211e2-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="211e2-185">Przykłady kolejnych powinien kompilacji na tych przykładów (np. utworzenie maszyny Wirtualnej z dysku VHD, usuwanie maszyny Wirtualnej, modyfikując maszyny Wirtualnej), a Pokaż zaawansowane funkcje (np. utworzenie maszyny Wirtualnej z pamięcią dynamiczną)</span><span class="sxs-lookup"><span data-stu-id="211e2-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="211e2-186">Przykładowe konfiguracje należy ustawiać parametry (wszystkie wartości powinny zostać przekazane do konfiguracji jako parametry i nie powinna istnieć bez wartości zapisane na stałe):</span><span class="sxs-lookup"><span data-stu-id="211e2-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>
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
- <span data-ttu-id="211e2-187">Dobrym rozwiązaniem, aby uwzględnić (komentarze out) przykładem wywołań konfiguracji o wartości rzeczywistych na końcu przykładowy skrypt jest.</span><span class="sxs-lookup"><span data-stu-id="211e2-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
<span data-ttu-id="211e2-188">Na przykład w powyższej konfiguracji nie jest zawsze widoczne, to najlepszy sposób, aby określić agenta użytkownika:</span><span class="sxs-lookup"><span data-stu-id="211e2-188">For example, in the configuration above it isn't neccessarily obvious that the best way to specify UserAgent is:</span></span>

<span data-ttu-id="211e2-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` W takim przypadku komentarz można wyjaśnić zamierzone wykonywania konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="211e2-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>
```
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```
- <span data-ttu-id="211e2-190">Przykładowo każdego zapisu krótki opis, który opisano, jakie operacje oraz na znaczenie właściwości parametrów.</span><span class="sxs-lookup"><span data-stu-id="211e2-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="211e2-191">Upewnij się, przykłady obejmują większość ważne scenariusze dla zasobu i jeśli nic nie Brak, sprawdź, czy wszystkie wykonania i umieść maszyny w żądanym stanie.</span><span class="sxs-lookup"><span data-stu-id="211e2-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="211e2-192">Komunikaty o błędach są łatwe do zrozumienia i pomaganie użytkownikom w rozwiązywaniu problemów</span><span class="sxs-lookup"><span data-stu-id="211e2-192">Error messages are easy to understand and help users solve problems</span></span> ##
<span data-ttu-id="211e2-193">Powinny być dobrym komunikaty:</span><span class="sxs-lookup"><span data-stu-id="211e2-193">Good error messages should be:</span></span>
- <span data-ttu-id="211e2-194">: Największych problem z komunikatami o błędach jest często nie istnieje, dlatego upewnij się, że są one dostępne.</span><span class="sxs-lookup"><span data-stu-id="211e2-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="211e2-195">Łatwe do zrozumienia: kody błędów ludzkich do odczytu, nie zasłoniętej</span><span class="sxs-lookup"><span data-stu-id="211e2-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="211e2-196">Dokładne: Co to jest dokładnie problem opisano</span><span class="sxs-lookup"><span data-stu-id="211e2-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="211e2-197">Zwyczajowo: Porady jak rozwiązać ten problem</span><span class="sxs-lookup"><span data-stu-id="211e2-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="211e2-198">Proces łagodnego: Nie winy użytkownika lub upewnij, możesz je zły upewnij się, sprawdź błędy w scenariuszach kompleksowego (przy użyciu **Start DscConfiguration**), ponieważ elementy różnią od tych zwrócony podczas uruchamiania funkcji zasobów bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="211e2-198">Polite: Don’t blame user or make them feel bad Make sure you verify errors in End to End scenarios (using **Start-DscConfiguration**), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="211e2-199">Komunikaty dziennika są łatwe do zrozumienia i informacyjnej (łącznie-verbose, — debugowania i dzienniki zdarzeń systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="211e2-199">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span> ##
<span data-ttu-id="211e2-200">Upewnij się, że dzienniki wyjściowych przez zasób są łatwe do zrozumienia i podaj wartość dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="211e2-200">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="211e2-201">Zasoby powinny output wszystkie informacje, które mogą być przydatne do użytkownika, ale nie więcej dzienników zawsze jest lepsze.</span><span class="sxs-lookup"><span data-stu-id="211e2-201">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="211e2-202">Należy unikać nadmiarowości i wyprowadzania danych, która nie zapewniają dodatkowe wartość — nie są przenoszone ktoś przejść przez setki wpisów dziennika, aby znaleźć ich wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="211e2-202">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="211e2-203">Oczywiście nie dzienniki nie jest dopuszczalne rozwiązanie tego problemu albo.</span><span class="sxs-lookup"><span data-stu-id="211e2-203">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="211e2-204">Podczas testowania, należy również analizować pełne i dzienników debugowania (uruchamiając **Start DscConfiguration** z — pełne i — przełączników debugowania odpowiednio), jak również jako dzienniki zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="211e2-204">When testing, you should also analyze verbose and debug logs (by running **Start-DscConfiguration** with –verbose and –debug switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="211e2-205">Aby wyświetlić dzienniki DSC ETW, przejdź do podglądu zdarzeń i otwórz następujący folder: aplikacji i usług firmy Microsoft - Windows - konfiguracji żądanego stanu.</span><span class="sxs-lookup"><span data-stu-id="211e2-205">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="211e2-206">Domyślnie zostanie operacyjne kanału, ale upewnij się, że możesz włączyć analityczne i debugowania kanały przed uruchomieniem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="211e2-206">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="211e2-207">Aby włączyć kanały analityczne/Debug, można wykonać skryptu poniżej:</span><span class="sxs-lookup"><span data-stu-id="211e2-207">To enable Analytic/Debug channels, you can execute script below:</span></span>
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
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="211e2-208">Implementacja zasobu nie zawiera ścieżki zapisane na stałe</span><span class="sxs-lookup"><span data-stu-id="211e2-208">Resource implementation does not contain hardcoded paths</span></span> ##
<span data-ttu-id="211e2-209">Upewnić nie ścieżek zapisane na stałe w implementacji zasobów, zwłaszcza w wypadku zakładają języka (en-us), lub gdy występują zmienne systemowe, które mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="211e2-209">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="211e2-210">Jeśli potrzebujesz zasobu dostęp do określonej ścieżki, używać zmiennych środowiskowych zamiast hardcoding ścieżki, ponieważ mogą się różnić na innych komputerach.</span><span class="sxs-lookup"><span data-stu-id="211e2-210">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="211e2-211">Przykład:</span><span class="sxs-lookup"><span data-stu-id="211e2-211">Example:</span></span>

<span data-ttu-id="211e2-212">Zamiast:</span><span class="sxs-lookup"><span data-stu-id="211e2-212">Instead of:</span></span>
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
<span data-ttu-id="211e2-213">Można napisać:</span><span class="sxs-lookup"><span data-stu-id="211e2-213">You can write:</span></span>
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```
## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="211e2-214">Implementacja zasobu nie zawiera informacji o użytkowniku</span><span class="sxs-lookup"><span data-stu-id="211e2-214">Resource implementation does not contain user information</span></span> ##
<span data-ttu-id="211e2-215">Upewnij się, że nie ma żadnych nazw poczty e-mail, informacje o koncie lub nazwy osób w kodzie.</span><span class="sxs-lookup"><span data-stu-id="211e2-215">Make sure there are no email names, account information, or names of people in the code.</span></span>
## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="211e2-216">Zasób była testowana przy prawidłowy lub jest ono nieprawidłowe poświadczenia</span><span class="sxs-lookup"><span data-stu-id="211e2-216">Resource was tested with valid/invalid credentials</span></span> ##
<span data-ttu-id="211e2-217">Jeśli zasób przyjmuje poświadczenia jako parametr:</span><span class="sxs-lookup"><span data-stu-id="211e2-217">If your resource takes a credential as parameter:</span></span>
- <span data-ttu-id="211e2-218">Weryfikowanie działania zasobów, gdy System lokalny (lub konto komputera dla zasobów zdalnych) nie ma dostępu.</span><span class="sxs-lookup"><span data-stu-id="211e2-218">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="211e2-219">Sprawdź działa zasobów z poświadczenia określone dla Get Set i testowanie</span><span class="sxs-lookup"><span data-stu-id="211e2-219">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="211e2-220">Jeśli zasób uzyskuje dostęp do udziałów, przetestuj wszystkich wariantów potrzebnych do obsługi, takie jak:</span><span class="sxs-lookup"><span data-stu-id="211e2-220">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="211e2-221">Udziały standardowego systemu windows.</span><span class="sxs-lookup"><span data-stu-id="211e2-221">Standard windows shares.</span></span>
  - <span data-ttu-id="211e2-222">Udziały systemu plików DFS.</span><span class="sxs-lookup"><span data-stu-id="211e2-222">DFS shares.</span></span>
  - <span data-ttu-id="211e2-223">Udziały SAMBA (jeśli mają być obsługiwane systemu Linux.)</span><span class="sxs-lookup"><span data-stu-id="211e2-223">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="211e2-224">Zasób nie wymaga interaktywnego dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="211e2-224">Resource does not require interactive input</span></span> ##
<span data-ttu-id="211e2-225">**Get/Set/Test-TargetResource** funkcje mają zostać wykonane automatycznie i nie musi czekać dla danych wejściowych użytkownika na każdym etapie wykonywania (np. nie należy używać **Get-Credential** wewnątrz tych funkcji).</span><span class="sxs-lookup"><span data-stu-id="211e2-225">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use **Get-Credential** inside these functions).</span></span> <span data-ttu-id="211e2-226">Jeśli potrzebujesz podawanie danych wejściowych użytkownika, należy przekazujesz ją do konfiguracji jako parametr podczas fazy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="211e2-226">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>
## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="211e2-227">Funkcje zasobów została dokładnie przetestowana.</span><span class="sxs-lookup"><span data-stu-id="211e2-227">Resource functionality was thoroughly tested</span></span> ##
<span data-ttu-id="211e2-228">Ta lista kontrolna zawiera elementy, które są ważne do sprawdzenia i/lub często zostaną pominięte.</span><span class="sxs-lookup"><span data-stu-id="211e2-228">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="211e2-229">Będzie bunch testów, głównie funkcjonalności te, które są specyficzne dla zasobu, testowania i nie są wymienione w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="211e2-229">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="211e2-230">Nie zapomnij o ujemna przypadków testowych.</span><span class="sxs-lookup"><span data-stu-id="211e2-230">Don’t forget about negative test cases.</span></span>
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="211e2-231">Najlepsze praktyki: moduł zasobów zawiera folder testy przy użyciu skryptu ResourceDesignerTests.ps1</span><span class="sxs-lookup"><span data-stu-id="211e2-231">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span> ##
<span data-ttu-id="211e2-232">Dobrym rozwiązaniem, aby utworzyć folder "testy" wewnątrz moduł zasobów, Utwórz plik ResourceDesignerTests.ps1 i dodać testów za pomocą jest **xDscResource testu** i **xDscSchema testu** dla wszystkich zasobów w danych Moduł.</span><span class="sxs-lookup"><span data-stu-id="211e2-232">It’s a good practice to create folder “Tests” inside resource module, create ResourceDesignerTests.ps1 file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="211e2-233">Dzięki temu można szybko Zweryfikuj schematy wszystkich zasobów z modułów danego i nie wykonuje sprawdzanie przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="211e2-233">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="211e2-234">Dla xRemoteFile ResourceTests.ps1 może wyglądać tak proste, jak:</span><span class="sxs-lookup"><span data-stu-id="211e2-234">For xRemoteFile, ResourceTests.ps1 could look as simple as:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="211e2-235">Najlepsze praktyki: folder zasobów zawiera zasób skryptu projektanta podczas generowania schematu ##</span><span class="sxs-lookup"><span data-stu-id="211e2-235">Best practice: Resource folder contains resource designer script for generating schema##</span></span>
<span data-ttu-id="211e2-236">Każdy zasób powinien zawierać projektanta skryptu zasobu, który generuje schematu mof zasobu.</span><span class="sxs-lookup"><span data-stu-id="211e2-236">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="211e2-237">Ten plik powinien być umieszczony w <ResourceName>\ResourceDesignerScripts i będzie nosić nazwę Generuj<ResourceName>Schema.ps1 dla zasobu xRemoteFile ten plik może być wywoływana GenerateXRemoteFileSchema.ps1 i zawierają:</span><span class="sxs-lookup"><span data-stu-id="211e2-237">This file should be placed in <ResourceName>\ResourceDesignerScripts and be named Generate<ResourceName>Schema.ps1 For xRemoteFile resource this file would be called GenerateXRemoteFileSchema.ps1 and contain:</span></span>
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
## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="211e2-238">Najlepsze praktyki: zasób obsługuje - whatif</span><span class="sxs-lookup"><span data-stu-id="211e2-238">Best practice: Resource supports -whatif</span></span> ##
<span data-ttu-id="211e2-239">Jeśli zasób jest wykonywanie operacji "niebezpieczne", jest dobrym rozwiązaniem do implementowania - whatif.</span><span class="sxs-lookup"><span data-stu-id="211e2-239">If your resource is performing “dangerous” operations, it’s a good practice to implement -whatif functionality.</span></span> <span data-ttu-id="211e2-240">Po zakończeniu upewnij się, czy dane wyjściowe whatif poprawnie opisano operacje, co się stanie, jeśli polecenie zostało wykonane bez przełącznika whatif.</span><span class="sxs-lookup"><span data-stu-id="211e2-240">After it’s done, make sure that whatif output correctly describes operations which would happen if command was executed without whatif switch.</span></span>
<span data-ttu-id="211e2-241">Sprawdź także, czy operacje nie wykonuj (nie do stanu węzła jest zmieniana) po ma przełącznika-whatif.</span><span class="sxs-lookup"><span data-stu-id="211e2-241">Also, verify that operations does not execute (no changes to the node’s state are made) when –whatif switch is present.</span></span>
<span data-ttu-id="211e2-242">Załóżmy na przykład, że testujemy pliku zasobu.</span><span class="sxs-lookup"><span data-stu-id="211e2-242">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="211e2-243">Poniżej znajdują się prostą konfigurację, która tworzy plik "test.txt" zawartość "test":</span><span class="sxs-lookup"><span data-stu-id="211e2-243">Below is simple configuration which creates file “test.txt” with contents “test”:</span></span>
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
<span data-ttu-id="211e2-244">Jeśli firma Microsoft kompilacji, a następnie wykonaj konfiguracji z przełącznikiem-whatif, dane wyjściowe informuje NAS dokładnie co się stanie, gdy przeprowadzana konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="211e2-244">If we compile and then execute the configuration with the –whatif switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="211e2-245">Konfiguracja się jednak nie zostało wykonane (test.txt Plik nie został utworzony).</span><span class="sxs-lookup"><span data-stu-id="211e2-245">The configuration itself however was not executed (test.txt file was not created).</span></span>
```powershell
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
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

<span data-ttu-id="211e2-246">Ta lista nie jest wyczerpująca, ale obejmuje wiele ważnych kwestii, które można napotkał podczas projektowania, tworzenia i testowania DSC zasobów.</span><span class="sxs-lookup"><span data-stu-id="211e2-246">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>