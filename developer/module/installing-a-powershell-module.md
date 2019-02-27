---
title: Instalowanie modułu programu PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: f7899713dd273b793017adfa0a20b3ff3352b62a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851128"
---
# <a name="installing-a-powershell-module"></a>Instalowanie modułu programu PowerShell

Po utworzeniu modułu programu PowerShell, prawdopodobnie należy zainstalować moduł w systemie, aby inni użytkownicy mogą go używać. Ogólnie rzecz biorąc to po prostu składa się z modułu pliki kopiowane (ie, psm1 lub zestawie binarnym, manifestu modułu i inne skojarzone pliki) do katalogu na tym komputerze. Dla bardzo małym projektem może to być proste i polega na kopiowanie i wklejanie plików za pomocą Eksploratora Windows na pojedynczym komputerze zdalnym; Jednak w przypadku większych rozwiązań możesz korzystać z bardziej zaawansowanych procesu instalacji. Niezależnie od tego, jak się dostać modułu do systemu programu PowerShell można użyć szereg technik, które umożliwi użytkownikom wyszukiwanie i korzystanie z modułów. (Aby uzyskać więcej informacji, zobacz [zaimportowanie modułu PowerShell](./importing-a-powershell-module.md).) W związku z tym główny problem w przypadku instalacji jest zapewnienie środowiska PowerShell będzie można znaleźć modułu.

Ten temat zawiera następujące sekcje:

- Zasady dotyczące instalowania modułów

- Gdzie można zainstalować moduły

- Instalowanie wielu wersji modułu

- Wystąpił konflikt między nazwą polecenia obsługi

## <a name="rules-for-installing-modules"></a>Zasady dotyczące instalowania modułów

Poniższe informacje odnoszą się do wszystkich modułów, w tym moduły, które tworzysz własne użytkowania, moduły, które otrzymujesz pochodzące od innych firm i moduły, które możesz udostępnić innym osobom.

### <a name="install-modules-in-psmodulepath"></a>Zainstaluj moduły w PSModulePath

Jeśli to możliwe, należy zainstalować wszystkie moduły w ścieżce, która znajduje się w **PSModulePath** zmiennej środowiskowej lub ścieżka modułu, aby dodać **PSModulePath** wartości zmiennej środowiskowej.

**PSModulePath** zmienna środowiskowa ($Env: PSModulePath) zawiera lokalizacje modułów programu Windows PowerShell. Polecenia cmdlet oparte na wartość tej zmiennej środowiskowej, aby znaleźć modułów.

Domyślnie **PSModulePath** wartości zmiennej środowiskowej zawiera następujące systemu i użytkownika modułu katalogów, ale można dodać do i edytować wartość.

- $PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Ta lokalizacja jest zarezerwowana dla modułów, które są dostarczane z Windows. Nie należy instalować modułów do tej lokalizacji.

- $Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)

- $Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)

  Aby uzyskać wartość **PSModulePath** zmiennej środowiskowej, użyj jednej z następujących poleceń.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Aby dodać ścieżkę modułu wartość **PSModulePath** zmiennej środowiskowej wartość, należy użyć następującego formatu polecenia. Ten format używa **setenvironmentvariable nie zawiera** metody **System.Environment** klasy w celu zmiany niezależne od sesji **PSModulePath** środowiska Zmienna.

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Po dodaniu ścieżki do **PSModulePath**, należy emisji komunikat środowiska o zmianie. Zmianie rozgłaszania umożliwia innych aplikacji, takich jak powłoki wczytać zmiany. Do emisji przeznaczonych jest zmiana, mają kodów instalacji produktu, Wyślij **WM_SETTINGCHANGE** komunikatu o `lParam` ustawiony na ciąg "Environment". Pamiętaj wysłać wiadomość po kodzie instalacji modułu został zaktualizowany **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Użyj nazwy katalogu poprawny modułu

Moduł "sformułowany" jest to moduł, który jest przechowywany w katalogu, który ma taką samą nazwę jak podstawowa nazwa co najmniej jeden plik w katalogu modułu. Jeśli moduł nie jest poprawnie sformułowany, programu Windows PowerShell nie rozpoznaje je jako moduł.

