---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Dodatek 2 Tworzenie niestandardowego skrótu programu PowerShell
ms.openlocfilehash: 6f1a6a8187b1797103e3620b2cf9155978807ea5
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030302"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="c88a9-103">Dodatek 2 — Tworzenie niestandardowego skrótu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="c88a9-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="c88a9-104">Poniższa procedura opisuje sposób tworzenia skrótu do programu PowerShell Windows, który ma kilka opcji wygodne dostosowane.</span><span class="sxs-lookup"><span data-stu-id="c88a9-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="c88a9-105">Utwórz skrót, który wskazuje na Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="c88a9-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="c88a9-106">Kliknij prawym przyciskiem myszy skrót, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c88a9-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="c88a9-107">Kliknij przycisk **Opcje** kartę.</span><span class="sxs-lookup"><span data-stu-id="c88a9-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="c88a9-108">W **opcje edytowania** zaznacz **szybkiej edycji** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="c88a9-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="c88a9-109">To ustawienie umożliwia zaznacz tekst w oknie konsoli środowiska Windows PowerShell przez przeciągnięcie lewym przyciskiem myszy, a dzięki temu można skopiować tekst do Schowka, naciskając klawisz ENTER lub klikając prawym przyciskiem myszy przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="c88a9-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="c88a9-110">W **opcje edytowania** zaznacz **tryb wstawiania** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="c88a9-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="c88a9-111">To ustawienie umożliwia kliknij prawym przyciskiem myszy w oknie konsoli, aby automatycznie Wklej tekst ze Schowka.</span><span class="sxs-lookup"><span data-stu-id="c88a9-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="c88a9-112">W **historii poleceń** sekcji, wpisz lub wybierz liczbę z zakresu od 1 do 999 w **rozmiar buforu** pole.</span><span class="sxs-lookup"><span data-stu-id="c88a9-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="c88a9-113">To ustawia liczbę wpisanych poleceń, które będą znajdować się w buforze konsoli.</span><span class="sxs-lookup"><span data-stu-id="c88a9-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="c88a9-114">W **historii poleceń** zaznacz **Odrzuć stare duplikaty** pole wyboru w celu wyeliminowania powtarzających poleceń z buforu konsoli.</span><span class="sxs-lookup"><span data-stu-id="c88a9-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="c88a9-115">Kliknij przycisk **układu** kartę.</span><span class="sxs-lookup"><span data-stu-id="c88a9-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="c88a9-116">W **buforu ekranu** sekcji, wpisz liczbę z zakresu od 1 do 9999 w **wysokość** pole.</span><span class="sxs-lookup"><span data-stu-id="c88a9-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="c88a9-117">Wysokość reprezentuje liczbę wierszy danych wyjściowych, które są buforowane.</span><span class="sxs-lookup"><span data-stu-id="c88a9-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="c88a9-118">Jest to maksymalna liczba wierszy zachowana na potrzeby wyświetlania podczas przewijania w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c88a9-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="c88a9-119">Jeśli ta liczba jest niższa niż wysokość objętego **rozmiar okna** sekcji wysokości rozmiaru okna automatycznie zostanie zredukowana do tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="c88a9-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="c88a9-120">W **rozmiar okna** sekcji, wpisz liczbę z zakresu od 1 do 9999 szerokości.</span><span class="sxs-lookup"><span data-stu-id="c88a9-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="c88a9-121">Reprezentuje liczbę znaków, które są wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c88a9-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="c88a9-122">Domyślna szerokość to 80 i formatowanie danych wyjściowych programu Windows PowerShell jest przeznaczony dla tej szerokości.</span><span class="sxs-lookup"><span data-stu-id="c88a9-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="c88a9-123">Jeśli chcesz umieścić konsoli w określonym punkcie na pulpicie, gdy zostanie otwarta, wyczyść **wybór pozycji okna przez system** pole wyboru w **położenie okna** sekcji, a następnie zmień wartości w  **Po lewej stronie** i **górnej** pola **położenie okna** sekcji.</span><span class="sxs-lookup"><span data-stu-id="c88a9-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="c88a9-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="c88a9-124">Click **OK**.</span></span>
