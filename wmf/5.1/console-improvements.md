---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
title: Ulepszenia konsoli w WMF 5.1
ms.openlocfilehash: b0859191ea310c9b73fe9f255d7f256a1cc1af1f
ms.sourcegitcommit: fee03bb9802222078c8d5f6c8efb0698024406ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2017
---
# <a name="console-improvements-in-wmf-51"></a>Ulepszenia konsoli w WMF 5.1#

## <a name="powershell-console-improvements"></a>Ulepszenia konsoli programu PowerShell

Następujące zmiany zostały wprowadzone do powershell.exe w wersji 5.1 WMF celu usprawnienie obsługi konsoli:

###<a name="vt100-support"></a>Obsługa VT100

Windows 10 dodano obsługę [sekwencji unikowych VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell zignoruje sekwencje specjalne formatowanie niektórych VT100 podczas obliczania szerokości tabel.

Programu PowerShell również został dodany nowy interfejs API, który może być używany w formatowaniu kod, aby określić, czy VT100 jest obsługiwana. Przykład:

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
W tym miejscu jest kompletna [przykład](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) można wyróżnić zgodny z wybierz ciągu.
Zapisz przykładu w pliku o nazwie `MatchInfo.format.ps1xml`, aby użyć go w profilu lub w innym miejscu, i uruchom `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Należy pamiętać, że sekwencje unikowe VT100 są obsługiwane tylko począwszy od aktualizacji systemu Windows 10 Anniversary; nie są obsługiwane w starszych systemach.   

### <a name="vi-mode-support-in-psreadline"></a>Pomoc techniczna trybu VI w PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) dodaje obsługę trybu vi. Aby użyć trybu vi, uruchom `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Stdin przekierowane przy użyciu interaktywnych danych wejściowych 

We wcześniejszych wersjach uruchamiania programu PowerShell z `powershell -File -` była wymagana, gdy stdin zostało przekierowane i chcesz interaktywnie wprowadź poleceń.

Z 5.1 WMF, tym twardym dowiedzieć się, że opcja nie jest już konieczne. Można uruchomić programu PowerShell bez żadnych opcji, np. `powershell`.

Należy pamiętać, że PSReadline nie obsługuje obecnie przekierowanie stdin i wbudowane proces edycji wiersza polecenia z przekierowanego stdin jest bardzo ograniczona, na przykład klawisze strzałek nie działają. Przyszłym wydaniu PSReadline powinno rozwiązać ten problem.   

