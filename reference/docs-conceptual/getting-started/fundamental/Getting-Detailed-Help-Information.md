---
ms.date: 08/27/2018
keywords: polecenia cmdlet programu PowerShell
title: Uzyskiwanie szczegółowych informacji pomocy
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 88f0357b935a7c75df07d667e3f2f2d0e493f89d
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134038"
---
# <a name="getting-detailed-help-information"></a>Uzyskiwanie szczegółowych informacji pomocy

Program PowerShell zawiera szczegółowe artykuły pomocy pojęcia programu PowerShell i języka programu PowerShell. Dostępne są także artykuły pomocy dla każdego polecenia cmdlet i dostawcy i wiele funkcji i skryptów.

Można wyświetlić tych artykułów pomocy, w wierszu polecenia lub Wyświetl ostatnio zaktualizowane wersje tych artykułów w [PowerShell](/powershell/scripting/powershell-scripting) dokumentacji online.

## <a name="getting-help-for-cmdlets"></a>Uzyskiwanie pomocy dla poleceń cmdlet

Aby uzyskać pomoc dotyczącą poleceń cmdlet programu PowerShell, należy użyć [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) polecenia cmdlet. Na przykład, aby uzyskać pomoc dotyczącą `Get-ChildItem` polecenia cmdlet, wpisz:

```powershell
Get-Help Get-ChildItem
```

lub

```powershell
Get-ChildItem -?
```

Można nawet uzyskać pomoc dotyczącą polecenia cmdlet Get-Help. Przykład:

```powershell
Get-Help Get-Help
```

Aby uzyskać listę polecenia cmdlet artykułów pomocy, w sesji, wpisz:

```powershell
Get-Help -Category Cmdlet
```

Aby wyświetlić jedną stronę części każdego artykułu pomocy w czasie, użyj `help` funkcji lub jego alias `man`.
Na przykład, aby wyświetlić Pomoc dla `Get-ChildItem` polecenia cmdlet, typ

```powershell
man Get-ChildItem
```

lub

```powershell
help Get-ChildItem
```

Aby wyświetlić szczegółowe informacje, należy użyć **szczegółowe** parametru `Get-Help` polecenia cmdlet. Na przykład, aby uzyskać szczegółowe informacje na `Get-ChildItem` polecenia cmdlet, wpisz:

```powershell
Get-Help Get-ChildItem -Detailed
```

Aby wyświetlić całą zawartość w artykule pomocy, użyj **pełne** parametru `Get-Help` polecenia cmdlet. Na przykład, aby wyświetlić całą zawartość w artykule pomocy, aby `Get-ChildItem` polecenia cmdlet, wpisz:

```powershell
Get-Help Get-ChildItem -Full
```

Aby uzyskać szczegółową pomoc dotyczącą parametry polecenia cmdlet, użyj **parametru** parametru `Get-Help` polecenia cmdlet. Na przykład, aby uzyskać szczegółowe pomocy dla wszystkich parametrów `Get-ChildItem` polecenia cmdlet, wpisz:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Aby wyświetlić tylko w przykładach w artykule pomocy, użyj **przykłady** parametru `Get-Help`.
Na przykład, aby wyświetlić tylko w przykładach w artykule pomocy, aby `Get-ChildItem `polecenia cmdlet, wpisz:

```powershell
Get-Help Get-ChildItem -Examples
```

Aby uzyskać informacji na temat sposobu pisania artykułów pomocy dla poleceń cmdlet, które piszesz, zobacz [sposobu pisania pomoc dotyczącą polecenia Cmdlet](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).

## <a name="getting-conceptual-help"></a>Uzyskiwanie pomocy koncepcyjne

`Get-Help` Polecenie cmdlet wyświetla również informacji na temat artykułów koncepcyjnych w programie PowerShell, w tym artykuły na temat języka programu PowerShell. Koncepcyjny pomocy artykuły zaczynają się od prefiksu "about_", takich jak about_line_editing. (Nazwa artykuł koncepcyjny należy podać w języku angielskim nawet w przypadku wersji innej niż angielska programu PowerShell.)

Aby wyświetlić listę artykułów koncepcyjnych, wpisz:

```powershell
Get-Help about_*
```

Aby wyświetlić określonego artykułu pomocy, wpisz nazwę artykułu, na przykład:

