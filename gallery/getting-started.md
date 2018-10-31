---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Rozpoczynanie pracy z galerii programu PowerShell
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225679"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="e4749-103">Rozpoczęcie korzystania z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4749-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="e4749-104">Właściwy sposób, aby zainstalować pakiety z galerii programu PowerShell jest użycie polecenia cmdlet w [PowerShellGet](/powershell/module/powershellget) modułu.</span><span class="sxs-lookup"><span data-stu-id="e4749-104">The proper way to install packages from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="e4749-105">Nie musisz zalogować się do pobierania elementów z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4749-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="e4749-106">Istnieje możliwość pobrania pakietu z galerii programu PowerShell bezpośrednio, ale nie jest to zalecane podejście.</span><span class="sxs-lookup"><span data-stu-id="e4749-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="e4749-107">Aby uzyskać więcej informacji, zobacz [Pobieranie pakietu ręczne](/powershell/gallery/how-to/working-with-packages/manual-download).</span><span class="sxs-lookup"><span data-stu-id="e4749-107">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="e4749-108">Wykrywanie pakietów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4749-108">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="e4749-109">Pakietów można znaleźć w galerii programu PowerShell, za pomocą **wyszukiwania** kontroli w tej witrynie internetowej lub przeglądania stron modułów i skryptów.</span><span class="sxs-lookup"><span data-stu-id="e4749-109">You can find packages in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="e4749-110">Można również wyszukiwać pakiety z galerii programu PowerShell, uruchamiając [Find-Module][] i [Find-Script][] poleceń cmdlet, w zależności od typu elementu z `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="e4749-110">You can also find packages from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="e4749-111">Filtrowanie wyników za pomocą galerii może odbywać się przy użyciu następujących parametrów:</span><span class="sxs-lookup"><span data-stu-id="e4749-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="e4749-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e4749-112">Name</span></span>
- <span data-ttu-id="e4749-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="e4749-113">AllVersions</span></span>
- <span data-ttu-id="e4749-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e4749-114">MinimumVersion</span></span>
- <span data-ttu-id="e4749-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e4749-115">RequiredVersion</span></span>
- <span data-ttu-id="e4749-116">Tag</span><span class="sxs-lookup"><span data-stu-id="e4749-116">Tag</span></span>
- <span data-ttu-id="e4749-117">Zawiera</span><span class="sxs-lookup"><span data-stu-id="e4749-117">Includes</span></span>
- <span data-ttu-id="e4749-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="e4749-118">DscResource</span></span>
- <span data-ttu-id="e4749-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e4749-119">RoleCapability</span></span>
- <span data-ttu-id="e4749-120">Polecenie</span><span class="sxs-lookup"><span data-stu-id="e4749-120">Command</span></span>
- <span data-ttu-id="e4749-121">Filtr</span><span class="sxs-lookup"><span data-stu-id="e4749-121">Filter</span></span>

<span data-ttu-id="e4749-122">Jeśli interesuje Cię tylko odnajdywanie określone zasoby DSC w galerii, możesz uruchomić [Find-DscResource] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4749-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="e4749-123">Znajdź-DscResource zwraca dane dla zasobów DSC znajdujących się w galerii.</span><span class="sxs-lookup"><span data-stu-id="e4749-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="e4749-124">Ponieważ zasoby DSC zawsze są dostarczane jako część modułu, nadal musisz uruchomić [Install-Module][] do zainstalowania tych zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="e4749-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="e4749-125">Informacje o pakietach w galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4749-125">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="e4749-126">Po zidentyfikowaniu pakietu, który chcesz wziąć można dowiedzieć się więcej na ten temat.</span><span class="sxs-lookup"><span data-stu-id="e4749-126">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="e4749-127">Można to zrobić, sprawdzając tego pakietu w określonej strony w galerii.</span><span class="sxs-lookup"><span data-stu-id="e4749-127">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="e4749-128">Na tej stronie można będzie wyświetlić wszystkie metadane zostały przesłane z pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-128">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="e4749-129">Te metadane są dostarczane przez autora pakietu, a nie został zweryfikowany przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e4749-129">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="e4749-130">Właściciel pakietu jest ściśle powiązane konto galerii, używane do opublikowania pakietu i jest bardziej wiarygodne niż pola Autor.</span><span class="sxs-lookup"><span data-stu-id="e4749-130">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="e4749-131">Jeśli użytkownik zauważy, pakietów, które uważasz, że nie został opublikowany w dobrej wierze, kliknij przycisk **Zgłoś nadużycie** na stronie tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-131">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="e4749-132">Jeśli korzystasz z [Find-Module][] lub [Find-Script][], dane te można wyświetlić w zwracany obiekt PSGetModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="e4749-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="e4749-133">Na przykład uruchomiony `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="e4749-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="e4749-134">Zwraca dane na temat modułu PSReadLine w galerii.</span><span class="sxs-lookup"><span data-stu-id="e4749-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="e4749-135">Pobieranie pakietów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4749-135">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="e4749-136">Firma Microsoft zachęca następujący proces pobierania pakietów z galerii programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e4749-136">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="e4749-137">Sprawdzanie</span><span class="sxs-lookup"><span data-stu-id="e4749-137">Inspect</span></span>

