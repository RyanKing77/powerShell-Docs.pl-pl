---
title: Omówienie modułu programu Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848068"
---
# <a name="understanding-a-windows-powershell-module"></a>Informacje o module programu Windows PowerShell

*Moduł* jest zestawem powiązanych funkcji programu Windows PowerShell pogrupowanych jako dogodna jednostka (zwykle zapisywana w jednym katalogu). Definiowanie zestawu powiązanych plików skryptów, zestawów i powiązanych zasobów jako modułu, można odwoływać się, ładować, utrwalać i udostępniać kod znacznie łatwiej niż w przeciwnym razie.

Głównym celem modułu jest umożliwienie modularization (IE, ponownego użycia i abstrakcji) kodu programu Windows PowerShell. Na przykład najbardziej podstawowym sposobem tworzenia modułu jest po prostu zapisanie skryptu programu Windows PowerShell jako pliku. PSM1. Dzięki temu można kontrolować (IE, udostępniać publiczne lub prywatne) funkcje i zmienne zawarte w skrypcie. Zapisanie skryptu jako pliku. PSM1 umożliwia również Sterowanie zakresem niektórych zmiennych. Na koniec można także użyć poleceń cmdlet, takich jak [Install-module](/powershell/module/PowershellGet/Install-Module) , aby organizować, instalować i używać skryptu jako bloków konstrukcyjnych dla większych rozwiązań.

## <a name="module-components-and-types"></a>Składniki i typy modułów

Moduł składa się z czterech podstawowych składników:

1. Rodzaj pliku kodu — zazwyczaj jest to skrypt programu PowerShell lub zarządzany zestaw poleceń cmdlet.

2. Wszystko, co może wymagać powyższego pliku kodu, takiego jak dodatkowe zestawy, pliki pomocy lub skrypty.

3. Plik manifestu, który opisuje powyższe pliki, a także przechowuje metadane, takie jak informacje o autorze i wersji.

4. Katalog zawierający całą powyższą zawartość i znajduje się w lokalizacji, w której program PowerShell może go znaleźć.

   Należy zauważyć, że żaden z tych składników nie jest rzeczywiście konieczny. Na przykład moduł może być technicznie tylko skrypt przechowywany w pliku. PSM1. Możesz również mieć moduł, który nie jest plikiem manifestu, który jest używany głównie do celów organizacyjnych. Możesz również napisać skrypt, który dynamicznie tworzy moduł i w związku z tym nie potrzebuje katalogu do przechowywania jakichkolwiek elementów. W poniższych sekcjach opisano typy modułów, które można uzyskać przez mieszanie i dopasowywanie różnych możliwych części modułu.

### <a name="script-modules"></a>Moduły skryptów

Jak nazywa się, *moduł skryptu* to plik (. PSM1), który zawiera dowolny prawidłowy kod programu Windows PowerShell. Deweloperzy skryptów i Administratorzy mogą używać tego typu modułu do tworzenia modułów, których członkowie zawierają funkcje, zmienne i inne. W tym scenariuszu moduł skryptu jest po prostu skryptem programu Windows PowerShell z innym rozszerzeniem, co umożliwia administratorom korzystanie z funkcji importu, eksportu i zarządzania.

Ponadto można użyć pliku manifestu w celu uwzględnienia innych zasobów w module, takich jak pliki danych, inne moduły zależne lub skrypty środowiska uruchomieniowego. Pliki manifestu są również przydatne do śledzenia metadanych, takich jak informacje o tworzeniu i wersji.

