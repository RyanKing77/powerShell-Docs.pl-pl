---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguracja, usługa, instalacja
title: Zapisywanie, kompilowanie i stosowanie konfiguracji
ms.openlocfilehash: 8bcd55518b0409b9a4b02ca95f027a0a77eb5300
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372178"
---
> Dotyczy: Windows PowerShell 4,0, Windows PowerShell 5,0

# <a name="write-compile-and-apply-a-configuration"></a>Zapisywanie, kompilowanie i stosowanie konfiguracji

To ćwiczenie polega na utworzeniu i zastosowaniu konfiguracji konfiguracji żądanego stanu (DSC) od początku do końca.
W poniższym przykładzie dowiesz się, jak napisać i zastosować bardzo prostą konfigurację. Konfiguracja spowoduje, że plik "HelloWorld. txt" istnieje na komputerze lokalnym. W przypadku usunięcia pliku Konfiguracja DSC zostanie ponownie utworzona podczas następnej aktualizacji.

Aby zapoznać się z omówieniem usługi DSC i jej działaniem, zobacz [Omówienie konfiguracji żądanego stanu dla deweloperów](../overview/overview.md).

## <a name="requirements"></a>Wymagania

Do uruchomienia tego przykładu będzie potrzebny komputer z uruchomionym programem PowerShell 4,0 lub nowszym.

## <a name="write-the-configuration"></a>Napisz konfigurację

[Konfiguracja](configurations.md) DSC to specjalna funkcja programu PowerShell, która definiuje, w jaki sposób należy skonfigurować co najmniej jeden komputer docelowy (węzły).

W ISE programu PowerShell lub w innym edytorze programu PowerShell wpisz następujące polecenie:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> ! Ważne w przypadku bardziej zaawansowanych scenariuszy, w których należy zaimportować wiele modułów, aby można było pracować z wieloma zasobami DSC w tej samej konfiguracji, upewnij się, że każdy moduł został umieszczony w `Import-DscResource`osobnym wierszu przy użyciu.
> Jest to łatwiejsze do utrzymania w kontroli źródła i wymagane podczas pracy z usługą DSC w konfiguracji stanu platformy Azure.
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

Zapisz plik jako "HelloWorld. ps1".

Definiowanie konfiguracji jest podobne do definiowania funkcji. Blok **węzła** określa węzeł docelowy, który ma zostać skonfigurowany w tym przypadku `localhost`.

Konfiguracja wywołuje jedno [zasoby](../resources/resources.md), `File` zasób. Zasoby wykonują czynności, aby upewnić się, że węzeł docelowy jest w stanie zdefiniowanym przez konfigurację.

## <a name="compile-the-configuration"></a>Kompiluj konfigurację

Aby Konfiguracja DSC została zastosowana do węzła, najpierw należy ją skompilować do pliku MOF.
Uruchomienie konfiguracji, takiej jak funkcja, spowoduje skompilowanie jednego pliku "MOF" dla każdego węzła zdefiniowanego przez `Node` blok.
Aby można było uruchomić konfigurację, należy umieścić w bieżącym zakresie skrypt "HelloWorld. ps1" jako *Źródło* danych.
Aby uzyskać więcej informacji, zobacz [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Źródło kropki* skrypt "helloworld. ps1", wpisując ścieżkę, w której został zapisany, po `. ` (kropka, spacja). Następnie możesz uruchomić konfigurację, wywołując ją jako funkcję.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

Spowoduje to wygenerowanie następujących danych wyjściowych:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Zastosuj konfigurację

Teraz, gdy masz skompilowany plik MOF, możesz zastosować konfigurację do węzła docelowego (w tym przypadku komputera lokalnego) przez wywołanie polecenia cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .

Polecenie cmdlet informuje [lokalny Configuration Manager (LCM)](../managing-nodes/metaConfig.md), aparat DSC, aby zastosować konfigurację. `Start-DscConfiguration`
LCM wykonuje działania wywołujące zasoby DSC, aby zastosować konfigurację.

Użyj poniższego kodu, aby uruchomić `Start-DSCConfiguration` polecenie cmdlet. Określ ścieżkę katalogu, w której plik "localhost. MOF" jest przechowywany w `-Path` parametrze. Polecenie cmdlet przeszuka katalog określony dla plików "\<ComputerName\>. MOF". `Start-DSCConfiguration` `Start-DSCConfiguration` Polecenie cmdlet próbuje zastosować każdy plik "MOF", który znajduje się na hoście określonym przez nazwę pliku ("localhost", "Serwer01", "DC-02" itp.).

> [!NOTE]
> Jeśli parametr nie jest określony, program `Start-DSCConfiguration` tworzy zadanie w tle w celu wykonania operacji. `-Wait` Określenie **parametru** pozwala obejrzeć pełne dane wyjściowe operacji. `-Verbose` `-Wait`i `-Verbose` są parametrami opcjonalnymi.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Testowanie konfiguracji

Po zakończeniu `Start-DSCConfiguration` tego polecenia cmdlet powinien zostać wyświetlony plik HelloWorld. txt w określonej lokalizacji. Zawartość można sprawdzić za pomocą polecenia cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content) .

Możesz również *przetestować* bieżący stan za pomocą polecenia [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

Dane wyjściowe powinny mieć wartość "true", jeśli węzeł jest aktualnie zgodny z zastosowaną konfiguracją.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>Ponowne zastosowanie konfiguracji

Aby zobaczyć, że konfiguracja zostanie zastosowana ponownie, można usunąć plik tekstowy utworzony przez konfigurację. Użyj `Start-DSCConfiguration` polecenia cmdlet `-UseExisting` z parametrem. `-UseExisting` Parametr instruujeponowniezastosowaćplik"Current.MOF",któryreprezentuje`Start-DSCConfiguration` ostatnio zastosowaną konfigurację.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Następne kroki

- Dowiedz się więcej na temat konfiguracji DSC w [konfiguracjach DSC](configurations.md).
- Zobacz, jakie zasoby DSC są dostępne i jak tworzyć niestandardowe zasoby DSC w [zasobach DSC](../resources/resources.md).
- Znajdź konfiguracje i zasoby DSC w [Galeria programu PowerShell](https://www.powershellgallery.com/).
