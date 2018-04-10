---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak utworzyć kartę programu PowerShell w środowisku Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 4d4388d889f2178b2cd24cb0f3350aee37327625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="cd414-103">Jak utworzyć kartę programu PowerShell w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="cd414-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="cd414-104">Karty w Windows PowerShell Integrated Scripting Environment (ISE) umożliwiają jednoczesne tworzenie i używanie kilku środowiskach wykonywania w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd414-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="cd414-105">Każdej karcie PowerShell odnosi się do środowiska wykonawczego oddzielne lub sesję.</span><span class="sxs-lookup"><span data-stu-id="cd414-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="cd414-106">**UWAGA**:</span><span class="sxs-lookup"><span data-stu-id="cd414-106">**NOTE**:</span></span>
>
> <span data-ttu-id="cd414-107">Zmienne, funkcje i aliasy, które możesz utworzyć w jednej karty nie jest przenoszone do innego.</span><span class="sxs-lookup"><span data-stu-id="cd414-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="cd414-108">Są one różnych sesjach programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd414-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="cd414-109">Wykonaj następujące kroki, aby otworzyć lub zamknąć kartę w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd414-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="cd414-110">Aby zmienić nazwę karty, ustaw [DisplayName](The-PowerShellTab-Object.md#displayname) właściwości w obiekcie skryptów Windows PowerShell kartę.</span><span class="sxs-lookup"><span data-stu-id="cd414-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="cd414-111">Tworzenie i używanie na nowej karcie środowiska PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd414-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="cd414-112">Na **pliku** menu, kliknij przycisk **nową kartę PowerShell**. Nowa karta programu PowerShell zawsze otwierany jako aktywne okno.</span><span class="sxs-lookup"><span data-stu-id="cd414-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="cd414-113">Karty PowerShell przyrostowo są numerowane w kolejności, że są otwarte.</span><span class="sxs-lookup"><span data-stu-id="cd414-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="cd414-114">Każda karta jest skojarzony z osobnym oknie konsoli środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cd414-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="cd414-115">Może mieć maksymalnie 32 kart programu PowerShell za pomocą ich własnych sesji otwarte w czasie (to jest ograniczone do 8 w programie Windows PowerShell ISE 2.0).</span><span class="sxs-lookup"><span data-stu-id="cd414-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="cd414-116">Należy pamiętać, że kliknięcie pozycji **nowy** lub **Otwórz** ikon na pasku narzędzi nie powoduje utworzenia nowej karty w oddzielnym sesji.</span><span class="sxs-lookup"><span data-stu-id="cd414-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="cd414-117">Zamiast tego tych przycisków Otwieranie pliku skryptu nowego lub istniejącego na karcie aktualnie aktywne w sesji.</span><span class="sxs-lookup"><span data-stu-id="cd414-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="cd414-118">Może mieć wiele skryptów, plików otwartych z każdej karcie i sesji.</span><span class="sxs-lookup"><span data-stu-id="cd414-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="cd414-119">Karty skryptu dla sesji są wyświetlone poniżej karty sesji tylko, gdy skojarzona sesja jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="cd414-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="cd414-120">Aby uaktywnić kartę programu PowerShell, kliknij kartę. Aby dokonać wyboru spośród wszystkich kart programu PowerShell, które są otwarte na **widoku** menu, kliknij kartę programu PowerShell, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="cd414-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="cd414-121">Tworzenie i używanie na nowej karcie zdalnego programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd414-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="cd414-122">Na **pliku** menu, kliknij przycisk **nową kartę zdalne programu PowerShell** ustanowienie sesji na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="cd414-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="cd414-123">Okno dialogowe zostanie wyświetlone i wyświetli monit o wprowadzenie szczegółowe informacje wymagane do nawiązania połączenia zdalnego.</span><span class="sxs-lookup"><span data-stu-id="cd414-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="cd414-124">Funkcje zdalnego kartę podobnie jak lokalny kartę programu PowerShell, ale poleceń i skryptów są uruchamiane na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="cd414-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="cd414-125">Aby zamknąć kartę programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd414-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="cd414-126">Aby zamknąć kartę, można użyć dowolnego z poniższych:</span><span class="sxs-lookup"><span data-stu-id="cd414-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="cd414-127">Kliknij kartę, która ma zostać zamknięte.</span><span class="sxs-lookup"><span data-stu-id="cd414-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="cd414-128">Na **pliku** menu, kliknij przycisk **zamknąć kartę PowerShell**, lub kliknij przycisk Zamknij (**X**) na aktywną kartę, aby zamknąć kartę.</span><span class="sxs-lookup"><span data-stu-id="cd414-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="cd414-129">Jeśli istnieją niezapisane pliki otwarte w karcie programu PowerShell, że zamykasz, zostanie wyświetlony monit o Zapisz lub Odrzuć je.</span><span class="sxs-lookup"><span data-stu-id="cd414-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="cd414-130">Aby uzyskać więcej informacji na temat zapisywania skryptu, zobacz [jak zapisać skrypt](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="cd414-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd414-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd414-131">See Also</span></span>

- [<span data-ttu-id="cd414-132">Wprowadzenie do programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="cd414-132">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="cd414-133">Jak używać okienku konsoli w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="cd414-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)