Na koniec moduł skryptu, taki jak każdy inny moduł, który nie jest tworzony dynamicznie, musi być zapisany w folderze, który program PowerShell może w rozsądny sposób odnaleźć. Zwykle jest to ścieżka modułu programu PowerShell. ale w razie potrzeby można jawnie opisać miejsce instalacji modułu. Aby uzyskać więcej informacji, zobacz [jak napisać moduł skryptu programu PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Moduły binarne

*Moduł binarny* jest zestawem .NET Framework (. dll), który zawiera skompilowany kod, taki C#jak. Deweloperzy poleceń cmdlet mogą używać tego typu modułu do udostępniania poleceń cmdlet, dostawców i nie tylko. (Istniejące przystawki mogą również być używane jako moduły binarne). W porównaniu do modułu skryptu moduł binarny umożliwia tworzenie szybszych poleceń cmdlet lub korzystanie z funkcji (takich jak wielowątkowość), które nie są łatwe w kodzie w skryptach programu Windows PowerShell.

Podobnie jak w przypadku modułów skryptów, można dołączyć plik manifestu w celu opisania dodatkowych zasobów używanych przez moduł oraz do śledzenia metadanych dotyczących modułu. Analogicznie, prawdopodobnie należy zainstalować moduł binarny w folderze poza ścieżką modułu programu PowerShell. Aby uzyskać więcej informacji, zobacz jak [napisać moduł binarny programu PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Moduły manifestu

*Moduł manifestu* jest modułem, który używa pliku manifestu do opisywania wszystkich składników, ale nie ma żadnego sortowania podstawowego zestawu lub skryptu. (Formalnie moduł manifestu pozostawia `ModuleToProcess` element lub `RootModule` w manifeście puste). Można jednak nadal korzystać z innych funkcji modułu, takich jak możliwość załadowania zestawów zależnych lub automatycznego uruchamiania pewnych skryptów przed przetwarzaniem. Modułu manifestu można także użyć jako wygodnego sposobu spakowania zasobów używanych przez inne moduły, takich jak zagnieżdżone moduły, zestawy, typy lub formaty. Aby uzyskać więcej informacji, zobacz [jak napisać manifest modułu programu PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Moduły dynamiczne

*Moduł dynamiczny* jest modułem, który nie jest ładowany ani zapisywany w pliku. Zamiast tego są tworzone dynamicznie przez skrypt przy użyciu polecenia cmdlet [New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) . Ten typ modułu umożliwia skryptowi utworzenie modułu na żądanie, którego nie trzeba ładować ani zapisać w magazynie trwałym. Ze względu na swój charakter moduł dynamiczny jest przeznaczony do krótkotrwałości i dlatego nie może uzyskać do niego dostępu za `Get-Module` pomocą polecenia cmdlet. Podobnie zazwyczaj nie wymagają manifestów modułów, ani nie potrzebują folderów trwałych do przechowywania powiązanych zestawów.

## <a name="module-manifests"></a>Manifesty modułów

*Manifest modułu* to plik. psd1, który zawiera tablicę skrótów. Klucze i wartości w tabeli skrótów wykonują następujące czynności:

- Opisz zawartość i atrybuty modułu.

- Zdefiniuj wymagania wstępne.

- Ustal, jak składniki są przetwarzane.

  Manifesty nie są wymagane dla modułu. Moduły mogą odwoływać się do plików skryptów (. ps1), plików modułów skryptów (. PSM1), plików manifestu (. psd1), formatowania i typów plików (. PS1XML), poleceń cmdlet i zestawów dostawców (. dll), plików zasobów, plików pomocy, plików lokalizacji lub dowolnego innego typu pliku lub zasobu jest powiązany z modułem. W przypadku skryptu międzynarodowego folder modułu zawiera również zestaw plików wykazu komunikatów. W przypadku dodania pliku manifestu do folderu modułu można odwoływać się do wielu plików jako pojedynczej jednostki, odwołując się do manifestu.

  Sam manifest opisuje następujące kategorie informacji:

- Metadane dotyczące modułu, takie jak numer wersji modułu, autor i opis.

- Wymagania wstępne wymagane do zaimportowania modułu, takie jak wersja programu Windows PowerShell, wersja środowiska uruchomieniowego języka wspólnego (CLR) i wymagane moduły.

- Dyrektywy przetwarzania, takie jak skrypty, formaty i typy do przetworzenia.

- Ograniczenia dotyczące elementów członkowskich modułu do eksportowania, takie jak aliasy, funkcje, zmienne i polecenia cmdlet do eksportowania.

  Aby uzyskać więcej informacji, zobacz [jak napisać manifest modułu programu PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Przechowywanie i Instalowanie modułu

Po utworzeniu skryptu, pliku binarnego lub modułu manifestu można zapisać swoją służbę w lokalizacji, w której inne osoby mogą uzyskać do niej dostęp. Na przykład moduł może być przechowywany w folderze systemowym, w którym jest zainstalowany program Windows PowerShell, lub może być przechowywany w folderze użytkownika.

Ogólnie mówiąc, można określić, gdzie należy zainstalować moduł przy użyciu jednej ze ścieżek przechowywanych w `$ENV:PSModulePath` zmiennej. Użycie jednej z tych ścieżek oznacza, że program PowerShell może automatycznie znajdować i ładować moduł, gdy użytkownik wywołuje je w kodzie. Jeśli przechowujesz moduł w innym miejscu, możesz jawnie pozwolić programowi PowerShell, przekazując lokalizację modułu jako parametr podczas wywoływania `Install-Module`.

Niezależnie od ścieżki do folderu jest określana jako *podstawa* modułu (ModuleBase), a nazwa skryptu, pliku binarnego lub modułu manifestu powinna być taka sama jak nazwa folderu modułu, z następującymi wyjątkami:

- Moduły dynamiczne tworzone za `New-Module` pomocą polecenia cmdlet mogą być nazwane `Name` przy użyciu parametru polecenia cmdlet.

- Moduły zaimportowane z obiektów zestawu za pomocą `"dynamic_code_module_" + assembly.GetName()`  **`Import-Module` polecenia-Assembly** są nazwane zgodnie z następującą składnią:.

  Aby uzyskać więcej informacji, zobacz [Instalowanie modułu programu PowerShell](./installing-a-powershell-module.md) i [Modyfikowanie ścieżki instalacji PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Polecenia cmdlet i zmienne modułu

Następujące polecenia cmdlet i zmienne są udostępniane przez środowisko Windows PowerShell do tworzenia modułów i zarządzania nimi.

Polecenie cmdlet [New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) to polecenie cmdlet tworzy nowy moduł dynamiczny, który istnieje tylko w pamięci. Moduł jest tworzony na podstawie bloku skryptu, a jego wyeksportowane elementy członkowskie, takie jak jego funkcje i zmienne, są natychmiast dostępne w sesji i pozostają dostępne do momentu zamknięcia sesji.

Polecenie cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) to polecenie cmdlet tworzy nowy plik manifestu modułu (. psd1), wypełnia jego wartości i zapisuje plik manifestu w określonej ścieżce. Tego polecenia cmdlet można również użyć do utworzenia szablonu manifestu modułu, który może być wypełniany ręcznie.

Polecenie cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) to polecenie cmdlet dodaje jeden lub więcej modułów do bieżącej sesji.

Polecenie cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) to polecenie cmdlet pobiera informacje o modułach, które zostały lub które mogą zostać zaimportowane do bieżącej sesji.

Polecenie cmdlet [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) to polecenie cmdlet określa elementy członkowskie modułu (takie jak polecenia cmdlet, funkcje, zmienne i aliasy), które są eksportowane z pliku modułu skryptu (. PSM1) lub modułu dynamicznego utworzonego przy użyciu `New-Module` polecenia cmdlet.

Polecenie cmdlet [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) to polecenie cmdlet usuwa moduły z bieżącej sesji.

Polecenie cmdlet [test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) to polecenie cmdlet sprawdza, czy manifest modułu dokładnie opisuje składniki modułu przez sprawdzenie, czy pliki wymienione w pliku manifestu modułu (. psd1) rzeczywiście istnieją w określonych ścieżkach.

$PSScriptRoot ta zmienna zawiera katalog, z którego jest wykonywany moduł skryptu. Umożliwia skryptom używanie ścieżki modułu do uzyskiwania dostępu do innych zasobów.

$env:P SModulePath ta zmienna środowiskowa zawiera listę katalogów, w których są przechowywane moduły programu Windows PowerShell. Program Windows PowerShell używa wartości tej zmiennej podczas automatycznego importowania modułów i aktualizowania tematów pomocy dla modułów.

## <a name="see-also"></a>Zobacz też

[Pisanie modułu programu Windows PowerShell](./writing-a-windows-powershell-module.md)
