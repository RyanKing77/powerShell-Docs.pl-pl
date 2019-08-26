---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Wymagania wstępne JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017937"
---
# <a name="prerequisites"></a><span data-ttu-id="cc961-103">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="cc961-103">Prerequisites</span></span>

<span data-ttu-id="cc961-104">Wystarczy, że jest dostępna funkcja programu PowerShell w wersji 5,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="cc961-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="cc961-105">W tym artykule opisano wymagania wstępne, które należy spełnić, aby rozpocząć korzystanie z usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="cc961-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="cc961-106">Sprawdź, która wersja programu PowerShell jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="cc961-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="cc961-107">Aby sprawdzić, która wersja programu PowerShell jest zainstalowana w systemie, sprawdź `$PSVersionTable` zmienną w wierszu polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc961-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="cc961-108">JEA jest dostępny w programie PowerShell 5,0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="cc961-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="cc961-109">W celu zapewnienia pełnej funkcjonalności zaleca się zainstalowanie najnowszej wersji programu PowerShell dostępnej dla danego systemu.</span><span class="sxs-lookup"><span data-stu-id="cc961-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="cc961-110">W poniższej tabeli opisano dostępność JEA w systemie Windows Server:</span><span class="sxs-lookup"><span data-stu-id="cc961-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="cc961-111">System operacyjny serwera</span><span class="sxs-lookup"><span data-stu-id="cc961-111">Server Operating System</span></span> |                <span data-ttu-id="cc961-112">Dostępność JEA</span><span class="sxs-lookup"><span data-stu-id="cc961-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="cc961-113">Windows Server 2016 +</span><span class="sxs-lookup"><span data-stu-id="cc961-113">Windows Server 2016+</span></span>    | <span data-ttu-id="cc961-114">Wstępnie zainstalowane</span><span class="sxs-lookup"><span data-stu-id="cc961-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="cc961-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="cc961-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="cc961-116">Pełna funkcjonalność z funkcją WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="cc961-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="cc961-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="cc961-117">Windows Server 2012</span></span>     | <span data-ttu-id="cc961-118">Pełna funkcjonalność z funkcją WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="cc961-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="cc961-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="cc961-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="cc961-120">Zredukowanie funkcjonalności<sup>1</sup> przy użyciu programu WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="cc961-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="cc961-121">Możesz również użyć JEA na komputerze w domu lub pracy:</span><span class="sxs-lookup"><span data-stu-id="cc961-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="cc961-122">System operacyjny klienta</span><span class="sxs-lookup"><span data-stu-id="cc961-122">Client Operating System</span></span> |                   <span data-ttu-id="cc961-123">Dostępność JEA</span><span class="sxs-lookup"><span data-stu-id="cc961-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="cc961-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="cc961-124">Windows 10 1607+</span></span>        | <span data-ttu-id="cc961-125">Wstępnie zainstalowane</span><span class="sxs-lookup"><span data-stu-id="cc961-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="cc961-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="cc961-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="cc961-127">Preinstalacja z ograniczoną funkcjonalnością<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cc961-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="cc961-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="cc961-128">Windows 10 1507</span></span>         | <span data-ttu-id="cc961-129">Niedostępne</span><span class="sxs-lookup"><span data-stu-id="cc961-129">Not available</span></span>                                        |
| <span data-ttu-id="cc961-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="cc961-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="cc961-131">Pełna funkcjonalność z funkcją WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="cc961-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="cc961-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="cc961-132">Windows 7</span></span>               | <span data-ttu-id="cc961-133">Zredukowanie funkcjonalności<sup>1</sup> przy użyciu programu WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="cc961-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="cc961-134"><sup>1</sup> jea nie można skonfigurować do korzystania z kont usług zarządzanych przez grupę w systemie windows Server 2008 R2 lub Windows 7.</span><span class="sxs-lookup"><span data-stu-id="cc961-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="cc961-135">Obsługiwane *są* konta wirtualne i inne funkcje jea.</span><span class="sxs-lookup"><span data-stu-id="cc961-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="cc961-136"><sup>2</sup> następujące funkcje jea nie są obsługiwane w systemie Windows 10 w wersji 1511 i 1603:</span><span class="sxs-lookup"><span data-stu-id="cc961-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="cc961-137">Uruchamianie jako konto usługi zarządzane przez grupę</span><span class="sxs-lookup"><span data-stu-id="cc961-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="cc961-138">Reguły dostępu warunkowego w konfiguracjach sesji</span><span class="sxs-lookup"><span data-stu-id="cc961-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="cc961-139">Dysk użytkownika</span><span class="sxs-lookup"><span data-stu-id="cc961-139">The user drive</span></span>
  - <span data-ttu-id="cc961-140">Udzielanie dostępu do kont użytkowników lokalnych</span><span class="sxs-lookup"><span data-stu-id="cc961-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="cc961-141">Aby uzyskać pomoc techniczną dotyczącą tych funkcji, zaktualizuj system Windows do wersji 1607 (Aktualizacja z rocznicą) lub wyższą.</span><span class="sxs-lookup"><span data-stu-id="cc961-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="cc961-142">Zainstaluj program Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="cc961-142">Install Windows Management Framework</span></span>

