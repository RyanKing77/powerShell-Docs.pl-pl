---
ms.date: 12/14/2018
keywords: polecenia cmdlet programu PowerShell
title: Zapisywanie przenośne modułów
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747725"
---
# <a name="portable-modules"></a><span data-ttu-id="36abe-103">Przenośne modułów</span><span class="sxs-lookup"><span data-stu-id="36abe-103">Portable Modules</span></span>

<span data-ttu-id="36abe-104">Program Windows PowerShell jest przeznaczony dla [.NET Framework][] podczas, gdy program PowerShell Core jest przeznaczony dla [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="36abe-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="36abe-105">Przenośne moduły są moduły, które działają zarówno w przypadku środowiska Windows PowerShell, jak i programu PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="36abe-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="36abe-106">.NET Framework i .NET Core jest wysoce zgodną, różnią się w dostępnych interfejsów API między nimi.</span><span class="sxs-lookup"><span data-stu-id="36abe-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="36abe-107">Istnieją także różnice w interfejsach API dostępnych w programie Windows PowerShell i program PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="36abe-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="36abe-108">Moduły, które mają być używane w obu środowiskach muszą się pod uwagę te różnice.</span><span class="sxs-lookup"><span data-stu-id="36abe-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="36abe-109">Przenoszenie istniejącego modułu</span><span class="sxs-lookup"><span data-stu-id="36abe-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="36abe-110">Przenoszenie PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="36abe-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="36abe-111">Konsola programu PowerShell (PSSnapIn) nie są obsługiwane w programie PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="36abe-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="36abe-112">Jednak jest prosta, aby przekonwertować PSSnapIn modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36abe-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="36abe-113">Zazwyczaj PSSnapIn kod rejestracji znajduje się w jednym pliku źródłowym klasy pochodzący z [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="36abe-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="36abe-114">Usuń ten plik źródłowy z kompilacji; nie jest już potrzebny.</span><span class="sxs-lookup"><span data-stu-id="36abe-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="36abe-115">Użyj [New-ModuleManifest][] do utworzenia nowego manifestu modułu, zastępujący potrzebę PSSnapIn kodu rejestracyjnego.</span><span class="sxs-lookup"><span data-stu-id="36abe-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="36abe-116">Niektóre wartości z PSSnapIn (na przykład opis) może nastąpić w manifeście modułu.</span><span class="sxs-lookup"><span data-stu-id="36abe-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="36abe-117">`RootModule` Właściwości w manifeście modułu powinna być równa Nazwa zestawu (dll), implementacja polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36abe-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="36abe-118">Narzędzia .NET Portability Analyzer (zwane również APIPort)</span><span class="sxs-lookup"><span data-stu-id="36abe-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="36abe-119">Port modułów napisanych dla środowiska Windows PowerShell do pracy za pomocą programu PowerShell Core, rozpoczynać się [narzędzia .NET Portability Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="36abe-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="36abe-120">Uruchom to narzędzie względem Twojej skompilowanego zestawu, aby ustalić, czy interfejsy API platformy .NET, używane w module są zgodne z programem .NET Framework, .NET Core i inne środowiska uruchomieniowe platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="36abe-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="36abe-121">Narzędzie sugeruje alternatywne interfejsy API, jeśli takie istnieją.</span><span class="sxs-lookup"><span data-stu-id="36abe-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="36abe-122">W przeciwnym razie użytkownik może być konieczne dodanie [testy środowiska uruchomieniowego][] i ograniczyć możliwości niedostępne w określonych środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="36abe-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="36abe-123">Tworzenie nowego modułu</span><span class="sxs-lookup"><span data-stu-id="36abe-123">Creating a New Module</span></span>

<span data-ttu-id="36abe-124">W przypadku tworzenia nowego modułu, zaleca się użycie [.NET CLI][].</span><span class="sxs-lookup"><span data-stu-id="36abe-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="36abe-125">Instalowanie szablon modułu programu PowerShell Standard</span><span class="sxs-lookup"><span data-stu-id="36abe-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="36abe-126">Po zainstalowaniu interfejsu wiersza polecenia platformy .NET, należy zainstalować biblioteki szablonów, aby wygenerować prosty moduł programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36abe-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="36abe-127">Moduł będzie zgodna z programu Windows PowerShell, program PowerShell Core, Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="36abe-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="36abe-128">Poniższy przykład pokazuje, jak zainstalować szablon:</span><span class="sxs-lookup"><span data-stu-id="36abe-128">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="36abe-129">Tworzenie nowego projektu modułu</span><span class="sxs-lookup"><span data-stu-id="36abe-129">Creating a New Module Project</span></span>

<span data-ttu-id="36abe-130">Po zainstalowaniu tego szablonu można utworzyć nowy projekt modułu programu PowerShell, za pomocą tego szablonu.</span><span class="sxs-lookup"><span data-stu-id="36abe-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="36abe-131">W tym przykładzie przykładowego modułu nosi nazwę "myModule".</span><span class="sxs-lookup"><span data-stu-id="36abe-131">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="36abe-132">Tworzenie modułu</span><span class="sxs-lookup"><span data-stu-id="36abe-132">Building the Module</span></span>

<span data-ttu-id="36abe-133">Użyj standardowych poleceń interfejsu wiersza polecenia platformy .NET do tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="36abe-133">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="36abe-134">Testowanie modułu</span><span class="sxs-lookup"><span data-stu-id="36abe-134">Testing the Module</span></span>

<span data-ttu-id="36abe-135">Po utworzeniu modułu, można go zaimportować i wykonaj przykładowe polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36abe-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

<span data-ttu-id="36abe-136">Poniżej opisano szczegółowo niektóre technologie używane przez ten szablon.</span><span class="sxs-lookup"><span data-stu-id="36abe-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="36abe-137">Biblioteka .NET standard</span><span class="sxs-lookup"><span data-stu-id="36abe-137">.NET Standard Library</span></span>

<span data-ttu-id="36abe-138">[.NET standard][] jest formalną specyfikację interfejsów API platformy .NET, które są dostępne we wszystkich wdrożeniach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="36abe-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="36abe-139">Zarządzany kod przeznaczonych dla platformy .NET Standard działa z wersjami .NET Framework i .NET Core, które są zgodne z tej wersji programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="36abe-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="36abe-140">Chociaż interfejs API może istnieć w programie .NET Standard, implementacja interfejsu API w programie .NET Core może zgłaszać `PlatformNotSupportedException` w czasie wykonywania, tak aby sprawdzić zgodność za pomocą programu Windows PowerShell i program PowerShell Core, najlepszym rozwiązaniem jest do uruchamiania testów dla modułu w obu środowiskach.</span><span class="sxs-lookup"><span data-stu-id="36abe-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="36abe-141">Również uruchomić testy w systemie Linux i macOS, jeżeli modułu jest przeznaczona do wielu platform.</span><span class="sxs-lookup"><span data-stu-id="36abe-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="36abe-142">Przeznaczonych dla platformy .NET Standard zapewnia, że w miarę rozwoju moduł, niezgodnych interfejsów API nie przypadkowo wprowadzenie do modułu.</span><span class="sxs-lookup"><span data-stu-id="36abe-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="36abe-143">Niezgodności są odnajdywane w czasie kompilacji zamiast środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="36abe-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="36abe-144">Jednak nie jest wymagane do obiektu docelowego .NET Standard dla modułu do pracy z programu Windows PowerShell i program PowerShell Core tak długo, jak używać zgodnych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="36abe-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="36abe-145">Języka pośredniego (IL) są zgodne między dwoma środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="36abe-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="36abe-146">Można kierować platformy .NET Framework 4.6.1, który jest zgodny z .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="36abe-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="36abe-147">Jeśli nie korzystasz z interfejsów API poza .NET Standard 2.0, następnie modułu działa przy użyciu programu PowerShell Core 6 bez ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="36abe-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="36abe-148">Biblioteka standardowa programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="36abe-148">PowerShell Standard Library</span></span>

<span data-ttu-id="36abe-149">[PowerShell Standard][] biblioteka jest formalną specyfikację interfejsów API programu PowerShell dostępny we wszystkich wersjach programu PowerShell, większa lub równa wersji tego standardu.</span><span class="sxs-lookup"><span data-stu-id="36abe-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="36abe-150">Na przykład [PowerShell Standard 5.1][] jest zgodne z programem Windows PowerShell 5.1 i PowerShell Core 6.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="36abe-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="36abe-151">Zaleca się skompilować modułu przy użyciu programu PowerShell Standard biblioteki.</span><span class="sxs-lookup"><span data-stu-id="36abe-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="36abe-152">Biblioteka zapewnia, że interfejsy API są dostępne i wdrożony zarówno w przypadku środowiska Windows PowerShell, jak i programu PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="36abe-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="36abe-153">PowerShell Standard jest przeznaczona do zawsze być zgodny z wyszukiwanie do przodu.</span><span class="sxs-lookup"><span data-stu-id="36abe-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="36abe-154">Moduł skompilowany przy użyciu programu PowerShell Standard biblioteki 5.1 zawsze będą zgodne z przyszłych wersji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36abe-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="36abe-155">Manifestu modułu</span><span class="sxs-lookup"><span data-stu-id="36abe-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="36abe-156">Wskazującymi zgodność za pomocą programu Windows PowerShell i program PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="36abe-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="36abe-157">Po upewnieniu się, że modułu współpracuje z programu Windows PowerShell i program PowerShell Core manifestu modułu należy jawnie wskazywały zgodność za pomocą [CompatiblePSEditions][] właściwości.</span><span class="sxs-lookup"><span data-stu-id="36abe-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="36abe-158">Wartość `Desktop` oznacza, że moduł jest zgodny z programu Windows PowerShell, podczas wartość `Core` oznacza, że moduł jest zgodny z programu PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="36abe-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="36abe-159">W tym zarówno `Desktop` i `Core` oznacza, że moduł jest zgodny z programu Windows PowerShell i program PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="36abe-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="36abe-160">`Core` automatycznie oznacza, że moduł jest zgodny z Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="36abe-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="36abe-161">**CompatiblePSEditions** właściwość wprowadzono w programie PowerShell w wersji 5.</span><span class="sxs-lookup"><span data-stu-id="36abe-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="36abe-162">Moduł manifesty używające **CompatiblePSEditions** właściwości nie można załadować w wersjach wcześniejszych niż programu PowerShell w wersji 5.</span><span class="sxs-lookup"><span data-stu-id="36abe-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="36abe-163">Oznaczający zgodność systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="36abe-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="36abe-164">Najpierw sprawdź, czy modułu działa w systemie Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="36abe-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="36abe-165">Następnie należy wskazać zgodność z tymi systemami operacyjnymi w manifeście modułu.</span><span class="sxs-lookup"><span data-stu-id="36abe-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="36abe-166">To ułatwia użytkownikom wyszukiwanie modułu dla swojego systemu operacyjnego podczas publikowania w [Galeria programu PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="36abe-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="36abe-167">W manifeście modułu `PrivateData` właściwość ma `PSData` właściwości podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="36abe-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="36abe-168">Opcjonalny `Tags` właściwość `PSData` przyjmuje tablicę wartości, które pojawiają się w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36abe-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="36abe-169">Galeria programu PowerShell obsługuje następujące wartości zgodności:</span><span class="sxs-lookup"><span data-stu-id="36abe-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="36abe-170">Tag</span><span class="sxs-lookup"><span data-stu-id="36abe-170">Tag</span></span>               | <span data-ttu-id="36abe-171">Opis</span><span class="sxs-lookup"><span data-stu-id="36abe-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="36abe-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="36abe-172">PSEdition_Core</span></span>    | <span data-ttu-id="36abe-173">Zgodne z programu PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="36abe-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="36abe-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="36abe-174">PSEdition_Desktop</span></span> | <span data-ttu-id="36abe-175">Zgodne z programem Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36abe-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="36abe-176">Windows</span><span class="sxs-lookup"><span data-stu-id="36abe-176">Windows</span></span>           | <span data-ttu-id="36abe-177">Zgodne z Windows</span><span class="sxs-lookup"><span data-stu-id="36abe-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="36abe-178">Linux</span><span class="sxs-lookup"><span data-stu-id="36abe-178">Linux</span></span>             | <span data-ttu-id="36abe-179">Zgodne z systemem Linux (nie określonej dystrybucji)</span><span class="sxs-lookup"><span data-stu-id="36abe-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="36abe-180">macOS</span><span class="sxs-lookup"><span data-stu-id="36abe-180">macOS</span></span>             | <span data-ttu-id="36abe-181">Zgodne z systemem macOS</span><span class="sxs-lookup"><span data-stu-id="36abe-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="36abe-182">Przykład:</span><span class="sxs-lookup"><span data-stu-id="36abe-182">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[testy środowiska uruchomieniowego]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET standard]: /dotnet/standard/net-standard
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[Galeria programu PowerShell]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[Narzędzia .NET portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
