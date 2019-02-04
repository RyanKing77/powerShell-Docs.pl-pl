---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Wymagania wstępne dotyczące usługi JEA
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688357"
---
# <a name="prerequisites"></a><span data-ttu-id="a5015-103">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a5015-103">Prerequisites</span></span>

> <span data-ttu-id="a5015-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a5015-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a5015-105">Just Enough Administration, jest to funkcja dostępna przy użyciu programu Windows PowerShell 5.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="a5015-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="a5015-106">W tym temacie opisano wymagania wstępne, które muszą zostać spełnione, aby rozpocząć korzystanie z usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="a5015-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="a5015-107">Instalowanie usługi JEA</span><span class="sxs-lookup"><span data-stu-id="a5015-107">Install JEA</span></span>

<span data-ttu-id="a5015-108">Technologia JEA jest dostępny za pomocą programu Windows PowerShell 5.0 lub nowszy, ale do pełnego zestawu funkcji zalecane jest, zainstaluj najnowszą wersję programu PowerShell dostępnych w systemie.</span><span class="sxs-lookup"><span data-stu-id="a5015-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="a5015-109">W poniższej tabeli opisano dostępności JEA firmy w systemie Windows Server:</span><span class="sxs-lookup"><span data-stu-id="a5015-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="a5015-110">System operacyjny serwera</span><span class="sxs-lookup"><span data-stu-id="a5015-110">Server Operating System</span></span>   | <span data-ttu-id="a5015-111">Dostępność usługi JEA</span><span class="sxs-lookup"><span data-stu-id="a5015-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="a5015-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a5015-112">Windows Server 2016</span></span>       | <span data-ttu-id="a5015-113">Wstępnie zainstalowane</span><span class="sxs-lookup"><span data-stu-id="a5015-113">Preinstalled</span></span>
<span data-ttu-id="a5015-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a5015-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="a5015-115">Pełna funkcjonalność z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a5015-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="a5015-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a5015-116">Windows Server 2012</span></span>       | <span data-ttu-id="a5015-117">Pełna funkcjonalność z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a5015-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="a5015-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="a5015-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="a5015-119">Ograniczona funkcjonalność<sup>1</sup> z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a5015-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="a5015-120">Umożliwia także JEA na komputerze domowe lub firmowe:</span><span class="sxs-lookup"><span data-stu-id="a5015-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="a5015-121">System operacyjny klienta</span><span class="sxs-lookup"><span data-stu-id="a5015-121">Client Operating System</span></span>   | <span data-ttu-id="a5015-122">Dostępność usługi JEA</span><span class="sxs-lookup"><span data-stu-id="a5015-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="a5015-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="a5015-123">Windows 10 1607+</span></span>          | <span data-ttu-id="a5015-124">Wstępnie zainstalowane</span><span class="sxs-lookup"><span data-stu-id="a5015-124">Preinstalled</span></span>
<span data-ttu-id="a5015-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="a5015-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="a5015-126">Wstępnie zainstalowane, za pomocą funkcjonalność ograniczona<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="a5015-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="a5015-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="a5015-127">Windows 10 1507</span></span>           | <span data-ttu-id="a5015-128">Niedostępne</span><span class="sxs-lookup"><span data-stu-id="a5015-128">Not available</span></span>
<span data-ttu-id="a5015-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="a5015-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="a5015-130">Pełna funkcjonalność z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a5015-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="a5015-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="a5015-131">Windows 7</span></span>                 | <span data-ttu-id="a5015-132">Ograniczona funkcjonalność<sup>1</sup> z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a5015-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="a5015-133"><sup>1</sup> JEA nie można skonfigurować do kont usług zarządzanych przez grupę w systemie Windows Server 2008 R2 lub Windows 7.</span><span class="sxs-lookup"><span data-stu-id="a5015-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="a5015-134">Kont wirtualnych i innych funkcji JEA *są* obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a5015-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="a5015-135"><sup>2</sup> systemu Windows 10 w wersji 1511 i 1603 nie obsługują następujące funkcje usługi JEA: uruchamianie zgodnie z grupą zarządzane konta usług, zasady dostępu warunkowego w konfiguracji sesji, dysku użytkownika i musi udzielać dostępu do kont użytkowników lokalnych.</span><span class="sxs-lookup"><span data-stu-id="a5015-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="a5015-136">Aby uzyskać pomoc techniczną dla tych funkcji, należy zaktualizować Windows do wersji 1607 (Rocznicowa aktualizacja) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="a5015-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="a5015-137">Sprawdź, która wersja programu PowerShell jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="a5015-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="a5015-138">Aby sprawdzić, jaka wersja programu PowerShell jest zainstalowany w systemie, zapoznaj się z `$PSVersionTable` zmiennej w wierszu polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5015-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="a5015-139">Jesteś gotowy do użycia usługi JEA, jeśli *głównych* wersja jest równa lub większa niż **5**.</span><span class="sxs-lookup"><span data-stu-id="a5015-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="a5015-140">Aby uzyskać najlepsze wyniki, a dostęp do najnowszych funkcji, zaleca się uaktualnienie do wersji programu PowerShell **5.1** gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a5015-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="a5015-141">Zainstaluj program Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="a5015-141">Install Windows Management Framework</span></span>

