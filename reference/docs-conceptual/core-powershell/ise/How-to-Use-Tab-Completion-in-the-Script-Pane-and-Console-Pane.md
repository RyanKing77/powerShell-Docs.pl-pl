---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak używać funkcji uzupełniania po naciśnięciu klawisza TAB w okienku skryptów i okienku konsoli
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: e1f8146b6113a82fd3d857c98550ec2e459715a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="eae1c-103">Jak używać funkcji uzupełniania po naciśnięciu klawisza TAB w okienku skryptów i okienku konsoli</span><span class="sxs-lookup"><span data-stu-id="eae1c-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="eae1c-104">Uzupełnianie po naciśnięciu tabulatora zapewnia automatyczne pomocy podczas wpisywania, w okienku skryptów lub w okienku polecenia.</span><span class="sxs-lookup"><span data-stu-id="eae1c-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="eae1c-105">Aby móc korzystać z tej funkcji, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="eae1c-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="eae1c-106">Aby automatycznie wypełnić polecenie wpisu</span><span class="sxs-lookup"><span data-stu-id="eae1c-106">To automatically complete a command entry</span></span>

<span data-ttu-id="eae1c-107">W okienku polecenia lub skryptu w okienku wpisz polecenie kilku znaków, a następnie naciśnij klawisz TAB, aby wybrać żądaną uzupełniania tekstu.</span><span class="sxs-lookup"><span data-stu-id="eae1c-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="eae1c-108">Jeśli wiele elementów zaczyna się od tekstu, który został początkowo wpisany, Kontynuuj, naciskając klawisz Tab, aż zostanie wyświetlony element, który ma.</span><span class="sxs-lookup"><span data-stu-id="eae1c-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="eae1c-109">Uzupełnianie po naciśnięciu tabulatora może pomóc w trakcie pisania nazwa polecenia cmdlet, nazwa parametru, nazwa zmiennej, nazwa właściwości obiektu lub ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="eae1c-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="eae1c-110">W okienku skryptów naciskając klawisz TAB automatycznie ukończy polecenie tylko podczas edytowania .ps1, psd1 lub plikach .psm1.</span><span class="sxs-lookup"><span data-stu-id="eae1c-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="eae1c-111">Uzupełnianie po naciśnięciu tabulatora działa w dowolnym momencie podczas wpisywania w okienku polecenia.</span><span class="sxs-lookup"><span data-stu-id="eae1c-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="eae1c-112">Aby automatycznie wypełnić zapis parametru polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="eae1c-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="eae1c-113">W okienku Okienko polecenia lub skryptu wpisz polecenie cmdlet następuje myślnik, a następnie naciśnij klawisz TAB.</span><span class="sxs-lookup"><span data-stu-id="eae1c-113">In the Command Pane or Script pane, type a cmdlet followed by a dash, and then press TAB.</span></span>

<span data-ttu-id="eae1c-114">Na przykład wpisz `Get-Process -` , a następnie naciśnij kilkakrotnie klawisz TAB do wyświetlania każdego z parametrów polecenia cmdlet z kolei.</span><span class="sxs-lookup"><span data-stu-id="eae1c-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="eae1c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eae1c-115">See Also</span></span>

- [<span data-ttu-id="eae1c-116">Wprowadzenie do programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eae1c-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="eae1c-117">Jak utworzyć kartę programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="eae1c-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)