"Nazwa podstawowa" pliku jest nazwę bez rozszerzenia nazwy pliku. W module poprawnie sformułowany nazwę katalogu, który zawiera pliki modułu musi odpowiadać nazwa podstawowa co najmniej jeden plik w module.

Na przykład w module Fabrikam przykładowe katalogu, który zawiera pliki modułu nosi nazwę "Fabrikam", a nazwa podstawowa "Fabrikam" ma co najmniej jeden plik. W takim przypadku zarówno Fabrikam.psd1 Fabrikam.dll się nazwa podstawowa "Fabrikam".

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Efekt niepoprawne instalacji

Jeśli moduł nie jest poprawnie sformułowany, a jego lokalizacja jest niedostępna w wartości **PSModulePath** zmiennej środowiskowej, odnajdywania podstawowe funkcje programu Windows PowerShell, podobny do następującego nie będą działać.

- Funkcja automatycznego modułu ładowania nie może automatycznie zaimportować moduł.

- `ListAvailable` Parametru [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet nie można odnaleźć modułu.

- [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenie cmdlet nie można odnaleźć modułu. Aby zaimportować moduł, należy podać pełną ścieżkę do pliku modułu głównego lub plik manifestu modułu.

  Dodatkowe funkcje, takie jak następujące polecenie, nie działają, chyba że moduł są importowane do sesji. W modułach sformułowany **PSModulePath** zmiennej środowiskowej, te funkcje działają, nawet wtedy, gdy moduł nie są importowane do sesji.

- [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) polecenie cmdlet nie może odnaleźć poleceń w module.

- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) i [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) poleceń cmdlet nie można zaktualizować ani zapisać Pomoc dla modułu.

- [Polecenie Pokaż](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) polecenie cmdlet nie może znaleźć i wyświetlić poleceń w module.

  Brakuje poleceń w module `Show-Command` okna w Windows PowerShell zintegrowane Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>Gdzie można zainstalować moduły

W tej sekcji opisano miejsca w systemie plików, aby zainstalować moduły programu Windows PowerShell. Lokalizacja zależy od tego, jak moduł jest używany.

### <a name="installing-modules-for-a-specific-user"></a>Instalowanie modułów dla określonego użytkownika

Jeśli możesz utworzyć własny moduł lub uzyskać modułu z drugiej strony, takich jak witryny internetowej społeczności programu Windows PowerShell, i chcesz, aby moduł, który ma być dostępny dla tego konta użytkownika, należy zainstalować moduł, w katalogu moduły specyficzne dla użytkownika.

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

Katalog moduły specyficzne dla użytkownika jest dodawany do wartości **PSModulePath** zmiennej środowiskowej domyślnie.

### <a name="installing-modules-for-all-users-in-program-files"></a>Instalowanie modułów dla wszystkich użytkowników w folderze Program Files

Jeśli chcesz, aby moduł mają być dostępne dla wszystkich kont użytkowników na komputerze, należy zainstalować moduł, w lokalizacji plików programów.

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> Lokalizacja plików programu zostanie dodany do wartości zmiennej środowiskowej PSModulePath domyślnie w programie Windows PowerShell 4.0 i nowszych wersjach. We wcześniejszych wersjach programu Windows PowerShell, można ręcznie utworzyć ((%ProgramFiles%\WindowsPowerShell\Modules) lokalizacji Program Files i Dodaj tę ścieżkę do zmiennej środowiskowej PSModulePath, zgodnie z powyższym opisem.

### <a name="installing-modules-in-a-product-directory"></a>Instalowanie modułów w katalogu produktów

Jeśli przekazujesz modułu do innych stron, użyj domyślna lokalizacja plików programu opisanych powyżej, lub Utwórz własne podkatalogu specyficzny dla firmy lub specyficzne dla produktu z katalogu % ProgramFiles %.

Na przykład fikcyjnej firmy Fabrikam technologii dostarcza modułu programu Windows PowerShell dla ich firmy Fabrikam, Menedżer produktu. Ich Instalator modułu tworzy podkatalog modułów w podkatalogu Fabrikam Menedżera produktu.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Aby włączyć funkcje odnajdywania modułu programu Windows PowerShell można znaleźć modułu firmy Fabrikam, Instalator modułu Fabrikam dodaje wartość lokalizacja modułu **PSModulePath** zmiennej środowiskowej.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technolgies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Instalowanie modułów w katalogu wspólnych plików

Jeśli moduł jest używany przez wiele składników produktu lub przez wiele wersji produktu, należy zainstalować moduł w podkatalogu podkatalogu Files\Modules %ProgramFiles%\Common specyficzne dla modułu.

W poniższym przykładzie moduł Fabrikam jest zainstalowany w podkatalogu Fabrikam podkatalogu Files\Modules %ProgramFiles%\Common. Należy pamiętać, że każdy moduł znajduje się w jego własnej podkatalogu w podkatalogu modułów.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

Następnie Instalator gwarantuje wartość **PSModulePath** zmienna środowiskowa zawiera ścieżkę podkatalogu wspólnego moduły plików.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Instalowanie wielu wersji modułu

Aby zainstalować wiele wersji tego samego modułu, użyj następującej procedury.

1. Utwórz katalog dla każdej wersji modułu. Numer wersji należy uwzględnić w nazwie katalogu.

2. Tworzenie manifestu modułu dla każdej wersji modułu. W wartości **ModuleVersion** klucza w manifeście, wprowadź numer wersji modułu. Zapisz plik manifestu (psd1), w tym katalogu specyficzny dla wersji modułu.

3. Dodaj ścieżka folderu głównego modułu wartość **PSModulePath** zmiennej środowiskowej, jak pokazano w poniższych przykładach.

Aby zaimportować określoną wersję modułu, można użyć użytkownik końcowy `MinimumVersion` lub `RequiredVersion` parametry [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet.

Na przykład jeśli moduł Fabrikam jest dostępny w wersji 8.0 i 9.0, struktura katalogów modułu Fabrikam może wyglądać w następujący sposób.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

Instalator dodaje obu ścieżek modułu do **PSModulePath** wartości zmiennej środowiskowej.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Po zakończeniu tych kroków **ListAvailable** parametru [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet pobiera oba moduły firmy Fabrikam. Aby zaimportować konkretnym module, użyj `MiminumVersion` lub `RequiredVersion` parametry [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet.

Jeśli oba moduły są importowane do tej samej sesji i moduły zawierają polecenia cmdlet, za pomocą tej samej nazwy, polecenia cmdlet, które są importowane ostatnio obowiązują w sesji.

## <a name="handling-command-name-conflicts"></a>Wystąpił konflikt między nazwą polecenia obsługi

Konfliktom nazw poleceń może wystąpić, gdy polecenia, które eksportuje modułu mają taką samą nazwę jak polecenia w sesji użytkownika.

W przypadku sesji zawiera dwa polecenia, które mają taką samą nazwę, programu Windows PowerShell działa typ polecenia, który ma pierwszeństwo. Gdy sesja zawiera dwa polecenia, które mają taką samą nazwę i ten sam typ, programu Windows PowerShell uruchamia polecenia, który został dodany ostatnio do sesji. Aby uruchomić polecenie, które nie jest uruchamiane domyślnie, użytkownicy mogą polecenia Zakwalifikuj nazwę przez określenie z nazwą modułu.

Na przykład, jeśli sesja zawiera `Get-Date` funkcji i `Get-Date` funkcja domyślnie uruchamia polecenie cmdlet programu Windows PowerShell. Aby uruchomić polecenia cmdlet, należy poprzedzić polecenie nazwę modułu, takie jak:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Aby zapobiec konfliktom nazw, można użyć autorzy modułów **DefaultCommandPrefix** klucza w manifeście modułu do określania prefiksu rzeczownik dla wszystkich poleceń wyeksportowane z modułu.

Użytkownicy mogą używać **prefiks** parametru `Import-Module` polecenia cmdlet, aby używać alternatywnego prefiks. Wartość **prefiksu** parametru mają pierwszeństwo przed wartością **DefaultCommandPrefix** klucza.

## <a name="see-also"></a>Zobacz też

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Pisanie modułu programu Windows PowerShell](./writing-a-windows-powershell-module.md)
