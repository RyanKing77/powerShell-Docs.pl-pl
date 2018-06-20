---
ms.date: 08/23/2017
keywords: polecenia cmdlet programu PowerShell
title: Odinstalowywanie programu windows powershell web access
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952957"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="3ee1a-103">Odinstalowywanie programu Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="3ee1a-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="3ee1a-104">Zaktualizowano: 24 czerwca 2013</span><span class="sxs-lookup"><span data-stu-id="3ee1a-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="3ee1a-105">Dotyczy: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3ee1a-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="3ee1a-106">Kroki opisane w tym temacie Usuń witrynę sieci Web Windows PowerShell Web Access i odpowiednią aplikację z serwera bramy, w którym jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="3ee1a-107">Powiadom użytkowników</span><span class="sxs-lookup"><span data-stu-id="3ee1a-107">Notify users</span></span>

<span data-ttu-id="3ee1a-108">Przed rozpoczęciem należy powiadomić użytkowników konsoli internetowej o usunięciu witryny internetowej.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="3ee1a-109">Odinstalowywanie programu Windows PowerShell Web Access nie powoduje odinstalowania usług IIS lub innych funkcji, które zostały zainstalowane automatycznie, ponieważ program Windows PowerShell Web Access wymagane do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="3ee1a-110">Proces odinstalowywania pozostawia zainstalowane funkcje, na których był zależny; Windows PowerShell Web Access Funkcje te można odinstalować oddzielnie, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="3ee1a-111">Zalecana (szybka) dezinstalacja</span><span class="sxs-lookup"><span data-stu-id="3ee1a-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="3ee1a-112">Procedury przedstawione w tej sekcji ułatwiają odinstalowywanie zarówno:</span><span class="sxs-lookup"><span data-stu-id="3ee1a-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="3ee1a-113">Aplikacja sieci web programu Windows PowerShell Web Access, i</span><span class="sxs-lookup"><span data-stu-id="3ee1a-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="3ee1a-114">Funkcja Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="3ee1a-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="3ee1a-115">za pomocą poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="3ee1a-116">Krok 1: Usuwanie aplikacji sieci web przy użyciu poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="3ee1a-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="3ee1a-117">Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="3ee1a-118">Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **programu Windows PowerShell** na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="3ee1a-119">W systemie Windows **Start** kliknij **programu Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="3ee1a-120">Typ `Uninstall-PswaWebApplication`, a następnie naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="3ee1a-121">Jeśli masz określoną własną, niestandardową nazwę witryny internetowej, możesz dodać do polecenia parametr `-WebsiteName` i określić nazwę witryny internetowej.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="3ee1a-122">Jeśli używasz niestandardowej aplikacji sieci web (innej niż aplikacja domyślna, **pswa**, Dodaj `-WebApplicationName` parametru polecenia i określ nazwę aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="3ee1a-123">Jeśli używasz certyfikatu testowego, dodaj parametr `DeleteTestCertificate` do polecenia cmdlet, jak pokazano w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="3ee1a-124">Krok 2: Odinstalowywanie za pomocą poleceń cmdlet programu Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="3ee1a-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="3ee1a-125">Wykonaj jedną z następujących czynności, aby otworzyć sesję środowiska Windows PowerShell z podwyższonym poziomem uprawnień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="3ee1a-126">Jeśli sesja jest już otwarta, przejdź do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="3ee1a-127">Na pulpicie systemu Windows kliknij prawym przyciskiem myszy **środowiska Windows PowerShell** na pasku zadań, a następnie kliknij przycisk **Uruchom jako Administrator**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="3ee1a-128">W systemie Windows **Start** ekranu, kliknij prawym przyciskiem myszy **programu Windows PowerShell**, a następnie kliknij przycisk **Uruchom jako Administrator**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="3ee1a-129">Wpisz następujące polecenie, a następnie naciśnij klawisz **Enter**, gdzie *nazwa_komputera* reprezentuje serwer zdalny, z którego chcesz usunąć Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="3ee1a-130">Parametr `-Restart` powoduje automatyczne ponowne uruchomienie serwerów docelowych, jeśli jest to wymagane w związku z usunięciem składnika.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="3ee1a-131">Aby usunąć role i funkcje z dysku VHD trybu offline, należy dodać zarówno parametr `-ComputerName`, jak i parametr `-VHD`.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="3ee1a-132">Parametr `-ComputerName` zawiera nazwę serwera, na którym należy zainstalować dysk VHD, a parametr `-VHD` zawiera ścieżkę do pliku dysku VHD na określonym serwerze.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="3ee1a-133">Po zakończeniu operacji usunięcia Sprawdź, czy Windows PowerShell Web Access jest usunięte, otwierając **wszystkie serwery** strony w Menedżerze serwera, wybierając serwer, z którego usunięto funkcję i wyświetlając **ról i Funkcje** kafelka na stronie wybranego serwera.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="3ee1a-134">Można również uruchomić `Get-WindowsFeature` polecenia cmdlet docelowym będzie wybrany serwer (Get-WindowsFeature - ComputerName &lt; *nazwa_komputera*&gt;), aby wyświetlić listę ról i funkcji, które są zainstalowane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="3ee1a-135">Dezinstalacja niestandardowa</span><span class="sxs-lookup"><span data-stu-id="3ee1a-135">Custom uninstallation</span></span>

