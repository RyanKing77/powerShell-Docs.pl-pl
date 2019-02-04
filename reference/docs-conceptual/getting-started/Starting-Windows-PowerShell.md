---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Uruchamianie programu Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688322"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="e3469-103">Uruchamianie programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3469-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="e3469-104">Program PowerShell jest skryptów dll aparat, który jest osadzony na wielu hostach.</span><span class="sxs-lookup"><span data-stu-id="e3469-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="e3469-105">Najbardziej typowe hosta, który będzie uruchamiany są interaktywne wiersza polecenia PowerShell.exe i PowerShell_ISE.exe interaktywne środowisko obsługi skryptów.</span><span class="sxs-lookup"><span data-stu-id="e3469-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="e3469-106">Aby rozpocząć Windows PowerShell® w systemie Windows Server® 2012 R2, Windows 8.1, Windows Server 2012 i Windows 8, zobacz [typowe zadania zarządzania i nawigacja](https://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="e3469-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="e3469-107">Jak uruchomić program Windows PowerShell we wcześniejszych wersjach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e3469-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="e3469-108">W tej sekcji wyjaśniono, jak można uruchomić programu Windows PowerShell i Windows PowerShell zintegrowane Scripting Environment (ISE) na Windows® 7, Windows Server® 2008 R2 i Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="e3469-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="e3469-109">Wyjaśniono również sposób włączania opcjonalna funkcja w środowisku Windows PowerShell ISE w programie Windows PowerShell 2.0 w systemie Windows Server® 2008 R2 i Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="e3469-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="e3469-110">Użyj dowolnej z następujących metod można uruchomić zainstalowana wersja programu Windows PowerShell 3.0 lub Windows PowerShell 4.0, jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="e3469-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="e3469-111">Z Start Menu</span><span class="sxs-lookup"><span data-stu-id="e3469-111">From the Start Menu</span></span>

- <span data-ttu-id="e3469-112">Kliknij przycisk **Start**, typ **PowerShell**, a następnie kliknij przycisk **programu Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e3469-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="e3469-113">Z **Start** menu, kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij przycisk **programu Windows PowerShell**  folder, a następnie kliknij **programu Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e3469-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="e3469-114">W wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="e3469-114">At the Command Prompt</span></span>

