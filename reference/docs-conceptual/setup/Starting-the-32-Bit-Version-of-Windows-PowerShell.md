---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Uruchamianie 32-bitowej wersji programu Windows PowerShell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="6bedf-103">Uruchamianie 32-bitowej wersji programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6bedf-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="6bedf-104">Podczas instalowania programu Windows PowerShell na komputerze 64-bitowym **programu Windows PowerShell (x86)**, jest zainstalowany 32-bitowej wersji programu Windows PowerShell, oprócz wersji 64-bitowej.</span><span class="sxs-lookup"><span data-stu-id="6bedf-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="6bedf-105">Po uruchomieniu programu Windows PowerShell domyślnie uruchamia wersję 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="6bedf-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="6bedf-106">Jednak czasami konieczne może być uruchomienie **programu Windows PowerShell (x86)**, takie jak podczas korzystania z modułu, który wymaga 32-bitowej wersji lub podczas łączenia w zdalnie do komputera 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="6bedf-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="6bedf-107">Aby uruchomić 32-bitowej wersji programu Windows PowerShell, użyj dowolnej z następujących procedur.</span><span class="sxs-lookup"><span data-stu-id="6bedf-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="6bedf-108">W systemie Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6bedf-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="6bedf-109">Na **Start** ekranu, wpisz **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="6bedf-110">Kliknij przycisk **programu Windows PowerShell x86** kafelka.</span><span class="sxs-lookup"><span data-stu-id="6bedf-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="6bedf-111">W **Menedżera serwera**, z **narzędzia** menu, wybierz opcję **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="6bedf-112">Na pulpicie kliknij przycisk Ustaw kursor w prawym górnym rogu **wyszukiwania**, typ **PowerShell x86** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="6bedf-113">Za pomocą wiersza polecenia wpisz polecenie:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="6bedf-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="6bedf-114">W systemie Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="6bedf-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="6bedf-115">Na **Start** ekranu, wpisz **PowerShell** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="6bedf-116">W **Menedżera serwera**, z **narzędzia** menu, wybierz opcję **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="6bedf-117">Na pulpicie kliknij przycisk Ustaw kursor w prawym górnym rogu **wyszukiwania**, typ **PowerShell** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="6bedf-118">Za pomocą wiersza polecenia wpisz polecenie:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="6bedf-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="6bedf-119">W Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="6bedf-119">In Windows® 8.1</span></span>

- <span data-ttu-id="6bedf-120">Na **Start** ekranu, wpisz **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="6bedf-121">Kliknij przycisk **programu Windows PowerShell x86** kafelka.</span><span class="sxs-lookup"><span data-stu-id="6bedf-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="6bedf-122">Jeśli używasz [narzędzi administracji zdalnej serwera](http://go.microsoft.com/fwlink/?LinkID=304145) dla Windows 8.1, można również otworzyć programu Windows PowerShell x86 z **ManagerTools serwera** menu.</span><span class="sxs-lookup"><span data-stu-id="6bedf-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="6bedf-123">Wybierz **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="6bedf-124">Na pulpicie kliknij przycisk Ustaw kursor w prawym górnym rogu **wyszukiwania**, typ **PowerShell x86** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="6bedf-125">Za pomocą wiersza polecenia wpisz polecenie:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="6bedf-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="6bedf-126">W Windows® 8</span><span class="sxs-lookup"><span data-stu-id="6bedf-126">In Windows® 8</span></span>

- <span data-ttu-id="6bedf-127">Na **Start** ekranu, ustaw kursor w prawym górnym rogu kliknij pozycję **ustawienia**, kliknij przycisk **Kafelki**, a następnie przenieść **Pokaż narzędzia administracyjne** suwaka Yes (tak).</span><span class="sxs-lookup"><span data-stu-id="6bedf-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="6bedf-128">Następnie wpisz **PowerShell** i kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="6bedf-129">Jeśli używasz [narzędzi administracji zdalnej serwera](http://www.microsoft.com/download/details.aspx?id=28972) dla systemu Windows 8, można również otworzyć programu Windows PowerShell x86 z **ManagerTools serwera** menu.</span><span class="sxs-lookup"><span data-stu-id="6bedf-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="6bedf-130">Wybierz **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="6bedf-131">Na **Start** ekranu lub pulpit, wpisz **PowerShell (x86)** , a następnie kliknij przycisk **programu Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="6bedf-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="6bedf-132">Za pomocą wiersza polecenia wpisz polecenie:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="6bedf-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

