---
ms.date: 12/14/2018
keywords: polecenia cmdlet programu PowerShell
title: Zapisywanie przenośne modułów
ms.openlocfilehash: 237f6aaea0ed019c54d04a8477d7a456edf00910
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470982"
---
# <a name="portable-modules"></a>Przenośne modułów

Program Windows PowerShell jest przeznaczony dla [.NET Framework][] podczas, gdy program PowerShell Core jest przeznaczony dla [.NET Core][]. Przenośne moduły są moduły, które działają zarówno w przypadku środowiska Windows PowerShell, jak i programu PowerShell Core. .NET Framework i .NET Core jest wysoce zgodną, różnią się w dostępnych interfejsów API między nimi. Istnieją także różnice w interfejsach API dostępnych w programie Windows PowerShell i program PowerShell Core. Moduły, które mają być używane w obu środowiskach muszą się pod uwagę te różnice.

## <a name="porting-an-existing-module"></a>Przenoszenie istniejącego modułu

### <a name="porting-a-pssnapin"></a>Przenoszenie PSSnapIn

Program PowerShell [konsola](/powershell/developer/cmdlet/modules-and-snap-ins) nie są obsługiwane w programie PowerShell Core. Jednak jest prosta, aby przekonwertować PSSnapIn modułu programu PowerShell. Zazwyczaj PSSnapIn kod rejestracji znajduje się w jednym pliku źródłowym klasy pochodzący z [PSSnapIn][].
Usuń ten plik źródłowy z kompilacji; nie jest już potrzebny.

Użyj [New-ModuleManifest][] do utworzenia nowego manifestu modułu, zastępujący potrzebę PSSnapIn kodu rejestracyjnego. Niektóre wartości z **PSSnapIn** (takie jak **opis**) mogą zostać ponownie użyte w manifeście modułu.

**Polach RootModule** właściwości w manifeście modułu powinna być równa Nazwa zestawu (dll), implementacja polecenia cmdlet.

### <a name="the-net-portability-analyzer-aka-apiport"></a>Narzędzia .NET Portability Analyzer (zwane również APIPort)

Port modułów napisanych dla środowiska Windows PowerShell do pracy za pomocą programu PowerShell Core, rozpoczynać się [narzędzia .NET Portability Analyzer][]. Uruchom to narzędzie względem Twojej skompilowanego zestawu, aby ustalić, czy interfejsy API platformy .NET, używane w module są zgodne z programem .NET Framework, .NET Core i inne środowiska uruchomieniowe platformy .NET. Narzędzie sugeruje alternatywne interfejsy API, jeśli takie istnieją. W przeciwnym razie użytkownik może być konieczne dodanie [testy środowiska uruchomieniowego][] i ograniczyć możliwości niedostępne w określonych środowisk uruchomieniowych.

## <a name="creating-a-new-module"></a>Tworzenie nowego modułu

W przypadku tworzenia nowego modułu, zaleca się użycie [INTERFEJS WIERSZA POLECENIA PLATFORMY .NET][].

### <a name="installing-the-powershell-standard-module-template"></a>Instalowanie szablon modułu programu PowerShell standardowe

Po zainstalowaniu interfejsu wiersza polecenia platformy .NET, należy zainstalować biblioteki szablonów, aby wygenerować prosty moduł programu PowerShell.
Moduł będzie zgodna z programu Windows PowerShell, program PowerShell Core, Windows, Linux i macOS.

Poniższy przykład pokazuje, jak zainstalować szablon:

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

### <a name="creating-a-new-module-project"></a>Tworzenie nowego projektu modułu

Po zainstalowaniu tego szablonu można utworzyć nowy projekt modułu programu PowerShell, za pomocą tego szablonu. W tym przykładzie przykładowego modułu nosi nazwę "myModule".

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

### <a name="building-the-module"></a>Tworzenie modułu

Użyj standardowych poleceń interfejsu wiersza polecenia platformy .NET do tworzenia projektu.

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

### <a name="testing-the-module"></a>Testowanie modułu

Po utworzeniu modułu, można go zaimportować i wykonaj przykładowe polecenie cmdlet.

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

Poniżej opisano szczegółowo niektóre technologie używane przez ten szablon.

## <a name="net-standard-library"></a>Biblioteka .NET standard

[.NET standard][] jest formalną specyfikację interfejsów API platformy .NET, które są dostępne we wszystkich wdrożeniach platformy .NET. Zarządzany kod przeznaczonych dla platformy .NET Standard działa z wersjami .NET Framework i .NET Core, które są zgodne z tej wersji programu .NET Standard.