<span data-ttu-id="a5015-142">Jeśli używasz starszej wersji programu PowerShell, należy zaktualizować system najnowsza aktualizacja usługi Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="a5015-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="a5015-143">Pakiety aktualizacji i link do najnowszej wersji programu WMF są dostępne w [Centrum pobierania](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span><span class="sxs-lookup"><span data-stu-id="a5015-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span></span>

<span data-ttu-id="a5015-144">Zdecydowanie zaleca się testowanie zgodności Twojego obciążenia za pomocą programu WMF przed uaktualnieniem wszystkich serwerów.</span><span class="sxs-lookup"><span data-stu-id="a5015-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="a5015-145">Użytkownicy systemu Windows 10, należy zainstalować najnowsze aktualizacje funkcji, aby uzyskać bieżącą wersję środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5015-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="a5015-146">Włączanie komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5015-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="a5015-147">Komunikacja zdalna programu PowerShell zapewnia podstawę, na którym bazuje JEA.</span><span class="sxs-lookup"><span data-stu-id="a5015-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="a5015-148">W związku z tym jest niezbędne do zapewnienia komunikacji zdalnej programu PowerShell jest włączona i [zabezpieczenie](/powershell/scripting/setup/winrmsecurity) w systemie, zanim użyjesz usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="a5015-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="a5015-149">Komunikacja zdalna programu PowerShell jest włączona domyślnie w systemie Windows Server 2012, 2012 R2 i 2016.</span><span class="sxs-lookup"><span data-stu-id="a5015-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="a5015-150">Komunikacja zdalna programu PowerShell można włączyć, uruchamiając następujące polecenie w oknie programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="a5015-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="a5015-151">Włączanie rejestrowania blok skryptu jest (opcjonalnie) i moduł programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5015-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="a5015-152">Następujące kroki włączyć rejestrowanie dla wszystkich akcji programu PowerShell w systemie.</span><span class="sxs-lookup"><span data-stu-id="a5015-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="a5015-153">Rejestrowanie modułu programu PowerShell nie jest wymagane dla usługi JEA, jednak zdecydowanie zalecane jest włączenie go w celu upewnij się, że użytkownicy polecenia uruchamiają są rejestrowane w centralnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a5015-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="a5015-154">Można skonfigurować zasad logowania modułu programu PowerShell, za pomocą zasad grupy.</span><span class="sxs-lookup"><span data-stu-id="a5015-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="a5015-155">Otwórz Edytor lokalnych zasad grupy na stacji roboczej lub obiektu zasad grupy w konsoli zarządzania zasadami grupy na kontrolerze domeny usługi Active Directory</span><span class="sxs-lookup"><span data-stu-id="a5015-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="a5015-156">Przejdź do **konfiguracji komputera\\Szablony administracyjne\\składników Windows\\programu Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="a5015-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="a5015-157">Kliknij dwukrotnie **mogą włączyć rejestrowanie modułów**</span><span class="sxs-lookup"><span data-stu-id="a5015-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="a5015-158">Kliknij przycisk **włączone**</span><span class="sxs-lookup"><span data-stu-id="a5015-158">Click **Enabled**</span></span>
5. <span data-ttu-id="a5015-159">W sekcji Opcje kliknąć **Pokaż** obok nazwy modułu</span><span class="sxs-lookup"><span data-stu-id="a5015-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="a5015-160">Typ `\*` w wyświetlonym oknie.</span><span class="sxs-lookup"><span data-stu-id="a5015-160">Type `\*` in the pop up window.</span></span> <span data-ttu-id="a5015-161">To powoduje, że rejestrowanie poleceń z wszystkich modułów programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5015-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="a5015-162">Kliknij przycisk **OK** do ustawiania zasad</span><span class="sxs-lookup"><span data-stu-id="a5015-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="a5015-163">Kliknij dwukrotnie **mogą włączyć rejestrowanie programu PowerShell skrypt bloku**</span><span class="sxs-lookup"><span data-stu-id="a5015-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="a5015-164">Kliknij przycisk **włączone**</span><span class="sxs-lookup"><span data-stu-id="a5015-164">Click **Enabled**</span></span>
10. <span data-ttu-id="a5015-165">Kliknij przycisk **OK** do ustawiania zasad</span><span class="sxs-lookup"><span data-stu-id="a5015-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="a5015-166">(W przypadku przyłączonych do domeny komputerów tylko) Uruchom `gpupdate` lub zaczekaj na przetwarzanie zaktualizowane zasady i zastosować ustawienia zasad grupy</span><span class="sxs-lookup"><span data-stu-id="a5015-166">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="a5015-167">Można również włączyć transkrypcji PowerShell całego systemu za pomocą zasad grupy.</span><span class="sxs-lookup"><span data-stu-id="a5015-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a5015-168">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a5015-168">Next steps</span></span>

[<span data-ttu-id="a5015-169">Utwórz plik możliwości roli</span><span class="sxs-lookup"><span data-stu-id="a5015-169">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="a5015-170">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="a5015-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="a5015-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5015-171">See also</span></span>

[<span data-ttu-id="a5015-172">Dodatkowe informacje na temat zabezpieczeń komunikacji zdalnej programu PowerShell i usługi WinRM</span><span class="sxs-lookup"><span data-stu-id="a5015-172">Additional information about PowerShell Remoting and WinRM security</span></span>](/powershell/scripting/setup/winrmsecurity)

[<span data-ttu-id="a5015-173">*Program PowerShell ♥ zespołem niebieskim* wpis w blogu dotyczący zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a5015-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)