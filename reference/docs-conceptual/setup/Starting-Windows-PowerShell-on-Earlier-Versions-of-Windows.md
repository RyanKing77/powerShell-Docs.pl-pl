---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Uruchamianie programu Windows PowerShell we wcześniejszych wersjach systemu Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2018
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="1892e-103">Uruchamianie programu Windows PowerShell we wcześniejszych wersjach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1892e-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="1892e-104">W tej sekcji wyjaśniono, jak można uruchomić programu Windows PowerShell i Windows PowerShell Integrated Scripting Environment (ISE) na Windows® 7, Windows Server® 2008 R2 i Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="1892e-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="1892e-105">Ponadto wyjaśniono, jak włączyć funkcję opcjonalne dla programu Windows PowerShell ISE w programie Windows PowerShell 2.0 w systemie Windows Server® 2008 R2 i Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="1892e-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="1892e-106">Aby zainstalować program Windows PowerShell 4.0 w obsługiwanych systemach, Pobierz i zainstaluj [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span><span class="sxs-lookup"><span data-stu-id="1892e-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="1892e-107">Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="1892e-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="1892e-108">Aby zainstalować program Windows PowerShell 3.0 w obsługiwanych systemach, Pobierz i zainstaluj [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="1892e-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="1892e-109">Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="1892e-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="1892e-110">Jak uruchomić środowisko Windows PowerShell we wcześniejszych wersjach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1892e-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="1892e-111">Użyj dowolnej z następujących metod, aby uruchomić zainstalowana wersja programu Windows PowerShell 3.0 lub Windows PowerShell 4.0, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="1892e-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="1892e-112">Z Start Menu</span><span class="sxs-lookup"><span data-stu-id="1892e-112">From the Start Menu</span></span>

- <span data-ttu-id="1892e-113">Kliknij przycisk **Start**, typ **PowerShell**, a następnie kliknij przycisk **programu Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1892e-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

- <span data-ttu-id="1892e-114">Z **Start** menu, kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij przycisk **środowiska Windows PowerShell**  folder, a następnie kliknij przycisk **programu Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1892e-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="1892e-115">W wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="1892e-115">At the Command Prompt</span></span>

- <span data-ttu-id="1892e-116">Cmd.exe, środowiska Windows PowerShell lub programu Windows PowerShell ISE Aby uruchomić środowisko Windows PowerShell, wpisz:</span><span class="sxs-lookup"><span data-stu-id="1892e-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="1892e-117">Aby dostosować sesji umożliwia także parametry PowerShell.exe program.</span><span class="sxs-lookup"><span data-stu-id="1892e-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="1892e-118">Aby uzyskać więcej informacji, zobacz [PowerShell.exe pomocy](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="1892e-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="1892e-119">Z administracyjne uprawnień ("Uruchom jako administrator")</span><span class="sxs-lookup"><span data-stu-id="1892e-119">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="1892e-120">Kliknij przycisk **Start**, typ **PowerShell**, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="1892e-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="1892e-121">Uruchamianie programu Windows PowerShell ISE we wcześniejszych wersjach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1892e-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="1892e-122">Użyj dowolnej z następujących metod, aby uruchomić program Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1892e-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="1892e-123">Z Start Menu</span><span class="sxs-lookup"><span data-stu-id="1892e-123">From the Start Menu</span></span>

- <span data-ttu-id="1892e-124">Kliknij przycisk **Start**, typ **ISE**, a następnie kliknij przycisk **programu Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="1892e-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

- <span data-ttu-id="1892e-125">Z **Start** menu, kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij przycisk **środowiska Windows PowerShell**  folder, a następnie kliknij przycisk **programu Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="1892e-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="1892e-126">W wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="1892e-126">At the Command Prompt</span></span>

- <span data-ttu-id="1892e-127">Cmd.exe, środowiska Windows PowerShell lub programu Windows PowerShell ISE Aby uruchomić środowisko Windows PowerShell, wpisz:</span><span class="sxs-lookup"><span data-stu-id="1892e-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="1892e-128">lub</span><span class="sxs-lookup"><span data-stu-id="1892e-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="1892e-129">Z administracyjne uprawnień ("Uruchom jako administrator")</span><span class="sxs-lookup"><span data-stu-id="1892e-129">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="1892e-130">Kliknij przycisk **Start**, typ **ISE**, kliknij prawym przyciskiem myszy **programu Windows PowerShell ISE**, a następnie kliknij przycisk **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="1892e-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="1892e-131">Włączanie programu Windows PowerShell ISE we wcześniejszych wersjach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1892e-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="1892e-132">W programie Windows PowerShell 4.0 i programu Windows PowerShell 3.0 programu Windows PowerShell ISE jest włączona domyślnie we wszystkich wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1892e-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="1892e-133">Jeśli nie jest jeszcze włączone, system Windows Management Framework 4.0 lub Windows Management Framework 3.0 włączy ją.</span><span class="sxs-lookup"><span data-stu-id="1892e-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="1892e-134">W programie Windows PowerShell 2.0 Windows PowerShell ISE jest włączona domyślnie w systemie Windows 7.</span><span class="sxs-lookup"><span data-stu-id="1892e-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="1892e-135">Jednak w systemie Windows Server 2008 R2 i Windows Server 2008 jest funkcją opcjonalną.</span><span class="sxs-lookup"><span data-stu-id="1892e-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="1892e-136">Aby włączyć program Windows PowerShell ISE w programie Windows PowerShell 2.0 w systemie Windows Server 2008 R2 lub Windows Server 2008, należy użyć następującej procedury.</span><span class="sxs-lookup"><span data-stu-id="1892e-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="1892e-137">Aby włączyć Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="1892e-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="1892e-138">Uruchom Menedżera serwera.</span><span class="sxs-lookup"><span data-stu-id="1892e-138">Start Server Manager.</span></span>

2. <span data-ttu-id="1892e-139">Kliknij przycisk **funkcje** , a następnie kliknij przycisk **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="1892e-139">Click **Features** and then click **Add Features**.</span></span>

3. <span data-ttu-id="1892e-140">Na stronie Wybieranie funkcji kliknij system Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="1892e-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

