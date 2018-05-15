---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: c3aafe9e76eda9acdd4787f63dc0f8c71a20d02a
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="e583e-103">Rozpoczynanie pracy z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e583e-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="e583e-104">Pobieranie elementów z galerii programu PowerShell w systemie wymaga [PowerShellGet](/powershell/module/powershellget) modułu.</span><span class="sxs-lookup"><span data-stu-id="e583e-104">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="e583e-105">Moduł PowerShellGet można znaleźć w jednym z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="e583e-105">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="e583e-106">Nie trzeba zalogować się do pobierania elementów z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e583e-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="e583e-107">Wykrywanie elementów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e583e-107">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="e583e-108">Elementy można znaleźć w galerii programu PowerShell, za pomocą **wyszukiwania** formantu w tej witrynie sieci Web lub przechodząc na stronach moduły i skryptów.</span><span class="sxs-lookup"><span data-stu-id="e583e-108">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="e583e-109">Możesz również znaleźć elementów z galerii programu PowerShell, uruchamiając [Znajdź moduł][] i [skryptu Znajdź][] poleceń cmdlet, w zależności od typu elementu z `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="e583e-109">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="e583e-110">Filtrowanie wyników z galerii może odbywać się przy użyciu następujących parametrów:</span><span class="sxs-lookup"><span data-stu-id="e583e-110">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="e583e-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e583e-111">Name</span></span>
- <span data-ttu-id="e583e-112">AllVersions</span><span class="sxs-lookup"><span data-stu-id="e583e-112">AllVersions</span></span>
- <span data-ttu-id="e583e-113">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e583e-113">MinimumVersion</span></span>
- <span data-ttu-id="e583e-114">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e583e-114">RequiredVersion</span></span>
- <span data-ttu-id="e583e-115">Tag</span><span class="sxs-lookup"><span data-stu-id="e583e-115">Tag</span></span>
- <span data-ttu-id="e583e-116">Zawiera</span><span class="sxs-lookup"><span data-stu-id="e583e-116">Includes</span></span>
- <span data-ttu-id="e583e-117">DscResource</span><span class="sxs-lookup"><span data-stu-id="e583e-117">DscResource</span></span>
- <span data-ttu-id="e583e-118">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e583e-118">RoleCapability</span></span>
- <span data-ttu-id="e583e-119">Polecenie</span><span class="sxs-lookup"><span data-stu-id="e583e-119">Command</span></span>
- <span data-ttu-id="e583e-120">Filtr</span><span class="sxs-lookup"><span data-stu-id="e583e-120">Filter</span></span>

<span data-ttu-id="e583e-121">Jeśli interesuje Cię tylko wykrywania określonych zasobów DSC w galerii, możesz uruchomić [DscResource Znajdź] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e583e-121">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="e583e-122">Znajdź DscResource zwraca dane na zasoby DSC zawarte w galerii.</span><span class="sxs-lookup"><span data-stu-id="e583e-122">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="e583e-123">Ponieważ DSC zasoby są zawsze dostarczane jako część modułu, nadal należy uruchomić [instalacji modułu][] do zainstalowania tych zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="e583e-123">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="e583e-124">Informacje o elementów w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e583e-124">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="e583e-125">Po wyłaniają element, który chcesz, możesz uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="e583e-125">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="e583e-126">Można to zrobić, sprawdzając określonej strony tego elementu w galerii.</span><span class="sxs-lookup"><span data-stu-id="e583e-126">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="e583e-127">Na tej stronie można wyświetlić wszystkie metadane przekazany do elementu.</span><span class="sxs-lookup"><span data-stu-id="e583e-127">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="e583e-128">Te metadane dla elementu jest zapewniana przez autora elementu i nie jest weryfikowany przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e583e-128">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="e583e-129">Właściciel elementu silnie jest powiązany z galerii konto używane do publikowania elementu i jest bardziej wiarygodny niż pole autora.</span><span class="sxs-lookup"><span data-stu-id="e583e-129">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="e583e-130">Jeśli uważasz, że element nie jest opublikowana w dobrej wierze, kliknij przycisk **zgłaszania nadużyć** na stronie tego elementu.</span><span class="sxs-lookup"><span data-stu-id="e583e-130">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="e583e-131">Jeśli korzystasz z [Znajdź moduł][] lub [skryptu Znajdź][], można wyświetlić te dane w zwrócony obiekt PSGetModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="e583e-131">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="e583e-132">Na przykład uruchomiona `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` zwraca dane dla modułu PSReadLine w galerii.</span><span class="sxs-lookup"><span data-stu-id="e583e-132">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="e583e-133">Pobieranie elementów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e583e-133">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="e583e-134">Firma Microsoft zachęca następujący proces pobierania elementów z galerii programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e583e-134">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="e583e-135">Sprawdź</span><span class="sxs-lookup"><span data-stu-id="e583e-135">Inspect</span></span>

<span data-ttu-id="e583e-136">Aby pobrać elementu galerii do inspekcji, uruchom [moduł zapisywania][] lub [Zapisz skrypt][] polecenia cmdlet, w zależności od typu elementu.</span><span class="sxs-lookup"><span data-stu-id="e583e-136">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="e583e-137">Dzięki temu można zapisać elementu lokalnie bez instalowania go i sprawdzić zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="e583e-137">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="e583e-138">Pamiętaj, aby ręcznie usunąć element zapisany.</span><span class="sxs-lookup"><span data-stu-id="e583e-138">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="e583e-139">Niektóre z tych elementów są utworzone przez firmę Microsoft, a inne są tworzone przez społeczność programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e583e-139">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="e583e-140">Firma Microsoft zaleca przejrzenie zawartość i kod elementów na tej galerii przed instalacją.</span><span class="sxs-lookup"><span data-stu-id="e583e-140">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="e583e-141">Jeśli uważasz, że element nie jest opublikowana w dobrej wierze, kliknij przycisk **zgłaszania nadużyć** na stronie tego elementu.</span><span class="sxs-lookup"><span data-stu-id="e583e-141">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="e583e-142">Instalowanie w klastrze zarządzania systemu</span><span class="sxs-lookup"><span data-stu-id="e583e-142">Install</span></span>

