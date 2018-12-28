---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie skryptów programu PowerShell
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405204"
---
# <a name="powershell"></a>PowerShell

PowerShell jest powłoką wiersza polecenia opartego na zadaniach i język skryptowy, oparte na platformie .NET.
Program PowerShell ułatwia administratorom systemu i użytkownicy zaawansowani szybko Automatyzuj zarządzanych systemów operacyjnych (Linux, macOS i Windows) oraz procesy.

Polecenia programu PowerShell umożliwiają zarządzanie komputerami z poziomu wiersza polecenia. Dostawcy programu PowerShell umożliwiają dostęp do magazynów danych, takich jak rejestr i magazyn certyfikatów, równie łatwo, jak dostęp do systemu plików. Program PowerShell zawiera analizator składni wyrażeń i pełni rozwinięty język skryptowy.

## <a name="powershell-is-open-source"></a>Program PowerShell jest typu open-source

Kod źródłowy podstawowej programu PowerShell są dostępne w usłudze GitHub i otwarty, aby kod wniesiony przez społeczność.
Zobacz [źródła programu PowerShell w usłudze GitHub](https://github.com/powershell/powershell).

Można uruchomić przy użyciu usługi bits na [pobieranie programu PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Lub, z krótkiego przewodnika po [wprowadzenie](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>Cele projektu programu PowerShell

Program PowerShell jest przeznaczony do dbać o środowisko wiersza polecenia i skryptów, eliminując problemy długotrwałych i dodając nowe funkcje.

### <a name="discoverability"></a>Odnajdowanie

PowerShell ułatwia odnajdywanie jego funkcji. Na przykład aby uzyskać listę poleceń cmdlet, które umożliwia wyświetlanie i zmienianie usług Windows, wpisz:

```powershell
Get-Command *-Service
```

Po odkryciu, które polecenie cmdlet w ramach zadania, możesz dowiedzieć się więcej informacji na temat polecenia cmdlet przy użyciu `Get-Help` polecenia cmdlet. Na przykład, aby wyświetlić Pomoc na temat `Get-Service` polecenia cmdlet, wpisz:

```powershell
Get-Help Get-Service
```

Większość poleceń cmdlet zwracany obiektów, które mogą być zmieniane i następnie renderowany jako tekst do wyświetlenia. Aby w pełni zrozumieć dane wyjściowe polecenia cmdlet, należy przekazać dane wyjściowe do `Get-Member` polecenia cmdlet. Na przykład następujące polecenie wyświetla informacje o członkach dane wyjściowe obiektu przez `Get-Service` polecenia cmdlet.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency

Zarządzanie systemami może być złożonym zadaniem. Narzędzia, które mają spójny interfejs ułatwiają kontrolowanie zamaskować złożoność. Niestety nie są znane w celu zachowania ich spójności za pomocą skryptów obiektów COM i narzędzi wiersza polecenia.

Spójność programu PowerShell jest jednym z jego głównej zasoby. Na przykład, jeśli dowiesz się, jak używać `Sort-Object` polecenia cmdlet, można użyć tę wiedzę, aby posortować dane wyjściowe każdego polecenia cmdlet. Nie masz dowiedzieć się różne procedury sortowania każdego polecenia cmdlet.

Ponadto deweloperzy polecenie cmdlet nie trzeba projektować funkcje sortowania dla ich poleceń cmdlet. Program PowerShell udostępnia framework z podstawowych funkcji, która wymusza spójność. Struktura eliminuje niektórych opcji, które są pozostawiane do deweloperów. Ale w zamian ułatwia rozwój poleceń cmdlet znacznie prostsza.

### <a name="interactive-and-scripting-environments"></a>Środowiska interaktywnego i skryptów

Wiersz polecenia Windows zapewnia interaktywnej powłoki, dostęp do narzędzia wiersza polecenia i skrypty podstawowe. Windows Script Host (WSH) zawiera narzędzia wiersza polecenia za pomocą skryptów i obiektów automatyzacji COM, ale nie zapewnia interaktywnej powłoki.

PowerShell łączy interaktywnej powłoki i skryptów środowiska. PowerShell można uzyskać dostęp do narzędzia wiersza polecenia, obiekty COM i bibliotek klasy .NET. Ta kombinacja funkcji rozszerza możliwości użytkownik interakcyjny, autor skryptu i administratorem systemu.

### <a name="object-orientation"></a>Orientacja obiektu

W obiekcie tekstowym nie jest oparte na programie PowerShell. Dane wyjściowe polecenia jest obiektem. Obiekt danych wyjściowych, za pośrednictwem potoku, możesz wysłać do innego polecenia jako dane wejściowe.

Ten potok zawiera znany interfejs dla osób doświadczenie w pracy z innymi powłoki. Program PowerShell rozszerza tę koncepcję przez wysyłanie obiektów zamiast tekstu.

### <a name="easy-transition-to-scripting"></a>Łatwe przejście do skryptów

Umożliwia odnajdowanie polecenia programu PowerShell ułatwiają przejścia do wpisywania poleceń interaktywnie do tworzenia i uruchamiania skryptów. Zapisy programu PowerShell i historię ułatwiają skopiowanie polecenia do pliku do użycia jako skrypt.