<span data-ttu-id="e4749-138">Aby pobrać pakiet z galerii w celu przeprowadzenia inspekcji, uruchom [Save-Module][] lub [Save-Script][] polecenia cmdlet, w zależności od typu pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-138">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="e4749-139">Dzięki temu można zapisać pakiet lokalnie bez instalowania i sprawdź zawartość pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-139">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="e4749-140">Pamiętaj, aby ręcznie usunąć zapisanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-140">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="e4749-141">Niektóre z tych pakietów są tworzone przez firmę Microsoft, a inne są tworzone przez społeczność użytkowników programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4749-141">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="e4749-142">Firma Microsoft zaleca przejrzenie treści i kodu pakietów w tej galerii, przed instalacją.</span><span class="sxs-lookup"><span data-stu-id="e4749-142">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="e4749-143">Jeśli użytkownik zauważy, pakietów, które uważasz, że nie został opublikowany w dobrej wierze, kliknij przycisk **Zgłoś nadużycie** na stronie tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-143">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="e4749-144">Instalowanie w klastrze zarządzania systemu</span><span class="sxs-lookup"><span data-stu-id="e4749-144">Install</span></span>

<span data-ttu-id="e4749-145">Aby zainstalować pakiet z galerii do użycia, uruchom [Install-Module][] lub [Install-Script][] polecenia cmdlet, w zależności od typu pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-145">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="e4749-146">[Install-Module][] instaluje moduł do `$env:ProgramFiles\WindowsPowerShell\Modules` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e4749-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="e4749-147">Wymaga to konto administratora.</span><span class="sxs-lookup"><span data-stu-id="e4749-147">This requires an administrator account.</span></span> <span data-ttu-id="e4749-148">Jeśli dodasz `-Scope CurrentUser` parametru moduł jest zainstalowany na `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="e4749-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="e4749-149">[Install-Script][] instaluje skrypt, aby `$env:ProgramFiles\WindowsPowerShell\Scripts` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e4749-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="e4749-150">Wymaga to konto administratora.</span><span class="sxs-lookup"><span data-stu-id="e4749-150">This requires an administrator account.</span></span> <span data-ttu-id="e4749-151">Jeśli dodasz `-Scope CurrentUser` parametru skryptu jest instalowana na `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="e4749-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="e4749-152">Domyślnie [Install-Module][] i [Install-Script][] instaluje najnowszą wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="e4749-153">Aby zainstalować starszą wersję pakietu, Dodaj `-RequiredVersion` parametru.</span><span class="sxs-lookup"><span data-stu-id="e4749-153">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="e4749-154">Wdróż program</span><span class="sxs-lookup"><span data-stu-id="e4749-154">Deploy</span></span>

<span data-ttu-id="e4749-155">Aby wdrożyć pakiet z galerii programu PowerShell w usłudze Azure Automation, kliknij przycisk **wdrażanie w usłudze Azure Automation** na stronie szczegółów pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-155">To deploy a package from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="e4749-156">Nastąpi przekierowanie do portalu zarządzania systemu Azure, w którym możesz logować się przy użyciu poświadczeń konta platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="e4749-156">You will be redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="e4749-157">Należy pamiętać, że wdrażanie pakietów z zależnościami wdroży wszystkie zależności do usługi Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="e4749-157">Note that deploying packages with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="e4749-158">Można wyłączyć przez dodanie przycisku "Wdroż do usługi Azure Automation" **AzureAutomationNotSupported** tagu metadanych pakietu.</span><span class="sxs-lookup"><span data-stu-id="e4749-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="e4749-159">Aby dowiedzieć się więcej o usłudze Azure Automation, zobacz [usługi Azure Automation](/azure/automation) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="e4749-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="e4749-160">Trwa aktualizowanie pakietów z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4749-160">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="e4749-161">Aby zaktualizować pakiety zainstalowany z galerii programu PowerShell, uruchom [Update-Module] [] lub polecenia cmdlet [] [skrypt aktualizacji].</span><span class="sxs-lookup"><span data-stu-id="e4749-161">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="e4749-162">Po uruchomieniu bez żadnych dodatkowych parametrów [] [Update-Module] próby uaktualnienia każdy moduł zainstalowane, uruchamiając [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="e4749-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="e4749-163">Aby selektywnie aktualizowanie modułów, należy dodać `-Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="e4749-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="e4749-164">Podobnie, gdy są uruchomione bez żadnych dodatkowych parametrów, [] [skrypt aktualizacji] również próby uaktualnienia każdego skryptu zainstalowane, uruchamiając [Install-Script][].</span><span class="sxs-lookup"><span data-stu-id="e4749-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="e4749-165">Aby selektywnie zaktualizować skrypty, Dodaj `-Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="e4749-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="e4749-166">Lista pakietów, zainstalowanych z galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4749-166">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="e4749-167">Aby dowiedzieć się, które moduły mają zainstalowany z galerii programu PowerShell, uruchom [Get-InstalledModule][] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4749-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="e4749-168">To polecenie wyświetla wszystkie moduły, które znajdują się w systemie i zainstalowanych bezpośrednio z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4749-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="e4749-169">Podobnie, aby dowiedzieć się, skrypty, które mają zainstalowany z galerii programu PowerShell, uruchom [Get-InstalledScript][] polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4749-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="e4749-170">To polecenie wyświetla wszystkie skrypty, które znajdują się w systemie i zainstalowanych bezpośrednio z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4749-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

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
