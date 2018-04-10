---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Używanie rozszerzenia karty
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="using-tab-expansion"></a><span data-ttu-id="020d7-103">Używanie rozszerzenia karty</span><span class="sxs-lookup"><span data-stu-id="020d7-103">Using Tab Expansion</span></span>

<span data-ttu-id="020d7-104">Wiersza polecenia powłoki często umożliwiają przeprowadzenie automatycznie, nazwy plików długa lub polecenia przyspieszenia polecenie wpisu i dostarczanie.</span><span class="sxs-lookup"><span data-stu-id="020d7-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing .</span></span> <span data-ttu-id="020d7-105">Windows PowerShell umożliwia podanie nazw plików i polecenia cmdlet przez naciśnięcie przycisku **kartę** klucza.</span><span class="sxs-lookup"><span data-stu-id="020d7-105">Windows PowerShell allows you to fill in file names and cmdlet names by pressing the **Tab** key.</span></span>

> [!NOTE]
> <span data-ttu-id="020d7-106">Karta rozszerzenia jest kontrolowana przez funkcji wewnętrznej TabExpansion lub TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="020d7-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="020d7-107">Od tej funkcji można zmodyfikowane lub zastąpione, rozważania jest przewodnik dotyczący zachowanie domyślnej konfiguracji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="020d7-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="020d7-108">Aby automatycznie wypełnić nazwę pliku lub ścieżki z dostępnych wyborów, wpisz część nazwy i naciśnij klawisz **kartę** klucza.</span><span class="sxs-lookup"><span data-stu-id="020d7-108">To fill in a filename or path from the available choices automatically, type part of the name and press the **Tab** key.</span></span> <span data-ttu-id="020d7-109">PowerShell zostanie automatycznie rozwiń nazwę do pierwszego znalezionego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="020d7-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="020d7-110">Naciśnięcie przycisku **kartę** klucza wielokrotnie może mieć wszystkich dostępnych opcji.</span><span class="sxs-lookup"><span data-stu-id="020d7-110">Pressing the **Tab** key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="020d7-111">Karta rozszerzenia nazw polecenia cmdlet są nieco inne.</span><span class="sxs-lookup"><span data-stu-id="020d7-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="020d7-112">Aby użyć karta rozszerzeń na nazwę polecenia cmdlet, wpisz cały pierwszej części nazwy (zlecenie) i następującym łącznik.</span><span class="sxs-lookup"><span data-stu-id="020d7-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="020d7-113">Możesz wpisać bardziej nazwy częściowe dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="020d7-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="020d7-114">Na przykład jeśli wpiszesz **get co** , a następnie naciśnij klawisz **kartę** klucza, programu PowerShell zostanie automatycznie Rozwiń do **Get-Command** polecenia cmdlet (Uwaga on również zmienia wielkość liter z listy do postaci standard).</span><span class="sxs-lookup"><span data-stu-id="020d7-114">For example, if you type **get-co** and then press the **Tab** key, PowerShell will automatically expand this to the **Get-Command** cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="020d7-115">Jeśli naciśniesz **kartę** klucza ponownie, programu PowerShell zastępuje to tylko innych pasującego nazwa polecenia cmdlet, **pobrania zawartości**.</span><span class="sxs-lookup"><span data-stu-id="020d7-115">If you press **Tab** key again, PowerShell replaces this with the only other matching cmdlet name, **Get-Content**.</span></span>

<span data-ttu-id="020d7-116">Karta rozszerzeń można użyć wielokrotnie w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="020d7-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="020d7-117">Na przykład można użyć karty rozszerzeń na nazwę **pobrania zawartości** polecenia cmdlet, wpisując:</span><span class="sxs-lookup"><span data-stu-id="020d7-117">For example, you can use tab expansion on the name of the **Get-Content** cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="020d7-118">Po naciśnięciu **kartę** klucza, polecenie rozwijany do:</span><span class="sxs-lookup"><span data-stu-id="020d7-118">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="020d7-119">Można częściowo określić ścieżkę do pliku dziennika Instalatora Active i użyć ponownie kartę rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="020d7-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="020d7-120">Po naciśnięciu **kartę** klucza, polecenie rozwijany do:</span><span class="sxs-lookup"><span data-stu-id="020d7-120">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="020d7-121">Jednym z ograniczeń procesu rozszerzenia karta jest czy karty są zawsze interpretowane jako próby wykonania programu word.</span><span class="sxs-lookup"><span data-stu-id="020d7-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="020d7-122">Jeśli skopiuj i Wklej przykładach poleceń w konsoli programu PowerShell, upewnij się, próbki nie zawiera karty; Jeśli tak, wyniki będą nieprzewidywalne i prawie na pewno nie będzie zgodny z zamierzonym.</span><span class="sxs-lookup"><span data-stu-id="020d7-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>