<span data-ttu-id="cc961-143">Jeśli używasz starszej wersji programu PowerShell, może być konieczne zaktualizowanie systemu przy użyciu najnowszej aktualizacji Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="cc961-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="cc961-144">Aby uzyskać więcej informacji, zobacz [dokumentację dotyczącą WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="cc961-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="cc961-145">Zaleca się przetestowanie zgodności obciążenia z pakietem WMF przed uaktualnieniem wszystkich serwerów.</span><span class="sxs-lookup"><span data-stu-id="cc961-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="cc961-146">Użytkownicy systemu Windows 10 powinni zainstalować najnowsze aktualizacje funkcji, aby uzyskać aktualną wersję programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc961-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="cc961-147">Włącz obsługę zdalną programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc961-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="cc961-148">Komunikacja zdalna programu PowerShell zapewnia podstawę, na której jest zbudowany JEA.</span><span class="sxs-lookup"><span data-stu-id="cc961-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="cc961-149">Jest to konieczne, aby zapewnić, że komunikacja zdalna programu PowerShell jest włączona i prawidłowo zabezpieczona przed użyciem JEA.</span><span class="sxs-lookup"><span data-stu-id="cc961-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="cc961-150">Aby uzyskać więcej informacji, zobacz [zabezpieczenia usługi WinRM](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="cc961-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="cc961-151">Komunikacja zdalna programu PowerShell jest domyślnie włączona w systemach Windows Server 2012, 2012 R2 i 2016.</span><span class="sxs-lookup"><span data-stu-id="cc961-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="cc961-152">Aby włączyć obsługę zdalną programu PowerShell, należy uruchomić następujące polecenie w oknie programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="cc961-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="cc961-153">Włącz rejestrowanie bloków skryptów i modułów programu PowerShell (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="cc961-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="cc961-154">Poniższe kroki umożliwiają rejestrowanie wszystkich akcji programu PowerShell w systemie.</span><span class="sxs-lookup"><span data-stu-id="cc961-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="cc961-155">Rejestrowanie modułu programu PowerShell nie jest wymagane dla JEA, jednak zaleca się włączenie rejestrowania, aby upewnić się, że polecenia uruchamiane przez użytkowników są rejestrowane w centralnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="cc961-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="cc961-156">Zasady rejestrowania modułu programu PowerShell można skonfigurować przy użyciu zasady grupy.</span><span class="sxs-lookup"><span data-stu-id="cc961-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="cc961-157">Otwórz Edytor lokalnych zasad grupy na stacji roboczej lub obiekcie zasady grupy w Konsola zarządzania zasadami grupy na kontrolerze domena usługi Active Directory</span><span class="sxs-lookup"><span data-stu-id="cc961-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="cc961-158">Przejdź do **\\konfiguracji komputera Szablony administracyjne\\\\składniki systemu Windows Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="cc961-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="cc961-159">Kliknij dwukrotnie pozycję **Włącz rejestrowanie modułu**</span><span class="sxs-lookup"><span data-stu-id="cc961-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="cc961-160">Kliknij pozycję **włączone**</span><span class="sxs-lookup"><span data-stu-id="cc961-160">Click **Enabled**</span></span>
5. <span data-ttu-id="cc961-161">W sekcji Opcje kliknij pozycję **Pokaż** obok pozycji nazwy modułów</span><span class="sxs-lookup"><span data-stu-id="cc961-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="cc961-162">Wpisz `*` w oknie podręcznym, aby rejestrować polecenia ze wszystkich modułów.</span><span class="sxs-lookup"><span data-stu-id="cc961-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="cc961-163">Kliknij przycisk **OK** , aby ustawić zasady</span><span class="sxs-lookup"><span data-stu-id="cc961-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="cc961-164">Kliknij dwukrotnie pozycję **Włącz rejestrowanie bloku skryptu programu PowerShell**</span><span class="sxs-lookup"><span data-stu-id="cc961-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="cc961-165">Kliknij pozycję **włączone**</span><span class="sxs-lookup"><span data-stu-id="cc961-165">Click **Enabled**</span></span>
10. <span data-ttu-id="cc961-166">Kliknij przycisk **OK** , aby ustawić zasady</span><span class="sxs-lookup"><span data-stu-id="cc961-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="cc961-167">(Tylko w przypadku komputerów przyłączonych do domeny) Uruchom `gpupdate` lub zaczekaj na zasady grupy, aby przetworzyć zaktualizowane zasady i zastosować ustawienia</span><span class="sxs-lookup"><span data-stu-id="cc961-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="cc961-168">Można również włączyć transkrypcję programu PowerShell dla całego systemu za poorednictwem zasady grupy.</span><span class="sxs-lookup"><span data-stu-id="cc961-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cc961-169">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="cc961-169">Next steps</span></span>

[<span data-ttu-id="cc961-170">Utwórz plik możliwości roli</span><span class="sxs-lookup"><span data-stu-id="cc961-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="cc961-171">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="cc961-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="cc961-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc961-172">See also</span></span>

[<span data-ttu-id="cc961-173">Zabezpieczenia usługi WinRM</span><span class="sxs-lookup"><span data-stu-id="cc961-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="cc961-174">Program PowerShell ♥ niebieskiego zespołu</span><span class="sxs-lookup"><span data-stu-id="cc961-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
