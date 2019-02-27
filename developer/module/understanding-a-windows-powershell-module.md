---
title: Opis modułu programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851527"
---
# <a name="understanding-a-windows-powershell-module"></a>Informacje o module programu Windows PowerShell

A *modułu* to zbiór powiązane funkcje programu Windows PowerShell, grupowane jako wygodny jednostka (zazwyczaj zapisane w pojedynczym katalogu). Definiując zestaw plików skryptów powiązanych, zespoły i powiązane zasoby jako moduł, można odwoływać się do, obciążenia, utrwalanie i udostępnić swój kod znacznie łatwiejsze niż w przypadku, w przeciwnym razie.

Głównym celem modułu jest umożliwienie modularyzacji (tj. i ponowne użycie abstrakcji) kodu programu Windows PowerShell. Na przykład najbardziej podstawową metodą tworzenia modułu jest po prostu Zapisz skrypt programu Windows PowerShell jako pliku psm1. Spowoduje to więc umożliwia formantu (ie, Utwórz publiczny lub prywatny) funkcje i zmienne, zawarty w skrypcie. Zapisywanie skrypt jako plik psm1 również pozwala na kontrolowanie zakresu niektórych zmiennych. Ponadto umożliwia także polecenia cmdlet takie jak [Install-Module](/powershell/module/PowershellGet/Install-Module) do organizowania, zainstalować i używać skryptu jako bloków konstrukcyjnych dla większe rozwiązania.

## <a name="module-components-and-types"></a>Składniki modułu i typów

Moduł składa się z czterech podstawowych składników:

1. Niektóre Sortowanie pliku kodu — zwykle skrypt programu PowerShell lub zestawu zarządzane poleceń cmdlet.

2. Jakikolwiek inny powyżej plik kodu może być potrzebna takie jak dodatkowe zestawy pomoc pliki lub skrypty.

3. Plik manifestu, który opisano powyżej pliki, a także metadada, takie jak tworzenie i przechowywanie wersji informacje są przechowywane...

4. Katalog, który zawiera całą zawartość powyżej i znajduje się gdzie PowerShell rozsądnie go znaleźć.

   Należy pamiętać, że żadna z tych składników, samodzielnie, są rzeczywiście konieczne. Na przykład moduł z technicznego punktu widzenia można tylko skrypt, które są przechowywane w pliku psm1. Może również mieć moduł, który ma nic, ale plik manifestu, który jest używany głównie do celów organizacji. Można także napisać skrypt, który dynamicznie tworzy moduł i jako takie nie jest potrzebna katalog do przechowywania w. W poniższych sekcjach opisano typy moduły, w których można uzyskać za pomocą mieszanie i dopasowywanie ze sobą różne części modułu.

### <a name="script-modules"></a>Moduły skryptów

Jak wskazuje nazwa, *moduł skryptu* plik (.psm1), który zawiera dowolny prawidłowy kod programu Windows PowerShell. Skrypt deweloperom i administratorom służy ten typ modułu do tworzenia modułów, których elementy Członkowskie zawierają funkcje, zmienne i inne. Centralnym moduł skryptu jest po prostu skrypt programu Windows PowerShell z innym rozszerzeniem umożliwia administratorom używanie funkcji importu, eksportu i zarządzania na nim.

Ponadto umożliwia plik manifestu zostaną umieszczone inne zasoby w module, takie jak pliki danych, innych modułów zależnych lub skrypty środowiska uruchomieniowego. Pliki manifestu są także przydatne metadane, takie jak tworzenie i przechowywanie wersji informacji śledzenia.

