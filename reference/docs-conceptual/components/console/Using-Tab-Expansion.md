---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie rozszerzenia karty
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 437c1e3c04352f2c5c3aba4c67b542821975f739
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229434"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="d6d96-103">Używanie rozszerzenia karty</span><span class="sxs-lookup"><span data-stu-id="d6d96-103">Using Tab Expansion</span></span>

<span data-ttu-id="d6d96-104">Wiersza polecenia powłoki często umożliwiają automatyczne, ukończenie nazwy plików długi lub polecenia przyspieszanie wprowadzania polecenia, a także wskazówki.</span><span class="sxs-lookup"><span data-stu-id="d6d96-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="d6d96-105">Program PowerShell umożliwia Wypełnij nazw plików i polecenia cmdlet, naciskając klawisz <kbd>kartę</kbd> klucza.</span><span class="sxs-lookup"><span data-stu-id="d6d96-105">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="d6d96-106">Rozszerzenia karty jest kontrolowana przez funkcji wewnętrznej TabExpansion lub TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="d6d96-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="d6d96-107">Ponieważ ta funkcja mogą być zmodyfikowane lub zastąpione, tej dyskusji jest Przewodnik z zachowaniem domyślnej konfiguracji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6d96-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="d6d96-108">Automatyczne wypełnianie nazwę pliku lub ścieżki z listy dostępnych opcji, wpisz część nazwy i naciśnij klawisz <kbd>kartę</kbd> klucza.</span><span class="sxs-lookup"><span data-stu-id="d6d96-108">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="d6d96-109">PowerShell będzie automatycznie rozwiń nazwę pierwsze dopasowanie, które znajdzie.</span><span class="sxs-lookup"><span data-stu-id="d6d96-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="d6d96-110">Naciśnięcie klawisza <kbd>kartę</kbd> klucz będzie wielokrotnie przechodzić przez wszystkie dostępne opcje.</span><span class="sxs-lookup"><span data-stu-id="d6d96-110">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="d6d96-111">Karta rozszerzenia nazwy poleceń cmdlet jest nieco inne.</span><span class="sxs-lookup"><span data-stu-id="d6d96-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="d6d96-112">Aby użyć rozszerzenia karty na nazwę polecenia cmdlet, wpisz całą pierwszej części nazwy (zlecenie) i łącznik, który po nim następuje.</span><span class="sxs-lookup"><span data-stu-id="d6d96-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="d6d96-113">Można wypełnić więcej nazwy częściowe dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="d6d96-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="d6d96-114">Na przykład, jeśli wpiszesz `get-co` , a następnie naciśnij klawisz <kbd>kartę</kbd> klucza, programu PowerShell automatycznie rozwinie to `Get-Command` polecenia cmdlet (Uwaga on również zmiany wielkości liter do postaci standard).</span><span class="sxs-lookup"><span data-stu-id="d6d96-114">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="d6d96-115">Jeśli użytkownik naciśnie klawisz <kbd>kartę</kbd> klucza ponownie, programu PowerShell zastępuje to tylko innych zgodnych nazwa polecenia cmdlet, `Get-Content`.</span><span class="sxs-lookup"><span data-stu-id="d6d96-115">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="d6d96-116">Rozszerzenia karty można użyć wielokrotnie, w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="d6d96-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="d6d96-117">Na przykład, można użyć rozszerzenia karty nazwę `Get-Content` polecenia cmdlet, wpisując:</span><span class="sxs-lookup"><span data-stu-id="d6d96-117">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="d6d96-118">Po naciśnięciu klawisza <kbd>kartę</kbd> klucza, polecenie jest rozszerzany, aby:</span><span class="sxs-lookup"><span data-stu-id="d6d96-118">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="d6d96-119">Można następnie częściowo Określ ścieżkę do pliku dziennika Instalatora Active i użyć ponownie rozszerzenia karty:</span><span class="sxs-lookup"><span data-stu-id="d6d96-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="d6d96-120">Po naciśnięciu klawisza <kbd>kartę</kbd> klucza, polecenie jest rozszerzany, aby:</span><span class="sxs-lookup"><span data-stu-id="d6d96-120">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="d6d96-121">Jednym z ograniczeń kartę proces rozszerzenia jest karty są zawsze interpretowane jako próby Dokończ wyraz.</span><span class="sxs-lookup"><span data-stu-id="d6d96-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="d6d96-122">Jeśli skopiujesz i wkleisz przykłady poleceń w konsoli programu PowerShell, upewnij się, plik nie zawiera karty; Jeśli tak jest, wyniki będą nieprzewidywalne i prawie na pewno nie będzie zamierzonym.</span><span class="sxs-lookup"><span data-stu-id="d6d96-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>