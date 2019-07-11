---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Wymagania wstępne dotyczące usługi JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734280"
---
# <a name="prerequisites"></a><span data-ttu-id="43e7d-103">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="43e7d-103">Prerequisites</span></span>

<span data-ttu-id="43e7d-104">Just Enough Administration, jest to funkcja dostępna w programie PowerShell 5.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="43e7d-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="43e7d-105">W tym artykule opisano wymagania wstępne, które muszą zostać spełnione, aby rozpocząć korzystanie z technologii JEA.</span><span class="sxs-lookup"><span data-stu-id="43e7d-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="43e7d-106">Sprawdź, która wersja programu PowerShell jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="43e7d-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="43e7d-107">Aby sprawdzić, jaka wersja programu PowerShell jest zainstalowany w systemie, zapoznaj się z `$PSVersionTable` zmiennej w wierszu polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43e7d-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="43e7d-108">JEA jest dostępne przy użyciu programu PowerShell w wersji 5.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="43e7d-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="43e7d-109">Do pełnej funkcjonalności zalecane jest, zainstaluj najnowszą wersję programu PowerShell dostępnych w systemie.</span><span class="sxs-lookup"><span data-stu-id="43e7d-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="43e7d-110">W poniższej tabeli opisano dostępności JEA firmy w systemie Windows Server:</span><span class="sxs-lookup"><span data-stu-id="43e7d-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="43e7d-111">System operacyjny serwera</span><span class="sxs-lookup"><span data-stu-id="43e7d-111">Server Operating System</span></span> |                <span data-ttu-id="43e7d-112">Dostępność usługi JEA</span><span class="sxs-lookup"><span data-stu-id="43e7d-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="43e7d-113">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="43e7d-113">Windows Server 2016+</span></span>    | <span data-ttu-id="43e7d-114">Wstępnie zainstalowane</span><span class="sxs-lookup"><span data-stu-id="43e7d-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="43e7d-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="43e7d-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="43e7d-116">Pełna funkcjonalność z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="43e7d-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="43e7d-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="43e7d-117">Windows Server 2012</span></span>     | <span data-ttu-id="43e7d-118">Pełna funkcjonalność z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="43e7d-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="43e7d-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="43e7d-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="43e7d-120">Ograniczona funkcjonalność<sup>1</sup> z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="43e7d-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="43e7d-121">Umożliwia także JEA na komputerze domowe lub firmowe:</span><span class="sxs-lookup"><span data-stu-id="43e7d-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="43e7d-122">System operacyjny klienta</span><span class="sxs-lookup"><span data-stu-id="43e7d-122">Client Operating System</span></span> |                   <span data-ttu-id="43e7d-123">Dostępność usługi JEA</span><span class="sxs-lookup"><span data-stu-id="43e7d-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="43e7d-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="43e7d-124">Windows 10 1607+</span></span>        | <span data-ttu-id="43e7d-125">Wstępnie zainstalowane</span><span class="sxs-lookup"><span data-stu-id="43e7d-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="43e7d-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="43e7d-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="43e7d-127">Wstępnie zainstalowane, za pomocą funkcjonalność ograniczona<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="43e7d-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="43e7d-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="43e7d-128">Windows 10 1507</span></span>         | <span data-ttu-id="43e7d-129">Niedostępne</span><span class="sxs-lookup"><span data-stu-id="43e7d-129">Not available</span></span>                                        |
| <span data-ttu-id="43e7d-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="43e7d-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="43e7d-131">Pełna funkcjonalność z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="43e7d-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="43e7d-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="43e7d-132">Windows 7</span></span>               | <span data-ttu-id="43e7d-133">Ograniczona funkcjonalność<sup>1</sup> z programem WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="43e7d-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="43e7d-134"><sup>1</sup> JEA nie można skonfigurować konta usług zarządzane przez grupę w systemie Windows Server 2008 R2 lub Windows 7.</span><span class="sxs-lookup"><span data-stu-id="43e7d-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="43e7d-135">Kont wirtualnych i innych funkcji JEA *są* obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="43e7d-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="43e7d-136"><sup>2</sup> następujące funkcje usługi JEA nie są obsługiwane w systemie Windows 10 w wersji 1511 i 1603:</span><span class="sxs-lookup"><span data-stu-id="43e7d-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="43e7d-137">Uruchamianie jako konto usługi zarządzane przez grupę</span><span class="sxs-lookup"><span data-stu-id="43e7d-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="43e7d-138">Zasady dostępu warunkowego w konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="43e7d-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="43e7d-139">Stacji użytkownika</span><span class="sxs-lookup"><span data-stu-id="43e7d-139">The user drive</span></span>
  - <span data-ttu-id="43e7d-140">Udzielanie dostępu do kont użytkowników lokalnych</span><span class="sxs-lookup"><span data-stu-id="43e7d-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="43e7d-141">Aby uzyskać pomoc techniczną dla tych funkcji, należy zaktualizować Windows do wersji 1607 (Rocznicowa aktualizacja) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="43e7d-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="43e7d-142">Zainstaluj program Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="43e7d-142">Install Windows Management Framework</span></span>

