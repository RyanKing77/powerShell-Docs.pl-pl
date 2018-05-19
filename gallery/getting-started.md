---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Rozpoczynanie pracy z galerii programu PowerShell
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="6e020-103">Rozpoczynanie pracy z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e020-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="6e020-104">Pobieranie elementów z galerii programu PowerShell w systemie wymaga [PowerShellGet](/powershell/module/powershellget) modułu.</span><span class="sxs-lookup"><span data-stu-id="6e020-104">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="6e020-105">Moduł PowerShellGet można znaleźć w jednym z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="6e020-105">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="6e020-106">Nie trzeba zalogować się do pobierania elementów z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e020-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="6e020-107">Wykrywanie elementów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e020-107">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="6e020-108">Elementy można znaleźć w galerii programu PowerShell, za pomocą **wyszukiwania** formantu w tej witrynie sieci Web lub przechodząc na stronach moduły i skryptów.</span><span class="sxs-lookup"><span data-stu-id="6e020-108">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="6e020-109">Możesz również znaleźć elementów z galerii programu PowerShell, uruchamiając [Znajdź moduł][] i [skryptu Znajdź][] poleceń cmdlet, w zależności od typu elementu z `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="6e020-109">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="6e020-110">Filtrowanie wyników z galerii może odbywać się przy użyciu następujących parametrów:</span><span class="sxs-lookup"><span data-stu-id="6e020-110">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="6e020-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6e020-111">Name</span></span>
- <span data-ttu-id="6e020-112">AllVersions</span><span class="sxs-lookup"><span data-stu-id="6e020-112">AllVersions</span></span>
- <span data-ttu-id="6e020-113">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6e020-113">MinimumVersion</span></span>
- <span data-ttu-id="6e020-114">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6e020-114">RequiredVersion</span></span>
- <span data-ttu-id="6e020-115">Tag</span><span class="sxs-lookup"><span data-stu-id="6e020-115">Tag</span></span>
- <span data-ttu-id="6e020-116">Zawiera</span><span class="sxs-lookup"><span data-stu-id="6e020-116">Includes</span></span>
- <span data-ttu-id="6e020-117">DscResource</span><span class="sxs-lookup"><span data-stu-id="6e020-117">DscResource</span></span>
- <span data-ttu-id="6e020-118">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="6e020-118">RoleCapability</span></span>
- <span data-ttu-id="6e020-119">Polecenie</span><span class="sxs-lookup"><span data-stu-id="6e020-119">Command</span></span>
- <span data-ttu-id="6e020-120">Filtr</span><span class="sxs-lookup"><span data-stu-id="6e020-120">Filter</span></span>

<span data-ttu-id="6e020-121">Jeśli interesuje Cię tylko wykrywania określonych zasobów DSC w galerii, możesz uruchomić [DscResource Znajdź] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6e020-121">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="6e020-122">Znajdź DscResource zwraca dane na zasoby DSC zawarte w galerii.</span><span class="sxs-lookup"><span data-stu-id="6e020-122">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="6e020-123">Ponieważ DSC zasoby są zawsze dostarczane jako część modułu, nadal należy uruchomić [instalacji modułu][] do zainstalowania tych zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="6e020-123">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="6e020-124">Informacje o elementów w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e020-124">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="6e020-125">Po wyłaniają element, który chcesz, możesz uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6e020-125">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="6e020-126">Można to zrobić, sprawdzając określonej strony tego elementu w galerii.</span><span class="sxs-lookup"><span data-stu-id="6e020-126">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="6e020-127">Na tej stronie można wyświetlić wszystkie metadane przekazany do elementu.</span><span class="sxs-lookup"><span data-stu-id="6e020-127">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="6e020-128">Te metadane dla elementu jest zapewniana przez autora elementu i nie jest weryfikowany przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6e020-128">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="6e020-129">Właściciel elementu silnie jest powiązany z galerii konto używane do publikowania elementu i jest bardziej wiarygodny niż pole autora.</span><span class="sxs-lookup"><span data-stu-id="6e020-129">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="6e020-130">Jeśli uważasz, że element nie jest opublikowana w dobrej wierze, kliknij przycisk **zgłaszania nadużyć** na stronie tego elementu.</span><span class="sxs-lookup"><span data-stu-id="6e020-130">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="6e020-131">Jeśli korzystasz z [Znajdź moduł][] lub [skryptu Znajdź][], można wyświetlić te dane w zwrócony obiekt PSGetModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="6e020-131">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="6e020-132">Na przykład uruchomiona `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` zwraca dane dla modułu PSReadLine w galerii.</span><span class="sxs-lookup"><span data-stu-id="6e020-132">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="6e020-133">Pobieranie elementów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e020-133">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="6e020-134">Firma Microsoft zachęca następujący proces pobierania elementów z galerii programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6e020-134">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="6e020-135">Sprawdź</span><span class="sxs-lookup"><span data-stu-id="6e020-135">Inspect</span></span>