Na koniec module skryptów, takich jak każdy inny moduł, który nie jest dynamicznie tworzony musi można zapisać w folderze, który PowerShell uzasadniony sposób można odnajdywać. Zazwyczaj jest na ścieżce modułu programu PowerShell; ale w razie potrzeby można jawnie opisać zainstalowanym module. Aby uzyskać więcej informacji, zobacz [jak napisać do modułu skryptu programu PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Moduły binarne

A *binarne modułu* jest zestaw .NET Framework (.dll), który zawiera skompilowanego kodu, takie jak C#. Polecenia cmdlet, deweloperzy mogą używać tego typu modułu, aby udostępnić poleceń cmdlet, dostawców i innych. (Istniejące przystawek może również służyć jako moduły binarne.) W porównaniu do modułu skryptu binarne moduł służy do tworzenia poleceń cmdlet, które są szybsze lub korzystanie z funkcji (takich jak wielowątkowość) które nie są łatwe do kodu w skryptów programu Windows PowerShell.

Zgodnie z modułami skryptu może zawierać plik manifestu do opisania dodatkowe zasoby, których używa modułu i do śledzenia metadane dotyczące modułu. Podobnie prawdopodobnie należy zainstalować modułu binarnego w folderze gdzieś na ścieżce modułu programu PowerShell. Aby uzyskać więcej informacji, zobacz instrukcje [sposobu pisania binarne modułu programu PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Moduły manifestu

A *manifestu modułu* jest moduł, który używa pliku manifestu do opisu, wszystkie jego składniki, lecz nieposiadającymi dowolny rodzaj zestaw podstawowych lub skryptu. (Formalnie, pozostawia manifestu modułu `ModuleToProcess` lub `RootModule` elemencie manifestu puste.) Jednak nadal można użyć funkcji modułu, takie jak możliwość ładowania zestawów zależnych lub automatycznie uruchamiać niektóre skrypty przetwarzania wstępnego. Można również użyć manifestu modułu, to wygodny sposób spakowanie zasoby, które będą używane inne moduły, takie jak moduły zagnieżdżonych, zestawy, typy lub formatów. Aby uzyskać więcej informacji, zobacz [jak napisać Manifest modułu programu PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Moduły dynamiczne

A *modułu dynamicznego* jest moduł nie jest załadowany z lub zapisany w pliku. Zamiast tego są one tworzone dynamicznie przez skrypt, za pomocą [nowy moduł](/powershell/module/Microsoft.PowerShell.Core/New-Module) polecenia cmdlet. Ten typ modułu pozwala skryptu, aby utworzyć moduł na żądanie, które nie musi być załadowany lub zapisany w magazynie trwałym. Z natury modułu dynamicznego ma być krótkotrwały i nie są dostępne dla `Get-Module` polecenia cmdlet. Podobnie zwykle nie ma potrzeby manifesty modułu ani czy prawdopodobnie potrzebuje stałe foldery do przechowywania ich powiązanych zestawów.

## <a name="module-manifests"></a>Manifesty modułu

A *manifestu modułu* plik psd1, który zawiera tabelę mieszania. Klucze i wartości w tabeli wyznaczania wartości skrótu, wykonaj następujące czynności:

- Opisano zawartość i atrybutów modułu.

- Zdefiniuj wymagania wstępne.

- Określ, jak są przetwarzane składników.

  Manifesty nie są wymagane dla modułu. Moduły mogą odwoływać się do plików skryptu (ps1), pliki modułów (.psm1), plików manifestu (psd1), formatowanie skryptów i typ plików (.ps1xml), polecenia cmdlet i dostawcy zestawów (.dll), pliki zasobów, pliki pomocy, pliki lokalizacyjne lub dowolny inny typ pliku lub zasobu, jest powiązany jako część modułu. Międzynarodowe skryptu folderem modułu zawiera zbiór plików katalog komunikatów. Jeśli dodasz plik manifestu do folderu modułu możesz odwoływać się wiele plików jako pojedyncza jednostka, odwołując się do manifestu.

  Manifest, sama w tym artykule opisano następujące kategorie informacji:

- Metadane dotyczące modułu, na przykład numer wersji modułu, autor i opis.

- Wymagania wstępne potrzebne do zaimportowania modułu, takie jak wersja programu Windows PowerShell, typowe wersję środowiska uruchomieniowego języka (wspólnego CLR) i wymaganych modułów.

- Dyrektywy przetwarzania, takich jak skrypty, formaty i typy do przetworzenia.

- Ograniczenia dotyczące elementów członkowskich modułu do wyeksportowania, takich jak aliasy, funkcje, zmienne i poleceń cmdlet do wyeksportowania.

  Aby uzyskać więcej informacji, zobacz [jak napisać Manifest modułu programu PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Przechowywanie i instalowania modułu

Po utworzeniu skryptu, binarne lub manifestu modułu, można zapisać swoją pracę w lokalizacji czy inne osoby mogą do niego dostęp. Na przykład modułu mogą być przechowywane w folderze systemu, w którym jest zainstalowany program Windows PowerShell lub mogą być przechowywane w folderze użytkownika.

Ogólnie rzecz biorąc, można określić, gdzie należy zainstalować przy użyciu jednej ze ścieżek, przechowywane w module `$ENV:PSModulePath` zmiennej. Przy użyciu jednej z tych ścieżek oznacza programu PowerShell można automatycznie znaleźć i załadować modułu, gdy użytkownik wywołuje on w ich kodzie. Jeśli przechowujesz gdzieś modułu, można jawnie pozwolić, aby wiedzieć, przekazując w lokalizacji modułu jako parametr, po wywołaniu programu PowerShell `Install-Module`.

Niezależnie od tego, ścieżka folderu jest określany jako *podstawowy* modułu (ModuleBase) i nazwę skryptu, plik binarny lub manifestu modułu powinna być taka sama jak nazwa folderu modułu, z następującymi wyjątkami:

- Moduły dynamiczne, które są tworzone przez `New-Module` polecenia cmdlet mogą być nazwane za pomocą `Name` parametru polecenia cmdlet.

- Moduły importowane z zestawów obiekty według  **`Import-Module` — zestawu** polecenia są określane według następującej składni: `"dynamic_code_module_" + assembly.GetName()`.

  Aby uzyskać więcej informacji, zobacz [Instalowanie modułu programu PowerShell](./installing-a-powershell-module.md) i [Modyfikowanie ścieżki instalacji PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Polecenia cmdlet modułu i zmienne

Następujące polecenia cmdlet i zmienne są dostarczane przez środowisko Windows PowerShell do tworzenia i zarządzania modułami.

[Nowy moduł](/powershell/module/Microsoft.PowerShell.Core/New-Module) polecenia cmdlet to polecenie cmdlet tworzy nowy moduł dynamiczny, czy istnieje tylko w pamięci. Moduł jest tworzony z bloku skryptu i jego członków wyeksportowane, takie jak jego funkcje i zmienne, są natychmiast dostępne w sesji i pozostają dostępne przed zamknięciem sesji.

[Nowe ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) polecenia cmdlet to polecenie cmdlet tworzy nowy plik manifestu (psd1) moduł, wypełnia wartości i zapisuje plik manifestu do określonej ścieżki. To polecenie cmdlet można również utworzyć szablon manifestu modułu, który można wypełnić ręcznie.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) polecenia cmdlet to polecenie cmdlet dodaje przynajmniej jeden moduł do bieżącej sesji.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenia cmdlet to polecenie cmdlet pobiera informacje dotyczące modułów, które zostały lub które mogą być importowane do bieżącej sesji.

[Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) polecenia cmdlet to polecenie cmdlet określa członków modułu (takich jak polecenia cmdlet, funkcje, zmienne i aliasów), które są eksportowane z pliku skryptu (.psm1) modułu lub utworzone przy użyciu modułu dynamicznego `New-Module` polecenia cmdlet.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) polecenia cmdlet to polecenie cmdlet usuwa modułów z bieżącej sesji.

[Test ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) polecenia cmdlet, to polecenie cmdlet sprawdza, czy manifest modułu dokładnie zawiera opis składników modułu, upewniając się, że pliki, które są wymienione w pliku manifestu (psd1) modułu istnieje w określonych ścieżek.

$PSScriptRoot ta zmienna uwzględnia katalogu, w którym jest wykonywana moduł skryptu. Dzięki temu skrypty, aby ścieżka modułu na dostęp do innych zasobów.

$env: PSModulePath ta zmienna środowiskowa zawiera listę katalogów, w których programu Windows PowerShell moduły są przechowywane. Wartość tej zmiennej, podczas importowania modułów automatycznie i aktualizowania tematy pomocy dla modułów korzysta z programu Windows PowerShell.

## <a name="see-also"></a>Zobacz też

[Pisanie modułu programu Windows PowerShell](./writing-a-windows-powershell-module.md)
