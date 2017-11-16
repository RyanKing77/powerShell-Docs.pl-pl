---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Cel programu Windows PowerShell ISE skryptów modelu obiektów"
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 3256d8bff3885d266f0db6f52932e40c4beaf8b1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="9beb5-103">Cel programu Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="9beb5-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>
  <span data-ttu-id="9beb5-104">Obiekt jest skojarzony z formularza i funkcji programu Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="9beb5-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="9beb5-105">Odwołanie do obiektu modelu zawiera szczegółowe informacje dotyczące elementu członkowskiego, właściwości i metody, które udostępniają te obiekty.</span><span class="sxs-lookup"><span data-stu-id="9beb5-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="9beb5-106">Aby pokazać, jak używać skryptów bezpośredni dostęp do tych metod i właściwości przedstawione przykłady.</span><span class="sxs-lookup"><span data-stu-id="9beb5-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="9beb5-107">Skryptów model obiektów ułatwia następującego zakresu zadań.</span><span class="sxs-lookup"><span data-stu-id="9beb5-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="9beb5-108">Dostosowywanie wyglądu programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9beb5-108">Customizing the appearance of Windows PowerShell ISE</span></span>
 <span data-ttu-id="9beb5-109">Model obiektów można użyć w celu zmodyfikowania ustawień aplikacji i opcje.</span><span class="sxs-lookup"><span data-stu-id="9beb5-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="9beb5-110">Na przykład można je zmodyfikować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9beb5-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="9beb5-111">Można zmienić kolor błędy, ostrzeżenia, pełne dane wyjściowe i danych wyjściowych debugowania.</span><span class="sxs-lookup"><span data-stu-id="9beb5-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>

- <span data-ttu-id="9beb5-112">Można pobrać lub ustawić kolory tła okienka polecenia, w okienku danych wyjściowych i w okienku skryptów.</span><span class="sxs-lookup"><span data-stu-id="9beb5-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>

- <span data-ttu-id="9beb5-113">Kolor pierwszego planu w okienku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="9beb5-113">You can set the foreground color for the Output pane.</span></span>

- <span data-ttu-id="9beb5-114">Można ustawić nazwę czcionki i rozmiar czcionki dla programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9beb5-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="9beb5-115">Można skonfigurować ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="9beb5-115">You can configure warnings.</span></span> <span data-ttu-id="9beb5-116">To ustawienie obejmuje ostrzeżenia, które są wydawane, gdy plik jest otwarty w wielu kartach programu PowerShell lub uruchamianie skryptu w pliku przed plik został zapisany.</span><span class="sxs-lookup"><span data-stu-id="9beb5-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>

- <span data-ttu-id="9beb5-117">Można przełączać się między widokiem skutkującej side-by-side okienko skryptu i w okienku danych wyjściowych oraz widok przypadku okienka Skrypt u góry w okienku danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="9beb5-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="9beb5-118">W okienku polecenie dokowany do dolnej lub górnej części okienka wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9beb5-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="9beb5-119">Rozszerzanie funkcji programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9beb5-119">Enhancing the functionality of Windows PowerShell ISE</span></span>
 <span data-ttu-id="9beb5-120">Model obiektów służy do rozszerzania funkcji programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9beb5-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="9beb5-121">Można na przykład:</span><span class="sxs-lookup"><span data-stu-id="9beb5-121">For example, you can:</span></span>

- <span data-ttu-id="9beb5-122">Dodawanie i modyfikowanie wystąpienie programu Windows PowerShell ISE samej siebie.</span><span class="sxs-lookup"><span data-stu-id="9beb5-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="9beb5-123">Na przykład aby zmienić menu, należy dodać nowe elementy menu i mapy skryptów nowych elementów menu.</span><span class="sxs-lookup"><span data-stu-id="9beb5-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>

- <span data-ttu-id="9beb5-124">Tworzenie skryptów, które wykonać kilka zadań, które można wykonać za pomocą poleceń menu i przycisków w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9beb5-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="9beb5-125">Na przykład można dodać, usunąć lub wybierz kartę programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9beb5-125">For example, you can add, remove, or select a PowerShell tab.</span></span>

