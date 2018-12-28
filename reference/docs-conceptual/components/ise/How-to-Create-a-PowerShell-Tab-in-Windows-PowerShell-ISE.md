---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Jak utworzyć kartę programu PowerShell w środowisku Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 080fe89bf1443f51460589b445431913fa20b4b8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404760"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="78a1e-103">Jak utworzyć kartę programu PowerShell w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="78a1e-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="78a1e-104">Karty w Windows PowerShell zintegrowane Scripting Environment (ISE) umożliwiają jednoczesne tworzenie i używanie kilku środowiskach wykonawczych w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="78a1e-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="78a1e-105">Każda karta środowiska PowerShell odnosi się do środowiska wykonawczego oddzielne lub sesji.</span><span class="sxs-lookup"><span data-stu-id="78a1e-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="78a1e-106">Zmienne, funkcje i aliasy, które tworzysz w jednej karty nie jest przenoszone do innego.</span><span class="sxs-lookup"><span data-stu-id="78a1e-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="78a1e-107">Są one różne sesje środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a1e-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="78a1e-108">Wykonaj następujące kroki, aby otworzyć lub zamknąć kartę w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a1e-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="78a1e-109">Aby zmienić nazwę karty, należy ustawić [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) właściwości w obiekcie skryptów programu Windows PowerShell kartę.</span><span class="sxs-lookup"><span data-stu-id="78a1e-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="78a1e-110">Aby utworzyć nową kartę programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="78a1e-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="78a1e-111">Na **pliku** menu, kliknij przycisk **Nowa karta programu PowerShell**. Jako aktywne okno zawsze zostanie otwarta nowa karta programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a1e-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="78a1e-112">Karty programu PowerShell przyrostowe są ponumerowane w kolejności ich otworzyć.</span><span class="sxs-lookup"><span data-stu-id="78a1e-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="78a1e-113">Każda karta jest skojarzony z własnego okna konsoli programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78a1e-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="78a1e-114">Może mieć maksymalnie 32 kart programu PowerShell za pomocą ich własnych sesji, które są otwarte w czasie (to jest ograniczony do 8 w wersji 2.0 programu Windows PowerShell ISE).</span><span class="sxs-lookup"><span data-stu-id="78a1e-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="78a1e-115">Należy pamiętać, że kliknięcie **New** lub **Otwórz** ikony na pasku narzędzi nie tworzy nową kartę z oddzielną sesję.</span><span class="sxs-lookup"><span data-stu-id="78a1e-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="78a1e-116">Te przyciski otwierać plik skryptu nowej lub istniejącej karty aktualnie aktywne w sesji.</span><span class="sxs-lookup"><span data-stu-id="78a1e-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="78a1e-117">Może mieć wiele skryptu, który pliki otwierane z każdej karty i sesji.</span><span class="sxs-lookup"><span data-stu-id="78a1e-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="78a1e-118">Karty skryptu dla sesji są wyświetlone poniżej karty sesji tylko wtedy, gdy skojarzona sesja jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="78a1e-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="78a1e-119">Aby uaktywnić kartę programu PowerShell, kliknij kartę. Aby dokonać wyboru spośród wszystkich kart programu PowerShell, które są otwarte, w **widoku** menu, kliknij kartę programu PowerShell, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="78a1e-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="78a1e-120">Tworzenie i używanie na nowej karcie zdalnego programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="78a1e-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="78a1e-121">Na **pliku** menu, kliknij przycisk **Nowa karta programu PowerShell zdalnego** nawiązać sesji na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="78a1e-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="78a1e-122">Okno dialogowe pojawia się i wyświetli monit o wprowadzenie szczegółowe informacje wymagane do nawiązania połączenia zdalnego.</span><span class="sxs-lookup"><span data-stu-id="78a1e-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="78a1e-123">Funkcje karty zdalny podobnie jak lokalne kartę programu PowerShell, ale polecenia i skrypty są uruchamiane na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="78a1e-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="78a1e-124">Aby zamknąć kartę programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="78a1e-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="78a1e-125">Aby zamknąć kartę, można użyć dowolnego z następujących technik:</span><span class="sxs-lookup"><span data-stu-id="78a1e-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="78a1e-126">Kliknij kartę która ma zostać zamknięte.</span><span class="sxs-lookup"><span data-stu-id="78a1e-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="78a1e-127">Na **pliku** menu, kliknij przycisk **Zamknij kartę programu PowerShell**, lub kliknij przycisk Zamknij (**X**) w aktywnej karcie, aby zamknąć kartę.</span><span class="sxs-lookup"><span data-stu-id="78a1e-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="78a1e-128">Jeśli istnieją niezapisane pliki otwarte w kartę programu PowerShell, że zamykasz, zostanie wyświetlony monit o zapisać lub odrzucić je.</span><span class="sxs-lookup"><span data-stu-id="78a1e-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="78a1e-129">Aby uzyskać więcej informacji na temat zapisywania skryptu, zobacz [jak zapisać skrypt](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="78a1e-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="78a1e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78a1e-130">See Also</span></span>

- [<span data-ttu-id="78a1e-131">Wprowadzenie do programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="78a1e-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="78a1e-132">Jak używać okienka konsoli w środowisku Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="78a1e-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)