---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Środowisko Windows PowerShell Integrated skryptów środowiska ISE"
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 66f36371cbb8ad8523aa1e1e3cd791cc692194c9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Integrated Scripting Environment (ISE)
Windows PowerShell Integrated Scripting Environment (ISE) jest jednym z dwóch hostów dla aparatu programu Windows PowerShell i języka. Z tym można zapisać, uruchamiania i przetestować skrypty w sposób, w którym nie są dostępne w konsoli programu Windows PowerShell. ISE dodaje kolorowanie składni, uzupełniania po naciśnięciu tabulatora, IntelliSense, debugowania visual i Pomoc kontekstowa.

ISE umożliwia uruchamianie poleceń w okienku konsoli, ale obsługuje ona również okienka, które umożliwiają wyświetlanie kodu źródłowego skrypt i innych narzędzi, które można podłączyć do ISE. W tym samym czasie, który jest szczególnie przydatne podczas debugowania skryptu, który używa funkcji zdefiniowanych w inne skrypty lub moduły można nawet zwolnić wielu skryptów systemu windows.

## <a name="whats-new"></a>Co nowego
Poniżej przedstawiono niektóre funkcje, które zostały dodane do ISE w najnowszych wersjach programu PowerShell.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Dodane w programie PowerShell 3.0 (Windows Server 2012, Windows 8)
**IntelliSense** automatycznie wykonuje poleceniach przez wyświetlanie menu pasującego poleceń cmdlet, parametry, wartości parametrów, plików lub folderów podczas pisania.

**Wstawki kodu programu** są krótkich fragmentów kodu łatwo wstawiany do skryptów z zapisu. Kolekcja przydatne wstawki znajduje się w polu i bardziej można za pomocą **nowy fragment** polecenia cmdlet.

**Dodatkowe narzędzia** dodaje funkcje do ISE mogą być tworzone przez pisania kodu, który współdziała z [Windows PowerShell ISE skryptów Model obiektów](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md). Narzędzia te można wyświetlić formantów w okienku z kartami lub działa w sposób niewidoczny w tle. **Polecenia** dodatek jest dobrym przykładem i znajduje się w wersji 3.0 lub nowszej, a później, który wyświetla listę dostępnych poleceń i ich pomocy.

**Ponownie uruchom Menedżera i automatycznego zapisywania** automatycznie co dwie minuty zapisać skrypty, aby pomóc w uniknięciu utraty danych, w przypadku awarii lub nieoczekiwane ponowne uruchomienie.

**Większość listy ostatnio używanych** jest obecnie częścią menu Otwórz plik, aby ułatwić uzyskanie dostępu do plików najczęściej używane.

**Scalone okienku konsoli**. W poprzednich wersjach programu ISE wystąpiły oddzielne polecenie z danymi wyjściowymi okienka. One zostały połączone w jeden czy więcej bezpośrednio naśladuje zostanie wyświetlony w konsoli programu Windows Powershell.

**Przełączniki wiersza polecenia**. Kilka nowych przełączników wiersza polecenia zapewniają większą kontrolę nad sposobem działania ISE. -NoProfile uruchamia ISE bez uruchamiania skryptów profilu. -Help otwiera okno Pomocy z ISE. -mta uruchamia ISE w "trybie wielowątkowej". Wartość domyślna to jednowątkowy.

**Nowe funkcje edytora** ułatwiają tworzenie i odczytywanie kodu:

- **Kolorowanie składni XML**. Edytor ISE teraz kolory składni XML w taki sam sposób jak jego kolory Składnia kodu programu Windows PowerShell.

- **Dopasowywanie nawiasu klamrowego**. ISEWindows PowerShell ISE wyróżnia pasujących nawiasów klamrowych pomaga zapewnić prawo liczba klamrowe nawiasy zamykające do zgodne z otwierania tych. Użyj klawiszy CTRL -\[ zlokalizować zamykający nawias klamrowy odpowiadającego nawiasu otwierającego, na którym znajduje się kursor.

- **Wyświetlanie konspektu**. Należy Zwiń lub rozwiń sekcje kodu, kliknij przycisk plus lub minus loguje lewy margines. Dzięki temu można łatwiej znaleźć kod, którego szukasz w skrypcie długi.

- **Przeciągnij i upuść edycji tekstu**. Można wybrać bloku tekstu i przeciągnij go do innej lokalizacji, aby go przenieść. Jeśli przytrzymując klawisz Ctrl podczas przeciągania zaznaczony tekst kopiowany zamiast przenieść.

- **Przeanalizować wyświetlania błędów**. Środowisko Windows PowerShell sprawdza, czy skrypt podczas pisania. Jeśli wykryje błąd zawiera czerwona falista kodem ataku. Po ustawieniu kursora wskazany błąd etykietka narzędzia zawiera problem, który został znaleziony.

- **Powiększenie**. Możesz powiększać tekst w taki sposób, aby ułatwić do odczytu lub pomniejszyć aby zobaczyć pełny obraz za pomocą suwaka w prawym dolnym rogu okna ISE.

- **Sformatowanego tekstu kopiowania i wklejania**. Podczas kopiowania z ISE Schowka czcionki, rozmiaru i koloru informacji zaznaczonego tekstu jest dołączony.

- **Blokowanie wybór**. Można wybrać fragment tekstu w kształcie bloku przez trzymając wciśnięty klawisz ALT Zaznaczanie tekstu w okienku skryptów myszą lub naciśnięcie **Alt + Shift + Strzałka w**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Dodane w programie PowerShell 2.0 (Windows Server 2008 R2, Windows 7)
ISE wprowadzono w systemie programu PowerShell w wersji 2.0.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Wymagania dotyczące systemu Windows PowerShell ISE
ISE jest dostępna na każdym komputerze z systemem Windows można uruchomić programu Windows PowerShell w wersji 2.0 lub nowszej.
Każda wersja programu Windows i Windows Server zawiera wersję środowiska Windows PowerShell i ISE, ale można uaktualnić do najnowszej dostępnej, instalując oprogramowanie Windows Management Framework.
Uruchomienie tego Wyszukaj, aby znaleźć najnowszej dostępnej wersji: [pobiera](http://www.microsoft.com/en-us/search/DownloadResults.aspx?q=%22windows%20management%20framework%22%20PowerShell&sortby=Relevancy~Descending).
Warto zauważyć, że wszystkie wpisy etykietę "Podgląd" to wersja wstępna kodu nie są kompletne funkcji.

> [!NOTE]
> Windows PowerShell ISE wymaga graficznego interfejsu użytkownika, dlatego nie można uruchomić go w opcji Server Core systemu Windows Server.

## <a name="see-also"></a>Zobacz też
- [Przy użyciu systemu Windows PowerShell zintegrowane środowisko obsługi skryptów](../../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