<span data-ttu-id="3ee1a-136">Procedury przedstawione w tej sekcji ułatwiają odinstalowywanie zarówno aplikacji sieci web programu Windows PowerShell Web Access i funkcji systemu Windows PowerShell Web Access za pomocą Usuń role i funkcje kreatora w Menedżerze serwera i konsoli Menedżera usług IIS.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="3ee1a-137">Krok 1: Usuwanie aplikacji sieci web przy użyciu Menedżera usług IIS</span><span class="sxs-lookup"><span data-stu-id="3ee1a-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="3ee1a-138">Otwórz konsolę Menedżera usług IIS, wykonując jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="3ee1a-139">Jeśli jest on już otwarty, przejdź do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="3ee1a-140">Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="3ee1a-141">Na **narzędzia** menu w Menedżerze serwera kliknij **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="3ee1a-142">W systemie Windows **Start** ekranu, wpisz dowolną część nazwy **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="3ee1a-143">Kliknij skrót jest wyświetlany w **aplikacji** wyników.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="3ee1a-144">W okienku drzewa Menedżera usług IIS wybierz witrynę internetową, która działa aplikacja sieci web programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="3ee1a-145">W **akcje** okienku w obszarze **Zarządzaj witryną internetową**, kliknij przycisk **zatrzymać**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="3ee1a-146">W okienku drzewa kliknij prawym przyciskiem myszy aplikację sieci web w witrynie sieci Web, na którym działa aplikacja sieci web programu Windows PowerShell Web Access, a następnie kliknij przycisk **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="3ee1a-147">W okienku drzewa wybierz **pul aplikacji**, wybierz folder puli aplikacji programu Windows PowerShell Web Access, kliknij przycisk **zatrzymać** w **akcje** okienka, a następnie kliknij przycisk  **Usuń** w okienku zawartości.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="3ee1a-148">Zamknij Menedżera usług IIS.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-148">Close IIS Manager.</span></span>

> <span data-ttu-id="3ee1a-149">![Uwaga ostrzeżenie](images/SecurityNote.jpeg)**Uwaga**:</span><span class="sxs-lookup"><span data-stu-id="3ee1a-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="3ee1a-150">Certyfikat nie jest usuwany podczas dezinstalacji.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="3ee1a-151">Jeśli chcesz usunąć utworzony przez Ciebie certyfikat z podpisem własnym lub używany certyfikat testowy, zrób to w Menedżerze usług IIS.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="3ee1a-152">Krok 2: Odinstalowywanie programu Windows PowerShell Web Access za pomocą usuwania ról i funkcji — Kreator</span><span class="sxs-lookup"><span data-stu-id="3ee1a-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="3ee1a-153">Jeśli Menedżer serwera jest już otwarty, przejdź do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="3ee1a-154">Jeśli Menedżer serwera nie jest już otwarty, otwórz go, wykonując jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="3ee1a-155">Na pulpicie systemu Windows, uruchom Menedżera serwera, klikając **Menedżera serwera** na pasku zadań systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="3ee1a-156">W systemie Windows **Start** kliknij **Menedżera serwera**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="3ee1a-157">Na **Zarządzaj** menu, kliknij przycisk **Usuń role i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="3ee1a-158">Na **serwera docelowego wybierz** wybierz serwer lub dysku VHD trybu offline, z którego chcesz usunąć funkcję.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="3ee1a-159">Aby wybrać dysk VHD trybu offline, najpierw wybierz serwer, na którym należy zainstalować dysk VHD, a następnie wybierz plik dysku VHD.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="3ee1a-160">Po wybraniu serwera docelowego kliknij **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="3ee1a-161">Kliknij przycisk **dalej** ponownie, aby przejść do **usuwanie funkcji** strony.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="3ee1a-162">Usuń zaznaczenie pola wyboru dla **programu Windows PowerShell Web Access**, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="3ee1a-163">Na **Potwierdzenie opcji usuwania** kliknij przycisk **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="3ee1a-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ee1a-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ee1a-164">See Also</span></span>

- [<span data-ttu-id="3ee1a-165">Zainstalować i używać programu Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="3ee1a-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="3ee1a-166">Pomoc Menedżera 7.0 usług IIS</span><span class="sxs-lookup"><span data-stu-id="3ee1a-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)