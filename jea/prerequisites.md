---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, programu powershell, zabezpieczeń"
title: "Wymagania wstępne JEA"
ms.openlocfilehash: e6ee16e34eb9f1f0b2f3601c1aa9e90ab4f785f1
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="prerequisites"></a><span data-ttu-id="d7c69-103">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d7c69-103">Prerequisites</span></span>

> <span data-ttu-id="d7c69-104">Dotyczy: środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d7c69-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d7c69-105">Tylko tyle administracji jest to funkcja dostępna z programu Windows PowerShell 5.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="d7c69-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="d7c69-106">W tym temacie opisano wymagania wstępne, które muszą być spełnione, aby rozpocząć korzystanie z JEA.</span><span class="sxs-lookup"><span data-stu-id="d7c69-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="d7c69-107">Zainstaluj JEA</span><span class="sxs-lookup"><span data-stu-id="d7c69-107">Install JEA</span></span>

<span data-ttu-id="d7c69-108">Technologia JEA jest dostępna w programie Windows PowerShell 5.0 lub nowszej, ale do pełnego zestawu funkcji zalecane jest, zainstaluj najnowszą wersję programu PowerShell, dostępna dla systemu.</span><span class="sxs-lookup"><span data-stu-id="d7c69-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="d7c69-109">W poniższej tabeli opisano w JEA dostępności w systemie Windows Server:</span><span class="sxs-lookup"><span data-stu-id="d7c69-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="d7c69-110">System operacyjny serwera</span><span class="sxs-lookup"><span data-stu-id="d7c69-110">Server Operating System</span></span>   | <span data-ttu-id="d7c69-111">Dostępność JEA</span><span class="sxs-lookup"><span data-stu-id="d7c69-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="d7c69-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d7c69-112">Windows Server 2016</span></span>       | <span data-ttu-id="d7c69-113">Preinstalowane</span><span class="sxs-lookup"><span data-stu-id="d7c69-113">Preinstalled</span></span>
<span data-ttu-id="d7c69-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d7c69-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="d7c69-115">Pełnej funkcjonalności z WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d7c69-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="d7c69-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d7c69-116">Windows Server 2012</span></span>       | <span data-ttu-id="d7c69-117">Pełnej funkcjonalności z WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d7c69-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="d7c69-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="d7c69-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="d7c69-119">Funkcjonalność ograniczona<sup>1</sup> z WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d7c69-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="d7c69-120">Można także użyć JEA na komputerze domowej lub firmowej:</span><span class="sxs-lookup"><span data-stu-id="d7c69-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="d7c69-121">System operacyjny klienta</span><span class="sxs-lookup"><span data-stu-id="d7c69-121">Client Operating System</span></span>   | <span data-ttu-id="d7c69-122">Dostępność JEA</span><span class="sxs-lookup"><span data-stu-id="d7c69-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="d7c69-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="d7c69-123">Windows 10 1607+</span></span>          | <span data-ttu-id="d7c69-124">Preinstalowane</span><span class="sxs-lookup"><span data-stu-id="d7c69-124">Preinstalled</span></span>
<span data-ttu-id="d7c69-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="d7c69-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="d7c69-126">Preinstalowane, dzięki ograniczone funkcje<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d7c69-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="d7c69-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="d7c69-127">Windows 10 1507</span></span>           | <span data-ttu-id="d7c69-128">Niedostępne</span><span class="sxs-lookup"><span data-stu-id="d7c69-128">Not available</span></span>
<span data-ttu-id="d7c69-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="d7c69-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="d7c69-130">Pełnej funkcjonalności z WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d7c69-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="d7c69-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="d7c69-131">Windows 7</span></span>                 | <span data-ttu-id="d7c69-132">Funkcjonalność ograniczona<sup>1</sup> z WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d7c69-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="d7c69-133"><sup>1</sup> JEA nie może być skonfigurowana do używania konta usług zarządzane przez grupę w systemie Windows Server 2008 R2 lub Windows 7.</span><span class="sxs-lookup"><span data-stu-id="d7c69-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="d7c69-134">Kont wirtualnych i inne funkcje JEA *są* obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d7c69-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="d7c69-135"><sup>2</sup> systemu Windows 10 w wersji 1511 i 1603 nie obsługują następujące funkcje JEA: uruchamianie zgodnie z grupą zarządzane konto usługi, zasady dostępu warunkowego w konfiguracji sesji, dysku użytkownika i udzielenie dostępu do kont użytkowników lokalnych.</span><span class="sxs-lookup"><span data-stu-id="d7c69-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="d7c69-136">Aby uzyskać pomoc techniczną dla tych funkcji, należy zaktualizować system Windows do wersji 1607 (rocznicy aktualizacji) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="d7c69-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="d7c69-137">Sprawdź, która wersja programu PowerShell jest zainstalowany</span><span class="sxs-lookup"><span data-stu-id="d7c69-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="d7c69-138">Aby sprawdzić, która wersja programu PowerShell jest zainstalowana w systemie, sprawdź `$PSVersionTable` zmiennej w wierszu polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7c69-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="d7c69-139">Wszystko jest gotowe do użycia JEA, jeśli *głównych* wersja jest równa lub większa niż **5**.</span><span class="sxs-lookup"><span data-stu-id="d7c69-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="d7c69-140">Aby uzyskać najlepsze wyniki, a dostęp do najnowszych funkcji, zaleca się uaktualnienie do wersji programu PowerShell **5.1** Jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="d7c69-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="d7c69-141">Zainstaluj oprogramowanie Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="d7c69-141">Install Windows Management Framework</span></span>

