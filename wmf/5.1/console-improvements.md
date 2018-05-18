---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Ulepszenia konsoli w WMF 5.1
ms.openlocfilehash: fb689002caf42203d760f11acc64e52cfa681069
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="59d3f-103">Ulepszenia konsoli w WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="59d3f-103">Console Improvements in WMF 5.1#</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="59d3f-104">Ulepszenia konsoli programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="59d3f-104">PowerShell console improvements</span></span>

<span data-ttu-id="59d3f-105">Następujące zmiany zostały wprowadzone do powershell.exe w wersji 5.1 WMF celu usprawnienie obsługi konsoli:</span><span class="sxs-lookup"><span data-stu-id="59d3f-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="59d3f-106">Obsługa VT100</span><span class="sxs-lookup"><span data-stu-id="59d3f-106">VT100 support</span></span>

<span data-ttu-id="59d3f-107">Windows 10 dodano obsługę [sekwencji unikowych VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="59d3f-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="59d3f-108">PowerShell zignoruje sekwencje specjalne formatowanie niektórych VT100 podczas obliczania szerokości tabel.</span><span class="sxs-lookup"><span data-stu-id="59d3f-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="59d3f-109">Programu PowerShell również został dodany nowy interfejs API, który może być używany w formatowaniu kod, aby określić, czy VT100 jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="59d3f-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="59d3f-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="59d3f-110">For example:</span></span>

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
<span data-ttu-id="59d3f-111">W tym miejscu jest kompletna [przykład](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) można wyróżnić zgodny z wybierz ciągu.</span><span class="sxs-lookup"><span data-stu-id="59d3f-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="59d3f-112">Zapisz przykładu w pliku o nazwie `MatchInfo.format.ps1xml`, aby użyć go w profilu lub w innym miejscu, i uruchom `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="59d3f-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="59d3f-113">Należy pamiętać, że sekwencje unikowe VT100 są obsługiwane tylko począwszy od aktualizacji systemu Windows 10 Anniversary; nie są obsługiwane w starszych systemach.</span><span class="sxs-lookup"><span data-stu-id="59d3f-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="59d3f-114">Pomoc techniczna trybu VI w PSReadline</span><span class="sxs-lookup"><span data-stu-id="59d3f-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="59d3f-115">[PSReadline](https://github.com/lzybkr/PSReadLine) dodaje obsługę trybu vi.</span><span class="sxs-lookup"><span data-stu-id="59d3f-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="59d3f-116">Aby użyć trybu vi, uruchom `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="59d3f-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="59d3f-117">Stdin przekierowane przy użyciu interaktywnych danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="59d3f-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="59d3f-118">We wcześniejszych wersjach uruchamiania programu PowerShell z `powershell -File -` była wymagana, gdy stdin zostało przekierowane i chcesz interaktywnie wprowadź poleceń.</span><span class="sxs-lookup"><span data-stu-id="59d3f-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="59d3f-119">Z 5.1 WMF, tym twardym dowiedzieć się, że opcja nie jest już konieczne.</span><span class="sxs-lookup"><span data-stu-id="59d3f-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="59d3f-120">Można uruchomić programu PowerShell bez żadnych opcji, np. `powershell`.</span><span class="sxs-lookup"><span data-stu-id="59d3f-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="59d3f-121">Należy pamiętać, że PSReadline nie obsługuje obecnie przekierowanie stdin i wbudowane proces edycji wiersza polecenia z przekierowanego stdin jest bardzo ograniczona, na przykład klawisze strzałek nie działają.</span><span class="sxs-lookup"><span data-stu-id="59d3f-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="59d3f-122">Przyszłym wydaniu PSReadline powinno rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="59d3f-122">A future release of PSReadline should address this issue.</span></span>