> [!NOTE]
> Chociaż interfejs API może istnieć w programie .NET Standard, implementacja interfejsu API w programie .NET Core może zgłaszać `PlatformNotSupportedException` w czasie wykonywania, tak aby sprawdzić zgodność za pomocą programu Windows PowerShell i program PowerShell Core, najlepszym rozwiązaniem jest do uruchamiania testów dla modułu w obu środowiskach.
> Również uruchomić testy w systemie Linux i macOS, jeżeli modułu jest przeznaczona do wielu platform.

Przeznaczonych dla platformy .NET Standard zapewnia, że w miarę rozwoju moduł, niezgodnych interfejsów API nie przypadkowo wprowadzenie do modułu. Niezgodności są odnajdywane w czasie kompilacji zamiast środowiska uruchomieniowego.

Jednak nie jest wymagane do obiektu docelowego .NET Standard dla modułu do pracy z programu Windows PowerShell i program PowerShell Core tak długo, jak używać zgodnych interfejsów API. Języka pośredniego (IL) są zgodne między dwoma środowisk uruchomieniowych. Można kierować platformy .NET Framework 4.6.1, który jest zgodny z .NET Standard 2.0. Jeśli nie korzystasz z interfejsów API poza .NET Standard 2.0, następnie modułu działa przy użyciu programu PowerShell Core 6 bez ponownej kompilacji.

## <a name="powershell-standard-library"></a>Biblioteka standardowa programu PowerShell

[Standardowy programu PowerShell][] biblioteka jest formalną specyfikację interfejsów API programu PowerShell dostępny we wszystkich wersjach programu PowerShell, większa lub równa wersji tego standardu.

Na przykład [PowerShell Standard 5.1][] jest zgodne z programem Windows PowerShell 5.1 i PowerShell Core 6.0 lub nowszej.

Zaleca się skompilować modułu przy użyciu programu PowerShell standardowe biblioteki. Biblioteka zapewnia, że interfejsy API są dostępne i wdrożony zarówno w przypadku środowiska Windows PowerShell, jak i programu PowerShell Core 6.
PowerShell Standard jest przeznaczona do zawsze być zgodny z wyszukiwanie do przodu. Moduł skompilowany przy użyciu programu PowerShell standardowe biblioteki 5.1 zawsze będą zgodne z przyszłych wersji programu PowerShell.

## <a name="module-manifest"></a>Manifestu modułu

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Wskazującymi zgodność za pomocą programu Windows PowerShell i program PowerShell Core

Po upewnieniu się, że modułu współpracuje z programu Windows PowerShell i program PowerShell Core manifestu modułu należy jawnie wskazywały zgodność za pomocą [CompatiblePSEditions][] właściwości. Wartość `Desktop` oznacza, że moduł jest zgodny z programu Windows PowerShell, podczas wartość `Core` oznacza, że moduł jest zgodny z programu PowerShell Core. W tym zarówno `Desktop` i `Core` oznacza, że moduł jest zgodny z programu Windows PowerShell i program PowerShell Core.

> [!NOTE]
> `Core` automatycznie oznacza, że moduł jest zgodny z Windows, Linux i macOS.
> **CompatiblePSEditions** właściwość wprowadzono w programie PowerShell w wersji 5. Moduł manifesty używające **CompatiblePSEditions** właściwości nie można załadować w wersjach wcześniejszych niż programu PowerShell w wersji 5.

### <a name="indicating-os-compatibility"></a>Oznaczający zgodność systemu operacyjnego

Najpierw sprawdź, czy modułu działa w systemie Linux i macOS. Następnie należy wskazać zgodność z tymi systemami operacyjnymi w manifeście modułu. To ułatwia użytkownikom wyszukiwanie modułu dla swojego systemu operacyjnego podczas publikowania w [Galeria programu PowerShell][].

W manifeście modułu `PrivateData` właściwość ma `PSData` właściwości podrzędnych. Opcjonalny `Tags` właściwość `PSData` przyjmuje tablicę wartości, które pojawiają się w galerii programu PowerShell. Galeria programu PowerShell obsługuje następujące wartości zgodności:

| Tag               | Opis                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Zgodne z programu PowerShell Core 6          |
| PSEdition_Desktop | Zgodne z programem Windows PowerShell         |
| Windows           | Zgodne z Windows                    |
| Linux             | Zgodne z systemem Linux (nie określonej dystrybucji) |
| macOS             | Zgodne z systemem macOS                      |

Przykład:

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
[Testy środowiska uruchomieniowego]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[INTERFEJS WIERSZA POLECENIA PLATFORMY .NET]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[Standardowy programu PowerShell]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[Galeria programu PowerShell]: https://www.powershellgallery.com
[Narzędzia .NET portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
