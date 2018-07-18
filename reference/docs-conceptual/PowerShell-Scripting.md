---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie skryptów programu PowerShell
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094055"
---
# <a name="powershell"></a>PowerShell

Oparta na programie .NET Framework, programu PowerShell jest, powłoka wiersza polecenia opartego na zadaniach oraz językiem skryptowym; jest on zaprojektowany specjalnie dla administratorów systemów i użytkownicy zaawansowani szybko zautomatyzować administracji wielu systemów operacyjnych (Linux, macOS, Unix i Windows) i procesów związanych z aplikacjami, które są uruchamiane w tych systemach operacyjnych.

## <a name="powershell-is-open-source"></a>Program PowerShell jest "open source"

Kod źródłowy podstawowej programu PowerShell są dostępne w usłudze GitHub i otwarty, aby kod wniesiony przez społeczność.
Zobacz [źródła programu PowerShell w usłudze GitHub](https://github.com/powershell/powershell).

Można uruchomić przy użyciu usługi bits na [pobieranie programu PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Lub, z krótkiego przewodnika po [wprowadzenie](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>Cele projektu programu PowerShell
Program PowerShell jest przeznaczony do dbać o środowisko wiersza polecenia i skryptów, eliminując problemy długotrwałych i dodając nowe funkcje.

### <a name="discoverability"></a>Odnajdowanie
PowerShell ułatwia odnajdywanie jego funkcji. Na przykład aby uzyskać listę poleceń cmdlet, które umożliwia wyświetlanie i zmienianie usług Windows, wpisz:

```powershell
Get-Command *-Service
```

Po odkryciu, które polecenie cmdlet w ramach zadania, możesz dowiedzieć się więcej informacji na temat polecenia cmdlet przy użyciu `Get-Help` polecenia cmdlet.
Na przykład, aby wyświetlić Pomoc na temat `Get-Service` polecenia cmdlet, wpisz:

```powershell
Get-Help Get-Service
```
Większość poleceń cmdlet emitować obiekty, które mogą być zmieniane i następnie renderowany na tekst do wyświetlenia.
Aby w pełni zrozumieć dane wyjściowe tego polecenia cmdlet, należy przekazać dane wyjściowe do `Get-Member` polecenia cmdlet.
Na przykład następujące polecenie wyświetla informacje o członkach dane wyjściowe obiektu przez `Get-Service` polecenia cmdlet.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency
Systemy zarządzania mogą być złożone pozwala i narzędzia, które mają spójny interfejs ułatwiają kontrolowanie zamaskować złożoność.
Niestety narzędzia wiersza polecenia ani za pomocą skryptów obiektów COM nie być znane w celu zachowania ich spójności.

Spójność programu PowerShell jest jednym z jego głównej zasoby.
Na przykład, jeśli dowiesz się, jak używać `Sort-Object` polecenia cmdlet, można użyć tę wiedzę, aby posortować dane wyjściowe każdego polecenia cmdlet.
Nie masz się różne procedury sortowania każdego polecenia cmdlet.

Ponadto deweloperzy polecenie cmdlet nie trzeba projektować funkcje sortowania dla ich poleceń cmdlet.
Program PowerShell nadaje im strukturę, która udostępnia podstawowe funkcje i wymusza, aby był spójny o wiele aspektów interfejsu.
Struktura eliminuje niektórych opcji, które zazwyczaj są pozostawiane do deweloperów, ale w zamian ułatwia rozwój niezawodne i łatwe w użyciu poleceń cmdlet znacznie prostsza.

### <a name="interactive-and-scripting-environments"></a>Środowiska interaktywnego i skryptów
PowerShell jest połączonym środowiskiem interakcyjne i skryptów, zapewnia dostęp do obiektów COM i narzędzi wiersza polecenia, a także umożliwia korzystanie z możliwości platformy .NET Framework klasy biblioteki (FCL).

To środowisko zwiększa na Windows wiersza polecenia, który zapewnia środowisko interaktywne z wielu narzędzi wiersza polecenia.
Zapewnia on także ulepszenia skryptów Windows Script Host (WSH), które pozwalają na korzystanie z wielu narzędzi wiersza polecenia i obiektów automatyzacji COM, ale nie zapewnia interaktywne środowisko.

Łącząc dostęp do wszystkich tych funkcji, programu PowerShell rozszerza możliwości użytkownik interakcyjny i autor skryptu i sprawia, że administracja systemu jest łatwiejsze w zarządzaniu.

### <a name="object-orientation"></a>Orientacja obiektu
Mimo że możesz korzystać przy użyciu programu PowerShell, wpisując tekst polecenia programu PowerShell jest oparty na obiektów, nie tekstu.
Dane wyjściowe polecenia jest obiektem.
Obiekt danych wyjściowych do innego polecenia można wysłać jako dane wejściowe.
W rezultacie PowerShell udostępnia znajomy interfejs do osób technicznego z systemem innymi powłok, podczas wprowadzania nowych i zaawansowanych paradygmat wiersza polecenia.
Rozszerza pojęcie przesyłania danych między poleceniami, umożliwiając wysyłać obiekty zamiast tekstu.

### <a name="easy-transition-to-scripting"></a>Łatwe przejście do skryptów
Umożliwia PowerShell ułatwiają przejścia do wpisywania poleceń interaktywnie do tworzenia i uruchamiania skryptów.
Polecenia można wpisać w wierszu polecenia programu PowerShell, aby odnaleźć poleceń, które wykonują zadania.
Następnie można zapisać tych poleceń w transkrypcji lub historię przed skopiowaniem ich do pliku do użycia jako skrypt.
