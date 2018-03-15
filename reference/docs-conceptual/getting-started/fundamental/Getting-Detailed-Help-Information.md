---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Uzyskiwanie szczegółowych informacji pomocy"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 67e02b503acf4d683c5a190d6642dea384bbfad2
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="getting-detailed-help-information"></a>Uzyskiwanie szczegółowych informacji pomocy
Program Windows PowerShell zawiera szczegółowe tematy pomocy, które opisano pojęcia dotyczące środowiska Windows PowerShell i język środowiska Windows PowerShell. Istnieją także tematy pomocy dla każdego polecenia cmdlet i dostawcy i tematy pomocy dla wielu funkcji i skryptów.

Możesz wyświetlić te tematy pomocy w wierszu polecenia lub wyświetlić najnowsze wersje tych tematów w Microsoft TechNet Library. Wiele programów obsługujące środowisko Windows PowerShell, takie jak Windows PowerShell zintegrowane skryptów środowisko, oferują dodatkowe funkcje pomocy, takich jak Pomoc kontekstowa i skompilowany plik pomocy (.chm).

## <a name="getting-help-for-cmdlets"></a>Uzyskiwanie pomocy dotyczącej poleceń cmdlet
Aby uzyskać pomoc dotyczącą poleceń cmdlet programu Windows PowerShell, użyj [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) polecenia cmdlet. Na przykład, aby uzyskać pomoc dotyczącą [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) polecenia cmdlet, wpisz:

```
get-help get-childitem
```

lub

```
get-childitem -?
```

Można nawet uzyskać pomoc dotyczącą polecenia cmdlet Get-Help. Przykład:

```
get-help get-help
```

Aby uzyskać listę wszystkich tematów pomocy polecenia cmdlet w sesji, wpisz:

```
get-help -category cmdlet
```

Aby wyświetlić jedną stronę każdego tematu pomocy w czasie, należy użyć **pomocy** funkcji lub aliasem **man**. Na przykład aby wyświetlić Pomoc dla polecenia cmdlet Get-ChildItem, wpisz

```
man get-childitem
```

lub

```
help get-childitem
```

Aby wyświetlić szczegółowe informacje na temat polecenia cmdlet, funkcji lub skryptu, między innymi opisy parametrów i przykłady ich użycia, należy użyć *szczegółowy* parametru polecenia cmdlet Get-Help. Na przykład aby uzyskać szczegółowe informacje na temat polecenia cmdlet Get-ChildItem, wpisz:

```
get-help get-childitem -detailed
```

Aby wyświetlić całą zawartość w temacie pomocy, użyj *pełne* parametru polecenia cmdlet Get-Help. Na przykład aby wyświetlić całą zawartość w temacie pomocy dla polecenia cmdlet Get-ChildItem, wpisz:

```
get-help get-childitem -full
```

Aby uzyskać szczegółową pomoc dotyczącą parametry polecenia cmdlet, użyj *parametru* parametru polecenia cmdlet Get-Help. Na przykład aby uzyskać szczegółowe pomocy dla wszystkich parametrów polecenia cmdlet Get-ChildItem, wpisz:

```
get-help get-childitem -parameter *
```

Aby wyświetlić tylko w przykładach w temacie pomocy, użyj *przykład* parametr Get-Help. Na przykład aby wyświetlić tylko w przykładach w temacie pomocy dla polecenia cmdlet Get-ChildItem, wpisz:

```
get-help get-childitem -examples
```

Aby uzyskać informacje dotyczące pisania tematy pomocy dla poleceń cmdlet, który można zapisać, zobacz [jak zapisać pomoc dotyczącą polecenia Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) w bibliotece MSDN.

## <a name="getting-conceptual-help"></a>Uzyskiwanie pomocy koncepcyjne
Polecenie cmdlet Get-Help Wyświetla również informacje o tematy dotyczące pojęć w programie Windows PowerShell, w tym tematy dotyczące języków środowiska Windows PowerShell. Tematy dotyczące pojęć pomocy zaczynać się prefiksem "about_", na przykład about_line_editing. (Nazwa bieżącego tematu należy podać w języku angielskim nawet w przypadku innych niż angielska wersji środowiska Windows PowerShell.)

Aby wyświetlić listę pojęć, wpisz:

```
get-help about_*
```

Aby wyświetlić określonego tematu pomocy, wpisz nazwę tematu, na przykład:

```
get-help about_command_syntax
```

Parametr Get-Help, takich jak *szczegółowy*, *parametru*, i *przykłady*, nie mają wpływu na wyświetlanie koncepcyjne tematy Pomocy.