<span data-ttu-id="6e020-136">Aby pobrać elementu galerii do inspekcji, uruchom [moduł zapisywania][] lub [Zapisz skrypt][] polecenia cmdlet, w zależności od typu elementu.</span><span class="sxs-lookup"><span data-stu-id="6e020-136">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="6e020-137">Dzięki temu można zapisać elementu lokalnie bez instalowania go i sprawdzić zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="6e020-137">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="6e020-138">Pamiętaj, aby ręcznie usunąć element zapisany.</span><span class="sxs-lookup"><span data-stu-id="6e020-138">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="6e020-139">Niektóre z tych elementów są utworzone przez firmę Microsoft, a inne są tworzone przez społeczność programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e020-139">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="6e020-140">Firma Microsoft zaleca przejrzenie zawartość i kod elementów na tej galerii przed instalacją.</span><span class="sxs-lookup"><span data-stu-id="6e020-140">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="6e020-141">Jeśli uważasz, że element nie jest opublikowana w dobrej wierze, kliknij przycisk **zgłaszania nadużyć** na stronie tego elementu.</span><span class="sxs-lookup"><span data-stu-id="6e020-141">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="6e020-142">Instalowanie w klastrze zarządzania systemu</span><span class="sxs-lookup"><span data-stu-id="6e020-142">Install</span></span>

<span data-ttu-id="6e020-143">Aby zainstalować element galerii do użycia, uruchom [instalacji modułu][] lub [skrypt instalacji][] polecenia cmdlet, w zależności od typu elementu.</span><span class="sxs-lookup"><span data-stu-id="6e020-143">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="6e020-144">[instalacji modułu][] instaluje moduł `$env:ProgramFiles\WindowsPowerShell\Modules` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6e020-144">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="6e020-145">Wymaga to konto administratora.</span><span class="sxs-lookup"><span data-stu-id="6e020-145">This requires an administrator account.</span></span> <span data-ttu-id="6e020-146">Jeśli dodasz `-Scope CurrentUser` parametru moduł jest zainstalowany na `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="6e020-146">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="6e020-147">[skrypt instalacji][] instaluje skrypt `$env:ProgramFiles\WindowsPowerShell\Scripts` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6e020-147">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="6e020-148">Wymaga to konto administratora.</span><span class="sxs-lookup"><span data-stu-id="6e020-148">This requires an administrator account.</span></span> <span data-ttu-id="6e020-149">Jeśli dodasz `-Scope CurrentUser` parametru skryptu jest instalowana na `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="6e020-149">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="6e020-150">Domyślnie [instalacji modułu][] i [skrypt instalacji][] instaluje najnowszą wersję elementu.</span><span class="sxs-lookup"><span data-stu-id="6e020-150">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="6e020-151">Aby zainstalować starszą wersję elementu, Dodaj `-RequiredVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="6e020-151">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="6e020-152">Wdróż program</span><span class="sxs-lookup"><span data-stu-id="6e020-152">Deploy</span></span>

<span data-ttu-id="6e020-153">Aby wdrożyć element z galerii programu PowerShell do automatyzacji Azure, kliknij przycisk **Wdróż automatyzacji Azure** na stronie szczegółów.</span><span class="sxs-lookup"><span data-stu-id="6e020-153">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="6e020-154">Nastąpi przekierowanie do portalu zarządzania Azure, której użytkownik loguje się przy użyciu poświadczeń konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="6e020-154">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="6e020-155">Należy pamiętać, że wdrażanie elementy z zależnościami wdroży wszystkie zależności w automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="6e020-155">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="6e020-156">Przycisk "Wdrażanie na automatyzacji Azure" można wyłączyć, dodając **AzureAutomationNotSupported** tag do metadanych elementu.</span><span class="sxs-lookup"><span data-stu-id="6e020-156">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="6e020-157">Aby dowiedzieć się więcej na temat usługi Automatyzacja Azure, zobacz [usługi Automatyzacja Azure](/azure/automation) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="6e020-157">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="6e020-158">Aktualizowanie elementów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e020-158">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="6e020-159">Aby zaktualizować elementów z galerii programu PowerShell, uruchom [] [aktualizacji modułu] albo polecenia cmdlet [] [skrypt aktualizacji].</span><span class="sxs-lookup"><span data-stu-id="6e020-159">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="6e020-160">Uruchomienie bez żadnych dodatkowych parametrów [] [aktualizacji modułu] dokona próby uaktualnienia zainstalowany, uruchamiając każdy moduł [instalacji modułu][].</span><span class="sxs-lookup"><span data-stu-id="6e020-160">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="6e020-161">Aby selektywnie zaktualizować modułów, Dodaj `-Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="6e020-161">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="6e020-162">Podobnie, uruchomienie bez żadnych dodatkowych parametrów [] [skrypt aktualizacji] próbuje również zaktualizować każdego skryptu zainstalowany, uruchamiając [skrypt instalacji][].</span><span class="sxs-lookup"><span data-stu-id="6e020-162">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="6e020-163">Aby selektywnie zaktualizować skryptów, Dodaj `-Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="6e020-163">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="6e020-164">Elementy listy, które zainstalowano z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e020-164">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="6e020-165">Aby dowiedzieć się, które moduły mają zainstalowane z galerii programu PowerShell, uruchom [Get-InstalledModule][] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6e020-165">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="6e020-166">To polecenie wyświetla listę wszystkich modułów w systemie, które zostały zainstalowane bezpośrednio z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e020-166">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="6e020-167">Podobnie, aby dowiedzieć się, które skrypty zainstalowano z galerii programu PowerShell, uruchom [Get-InstalledScript][] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6e020-167">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="6e020-168">To polecenie wyświetla wszystkie skrypty w systemie zainstalowanych bezpośrednio z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e020-168">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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