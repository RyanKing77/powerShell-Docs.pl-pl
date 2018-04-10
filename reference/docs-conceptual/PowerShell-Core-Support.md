# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="d0770-101">Cykl życia pomocy technicznej programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d0770-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="d0770-102">Podstawowe środowisko PowerShell jest różne zestaw narzędzi i składników, które zostały wydane, zainstalowane i skonfigurowane oddzielnie od środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0770-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="d0770-103">W związku z tym Core programu PowerShell nie jest uwzględniony w umowach licencjonowania systemu Windows 7/8.1/10 lub Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d0770-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="d0770-104">Jednak Core programu PowerShell jest obsługiwany w ramach tradycyjnego umów pomocy technicznej firmy Microsoft, w tym [Premier][], [umowy Enterprise firmy Microsoft][enterprise-agreement]i [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="d0770-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="d0770-105">Można również opłacać [asystowaną pomocą techniczną][] podstawowych programu PowerShell, zachowując żądania pomocy technicznej dla danego problemu.</span><span class="sxs-lookup"><span data-stu-id="d0770-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="d0770-106">Oferujemy również [techniczna dla społeczności][] w witrynie GitHub, w którym można pliku problemu, usterki lub żądanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="d0770-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="d0770-107">Alternatywnie mogą znaleźć pomoc od innych członków społeczności ogólne [Microsoft Community][] lub Microsoft [społeczność techniczna programu PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="d0770-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="d0770-108">Firma Microsoft oferuje żadnej gwarancji, występuje problem opisany lub rozwiązane w odpowiednim czasie.</span><span class="sxs-lookup"><span data-stu-id="d0770-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="d0770-109">Jeśli masz problem wymagający natychmiastowej uwagi, należy użyć tradycyjny, płatną opcje pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="d0770-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="d0770-110">Cykl życia podstawowych programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0770-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="d0770-111">Wdraża PowerShell Core [Microsoft nowoczesnych technicznego][modern].</span><span class="sxs-lookup"><span data-stu-id="d0770-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="d0770-112">Ten cykl pomocy technicznej ma na celu aktualizowanie do najnowszej wersji klientów.</span><span class="sxs-lookup"><span data-stu-id="d0770-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="d0770-113">Rozgałęzienie 6.x wersji Core programu PowerShell zostanie zaktualizowany mniej więcej co sześć miesięcy (np. w wersji 6.0, 6.1, 6.2, itp.)</span><span class="sxs-lookup"><span data-stu-id="d0770-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0770-114">Należy zaktualizować w ciągu sześciu miesięcy po każdej nowej wersji pomocniczej wersji nadal odbierać pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="d0770-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="d0770-115">Na przykład jeśli 6.1 Core programu PowerShell jest wydanej w dniu 1 lipca 2018 możesz oczekuje się do aktualizacji do programu PowerShell Core 6.1 przez 1 stycznia 2019 do obsługi pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="d0770-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![Cykl życia gałęzi Core programu PowerShell][lifecycle-chart]

<span data-ttu-id="d0770-117">Nowoczesne technicznego wymaga również, że Microsoft zawiadamiać klientów 12 miesięcy przed zaprzestanie obsługę produktu (tj. podstawowej programu PowerShell).</span><span class="sxs-lookup"><span data-stu-id="d0770-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="d0770-118">Po pewnym czasie oczekujemy PowerShell Core przyjmie "długoterminowej obsługi" podejście, w którym firma Microsoft będzie wymagać tylko obsługi i zabezpieczeń aktualizuje pozostanie w pomocy technicznej na określonej gałęzi/wersji 6.x.</span><span class="sxs-lookup"><span data-stu-id="d0770-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="d0770-119">Obsługiwane platformy</span><span class="sxs-lookup"><span data-stu-id="d0770-119">Supported platforms</span></span>

<span data-ttu-id="d0770-120">Podstawowe programu PowerShell oficjalnie jest obsługiwane na następujących platformach:</span><span class="sxs-lookup"><span data-stu-id="d0770-120">PowerShell Core is officially supported on the following platforms:</span></span>

