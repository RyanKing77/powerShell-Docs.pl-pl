---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Rozpoczynanie pracy z galerii programu PowerShell
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523060"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="896de-103">Rozpoczynanie pracy z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="896de-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="896de-104">Prawidłowego sposobu instalowanie elementów z galerii programu PowerShell jest użycie polecenia cmdlet w [PowerShellGet](/powershell/module/powershellget) modułu.</span><span class="sxs-lookup"><span data-stu-id="896de-104">The proper way to install items from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="896de-105">Nie musisz zalogować się do pobierania elementów z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="896de-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="896de-106">Istnieje możliwość pobrania pakietu z galerii programu PowerShell bezpośrednio, ale nie jest to zalecane podejście.</span><span class="sxs-lookup"><span data-stu-id="896de-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span> <span data-ttu-id="896de-107">Aby uzyskać więcej informacji, zobacz [Pobieranie pakietu ręczne](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span><span class="sxs-lookup"><span data-stu-id="896de-107">For more details, see [Manual Package Download](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span></span>  


## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="896de-108">Odnajdywanie elementów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="896de-108">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="896de-109">Elementy w galerii programu PowerShell można znaleźć przy użyciu **wyszukiwania** kontroli w tej witrynie internetowej lub przeglądania stron modułów i skryptów.</span><span class="sxs-lookup"><span data-stu-id="896de-109">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="896de-110">Możesz również znaleźć elementów z galerii programu PowerShell, uruchamiając [Find-Module][] i [Find-Script][] poleceń cmdlet, w zależności od typu elementu z `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="896de-110">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="896de-111">Filtrowanie wyników za pomocą galerii może odbywać się przy użyciu następujących parametrów:</span><span class="sxs-lookup"><span data-stu-id="896de-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="896de-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="896de-112">Name</span></span>
- <span data-ttu-id="896de-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="896de-113">AllVersions</span></span>
- <span data-ttu-id="896de-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="896de-114">MinimumVersion</span></span>
- <span data-ttu-id="896de-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="896de-115">RequiredVersion</span></span>
- <span data-ttu-id="896de-116">Tag</span><span class="sxs-lookup"><span data-stu-id="896de-116">Tag</span></span>
- <span data-ttu-id="896de-117">Zawiera</span><span class="sxs-lookup"><span data-stu-id="896de-117">Includes</span></span>
- <span data-ttu-id="896de-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="896de-118">DscResource</span></span>
- <span data-ttu-id="896de-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="896de-119">RoleCapability</span></span>
- <span data-ttu-id="896de-120">Polecenie</span><span class="sxs-lookup"><span data-stu-id="896de-120">Command</span></span>
- <span data-ttu-id="896de-121">Filtr</span><span class="sxs-lookup"><span data-stu-id="896de-121">Filter</span></span>

<span data-ttu-id="896de-122">Jeśli interesuje Cię tylko odnajdywanie określone zasoby DSC w galerii, możesz uruchomić [Find-DscResource] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="896de-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="896de-123">Znajdź-DscResource zwraca dane dla zasobów DSC znajdujących się w galerii.</span><span class="sxs-lookup"><span data-stu-id="896de-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="896de-124">Ponieważ zasoby DSC zawsze są dostarczane jako część modułu, nadal musisz uruchomić [Install-Module][] do zainstalowania tych zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="896de-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="896de-125">Zapoznawanie się elementy w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="896de-125">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="896de-126">Po zidentyfikowaniu element, który chcesz wziąć można dowiedzieć się więcej na ten temat.</span><span class="sxs-lookup"><span data-stu-id="896de-126">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="896de-127">Można to zrobić, sprawdzając określonej strony tego elementu w galerii.</span><span class="sxs-lookup"><span data-stu-id="896de-127">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="896de-128">Na tej stronie można będzie wyświetlić wszystkie metadane zostały przesłane z elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-128">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="896de-129">Te metadane dla elementu są dostarczane przez autora elementu, a nie został zweryfikowany przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="896de-129">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="896de-130">Właścicielem przedmiotu zdecydowanie jest powiązany z galerii konto używane do publikowania elementu i jest bardziej wiarygodne niż pola Autor.</span><span class="sxs-lookup"><span data-stu-id="896de-130">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="896de-131">Jeśli uważasz, że element nie został opublikowany w dobrej wierze, kliknij przycisk **Zgłoś nadużycie** na stronie tego elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-131">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="896de-132">Jeśli korzystasz z [Find-Module][] lub [Find-Script][], dane te można wyświetlić w zwracany obiekt PSGetModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="896de-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="896de-133">Na przykład uruchomiony `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="896de-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="896de-134">Zwraca dane na temat modułu PSReadLine w galerii.</span><span class="sxs-lookup"><span data-stu-id="896de-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="896de-135">Pobieranie elementów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="896de-135">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="896de-136">Firma Microsoft zachęca następującego procesu podczas pobierania elementów z galerii programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="896de-136">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="896de-137">Sprawdzanie</span><span class="sxs-lookup"><span data-stu-id="896de-137">Inspect</span></span>

<span data-ttu-id="896de-138">Aby pobrać element z galerii w celu przeprowadzenia inspekcji, uruchom [Save-Module][] lub [Save-Script][] polecenia cmdlet, w zależności od typu elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-138">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="896de-139">Dzięki temu można zapisać elementu lokalnie bez instalowania i sprawdź zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-139">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="896de-140">Pamiętaj, aby ręcznie usunąć zapisanego elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-140">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="896de-141">Niektóre z tych elementów są tworzone przez firmę Microsoft, a inne są tworzone przez społeczność użytkowników programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="896de-141">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="896de-142">Firma Microsoft zaleca przejrzenie treści i kodu elementy w tej galerii, przed instalacją.</span><span class="sxs-lookup"><span data-stu-id="896de-142">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="896de-143">Jeśli uważasz, że element nie został opublikowany w dobrej wierze, kliknij przycisk **Zgłoś nadużycie** na stronie tego elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-143">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="896de-144">Instalowanie w klastrze zarządzania systemu</span><span class="sxs-lookup"><span data-stu-id="896de-144">Install</span></span>

<span data-ttu-id="896de-145">Aby zainstalować elementu galerii do użycia, uruchom [Install-Module][] lub [Install-Script][] polecenia cmdlet, w zależności od typu elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-145">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="896de-146">[Install-Module][] instaluje moduł do `$env:ProgramFiles\WindowsPowerShell\Modules` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="896de-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="896de-147">Wymaga to konto administratora.</span><span class="sxs-lookup"><span data-stu-id="896de-147">This requires an administrator account.</span></span> <span data-ttu-id="896de-148">Jeśli dodasz `-Scope CurrentUser` parametru moduł jest zainstalowany na `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="896de-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="896de-149">[Install-Script][] instaluje skrypt, aby `$env:ProgramFiles\WindowsPowerShell\Scripts` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="896de-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="896de-150">Wymaga to konto administratora.</span><span class="sxs-lookup"><span data-stu-id="896de-150">This requires an administrator account.</span></span> <span data-ttu-id="896de-151">Jeśli dodasz `-Scope CurrentUser` parametru skryptu jest instalowana na `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="896de-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="896de-152">Domyślnie [Install-Module][] i [Install-Script][] instaluje najnowszą wersję elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="896de-153">Aby zainstalować starszą wersję elementu, należy dodać `-RequiredVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="896de-153">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="896de-154">Wdróż program</span><span class="sxs-lookup"><span data-stu-id="896de-154">Deploy</span></span>

<span data-ttu-id="896de-155">Aby wdrożyć element z galerii programu PowerShell w usłudze Azure Automation, kliknij **wdrażanie w usłudze Azure Automation** na stronie szczegółów elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-155">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="896de-156">Nastąpi przekierowanie do portalu zarządzania systemu Azure, w którym możesz logować się przy użyciu poświadczeń konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="896de-156">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="896de-157">Należy pamiętać, że wdrażanie elementy z zależnościami wdroży wszystkie zależności do usługi Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="896de-157">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="896de-158">Można wyłączyć przez dodanie przycisku "Wdroż do usługi Azure Automation" **AzureAutomationNotSupported** tagu metadanych elementu.</span><span class="sxs-lookup"><span data-stu-id="896de-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="896de-159">Aby dowiedzieć się więcej o usłudze Azure Automation, zobacz [usługi Azure Automation](/azure/automation) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="896de-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="896de-160">Aktualizowanie elementów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="896de-160">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="896de-161">Aby zaktualizować elementów zainstalowany z galerii programu PowerShell, uruchom [Update-Module] [] lub polecenia cmdlet [] [skrypt aktualizacji].</span><span class="sxs-lookup"><span data-stu-id="896de-161">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="896de-162">Po uruchomieniu bez żadnych dodatkowych parametrów [] [Update-Module] próby uaktualnienia każdy moduł zainstalowane, uruchamiając [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="896de-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="896de-163">Aby selektywnie aktualizowanie modułów, należy dodać `-Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="896de-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="896de-164">Podobnie, gdy są uruchomione bez żadnych dodatkowych parametrów, [] [skrypt aktualizacji] również próby uaktualnienia każdego skryptu zainstalowane, uruchamiając [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="896de-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="896de-165">Aby selektywnie zaktualizować skrypty, Dodaj `-Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="896de-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="896de-166">Elementy listy, które zostały zainstalowane z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="896de-166">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="896de-167">Aby dowiedzieć się, które moduły mają zainstalowany z galerii programu PowerShell, uruchom [Get-InstalledModule][] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="896de-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="896de-168">To polecenie wyświetla wszystkie moduły, które znajdują się w systemie i zainstalowanych bezpośrednio z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="896de-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="896de-169">Podobnie, aby dowiedzieć się, skrypty, które mają zainstalowany z galerii programu PowerShell, uruchom [Get-InstalledScript][] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="896de-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="896de-170">To polecenie wyświetla wszystkie skrypty, które znajdują się w systemie i zainstalowanych bezpośrednio z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="896de-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script