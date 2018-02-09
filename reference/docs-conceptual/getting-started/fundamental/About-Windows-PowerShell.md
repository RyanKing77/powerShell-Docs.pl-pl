---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Informacje o programie Windows PowerShell
ms.assetid: 979654ae-7994-47f8-be43-d79e7a140143
ms.openlocfilehash: 5e6d1bb4d8915ba3c83ba0020b959e444b5211cd
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2018
---
# <a name="about-windows-powershell"></a>Informacje o programie Windows PowerShell
Środowisko Windows PowerShell zaprojektowano w celu poprawy środowiska wiersza polecenia i skryptów, eliminując problemy, długotrwałe i dodać nowe funkcje.

## <a name="discoverability"></a>Odnajdowanie
Programu Windows PowerShell ułatwia odnajdywanie jego funkcje. Na przykład aby uzyskać listę poleceń cmdlet, które umożliwia wyświetlanie i modyfikowanie usług systemu Windows, wpisz:

```
Get-Command *-Service
```

Po odnalezieniu, które polecenia cmdlet wykonuje zadanie, możesz dowiedzieć się więcej polecenia cmdlet za pomocą polecenia cmdlet Get-Help. Na przykład aby wyświetlić Pomoc dotyczącą polecenia cmdlet Get-Service, wpisz:

```
Get-Help Get-Service
```
Większość poleceń cmdlet Emituj obiektów, które można wykonywać na nich operacji i następnie renderowane w tekst do wyświetlenia. Aby w pełni zrozumieć dane wyjściowe tego polecenia cmdlet, należy przekazać dane wyjściowe do polecenia cmdlet Get-elementu członkowskiego. Na przykład następujące polecenie wyświetla informacje o członkami dane wyjściowe obiektu przez polecenie cmdlet Get-Service.

```
Get-Service | Get-Member
```

## <a name="consistency"></a>Consistency
Systemy zarządzania mogą być złożonych pozwala i narzędzi, które mają spójny interfejs pomoc do kontrolowania dostępu do właściwych złożoności. Niestety narzędzia wiersza polecenia ani obiektów COM skryptowych być znane w celu zachowania ich spójności.

Spójność programu Windows PowerShell jest jednym z jego głównej zasobów. Na przykład jeśli zostanie przedstawiony sposób należy użyć polecenia cmdlet obiektu sortowania, umożliwia wiedzy posortować dane wyjściowe każdego polecenia cmdlet. Nie masz Dowiedz się różne procedury sortowania każde polecenie cmdlet.

Ponadto polecenia cmdlet programiści nie muszą projektowanie funkcji sortowania dla ich polecenia cmdlet. Środowisko Windows PowerShell daje im platforma, która udostępnia podstawowe funkcje i wymusza, aby były spójne wiele aspektów interfejsu. Platformę eliminuje niektórych opcji, które zwykle pozostało do projektanta, ale w zamian ułatwia programowanie szybki i łatwy w użyciu poleceń cmdlet znacznie prostsze.

## <a name="interactive-and-scripting-environments"></a>Interakcyjne i skryptów środowiska
Program Windows PowerShell jest połączonym środowiskiem interakcyjne i skryptów, która umożliwia dostęp do obiektów COM i narzędzia wiersza polecenia, a także pozwala na użycie zasilania programu .NET Framework klasy biblioteki (FCL).

To środowisko poprawia po wierszu polecenia systemu Windows, interaktywne środowisko z wielu narzędzi wiersza polecenia. Zapewnia on również ulepszenia skryptów Windows Script Host (WSH), które pozwalają używać wielu narzędzi wiersza polecenia i obiekty automatyzacji COM, ale nie zapewniają interaktywnym środowisku.

Dzięki połączeniu dostęp do wszystkich tych funkcji, programu Windows PowerShell rozszerza możliwości użytkownika interaktywnego i zapisywania skryptu i umożliwia łatwiejsze w zarządzaniu Administracja systemu.

## <a name="object-orientation"></a>Orientacja obiektu
Chociaż interakcję z programu Windows PowerShell, wpisując tekst polecenia środowiska Windows PowerShell jest oparta na obiektów, nie tekstu. Dane wyjściowe polecenia jest obiektem. Obiekt danych wyjściowych do innego polecenia można wysłać jako dane wejściowe. W związku z tym środowiska Windows PowerShell udostępnia interfejs znanych osób wystąpił z innych powłok podczas wprowadzania nowych i zaawansowanego modelu wiersza polecenia. Go, będąca pojęciem szerszym przesyłania danych między polecenia umożliwiając wysyłanie obiektów zamiast tekstu.

## <a name="easy-transition-to-scripting"></a>Łatwe przejście do wykonywania skryptów
Ułatwia środowiska Windows PowerShell ułatwiają przejścia z wpisanie polecenia interaktywnie do tworzenia i uruchamiania skryptów. Możesz wpisać poleceń w wierszu polecenia programu Windows PowerShell do odnajdywania poleceń, które wykonania zadania. Następnie można zapisać tych poleceń, zapisu lub historię przed skopiowaniem ich do pliku do użycia jako skrypt.