```powershell
Get-Help about_command_syntax
```

Parametry `Get-Help`, takich jak **szczegółowe**, **parametru**, i **przykłady**, nie mają wpływu na wyświetlanie artykuły koncepcyjne pomocy.

## <a name="getting-help-about-providers"></a>Uzyskiwanie pomocy na temat dostawców

`Get-Help` Polecenie cmdlet wyświetla informacje dotyczące dostawcy programu PowerShell. Aby uzyskać pomoc dotyczącą dostawcę, należy wpisać `Get-Help` następuje nazwa dostawcy. Na przykład aby uzyskać pomoc dotyczącą dostawcy rejestru, wpisz:

```powershell
Get-Help registry
```

Aby uzyskać listę wszystkich dostawca artykułów pomocy w sesji, wpisz

```powershell
Get-Help -Category provider
```

Parametry `Get-Help`, takich jak **szczegółowe**, **parametru**, i **przykłady**, nie mają wpływu na wyświetlanie dostawca artykułów pomocy.

## <a name="getting-help-about-scripts-and-functions"></a>Uzyskiwanie pomocy na temat skryptów i funkcji

Wiele skryptów i funkcji w programie PowerShell ma artykułów pomocy. Użyj `Get-Help` polecenia cmdlet, aby wyświetlić artykułów pomocy, skryptach i funkcjach.

Aby wyświetlić Pomoc dla funkcji, wpisz `Get-Help` przed nazwą funkcji. Na przykład, aby uzyskać pomoc dotyczącą `Disable-PSRemoting` funkcji, wpisz:

```powershell
Get-Help Disable-PSRemoting
```

Aby wyświetlić Pomoc, aby uzyskać skrypt, wpisz ścieżkę do pliku skryptu. Jeśli skrypt nie jest w ścieżce wymienione w zmiennej środowiskowej Path, musisz podać pełną ścieżkę.

Na przykład, jeśli masz skrypt o nazwie "TestScript.ps1" c:\\katalogu PS testów do wyświetlenia artykułu pomocy, aby skrypt, wpisz:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

Parametry, które są przeznaczone do wyświetlania pracy pomocy polecenia cmdlet dla skryptów i funkcję Pomoc zbyt. Jednak Pomoc dla funkcji i skryptów nie jest wyświetlany po uruchomieniu `Get-Help *`.

Informacje na temat pisania artykułów pomocy dla funkcji i skryptów zobacz następujące artykuły:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Uzyskiwanie pomocy online

Przeglądanie artykułów pomocy online jest jednym z najlepszych sposobów uzyskania pomocy. Artykuły w trybie online są łatwiejsze do aktualizacji i zapewnia najbardziej aktualną zawartość.

Aby uzyskać pomoc w trybie online, należy użyć **Online** parametru `Get-Help` polecenia cmdlet. Wszystkich artykułów pomocy, które przy użyciu programu PowerShell, włącznie z dostawcą pomocy i pojęciach (artykułów pomocy informacje) są dostępne w trybie online w [PowerShell](/powershell/scripting/powershell-scripting) dokumentacji.

> [!NOTE]
> Nie można użyć **Online** parametrem koncepcyjnej (about_ *) lub dostawca artykułów pomocy.
> Pomoc online jest opcjonalne, więc nie działa dla każdego polecenia cmdlet, funkcji lub skryptu.

Na przykład, aby uzyskać wersję online artykułu pomocy na temat `Get-ChildItem` polecenia cmdlet, wpisz:

```powershell
Get-Help Get-ChildItem -Online
```

Program PowerShell spowoduje otwarcie tego artykułu w domyślnej przeglądarce. Pomoc online jest przeznaczony do artykułu pomocy, można również wyświetlić adres URL artykułu pomocy. Adres URL pojawia się w sekcji linki powiązane artykułu pomocy.

Na przykład aby zobaczyć adres URL dla wersji online polecenia cmdlet Add-Computer, wpisz:

```powershell
Get-Help Add-Computer
```

Poniżej przedstawiono pierwszy wiersz w sekcji linki powiązane tego artykułu.

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

Aby uzyskać informacje o tym, jak zapewnienie wsparcia online dla artykułów pomocy, zobacz [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Zobacz też

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