<span data-ttu-id="43e7d-143">Jeśli używasz starszej wersji programu PowerShell może być konieczne zaktualizowanie systemu klienta przy użyciu najnowszych aktualizacji Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="43e7d-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="43e7d-144">Aby uzyskać więcej informacji, zobacz [dokumentacji programu WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="43e7d-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="43e7d-145">Zaleca się testowanie zgodności Twojego obciążenia za pomocą programu WMF przed uaktualnieniem wszystkich serwerów.</span><span class="sxs-lookup"><span data-stu-id="43e7d-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="43e7d-146">Użytkownicy systemu Windows 10, należy zainstalować najnowsze aktualizacje funkcji, aby uzyskać bieżącą wersję środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43e7d-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="43e7d-147">Włączanie komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="43e7d-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="43e7d-148">Komunikacja zdalna programu PowerShell zapewnia podstawę, na którym bazuje JEA.</span><span class="sxs-lookup"><span data-stu-id="43e7d-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="43e7d-149">Jest to niezbędne do zapewnienia komunikacji zdalnej programu PowerShell jest włączona i odpowiednio zabezpieczony, zanim będzie można użyć technologii JEA.</span><span class="sxs-lookup"><span data-stu-id="43e7d-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="43e7d-150">Aby uzyskać więcej informacji, zobacz [zabezpieczeń WinRM](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="43e7d-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="43e7d-151">Komunikacja zdalna programu PowerShell jest włączona domyślnie w systemie Windows Server 2012, 2012 R2 i 2016.</span><span class="sxs-lookup"><span data-stu-id="43e7d-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="43e7d-152">Komunikacja zdalna programu PowerShell można włączyć, uruchamiając następujące polecenie w oknie programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="43e7d-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="43e7d-153">Włączanie rejestrowania blok skryptu jest (opcjonalnie) i moduł programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="43e7d-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="43e7d-154">Następujące kroki włączyć rejestrowanie dla wszystkich akcji programu PowerShell w systemie.</span><span class="sxs-lookup"><span data-stu-id="43e7d-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="43e7d-155">Rejestrowanie modułu programu PowerShell nie jest wymagana dla usługi JEA, jednak zaleca się, że włączyć rejestrowanie, aby upewnić się, że użytkownicy polecenia uruchamiają są rejestrowane w centralnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="43e7d-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="43e7d-156">Można skonfigurować zasad logowania modułu programu PowerShell, za pomocą zasad grupy.</span><span class="sxs-lookup"><span data-stu-id="43e7d-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="43e7d-157">Otwórz Edytor lokalnych zasad grupy na stacji roboczej lub obiektu zasad grupy w konsoli zarządzania zasadami grupy na kontrolerze domeny usługi Active Directory</span><span class="sxs-lookup"><span data-stu-id="43e7d-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="43e7d-158">Przejdź do **konfiguracji komputera\\Szablony administracyjne\\składników Windows\\programu Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="43e7d-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="43e7d-159">Kliknij dwukrotnie **Włączanie logowania modułu**</span><span class="sxs-lookup"><span data-stu-id="43e7d-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="43e7d-160">Kliknij przycisk **włączone**</span><span class="sxs-lookup"><span data-stu-id="43e7d-160">Click **Enabled**</span></span>
5. <span data-ttu-id="43e7d-161">W sekcji Opcje kliknąć **Pokaż** obok nazwy modułu</span><span class="sxs-lookup"><span data-stu-id="43e7d-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="43e7d-162">Typ `*` w oknie podręcznym logowania polecenia ze wszystkich modułów.</span><span class="sxs-lookup"><span data-stu-id="43e7d-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="43e7d-163">Kliknij przycisk **OK** do ustawiania zasad</span><span class="sxs-lookup"><span data-stu-id="43e7d-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="43e7d-164">Kliknij dwukrotnie **włączyć w bloku skryptu środowiska PowerShell rejestrowania**</span><span class="sxs-lookup"><span data-stu-id="43e7d-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="43e7d-165">Kliknij przycisk **włączone**</span><span class="sxs-lookup"><span data-stu-id="43e7d-165">Click **Enabled**</span></span>
10. <span data-ttu-id="43e7d-166">Kliknij przycisk **OK** do ustawiania zasad</span><span class="sxs-lookup"><span data-stu-id="43e7d-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="43e7d-167">(W przypadku przyłączonych do domeny komputerów tylko) Uruchom `gpupdate` lub zaczekaj na przetwarzanie zaktualizowane zasady i zastosować ustawienia zasad grupy</span><span class="sxs-lookup"><span data-stu-id="43e7d-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="43e7d-168">Można również włączyć transkrypcji PowerShell całego systemu za pomocą zasad grupy.</span><span class="sxs-lookup"><span data-stu-id="43e7d-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="43e7d-169">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="43e7d-169">Next steps</span></span>

[<span data-ttu-id="43e7d-170">Utwórz plik możliwości roli</span><span class="sxs-lookup"><span data-stu-id="43e7d-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="43e7d-171">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="43e7d-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="43e7d-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43e7d-172">See also</span></span>

[<span data-ttu-id="43e7d-173">Zabezpieczenia usługi WinRM</span><span class="sxs-lookup"><span data-stu-id="43e7d-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="43e7d-174">Program PowerShell ♥ zespołem niebieskim</span><span class="sxs-lookup"><span data-stu-id="43e7d-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