- <span data-ttu-id="9beb5-126">Dopełnienia zadania, które mogą być wykonywane za pomocą poleceń menu i przycisków.</span><span class="sxs-lookup"><span data-stu-id="9beb5-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="9beb5-127">Na przykład można zmienić na karcie środowiska PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9beb5-127">For example, you can rename a PowerShell tab.</span></span>

- <span data-ttu-id="9beb5-128">Manipulowanie buforów tekst okienko poleceń, w okienku danych wyjściowych i w okienku skryptów, które są skojarzone z plikiem.</span><span class="sxs-lookup"><span data-stu-id="9beb5-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="9beb5-129">Można na przykład:</span><span class="sxs-lookup"><span data-stu-id="9beb5-129">For example, you can:</span></span>

    -   <span data-ttu-id="9beb5-130">GET lub set cały tekst.</span><span class="sxs-lookup"><span data-stu-id="9beb5-130">Get or set all text.</span></span>

    -   <span data-ttu-id="9beb5-131">GET lub set zaznaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="9beb5-131">Get or set a text selection.</span></span>

    -   <span data-ttu-id="9beb5-132">Uruchom skrypt lub uruchom wybrane części skryptu.</span><span class="sxs-lookup"><span data-stu-id="9beb5-132">Run a script or run a selected portion of a script.</span></span>

    -   <span data-ttu-id="9beb5-133">Przewiń wiersz do widoku.</span><span class="sxs-lookup"><span data-stu-id="9beb5-133">Scroll a line into view.</span></span>

    -   <span data-ttu-id="9beb5-134">Wstawianie tekstu w położeniu karetki.</span><span class="sxs-lookup"><span data-stu-id="9beb5-134">Insert text at a caret position.</span></span>

    -   <span data-ttu-id="9beb5-135">Wybierz blok tekstu.</span><span class="sxs-lookup"><span data-stu-id="9beb5-135">Select a block of text.</span></span>

    -   <span data-ttu-id="9beb5-136">Pobierz ostatni numer wiersza.</span><span class="sxs-lookup"><span data-stu-id="9beb5-136">Get the last line number.</span></span>

- <span data-ttu-id="9beb5-137">Wykonaj operacje na plikach.</span><span class="sxs-lookup"><span data-stu-id="9beb5-137">Perform file operations.</span></span> <span data-ttu-id="9beb5-138">Można na przykład:</span><span class="sxs-lookup"><span data-stu-id="9beb5-138">For example, you can:</span></span>

    -   <span data-ttu-id="9beb5-139">Otwórz plik, Zapisz plik lub zapisać plik przy użyciu innej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9beb5-139">Open a file, save a file, or save a file by using a different name.</span></span>

    -   <span data-ttu-id="9beb5-140">Ustal, czy plik został zmieniony od czasu ostatniego zapisania.</span><span class="sxs-lookup"><span data-stu-id="9beb5-140">Determine whether a file has been changed after it was last saved.</span></span>

    -   <span data-ttu-id="9beb5-141">Pobierz nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="9beb5-141">Get the file name.</span></span>

    -   <span data-ttu-id="9beb5-142">Wybierz plik.</span><span class="sxs-lookup"><span data-stu-id="9beb5-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="9beb5-143">Automatyzacja zadań</span><span class="sxs-lookup"><span data-stu-id="9beb5-143">Automating tasks</span></span>
 <span data-ttu-id="9beb5-144">Model obiektu skryptów służy do tworzenia skróty klawiaturowe dla często operacji.</span><span class="sxs-lookup"><span data-stu-id="9beb5-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="9beb5-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9beb5-145">See Also</span></span>
- [<span data-ttu-id="9beb5-146">Hierarchia modelu obiektów ISE</span><span class="sxs-lookup"><span data-stu-id="9beb5-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md) 
- [<span data-ttu-id="9beb5-147">Dotyczące modelu obiektów programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9beb5-147">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="9beb5-148">Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="9beb5-148">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
