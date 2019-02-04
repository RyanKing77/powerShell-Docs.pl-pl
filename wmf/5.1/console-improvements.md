---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Ulepszenia konsoli w programie WMF 5.1
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687342"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="2b730-103">Ulepszenia konsoli w programie WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2b730-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="2b730-104">Ulepszenia konsoli programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b730-104">PowerShell console improvements</span></span>

<span data-ttu-id="2b730-105">Wprowadzono następujące zmiany do powershell.exe programu WMF 5.1 do udoskonalenia środowiska konsoli:</span><span class="sxs-lookup"><span data-stu-id="2b730-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="2b730-106">Obsługa VT100</span><span class="sxs-lookup"><span data-stu-id="2b730-106">VT100 support</span></span>

<span data-ttu-id="2b730-107">Windows 10 dodano obsługę [sekwencje ucieczki VT100](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="2b730-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="2b730-108">PowerShell będzie ignorować niektórych sekwencji unikowych formatowania VT100, podczas obliczania szerokości tabel.</span><span class="sxs-lookup"><span data-stu-id="2b730-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="2b730-109">PowerShell również dodane do nowego interfejsu API, który może służyć do formatowania kodu w celu ustalenia, czy VT100 jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="2b730-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="2b730-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2b730-110">For example:</span></span>

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

<span data-ttu-id="2b730-111">Oto kompletny [przykład](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) można wyróżnić dopasowania z `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="2b730-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span>
<span data-ttu-id="2b730-112">Zapisz przykładowy plik o nazwie `MatchInfo.format.ps1xml`, aby użyć go w profilu lub w innych miejscach, uruchomi `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="2b730-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="2b730-113">Należy zauważyć, że VT100 sekwencje ucieczki są tylko obsługiwane począwszy od systemu Windows 10 rozliczenia aktualizacji. nie są obsługiwane w starszych systemach.</span><span class="sxs-lookup"><span data-stu-id="2b730-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="2b730-114">Obsługa trybu VI w PSReadline</span><span class="sxs-lookup"><span data-stu-id="2b730-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="2b730-115">[PSReadline](https://github.com/lzybkr/PSReadLine) dodaje obsługę trybu vi.</span><span class="sxs-lookup"><span data-stu-id="2b730-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="2b730-116">Aby użyć trybu vi, uruchom `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="2b730-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="2b730-117">Przekierowane stdin z danymi wejściowymi interaktywne</span><span class="sxs-lookup"><span data-stu-id="2b730-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="2b730-118">We wcześniejszych wersjach, uruchamianie programu PowerShell przy użyciu `powershell -File -` była wymagana, gdy zostało przekierowane stdin chciała interaktywnie wprowadzanie poleceń.</span><span class="sxs-lookup"><span data-stu-id="2b730-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="2b730-119">Z programem WMF 5.1, tym twardym dowiedzieć się, że opcja nie jest już konieczne.</span><span class="sxs-lookup"><span data-stu-id="2b730-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="2b730-120">Można uruchomić programu PowerShell bez żadnych opcji, np. `powershell`.</span><span class="sxs-lookup"><span data-stu-id="2b730-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="2b730-121">Należy zauważyć, że nie obsługuje obecnie PSReadline przekierowanie stdin i z przekierowanego stdin wbudowane środowisko edycji wiersza polecenia jest bardzo ograniczona, na przykład, nie działają klawisze strzałek.</span><span class="sxs-lookup"><span data-stu-id="2b730-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="2b730-122">Przyszłej wersji PSReadline powinno rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="2b730-122">A future release of PSReadline should address this issue.</span></span>