<span data-ttu-id="e583e-143">Aby zainstalować element galerii do użycia, uruchom [instalacji modułu][] lub [skrypt instalacji][] polecenia cmdlet, w zależności od typu elementu.</span><span class="sxs-lookup"><span data-stu-id="e583e-143">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="e583e-144">[instalacji modułu][] instaluje moduł `$env:ProgramFiles\WindowsPowerShell\Modules` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e583e-144">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="e583e-145">Wymaga to konto administratora.</span><span class="sxs-lookup"><span data-stu-id="e583e-145">This requires an administrator account.</span></span> <span data-ttu-id="e583e-146">Jeśli dodasz `-Scope CurrentUser` parametru moduł jest zainstalowany na `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="e583e-146">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="e583e-147">[skrypt instalacji][] instaluje skrypt `$env:ProgramFiles\WindowsPowerShell\Scripts` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e583e-147">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="e583e-148">Wymaga to konto administratora.</span><span class="sxs-lookup"><span data-stu-id="e583e-148">This requires an administrator account.</span></span> <span data-ttu-id="e583e-149">Jeśli dodasz `-Scope CurrentUser` parametru skryptu jest instalowana na `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="e583e-149">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="e583e-150">Domyślnie [instalacji modułu][] i [skrypt instalacji][] instaluje najnowszą wersję elementu.</span><span class="sxs-lookup"><span data-stu-id="e583e-150">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="e583e-151">Aby zainstalować starszą wersję elementu, Dodaj `-RequiredVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="e583e-151">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="e583e-152">Wdróż program</span><span class="sxs-lookup"><span data-stu-id="e583e-152">Deploy</span></span>

<span data-ttu-id="e583e-153">Aby wdrożyć element z galerii programu PowerShell do automatyzacji Azure, kliknij przycisk **Wdróż automatyzacji Azure** na stronie szczegółów.</span><span class="sxs-lookup"><span data-stu-id="e583e-153">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="e583e-154">Nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="e583e-154">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="e583e-155">Należy pamiętać, że wdrażanie elementy z zależnościami wdroży wszystkie zależności w automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="e583e-155">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="e583e-156">Przycisk "Wdrażanie na automatyzacji Azure" można wyłączyć, dodając **AzureAutomationNotSupported** tag do metadanych elementu.</span><span class="sxs-lookup"><span data-stu-id="e583e-156">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="e583e-157">Aby dowiedzieć się więcej na temat usługi Automatyzacja Azure, zobacz [usługi Automatyzacja Azure](/azure/automation) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="e583e-157">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="e583e-158">Aktualizowanie elementów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e583e-158">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="e583e-159">Aby zaktualizować elementów z galerii programu PowerShell, uruchom [] [aktualizacji modułu] albo polecenia cmdlet [] [skrypt aktualizacji].</span><span class="sxs-lookup"><span data-stu-id="e583e-159">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="e583e-160">Uruchomienie bez żadnych dodatkowych parametrów [] [aktualizacji modułu] dokona próby uaktualnienia zainstalowany, uruchamiając każdy moduł [instalacji modułu][].</span><span class="sxs-lookup"><span data-stu-id="e583e-160">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="e583e-161">Aby selektywnie zaktualizować modułów, Dodaj `-Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="e583e-161">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="e583e-162">Podobnie, uruchomienie bez żadnych dodatkowych parametrów [] [skrypt aktualizacji] próbuje również zaktualizować każdego skryptu zainstalowany, uruchamiając [skrypt instalacji][].</span><span class="sxs-lookup"><span data-stu-id="e583e-162">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="e583e-163">Aby selektywnie zaktualizować skryptów, Dodaj `-Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="e583e-163">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="e583e-164">Elementy listy, które zainstalowano z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e583e-164">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="e583e-165">Aby dowiedzieć się, które moduły mają zainstalowane z galerii programu PowerShell, uruchom [Get-InstalledModule][] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e583e-165">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="e583e-166">To polecenie wyświetla listę wszystkich modułów w systemie, które zostały zainstalowane bezpośrednio z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e583e-166">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="e583e-167">Podobnie, aby dowiedzieć się, które skrypty zainstalowano z galerii programu PowerShell, uruchom [Get-InstalledScript][] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e583e-167">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="e583e-168">To polecenie wyświetla wszystkie skrypty w systemie zainstalowanych bezpośrednio z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e583e-168">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[DscResource Znajdź]: /powershell/module/powershellget/Find-DscResource
[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Znajdź moduł]: /powershell/module/powershellget/Find-Module
[Find-Module]: /powershell/module/powershellget/Find-Module
[skryptu Znajdź]: /powershell/module/powershellget/Find-Script
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[instalacji modułu]: /powershell/module/powershellget/Install-Module
[Install-Module]: /powershell/module/powershellget/Install-Module
[skrypt instalacji]: /powershell/module/powershellget/Install-Script
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[moduł zapisywania]: /powershell/module/powershellget/Save-Module
[Save-Module]: /powershell/module/powershellget/Save-Module
[Zapisz skrypt]: /powershell/module/powershellget/Save-Script
[Save-Script]: /powershell/module/powershellget/Save-Script