<span data-ttu-id="e3469-115">Cmd.exe, programu Windows PowerShell lub programu Windows PowerShell ISE Aby uruchomić program Windows PowerShell, wpisz:</span><span class="sxs-lookup"><span data-stu-id="e3469-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="e3469-116">Można również użyć parametrów PowerShell.exe program do dostosowywania sesji.</span><span class="sxs-lookup"><span data-stu-id="e3469-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="e3469-117">Aby uzyskać więcej informacji, zobacz [Pomoc wiersza polecenia PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="e3469-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="e3469-118">Za pomocą administracyjne uprawnień ("Uruchom jako administrator")</span><span class="sxs-lookup"><span data-stu-id="e3469-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="e3469-119">Kliknij przycisk **Start**, typ **PowerShell**, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="e3469-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="e3469-120">Jak uruchomić program Windows PowerShell ISE we wcześniejszych wersjach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e3469-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="e3469-121">Użyj dowolnej z następujących metod, aby uruchomić program Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e3469-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="e3469-122">Z Start Menu</span><span class="sxs-lookup"><span data-stu-id="e3469-122">From the Start Menu</span></span>

- <span data-ttu-id="e3469-123">Kliknij przycisk **Start**, typ **ISE**, a następnie kliknij przycisk **środowiska Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="e3469-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="e3469-124">Z **Start** menu, kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij przycisk **programu Windows PowerShell**  folder, a następnie kliknij **środowiska Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="e3469-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="e3469-125">W wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="e3469-125">At the Command Prompt</span></span>

<span data-ttu-id="e3469-126">Cmd.exe, programu Windows PowerShell lub programu Windows PowerShell ISE Aby uruchomić program Windows PowerShell, wpisz:</span><span class="sxs-lookup"><span data-stu-id="e3469-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="e3469-127">lub</span><span class="sxs-lookup"><span data-stu-id="e3469-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="e3469-128">Za pomocą administracyjne uprawnień ("Uruchom jako administrator")</span><span class="sxs-lookup"><span data-stu-id="e3469-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="e3469-129">Kliknij przycisk **Start**, typ **ISE**, kliknij prawym przyciskiem myszy **środowiska Windows PowerShell ISE**, a następnie kliknij przycisk **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="e3469-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="e3469-130">Włączania środowiska Windows PowerShell ISE we wcześniejszych wersjach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e3469-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="e3469-131">W programie Windows PowerShell 4.0 i programu Windows PowerShell 3.0 program Windows PowerShell ISE jest domyślnie włączona, we wszystkich wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e3469-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="e3469-132">Jeśli nie jest już włączony, Windows Management Framework 4.0 lub Windows Management Framework 3.0 włączy ją.</span><span class="sxs-lookup"><span data-stu-id="e3469-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="e3469-133">W programie Windows PowerShell 2.0 programu Windows PowerShell ISE jest włączona domyślnie w systemie Windows 7.</span><span class="sxs-lookup"><span data-stu-id="e3469-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="e3469-134">Jednak w systemie Windows Server 2008 R2 i Windows Server 2008 to opcjonalna funkcja.</span><span class="sxs-lookup"><span data-stu-id="e3469-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="e3469-135">Aby włączyć program Windows PowerShell ISE w programie Windows PowerShell 2.0 w systemie Windows Server 2008 R2 lub Windows Server 2008, należy użyć następującej procedury.</span><span class="sxs-lookup"><span data-stu-id="e3469-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="e3469-136">Aby włączyć Windows PowerShell zintegrowane Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="e3469-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="e3469-137">Uruchom Menedżera serwera.</span><span class="sxs-lookup"><span data-stu-id="e3469-137">Start Server Manager.</span></span>
2. <span data-ttu-id="e3469-138">Kliknij przycisk **funkcji** a następnie kliknij przycisk **Dodaj funkcje**.</span><span class="sxs-lookup"><span data-stu-id="e3469-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="e3469-139">Na stronie Wybieranie funkcji kliknij Windows PowerShell zintegrowane Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="e3469-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="e3469-140">Uruchamianie 32-bitowej wersji programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3469-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="e3469-141">Po zainstalowaniu programu Windows PowerShell na komputerze 64-bitowych **programu Windows PowerShell (x86)**, 32-bitowej wersji programu Windows PowerShell jest zainstalowany, oprócz wersji 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="e3469-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="e3469-142">Po uruchomieniu programu Windows PowerShell, domyślnie uruchamia wersję 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="e3469-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="e3469-143">Jednak czasami konieczne może być uruchomienie **programu Windows PowerShell (x86)**, takie jak podczas korzystania z modułu, która wymaga 32-bitowej wersji lub nawiązywania połączenia zdalnego na komputerze 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="e3469-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="e3469-144">Aby rozpocząć 32-bitowej wersji programu Windows PowerShell, użyj dowolnej z następujących procedur.</span><span class="sxs-lookup"><span data-stu-id="e3469-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="e3469-145">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e3469-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="e3469-146">Na **Start** ekranu, wpisz **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="e3469-147">Kliknij przycisk **programu Windows PowerShell x86** kafelka.</span><span class="sxs-lookup"><span data-stu-id="e3469-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="e3469-148">W **Menedżera serwera**, z **narzędzia** menu, wybierz opcję **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-149">Na pulpicie, ustaw kursor w prawym górnym rogu kliknij **wyszukiwania**, typ **PowerShell x86** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-150">Za pomocą wiersza polecenia wpisz: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e3469-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="e3469-151">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="e3469-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="e3469-152">Na **Start** ekranu, wpisz **PowerShell** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-153">W **Menedżera serwera**, z **narzędzia** menu, wybierz opcję **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-154">Na pulpicie, ustaw kursor w prawym górnym rogu kliknij **wyszukiwania**, typ **PowerShell** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-155">Za pomocą wiersza polecenia wpisz: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e3469-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="e3469-156">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="e3469-156">In Windows® 8.1</span></span>

- <span data-ttu-id="e3469-157">Na **Start** ekranu, wpisz **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="e3469-158">Kliknij przycisk **programu Windows PowerShell x86** kafelka.</span><span class="sxs-lookup"><span data-stu-id="e3469-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="e3469-159">Jeśli używasz [narzędzia administracji zdalnej serwera](https://go.microsoft.com/fwlink/?LinkID=304145) dla Windows 8.1, możesz również otworzyć program Windows PowerShell x86 z **ManagerTools serwera** menu.</span><span class="sxs-lookup"><span data-stu-id="e3469-159">If you are running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="e3469-160">Wybierz **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-161">Na pulpicie, ustaw kursor w prawym górnym rogu kliknij **wyszukiwania**, typ **PowerShell x86** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-162">Za pomocą wiersza polecenia wpisz: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e3469-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="e3469-163">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="e3469-163">In Windows® 8</span></span>

- <span data-ttu-id="e3469-164">Na **Start** ekranu, ustaw kursor w prawym górnym rogu, kliknij przycisk **ustawienia**, kliknij przycisk **Kafelki**, a następnie przenieść **Pokaż narzędzia administracyjne** suwaka Yes (tak).</span><span class="sxs-lookup"><span data-stu-id="e3469-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="e3469-165">Następnie wpisz **PowerShell** i kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-166">Jeśli używasz [narzędzia administracji zdalnej serwera](https://www.microsoft.com/download/details.aspx?id=28972) dla systemu Windows 8, można również otworzyć program Windows PowerShell x86 z **ManagerTools serwera** menu.</span><span class="sxs-lookup"><span data-stu-id="e3469-166">If you are running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="e3469-167">Wybierz **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-168">Na **Start** ekranu lub pulpit, wpisz **PowerShell (x86)** a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e3469-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e3469-169">Za pomocą wiersza polecenia wpisz: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e3469-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>