<span data-ttu-id="d7c69-142">Jeśli używasz starszej wersji programu PowerShell, należy zaktualizować system z najnowszą aktualizacją Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="d7c69-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="d7c69-143">Pakiety aktualizacji i łącze do najnowszej wersji platformy WMF są dostępne w [Centrum pobierania](https://aka.ms/WMF5).</span><span class="sxs-lookup"><span data-stu-id="d7c69-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://aka.ms/WMF5).</span></span>

<span data-ttu-id="d7c69-144">Zdecydowanie zaleca się przetestowanie Twoje obciążenie zgodność z WMF przed uaktualnieniem wszystkich serwerów.</span><span class="sxs-lookup"><span data-stu-id="d7c69-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="d7c69-145">Użytkownicy systemu Windows 10 należy zainstalować najnowsze aktualizacje funkcji, aby uzyskać bieżącą wersję środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7c69-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="d7c69-146">Włącz obsługę zdalną środowiska PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7c69-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="d7c69-147">Obsługę zdalną środowiska PowerShell stanowi podstawę, na którym jest oparty JEA.</span><span class="sxs-lookup"><span data-stu-id="d7c69-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="d7c69-148">W związku z tym jest to niezbędne do zapewnienia komunikacji zdalnej programu PowerShell jest włączona i [zabezpieczenie](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) w systemie, zanim będzie możliwe użycie JEA.</span><span class="sxs-lookup"><span data-stu-id="d7c69-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="d7c69-149">Usługi zdalne środowiska PowerShell jest włączona domyślnie w systemie Windows Server 2012 i 2012 R2, 2016.</span><span class="sxs-lookup"><span data-stu-id="d7c69-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="d7c69-150">Można włączyć obsługę zdalną środowiska PowerShell, uruchamiając następujące polecenie w oknie programu PowerShell z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="d7c69-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="d7c69-151">Włączanie rejestrowania bloku skryptu (opcjonalnie) i moduł programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7c69-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="d7c69-152">Poniższe kroki należy włączyć rejestrowanie dla wszystkich działań programu PowerShell w systemie.</span><span class="sxs-lookup"><span data-stu-id="d7c69-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="d7c69-153">Rejestrowanie modułu programu PowerShell nie jest wymagane dla JEA, jednak zalecane jest włączenie go w celu upewnij się, że użytkownicy poleceń uruchom są rejestrowane w centralnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d7c69-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="d7c69-154">Można skonfigurować za pomocą zasad grupy zasady logowania modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7c69-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="d7c69-155">Otwórz Edytor lokalnych zasad grupy na stacji roboczej lub obiektu zasad grupy w konsoli zarządzania zasadami grupy na kontrolerze domeny usługi Active Directory</span><span class="sxs-lookup"><span data-stu-id="d7c69-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="d7c69-156">Przejdź do **Konfiguracja komputera\\Szablony administracyjne\\składniki systemu Windows\\środowiska Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="d7c69-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="d7c69-157">Kliknij dwukrotnie **Włącz rejestrowanie modułu**</span><span class="sxs-lookup"><span data-stu-id="d7c69-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="d7c69-158">Kliknij przycisk **włączone**</span><span class="sxs-lookup"><span data-stu-id="d7c69-158">Click **Enabled**</span></span>
5. <span data-ttu-id="d7c69-159">W sekcji Opcje, kliknij polecenie **Pokaż** obok nazwy modułu</span><span class="sxs-lookup"><span data-stu-id="d7c69-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="d7c69-160">Typ "**\***" w wyświetlonym oknie.</span><span class="sxs-lookup"><span data-stu-id="d7c69-160">Type "**\***" in the pop up window.</span></span> <span data-ttu-id="d7c69-161">To powoduje, że programu PowerShell do rejestrowania poleceń ze wszystkich modułów.</span><span class="sxs-lookup"><span data-stu-id="d7c69-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="d7c69-162">Kliknij przycisk **OK** ustawić zasad</span><span class="sxs-lookup"><span data-stu-id="d7c69-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="d7c69-163">Kliknij dwukrotnie **Włącz rejestrowanie bloku skryptu PowerShell**</span><span class="sxs-lookup"><span data-stu-id="d7c69-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="d7c69-164">Kliknij przycisk **włączone**</span><span class="sxs-lookup"><span data-stu-id="d7c69-164">Click **Enabled**</span></span>
10. <span data-ttu-id="d7c69-165">Kliknij przycisk **OK** ustawić zasad</span><span class="sxs-lookup"><span data-stu-id="d7c69-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="d7c69-166">(Maszynach przyłączonych do domeny jedynie) Uruchom **gpupdate** lub zaczekaj na mają zostać zaktualizowane zasady przetwarzania i stosować ustawienia zasad grupy</span><span class="sxs-lookup"><span data-stu-id="d7c69-166">(On domain-joined machines only) Run **gpupdate** or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="d7c69-167">Można również włączyć przekształcania PowerShell całego systemu za pomocą zasad grupy.</span><span class="sxs-lookup"><span data-stu-id="d7c69-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d7c69-168">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d7c69-168">Next steps</span></span>

- [<span data-ttu-id="d7c69-169">Utwórz plik możliwości roli</span><span class="sxs-lookup"><span data-stu-id="d7c69-169">Create a role capability file</span></span>](role-capabilities.md)
- [<span data-ttu-id="d7c69-170">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="d7c69-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="d7c69-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7c69-171">See also</span></span>

- [<span data-ttu-id="d7c69-172">Dodatkowe informacje o zabezpieczeniach usługi zdalne środowiska PowerShell i usługi WinRM</span><span class="sxs-lookup"><span data-stu-id="d7c69-172">Additional information about PowerShell Remoting and WinRM security</span></span>](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [<span data-ttu-id="d7c69-173">*PowerShell ♥ niebieski zespołu* wpis w blogu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d7c69-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

