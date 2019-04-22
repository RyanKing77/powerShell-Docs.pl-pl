---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguracja, usługi, Instalator
title: Zapisywanie, kompilowanie i stosowanie konfiguracji
ms.openlocfilehash: 947308efa165543571801c88a922daf44fa88be0
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59506822"
---
> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Zapisywanie, kompilowanie i stosowanie konfiguracji

To ćwiczenie zawiera opis sposobu tworzenia i stosowania konfiguracji Desired State Configuration (DSC), od początku do końca.
W poniższym przykładzie dowiesz się, jak pisać i Zastosuj konfigurację bardzo proste. Konfiguracja będzie upewnij się, że plik "HelloWorld.txt" istnieje na komputerze lokalnym. Jeśli usuniesz plik, DSC ponownie utworzy go następnym razem, który aktualizuje.

Aby uzyskać omówienie DSC i jak to działa, zobacz [omówienie Desired State Configuration dla deweloperów](../overview/overview.md).

## <a name="requirements"></a>Wymagania

Aby uruchomić ten przykład, należy komputer z systemem programu PowerShell w wersji 4.0 lub nowszej.

## <a name="write-the-configuration"></a>Zapisz konfigurację

DSC [konfiguracji](configurations.md) jest specjalną funkcję programu PowerShell, który definiuje, jak chcesz skonfigurować jeden lub więcej komputerów docelowych (węzły).

W środowisku ISE programu PowerShell lub innego edytora programu PowerShell wpisz następujące polecenie:

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

Zapisz plik jako "HelloWorld.ps1".

Definiowanie konfiguracji jest podobne do definiowania funkcji. **Węzła** bloku określa węzeł docelowy należy skonfigurować w tym przypadku `localhost`.

Konfiguracja wywołuje jedną [zasobów](../resources/resources.md), `File` zasobów. Zasoby wykonują pracę zapewnienia, że węzeł docelowy jest w stanie zdefiniowane przez tą konfigurację.

## <a name="compile-the-configuration"></a>Kompilowanie konfiguracji w

Dla konfiguracji DSC do zastosowania do węzła jej muszą najpierw być skompilowane w pliku MOF.
Uruchamianie konfiguracji, takich jak funkcja zostanie skompilowany jeden plik "MOF" dla każdego węzła zdefiniowane przez `Node` bloku.
Aby uruchomić konfigurację, trzeba *źródła z dot* skryptu "HelloWorld.ps1" w bieżącym zakresie.
Aby uzyskać więcej informacji, zobacz [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Źródło z dot* skryptu "HelloWorld.ps1", wpisując w polu Ścieżka, w której przechowywane, po `. ` (kropka, miejsca). Następnie możesz uruchomić konfigurację wywołując takich jak funkcja.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

Spowoduje to wygenerowanie następujące dane wyjściowe:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Zastosuj konfigurację

Teraz, gdy masz skompilowany plik MOF, konfigurację można zastosować do węzła docelowego (w tym przypadku komputer lokalny) przez wywołanie metody [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) polecenia cmdlet.

`Start-DscConfiguration` Informuje polecenia cmdlet [lokalnego Configuration Manager (LCM)](../managing-nodes/metaConfig.md), aparatu DSC, aby zastosować konfigurację.
LCM działa wywoływania zasoby DSC, aby zastosować konfigurację.

Użyj poniższego kodu do wykonania `Start-DSCConfiguration` polecenia cmdlet. Określ ścieżkę katalogu, do przechowywania Twojego "localhost.mof" Aby `-Path` parametru. `Start-DSCConfiguration` Polecenia cmdlet wygląda za pośrednictwem katalogu określonym dla dowolnego "\<computername\>MOF" pliki. `Start-DSCConfiguration` Polecenie cmdlet podejmie próbę dotyczą każdego pliku "MOF" znajdzie computername określony przez nazwę pliku ("localhost", "Serwer01", "dc-02" itp.).

> [!NOTE]
> Jeśli `-Wait` parametr nie jest określony, `Start-DSCConfiguration` tworzy zadania w tle do wykonania tej operacji. Określanie `-Verbose` parametr umożliwia Obejrzyj **pełne** wynik operacji. `-Wait`, a `-Verbose` są oba parametry opcjonalne.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Testowanie konfiguracji

Raz `Start-DSCConfiguration` polecenie cmdlet zostało zakończone, powinien zostać wyświetlony plik "HelloWorld.txt" w określonej lokalizacji. Można sprawdzić zawartość z [pobrania zawartości](/powershell/module/microsoft.powershell.management/get-content) polecenia cmdlet.

Możesz również *test* bieżący stan za pomocą [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

Dane wyjściowe powinny być "True", jeśli węzeł jest aktualnie zgodny ze stosowanych konfiguracji.

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

Aby sprawdzić konfigurację, ponownie zastosowane, można usunąć pliku tekstowego, utworzone przez konfigurację. Użycie `Start-DSCConfiguration` polecenia cmdlet z `-UseExisting` parametru. `-UseExisting` Powoduje, że parametr `Start-DSCConfiguration` Ponowne zgłoszenie chęci pliku "current.mof", która reprezentuje ostatnio pomyślnie zastosować konfigurację.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Następne kroki

- Dowiedz się więcej na temat konfiguracji DSC w [konfiguracje DSC](configurations.md).
- Zobacz, jakie zasoby DSC są dostępne i jak tworzyć niestandardowe zasoby DSC w [zasoby DSC](../resources/resources.md).
- Konfiguracje DSC i zasoby w [galerii programu PowerShell](https://www.powershellgallery.com/).