## <a name="getting-help-about-providers"></a>Uzyskiwanie pomocy dotyczące dostawców
Polecenie cmdlet Get-Help Wyświetla informacje dotyczące dostawcy programu Windows PowerShell. Aby uzyskać pomoc dla dostawcy, wpisz "Get-Help", a po niej nazwę dostawcy. Na przykład aby uzyskać pomoc dotyczącą dostawcy rejestru, wpisz:

```
get-help registry
```

Aby uzyskać listę wszystkich tematów pomocy dostawcy w sesji, wpisz

```
get-help -category provider
```

Parametr Get-Help, takich jak *szczegółowy*, *parametru*, i *przykłady*, nie mają wpływu na wyświetlanie tematy pomocy dostawcy.

## <a name="getting-help-about-scripts-and-functions"></a>Uzyskiwanie pomocy o skryptach i funkcjach
Wiele skryptów i funkcji w programie Windows PowerShell są dostępne tematy Pomocy. Aby wyświetlić tematy pomocy dla skryptów i funkcji, należy użyć polecenia cmdlet Get-Help.

Aby wyświetlić Pomoc dla funkcji, wpisz "get-help", a po niej nazwę funkcji. Na przykład aby uzyskać pomoc dotyczącą funkcja Disable-PSRemoting, wpisz:

```
get-help disable-psremoting
```

Aby wyświetlić Pomoc, aby uzyskać skrypt, wpisz w pełni kwalifikowana ścieżka do pliku skryptu. Jeśli skrypt jest w ścieżce, która znajduje się w zmiennej środowiskowej Path, ścieżka polecenia można pominąć.

Na przykład, jeśli masz skryptu o nazwie "TestScript.ps1" w Twojej C:\\katalogu PS testu, można wyświetlić tematu Pomocy dotyczącego skrypt, wpisz:

```
get-help c:\ps-test\TestScript.ps1
```

Pomoc parametrów, które zostały zaprojektowane do wyświetlania polecenia cmdlet, takich jak *szczegółowy*, *pełne*, *przykłady*, i *parametru*, nadają się do skrypt pomocy i funkcja Pomoc zbyt. Jednak po wyświetleniu wszystkich pomocy, wpisując "get-help \*" Pomoc dla funkcji i skryptów nie są wyświetlane.

Informacje na temat pisania tematy pomocy dla funkcji i skryptów, zobacz [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), i [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).

## <a name="getting-help-online"></a>Uzyskiwanie pomocy Online
Po nawiązaniu połączenia z Internetem, jednym z najlepszych sposobów uzyskania pomocy jest aby wyświetlić tematy Pomocy online. Ponieważ tematy online są łatwe do aktualizacji, są one może zapewnić aktualna zawartość.

Aby uzyskać pomoc w trybie online, spróbuj *Online* parametru polecenia cmdlet Get-Help. *Online* parametru działania polecenia cmdlet Get-Help tylko dla polecenia cmdlet pomocy, pomocy funkcji i skryptów pomocy. Nie można użyć *Online* parametr o pojęciach (informacje) tematy, albo tematy pomocy dostawcy. Ponadto ponieważ ta funkcja jest opcjonalny, go nie działa w przypadku każdego polecenia cmdlet, funkcji lub tematu Pomocy skryptu.

Jednak wszystkie tematy pomocy pochodzące z programu Windows PowerShell, w tym dostawcy pomocy i koncepcyjne (tematy Pomocy informacje) są dostępne w trybie online w [programu Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) sekcji Microsoft TechNet Library.

Aby użyć *Online* parametru polecenia cmdlet Get-Help, użyj następującego formatu polecenia.

```
get-help <command-name> -online
```

Na przykład aby uzyskać wersji online tematu Pomocy dotyczących polecenia cmdlet Get-ChildItem, wpisz:

```
get-help get-childitem -online
```

Jeśli wersji online tematu Pomocy jest dostępny, zostanie otwarty w domyślnej przeglądarce.

Pomoc online jest obsługiwana dla tematu pomocy, można również wyświetlić adres internetowy (URL) tematu Pomocy. Adres internetowy pojawia się w sekcji łączy pokrewnych tematu Pomocy.

Na przykład aby wyświetlić adres URL dla wersji online polecenia cmdlet Add-Computer, wpisz:

```
get-help add-computer
```

Pierwszy wiersz w sekcji łączy pokrewnych tego tematu przedstawiono poniżej.

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

Aby uzyskać informacje dotyczące zapewnienie pomocy technicznej online tematy pomocy, zobacz [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)i zobacz [jak zapisać pomoc dotyczącą polecenia Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) w bibliotece MSDN.

## <a name="see-also"></a>Zobacz też
- [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)

