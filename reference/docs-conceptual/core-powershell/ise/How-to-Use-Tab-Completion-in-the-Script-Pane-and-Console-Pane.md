---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak używać funkcji uzupełniania po naciśnięciu klawisza TAB w okienku skryptów i okienku konsoli
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: 24a3f00987ff5ca4bf82d1a3206857ec3c4b3f09
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851139"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="4d69c-103">Jak używać funkcji uzupełniania po naciśnięciu klawisza TAB w okienku skryptów i okienku konsoli</span><span class="sxs-lookup"><span data-stu-id="4d69c-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="4d69c-104">Uzupełnianie po naciśnięciu tabulatora zapewnia automatyczne pomocy podczas wpisywania, w okienku skryptów lub w okienku poleceń.</span><span class="sxs-lookup"><span data-stu-id="4d69c-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="4d69c-105">Aby móc korzystać z tej funkcji, należy użyć następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4d69c-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="4d69c-106">Aby automatycznie wypełnić pozycji polecenia</span><span class="sxs-lookup"><span data-stu-id="4d69c-106">To automatically complete a command entry</span></span>

<span data-ttu-id="4d69c-107">W okienku polecenia lub w okienku skryptów wpisać kilka znaków, polecenia, a następnie naciśnij klawisz TAB, aby zaznaczyć tekst żądanego zakończenia.</span><span class="sxs-lookup"><span data-stu-id="4d69c-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="4d69c-108">Jeśli wiele elementów zaczynają się od początku wpisany tekst, a następnie naciskając klawisz Tab, aż pojawi się element, który ma.</span><span class="sxs-lookup"><span data-stu-id="4d69c-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="4d69c-109">Uzupełnianie po naciśnięciu tabulatora może ułatwić wpisując nazwę polecenia cmdlet, nazwa parametru, nazwa zmiennej, nazwa właściwości obiektu lub ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="4d69c-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="4d69c-110">W okienku skryptu klawisza TAB automatycznie ukończy polecenia tylko wtedy, gdy edytujesz, ps1, psd1 lub plikach .psm1.</span><span class="sxs-lookup"><span data-stu-id="4d69c-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="4d69c-111">Uzupełnianie po naciśnięciu tabulatora działa w dowolnym momencie, kiedy wpisujesz w okienku poleceń.</span><span class="sxs-lookup"><span data-stu-id="4d69c-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="4d69c-112">Aby automatycznie wypełnić zapis parametru polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="4d69c-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="4d69c-113">W okienku okienka polecenia lub skryptu wpisz polecenie cmdlet kreska, a następnie naciśnij klawisz TAB.</span><span class="sxs-lookup"><span data-stu-id="4d69c-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press TAB.</span></span>

<span data-ttu-id="4d69c-114">Na przykład wpisz `Get-Process -` i następnie naciśnij klawisz TAB kilka razy do wyświetlenia każdego z parametrów polecenia cmdlet z osobna.</span><span class="sxs-lookup"><span data-stu-id="4d69c-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d69c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d69c-115">See Also</span></span>

- [<span data-ttu-id="4d69c-116">Wprowadzenie do programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4d69c-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="4d69c-117">Jak utworzyć kartę programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d69c-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
