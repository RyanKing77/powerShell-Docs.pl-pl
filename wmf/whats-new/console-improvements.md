---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Ulepszenia konsoli w programie WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856217"
---
# <a name="console-improvements-in-wmf-51"></a>Ulepszenia konsoli w programie WMF 5.1

## <a name="powershell-console-improvements"></a>Ulepszenia konsoli programu PowerShell

Wprowadzono następujące zmiany do powershell.exe programu WMF 5.1 do udoskonalenia środowiska konsoli:

### <a name="vt100-support"></a>Obsługa VT100

Windows 10 dodano obsługę [sekwencje ucieczki VT100](/windows/console/console-virtual-terminal-sequences).
PowerShell będzie ignorować niektórych sekwencji unikowych formatowania VT100, podczas obliczania szerokości tabel.

PowerShell również dodane do nowego interfejsu API, który może służyć do formatowania kodu w celu ustalenia, czy VT100 jest obsługiwana. Przykład:

```powershell
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

Oto kompletny [przykład](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) można wyróżnić dopasowania z `Select-String`. Zapisz przykładowy plik o nazwie `MatchInfo.format.ps1xml`, aby użyć go w profilu lub w innych miejscach, uruchomi `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Należy pamiętać, że VT100 sekwencje ucieczki są obsługiwane tylko począwszy od aktualizacji systemu Windows 10 rozliczenia.
Nie są obsługiwane w starszych systemach.

### <a name="vi-mode-support-in-psreadline"></a>Obsługa trybu VI w PSReadline

[PSReadline](https://github.com/PowerShell/PSReadLine) dodaje obsługę trybu vi. Aby użyć trybu vi, uruchom `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Przekierowane stdin z danymi wejściowymi interaktywne

We wcześniejszych wersjach, uruchamianie programu PowerShell przy użyciu `powershell -File -` była wymagana, gdy zostało przekierowane stdin chciała interaktywnie wprowadzanie poleceń.

Z programem WMF 5.1, tym twardym dowiedzieć się, że opcja nie jest już konieczne. Można uruchomić programu PowerShell bez żadnych opcji.

Należy zauważyć, że nie obsługuje PSReadline przekierowanie stdin i z przekierowanego stdin wbudowane środowisko edycji wiersza polecenia jest bardzo ograniczona, na przykład, nie działają klawisze strzałek. Przyszłej wersji PSReadline powinno rozwiązać ten problem.