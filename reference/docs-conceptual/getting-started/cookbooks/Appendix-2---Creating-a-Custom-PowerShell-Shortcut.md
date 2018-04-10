---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Dodatek 2 Tworzenie niestandardowego skrótu programu PowerShell
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="91ca1-103">Dodatek 2 — Tworzenie skrótu niestandardowego programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="91ca1-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="91ca1-104">Poniższa procedura opisuje sposób tworzenia skrótu do programu Windows PowerShell, który ma kilka opcji wygodny dostosowane.</span><span class="sxs-lookup"><span data-stu-id="91ca1-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="91ca1-105">Utwórz skrót, który wskazuje Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="91ca1-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="91ca1-106">Kliknij prawym przyciskiem myszy skrót, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="91ca1-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="91ca1-107">Kliknij przycisk **Opcje** kartę.</span><span class="sxs-lookup"><span data-stu-id="91ca1-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="91ca1-108">W **edytować opcje** zaznacz **szybkiej edycji** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="91ca1-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="91ca1-109">To ustawienie pozwala wybrać tekst w oknie konsoli środowiska Windows PowerShell, przeciągając lewego przycisku myszy, a dzięki temu można skopiować tekst do Schowka, naciskając klawisz ENTER lub przez kliknięcie prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="91ca1-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="91ca1-110">W **edytować opcje** zaznacz **tryb wstawiania** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="91ca1-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="91ca1-111">To ustawienie umożliwia kliknij prawym przyciskiem myszy w oknie konsoli, aby automatycznie Wklej tekst ze Schowka.</span><span class="sxs-lookup"><span data-stu-id="91ca1-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="91ca1-112">W **historii poleceń** sekcji, wpisz lub wybierz liczbę z zakresu od 1 do 999 w **rozmiar buforu** pole.</span><span class="sxs-lookup"><span data-stu-id="91ca1-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="91ca1-113">To ustawienie kod maszynowy poleceń, które będą znajdować się w buforze konsoli.</span><span class="sxs-lookup"><span data-stu-id="91ca1-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="91ca1-114">W **historii poleceń** zaznacz **Odrzuć stare duplikaty** pole wyboru w celu wyeliminowania powtarzających poleceń z buforu konsoli.</span><span class="sxs-lookup"><span data-stu-id="91ca1-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="91ca1-115">Kliknij przycisk **układu** kartę.</span><span class="sxs-lookup"><span data-stu-id="91ca1-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="91ca1-116">W **buforu ekranu** wpisz liczbę z zakresu od 1 do 9999 w **wysokość** pole.</span><span class="sxs-lookup"><span data-stu-id="91ca1-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="91ca1-117">Wysokość reprezentuje liczbę wierszy danych wyjściowych, które są buforowane.</span><span class="sxs-lookup"><span data-stu-id="91ca1-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="91ca1-118">Jest to maksymalna liczba wierszy, przechowywane przez wyświetlanie podczas przewijania okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="91ca1-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="91ca1-119">Jeśli ta liczba jest niższa niż wysokość pokazano **rozmiar okna** sekcji wysokości rozmiaru okna automatycznie zostanie zmniejszona do tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="91ca1-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="91ca1-120">W **rozmiar okna** wpisz liczbę z zakresu od 1 do 9999 szerokości.</span><span class="sxs-lookup"><span data-stu-id="91ca1-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="91ca1-121">To oznacza liczbę znaków, które są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="91ca1-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="91ca1-122">Domyślna szerokość to 80 i formatowanie danych wyjściowych programu Windows PowerShell jest przeznaczony dla tej szerokości.</span><span class="sxs-lookup"><span data-stu-id="91ca1-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="91ca1-123">Jeśli chcesz umieścić konsoli w określonym punkcie na pulpicie, gdy jest otwarta, wyczyść **wybór pozycji okna przez system** pole wyboru w **położenie okna** sekcji, a następnie zmień wartości w  **Po lewej** i **górnej** pól **położenie okna** sekcji.</span><span class="sxs-lookup"><span data-stu-id="91ca1-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="91ca1-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="91ca1-124">Click **OK**.</span></span>