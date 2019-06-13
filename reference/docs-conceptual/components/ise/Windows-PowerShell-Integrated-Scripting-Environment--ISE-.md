---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Windows PowerShell Integrated Scripting Environment środowiska ISE
ms.openlocfilehash: 9bcb297a9e1990ede2cfff1e147aeda7cd69e873
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030550"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Integrated Scripting Environment (ISE)

Windows PowerShell zintegrowane Scripting Environment (ISE) jest jednym z dwóch hostów dla aparatu programu Windows PowerShell i języka. Z nim, których można pisać uruchamianie i testowanie skryptów w sposób, który nie są dostępne w konsoli programu Windows PowerShell. Środowiska ISE dodaje kolorowanie składni, uzupełniania po naciśnięciu tabulatora, IntelliSense, debugowania visual i Pomoc kontekstowa.

Środowiska ISE umożliwia uruchamianie poleceń w okienku konsoli, ale obsługuje ona również okienek, które umożliwiają jednoczesne wyświetlanie kodu źródłowego, skrypt i innych narzędzi, które można podłączyć do środowiska ISE. Można nawet otwierają wiele okien skryptu w tym samym czasie, który jest szczególnie przydatne podczas debugowania skryptu, który korzysta z funkcji zdefiniowanych w innych skryptów i modułów.

## <a name="whats-new"></a>Co nowego

Poniżej przedstawiono niektóre funkcje, które zostały dodane do środowiska ISE w najnowszych wersjach programu PowerShell.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Dodane w programie PowerShell 3.0 (system Windows Server 2012, Windows 8)

**Funkcja IntelliSense** automatycznie wykonuje poleceń przez wyświetlanie menu pasującego poleceń cmdlet, parametry, wartości parametrów, plików lub folderów podczas wpisywania.

**Fragmenty kodu** są krótkich fragmentów kodu, czy można łatwo wstawiać do skryptów usługi zapisu. Zbiór fragmentów przydatne znajduje się w polu, a także bardziej przy użyciu **nowy fragment** polecenia cmdlet.

**Dodatkowe narzędzia** dodaje funkcje do środowiska ISE mogą być tworzone przez pisanie kodu, który współdziała z [Windows PowerShell Model obiektów skryptowych ISE](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

Te narzędzia można wyświetlić formanty do okienka z zakładkami lub działać w sposób niewidoczny w tle. **Polecenia** dodatek jest dobrym przykładem i jest dołączony do wersji 3.0 lub nowszej, a później, który wyświetla listę dostępnych poleceń i ich pomocy.

**Ponownie uruchom Menedżera i automatycznego zapisywania** automatycznie co dwie minuty zapisują skryptów, aby pomóc w uniknięciu utraty wykonanej pracy w przypadku awarii lub nieoczekiwane ponowne uruchomienie.

**Większość listy ostatnio używanych** jest teraz częścią menu Otwórz plik, aby ułatwić uzyskać dostęp do plików, o których najczęściej używane.

**Scalone okienku konsoli**. W poprzednich wersjach środowiska ISE wystąpiły oddzielne polecenie z danymi wyjściowymi okienka. Są teraz połączone w jeden czy więcej bezpośrednio naśladuje zostanie wyświetlony w konsoli programu Windows PowerShell.

**Przełączniki wiersza polecenia**. Kilka nowych przełączników wiersza polecenia umożliwiają większą kontrolę nad sposobem działania środowiska ISE. -NoProfile uruchamia środowiska ISE bez konieczności uruchamiania skryptu profilu. -Help otwiera okno pomocy przy użyciu środowiska ISE. -mta uruchamia środowiska ISE w "trybie wielowątkowej". Wartość domyślna to apartamentem.

**Nowe funkcje edytora** ułatwiają tworzenie i odczytywanie kodu:

- **Kolorowanie składni XML**. Edytora środowiska ISE teraz kolorów składni XML w taki sam sposób, zgodnie z jego kolory składni kodu programu Windows PowerShell.

- **Parowanie nawiasów klamrowych**. W środowisku PowerShell ISE ISEWindows wyróżnia parowanych nawiasów klamrowych ułatwiające upewnij się, że liczba zamykających nawiasów klamrowych, aby dopasować swoje otwieranie tych. Użyj klawiszy CTRL -\[ zlokalizować zamykającego nawiasu klamrowego, odpowiadającego nawiasu otwierającego, na którym znajduje się kursor.

- **Wyświetlanie konspektu**. Możesz zwijać i rozwijać sekcji kodu, kliknij przycisk plus lub minus znaki na lewym marginesie. Dzięki temu można łatwiej znaleźć kod, który potrzebujesz długo skryptu.

- **Przeciąganie i upuszczanie edycji tekstu**. Można wybrać blok tekstu i przeciągnij go do innej lokalizacji, aby go przenieść. Jeśli przytrzymując klawisz Ctrl podczas przeciągania zaznaczonego tekstu, który kopiujesz zamiast przenosić.

- **Analizowanie błędów**. Program Windows PowerShell sprawdza, czy skrypt podczas wpisywania. Jeśli wykryje błąd, pokazuje czerwona fala w kodzie powodujący problemy. Po umieszczeniu wskazany błąd etykietka narzędzia pokazuje problem, który został znaleziony.

- **Powiększenie**. Można powiększyć się w swoim tekście, aby ułatwić odczytu lub pomniejszyć, aby zobaczyć pełny obraz, używając suwaka w prawym dolnym rogu okna środowiska ISE.

- **Kopiuj tekst sformatowany i Wklej**. Podczas kopiowania z środowiska ISE do Schowka, czcionki, rozmiaru i informacje o kolorze zaznaczonego tekstu jest dołączony.

- **Zaznaczenie blokowe**. Można wybrać fragment tekstu w kształcie bloku, przytrzymując naciśnięty klawisz ALT podczas zaznaczania tekstu w okienku skryptów przy użyciu myszy lub naciskając **Alt + Shift + Strzałka**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Dodane w programie PowerShell 2.0 (system Windows Server 2008 R2, Windows 7)

Środowiska ISE został wprowadzony przy użyciu programu PowerShell w wersji 2.0.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Wymagania dotyczące uruchamiania środowiska Windows PowerShell ISE

Środowiska ISE jest dostępne na każdym komputerze Windows, która może uruchomić programu Windows PowerShell w wersji 2.0 lub nowszej. Każda wersja programu Windows i Windows Server zawiera wersję środowiska Windows PowerShell ISE, ale można uaktualnić do najnowszy dostępny, instalując program Windows Management Framework (WMF). Zobacz [WMF](/powershell/wmf) dokumentacji, aby uzyskać więcej informacji.

> [!NOTE]
> Windows PowerShell ISE wymagają graficznego interfejsu użytkownika, dlatego nie można uruchomić go w opcji Server Core systemu Windows Server.

## <a name="see-also"></a>Zobacz też

[Cel modelu obiektów skryptowych środowiska windows power shell ise](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
