---
title: Cykl życia pomocy technicznej programu PowerShell Core
description: Zasady dotyczące pomocy technicznej dla programu PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854373"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="c91ca-103">Cykl życia pomocy technicznej programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c91ca-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="c91ca-104">PowerShell Core to zestaw różne narzędzia i składniki, które są dostarczane, zainstalować i skonfigurować oddzielnie, za pomocą programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c91ca-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="c91ca-105">Tak program PowerShell Core nie są objęte umowami licencjonowania Windows 7/8.1/10 lub Windows Server.</span><span class="sxs-lookup"><span data-stu-id="c91ca-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="c91ca-106">Jednak program PowerShell Core jest obsługiwane w ramach tradycyjnego umowy pomocy technicznej firmy Microsoft, w tym [Premier][], [umowy Microsoft Enterprise Agreement][enterprise-agreement]i [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="c91ca-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="c91ca-107">Można również płacisz [asystowanej pomocy technicznej][] dla programu PowerShell Core, rejestrując żądanie pomocy technicznej dla danego problemu.</span><span class="sxs-lookup"><span data-stu-id="c91ca-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="c91ca-108">Pomoc techniczna w społeczności</span><span class="sxs-lookup"><span data-stu-id="c91ca-108">Community Support</span></span>

<span data-ttu-id="c91ca-109">Oferujemy również [pomoc techniczna w społeczności][] w serwisie GitHub, w którym mogą zgłaszać problem lub usterki zgłoszenie dotyczące funkcji.</span><span class="sxs-lookup"><span data-stu-id="c91ca-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="c91ca-110">Ponadto Pomoc z innymi członkami społeczności może się okazać ogólne [Microsoft Community][] lub Microsoft [Społeczność techniczna programu PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="c91ca-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="c91ca-111">Firma Microsoft nie oferuje żadnej gwarancji, istnieje czy społeczności zostanie adres lub rozwiązać problem w odpowiednim czasie.</span><span class="sxs-lookup"><span data-stu-id="c91ca-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="c91ca-112">Jeśli masz problem wymagający natychmiastowej uwagi, należy użyć tradycyjny, płatnych opcji pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="c91ca-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="c91ca-113">Cykl życia programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="c91ca-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="c91ca-114">Program PowerShell Core jest przyjęcie [nowoczesne zasady cyklu życia firmy Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="c91ca-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="c91ca-115">Ten cykl wsparcia technicznego jest przeznaczona dla aktualnych klientów przy użyciu najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="c91ca-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="c91ca-116">Gałęzi wersji 6.x, programu PowerShell Core będą aktualizowane mniej więcej co sześć miesięcy (przykłady: w wersji 6.0, 6.1, 6.2, itp.)</span><span class="sxs-lookup"><span data-stu-id="c91ca-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c91ca-117">Należy zaktualizować w ciągu sześciu miesięcy po każdej nowej wersji pomocniczej wersji, aby nadal otrzymywać pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="c91ca-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="c91ca-118">Na przykład jeśli program PowerShell Core 6.1 jest wydanej w dniu 1 lipca 2018 r. można oczekuje się do aktualizacji do programu PowerShell Core 6.1 1 stycznia 2019 r do obsługi pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="c91ca-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c91ca-119">Należy zaktualizować w ciągu 30 dni po każdej nowej wersji poprawki wersji, aby nadal otrzymywać pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="c91ca-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="c91ca-120">Na przykład jeśli używasz programu PowerShell Core 6.1 i 6.1.3 została wydana 19 lutego 2019 r można oczekuje się do aktualizacji do programu PowerShell Core 6.1.3 21 marca 2019 r, czyli 30 dni po wydaniu do obsługi pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="c91ca-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="c91ca-121">Jeśli wymagana znajdują się wszystkie poprawki, poprawki zostaną wydane w następną aktualizację zbiorczą.</span><span class="sxs-lookup"><span data-stu-id="c91ca-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="c91ca-122">Nowoczesne zasady cyklu życia wymaga również, że Microsoft zawarcia klientów przez 12 miesięcy przed zaprzestaniem pomocy technicznej dla produktu (oznacza to, programu PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="c91ca-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="c91ca-123">Po pewnym czasie oczekujemy, że program PowerShell Core przyjmie "długoterminowej obsługi" podejście.</span><span class="sxs-lookup"><span data-stu-id="c91ca-123">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="c91ca-124">W tym podejściu obsługi będzie wymagamy tylko obsługi i aktualizacje zabezpieczeń pozostanie w pomocy technicznej w określonej gałęzi/wersji 6.x.</span><span class="sxs-lookup"><span data-stu-id="c91ca-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="c91ca-125">Obsługiwane platformy</span><span class="sxs-lookup"><span data-stu-id="c91ca-125">Supported platforms</span></span>

<span data-ttu-id="c91ca-126">Poniższej tabeli, aby wyświetlić wersję programu PowerShell Core w przypadku korzystania z platformy jest oficjalnie obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="c91ca-126">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="c91ca-127">Naszej społeczności współtworzonej również pakiety dla niektórych platform, ale nie jest oficjalnie obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="c91ca-127">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="c91ca-128">Te pakiety są oznaczone jako `Community` w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c91ca-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="c91ca-129">Platformy wymienione jako `Experimental` oficjalnie nie są obsługiwane, ale są dostępne do eksperymentowania i przesyłania opinii.</span><span class="sxs-lookup"><span data-stu-id="c91ca-129">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="c91ca-130">6.1</span><span class="sxs-lookup"><span data-stu-id="c91ca-130">6.1</span></span>         | <span data-ttu-id="c91ca-131">6.2</span><span class="sxs-lookup"><span data-stu-id="c91ca-131">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="c91ca-132">Windows 7, 8.1 i 10</span><span class="sxs-lookup"><span data-stu-id="c91ca-132">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="c91ca-133">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-133">Supported</span></span>   | <span data-ttu-id="c91ca-134">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-134">Supported</span></span>   |
| <span data-ttu-id="c91ca-135">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="c91ca-135">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="c91ca-136">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-136">Supported</span></span>   | <span data-ttu-id="c91ca-137">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-137">Supported</span></span>   |
| <span data-ttu-id="c91ca-138">[Półroczny kanał dystrybucji systemu Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="c91ca-138">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="c91ca-139">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-139">Supported</span></span>   | <span data-ttu-id="c91ca-140">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-140">Supported</span></span>   |
| <span data-ttu-id="c91ca-141">Ubuntu 16.04 i 18.04</span><span class="sxs-lookup"><span data-stu-id="c91ca-141">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="c91ca-142">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-142">Supported</span></span>   | <span data-ttu-id="c91ca-143">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-143">Supported</span></span>   |
| <span data-ttu-id="c91ca-144">Ubuntu 18.10 (za pośrednictwem przyciągania pakiet)</span><span class="sxs-lookup"><span data-stu-id="c91ca-144">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="c91ca-145">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-145">Community</span></span>   | <span data-ttu-id="c91ca-146">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-146">Community</span></span>   |
| <span data-ttu-id="c91ca-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="c91ca-147">Debian 9</span></span>                                          | <span data-ttu-id="c91ca-148">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-148">Supported</span></span>   | <span data-ttu-id="c91ca-149">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-149">Supported</span></span>   |
| <span data-ttu-id="c91ca-150">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c91ca-150">CentOS 7</span></span>                                          | <span data-ttu-id="c91ca-151">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-151">Supported</span></span>   | <span data-ttu-id="c91ca-152">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-152">Supported</span></span>   |
| <span data-ttu-id="c91ca-153">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="c91ca-153">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="c91ca-154">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-154">Supported</span></span>   | <span data-ttu-id="c91ca-155">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-155">Supported</span></span>   |
| <span data-ttu-id="c91ca-156">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c91ca-156">openSUSE 42.3</span></span>                                     | <span data-ttu-id="c91ca-157">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-157">Supported</span></span>   | <span data-ttu-id="c91ca-158">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-158">Supported</span></span>   |
| <span data-ttu-id="c91ca-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c91ca-159">Fedora 28</span></span>                                         | <span data-ttu-id="c91ca-160">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-160">Supported</span></span>   | <span data-ttu-id="c91ca-161">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-161">Supported</span></span>   |
| <span data-ttu-id="c91ca-162">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="c91ca-162">macOS 10.12+</span></span>                                      | <span data-ttu-id="c91ca-163">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-163">Supported</span></span>   | <span data-ttu-id="c91ca-164">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c91ca-164">Supported</span></span>   |
| <span data-ttu-id="c91ca-165">Architektura</span><span class="sxs-lookup"><span data-stu-id="c91ca-165">Arch</span></span>                                              | <span data-ttu-id="c91ca-166">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-166">Community</span></span>   | <span data-ttu-id="c91ca-167">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-167">Community</span></span>   |
| <span data-ttu-id="c91ca-168">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c91ca-168">Raspbian</span></span>                                          | <span data-ttu-id="c91ca-169">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-169">Community</span></span>   | <span data-ttu-id="c91ca-170">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-170">Community</span></span>   |
| <span data-ttu-id="c91ca-171">Kali</span><span class="sxs-lookup"><span data-stu-id="c91ca-171">Kali</span></span>                                              | <span data-ttu-id="c91ca-172">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-172">Community</span></span>   | <span data-ttu-id="c91ca-173">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-173">Community</span></span>   |
| <span data-ttu-id="c91ca-174">AppImage (działa na wielu platformach systemu Linux)</span><span class="sxs-lookup"><span data-stu-id="c91ca-174">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="c91ca-175">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-175">Community</span></span>   | <span data-ttu-id="c91ca-176">Społeczność</span><span class="sxs-lookup"><span data-stu-id="c91ca-176">Community</span></span>   |
| [<span data-ttu-id="c91ca-177">Przyciągaj pakietu</span><span class="sxs-lookup"><span data-stu-id="c91ca-177">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="c91ca-178">Patrz Uwaga</span><span class="sxs-lookup"><span data-stu-id="c91ca-178">See note</span></span>    | <span data-ttu-id="c91ca-179">Patrz Uwaga</span><span class="sxs-lookup"><span data-stu-id="c91ca-179">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="c91ca-180">Przyciągaj pakietów takie same jak w przypadku dystrybucji korzystania z pakietu.</span><span class="sxs-lookup"><span data-stu-id="c91ca-180">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="c91ca-181">Program PowerShell wersji koniec cyklu życia</span><span class="sxs-lookup"><span data-stu-id="c91ca-181">PowerShell release end of life</span></span>

<span data-ttu-id="c91ca-182">Na podstawie [cyklu życia programu PowerShell Core](#lifecycle-of-powershell-core), Poniższa tabela zawiera daty, kiedy różnych wersji będzie nie będzie już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="c91ca-182">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="c91ca-183">Wersja</span><span class="sxs-lookup"><span data-stu-id="c91ca-183">Version</span></span> | <span data-ttu-id="c91ca-184">Koniec cyklu życia</span><span class="sxs-lookup"><span data-stu-id="c91ca-184">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="c91ca-185">6.0</span><span class="sxs-lookup"><span data-stu-id="c91ca-185">6.0</span></span>     | <span data-ttu-id="c91ca-186">13 lutego 2019 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-186">February 13, 2019</span></span>             |
| <span data-ttu-id="c91ca-187">6.1</span><span class="sxs-lookup"><span data-stu-id="c91ca-187">6.1</span></span>     | <span data-ttu-id="c91ca-188">28 września 2019 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-188">September 28, 2019</span></span>            |
| <span data-ttu-id="c91ca-189">6.2</span><span class="sxs-lookup"><span data-stu-id="c91ca-189">6.2</span></span>     | <span data-ttu-id="c91ca-190">6 miesięcy od wersji 7</span><span class="sxs-lookup"><span data-stu-id="c91ca-190">6 months after 7 releases</span></span>     |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="c91ca-191">Platform, które są poza pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="c91ca-191">Platforms, which are out of support</span></span>

<span data-ttu-id="c91ca-192">Gdy wersja platformy osiągnie wycofanych z eksploatacji, zgodnie z definicją właściciela platformy, program PowerShell Core przestaną się również do obsługi tej wersji platformy.</span><span class="sxs-lookup"><span data-stu-id="c91ca-192">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="c91ca-193">Wcześniej wydane pakiety, pozostaną dostępne dla klientów wymagające dostępu, ale obsługa formalne i aktualizacje dowolnego rodzaju już nie będą udostępniane.</span><span class="sxs-lookup"><span data-stu-id="c91ca-193">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="c91ca-194">Dlatego właściciele dystrybucji zakończone obsługę następujących wersji i nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c91ca-194">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="c91ca-195">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="c91ca-195">OS</span></span>       | <span data-ttu-id="c91ca-196">Wersja</span><span class="sxs-lookup"><span data-stu-id="c91ca-196">Version</span></span> | <span data-ttu-id="c91ca-197">Koniec cyklu życia</span><span class="sxs-lookup"><span data-stu-id="c91ca-197">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="c91ca-198">Fedora</span><span class="sxs-lookup"><span data-stu-id="c91ca-198">Fedora</span></span>   | <span data-ttu-id="c91ca-199">24</span><span class="sxs-lookup"><span data-stu-id="c91ca-199">24</span></span>      | [<span data-ttu-id="c91ca-200">Sierpnia 2017 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-200">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="c91ca-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="c91ca-201">Fedora</span></span>   | <span data-ttu-id="c91ca-202">25</span><span class="sxs-lookup"><span data-stu-id="c91ca-202">25</span></span>      | [<span data-ttu-id="c91ca-203">Grudnia 2017 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-203">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="c91ca-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="c91ca-204">Fedora</span></span>   | <span data-ttu-id="c91ca-205">26</span><span class="sxs-lookup"><span data-stu-id="c91ca-205">26</span></span>      | [<span data-ttu-id="c91ca-206">Maja 2018 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-206">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="c91ca-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c91ca-207">openSUSE</span></span> | <span data-ttu-id="c91ca-208">42.1</span><span class="sxs-lookup"><span data-stu-id="c91ca-208">42.1</span></span>    | [<span data-ttu-id="c91ca-209">Maja 2017 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-209">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="c91ca-210">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c91ca-210">openSUSE</span></span> | <span data-ttu-id="c91ca-211">42.2</span><span class="sxs-lookup"><span data-stu-id="c91ca-211">42.2</span></span>    | [<span data-ttu-id="c91ca-212">Stycznia 2018 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-212">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="c91ca-213">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c91ca-213">Ubuntu</span></span>   | <span data-ttu-id="c91ca-214">16.10</span><span class="sxs-lookup"><span data-stu-id="c91ca-214">16.10</span></span>   | [<span data-ttu-id="c91ca-215">Lipca 2017 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-215">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="c91ca-216">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c91ca-216">Ubuntu</span></span>   | <span data-ttu-id="c91ca-217">17.04</span><span class="sxs-lookup"><span data-stu-id="c91ca-217">17.04</span></span>   | [<span data-ttu-id="c91ca-218">Stycznia 2018 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-218">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="c91ca-219">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c91ca-219">Ubuntu</span></span>   | <span data-ttu-id="c91ca-220">17.10</span><span class="sxs-lookup"><span data-stu-id="c91ca-220">17.10</span></span>   | [<span data-ttu-id="c91ca-221">Lipca 2018 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-221">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="c91ca-222">Debian</span><span class="sxs-lookup"><span data-stu-id="c91ca-222">Debian</span></span>   | <span data-ttu-id="c91ca-223">8</span><span class="sxs-lookup"><span data-stu-id="c91ca-223">8</span></span>       | [<span data-ttu-id="c91ca-224">Czerwca 2018 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-224">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="c91ca-225">Fedora</span><span class="sxs-lookup"><span data-stu-id="c91ca-225">Fedora</span></span>   | <span data-ttu-id="c91ca-226">27</span><span class="sxs-lookup"><span data-stu-id="c91ca-226">27</span></span>      | [<span data-ttu-id="c91ca-227">Listopada 2018 r.</span><span class="sxs-lookup"><span data-stu-id="c91ca-227">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="c91ca-228">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c91ca-228">Ubuntu</span></span>   | <span data-ttu-id="c91ca-229">14.04</span><span class="sxs-lookup"><span data-stu-id="c91ca-229">14.04</span></span>   | [<span data-ttu-id="c91ca-230">2019 kwietnia</span><span class="sxs-lookup"><span data-stu-id="c91ca-230">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="c91ca-231">Uwagi dotyczące licencjonowania</span><span class="sxs-lookup"><span data-stu-id="c91ca-231">Notes on licensing</span></span>

<span data-ttu-id="c91ca-232">Program PowerShell Core jest wydawane na mocy [Licencja MIT][].</span><span class="sxs-lookup"><span data-stu-id="c91ca-232">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="c91ca-233">W ramach niniejszej licencji, a nie towarzyszy stosowna umowa płatnej pomocy technicznej, użytkownicy są ograniczone do [pomoc techniczna w społeczności][].</span><span class="sxs-lookup"><span data-stu-id="c91ca-233">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="c91ca-234">Za pomocą pomoc techniczna w społeczności firmy Microsoft nie udziela żadnych gwarancji czasu odpowiedzi lub poprawki.</span><span class="sxs-lookup"><span data-stu-id="c91ca-234">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="c91ca-235">Moduł programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c91ca-235">Windows PowerShell Module</span></span>

<span data-ttu-id="c91ca-236">Pomocy technicznej dla programu PowerShell Core nie obejmuje moduły produktu, chyba że moduły jawnego zapewnienia obsługi programu PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c91ca-236">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="c91ca-237">Na przykład za pomocą `ActiveDirectory` modułu, który jest dostarczany jako część systemu Windows Server jest to nieobsługiwany scenariusz.</span><span class="sxs-lookup"><span data-stu-id="c91ca-237">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="c91ca-238">Jednak może być zgodny w niektórych przypadkach moduły, które nie obsługują jawnie programu PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c91ca-238">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="c91ca-239">Instalując [ `WindowsPSModulePath` ][] modułu programu Windows PowerShell można dodać `PSModulePath` do podstawowego środowiska PowerShell `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="c91ca-239">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="c91ca-240">Najpierw zainstaluj `WindowsPSModulePath` modułu z galerii programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c91ca-240">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="c91ca-241">Po zainstalowaniu tego modułu, należy uruchomić `Add-WindowsPSModulePath` polecenie cmdlet programu Windows PowerShell dodanie `PSModulePath` do programu PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="c91ca-241">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="c91ca-242">Funkcje eksperymentalne</span><span class="sxs-lookup"><span data-stu-id="c91ca-242">Experimental features</span></span>

<span data-ttu-id="c91ca-243">[Funkcje eksperymentalne][] są ograniczone do [pomoc techniczna w społeczności](#community-support).</span><span class="sxs-lookup"><span data-stu-id="c91ca-243">[Experimental features][] are limited to [community support](#community-support).</span></span>

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Pomoc techniczna w społeczności]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[Społeczność techniczna programu PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[asystowanej pomocy technicznej]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licencja MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Funkcje eksperymentalne]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