* <span data-ttu-id="d0770-121">Windows 7, 8.1 i 10</span><span class="sxs-lookup"><span data-stu-id="d0770-121">Windows 7, 8.1, and 10</span></span>
* <span data-ttu-id="d0770-122">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="d0770-122">Windows Server 2008 R2, 2012 R2, 2016</span></span>
* <span data-ttu-id="d0770-123">[Windows Server częściowo roczna kanału][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="d0770-123">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
* <span data-ttu-id="d0770-124">Ubuntu 14.04 i 16.04, 17.04</span><span class="sxs-lookup"><span data-stu-id="d0770-124">Ubuntu 14.04, 16.04, and 17.04</span></span>
* <span data-ttu-id="d0770-125">Debian 8.7 + i 9</span><span class="sxs-lookup"><span data-stu-id="d0770-125">Debian 8.7+, and 9</span></span>
* <span data-ttu-id="d0770-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d0770-126">CentOS 7</span></span>
* <span data-ttu-id="d0770-127">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="d0770-127">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="d0770-128">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="d0770-128">OpenSUSE 42.2</span></span>
* <span data-ttu-id="d0770-129">Fedora 25, 26</span><span class="sxs-lookup"><span data-stu-id="d0770-129">Fedora 25, 26</span></span>
* <span data-ttu-id="d0770-130">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="d0770-130">macOS 10.12+</span></span>

<span data-ttu-id="d0770-131">Naszej społeczności przyczynił się również pakiety dla następujących platform, ale nie są one oficjalnie suppported:</span><span class="sxs-lookup"><span data-stu-id="d0770-131">Our community has also contributed packages for the following platforms, but they are not officially suppported:</span></span>

* <span data-ttu-id="d0770-132">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="d0770-132">Arch Linux</span></span>
* <span data-ttu-id="d0770-133">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="d0770-133">Kali Linux</span></span>
* <span data-ttu-id="d0770-134">AppImage (działa na wielu platformach systemu Linux)</span><span class="sxs-lookup"><span data-stu-id="d0770-134">AppImage (works on multiple Linux platforms)</span></span>

## <a name="notes-on-licensing"></a><span data-ttu-id="d0770-135">Uwagi dotyczące licencjonowania</span><span class="sxs-lookup"><span data-stu-id="d0770-135">Notes on licensing</span></span>

<span data-ttu-id="d0770-136">Z dodatkiem PowerShell Core [licencji MIT][].</span><span class="sxs-lookup"><span data-stu-id="d0770-136">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="d0770-137">W ramach tej licencji, a w przypadku braku umowy płatnej pomocy technicznej, użytkownicy są ograniczone do [techniczna dla społeczności][].</span><span class="sxs-lookup"><span data-stu-id="d0770-137">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="d0770-138">Z obsługą społeczności firma Microsoft nie udziela żadnych gwarancji, czas odpowiedzi lub poprawki.</span><span class="sxs-lookup"><span data-stu-id="d0770-138">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="d0770-139">Moduł programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0770-139">Windows PowerShell Module</span></span>

<span data-ttu-id="d0770-140">Obsługuje dla podstawowych programu PowerShell nie obejmuje innych modułów produktu, chyba że moduły jawnie obsługuje Core programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0770-140">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="d0770-141">Na przykład za pomocą `ActiveDirectory` moduł, który jest dostarczany jako część systemu Windows Server jest to nieobsługiwany scenariusz.</span><span class="sxs-lookup"><span data-stu-id="d0770-141">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="d0770-142">Jednak może być zgodne w niektórych przypadkach modułów, które nie obsługują jawnie Core programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0770-142">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="d0770-143">Instalując [ `WindowsPSModulePath` ][] moduł, możesz dołączyć programu Windows PowerShell `PSModulePath` do podstawowego środowiska PowerShell `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="d0770-143">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="d0770-144">Najpierw zainstaluj `WindowsPSModulePath` modułu z galerii programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d0770-144">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="d0770-145">Po zainstalowaniu tego modułu, uruchom `Add-WindowsPSModulePath` polecenia cmdlet programu Windows PowerShell Dodaj `PSModulePath` na rdzeń środowiska PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d0770-145">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[techniczna dla społeczności]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[społeczność techniczna programu PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[asystowaną pomocą techniczną]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[licencji MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/