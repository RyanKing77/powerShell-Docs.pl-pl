---
ms.date: 08/23/2017
keywords: polecenia cmdlet programu PowerShell
title: Rozwiązywanie problemów z dostępem w programie windows powershell web access
ms.openlocfilehash: ef476d8e386e5380cb2c9dda69180dfce8748bf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="56ba9-103">Rozwiązywanie problemów z programem Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="56ba9-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="56ba9-104">Aktualizacja: 24 czerwiec 2013 (zaktualizowany 23 sierpnia 2017 r.)</span><span class="sxs-lookup"><span data-stu-id="56ba9-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="56ba9-105">Dotyczy: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="56ba9-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="56ba9-106">W poniższych sekcjach zidentyfikować niektóre typowe problemy podczas próby nawiązania połączenia z komputerem zdalnym za pomocą programu Windows PowerShell Web Access i zawiera sugestie dotyczące rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="56ba9-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="56ba9-107">Błąd logowania</span><span class="sxs-lookup"><span data-stu-id="56ba9-107">Sign-in failure</span></span>

<span data-ttu-id="56ba9-108">Błąd logowania może wystąpić z następujących powodów.</span><span class="sxs-lookup"><span data-stu-id="56ba9-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="56ba9-109">Nie istnieje reguła autoryzacji umożliwiająca użytkownikowi dostęp do komputera ani konfiguracja określonej sesji na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="56ba9-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="56ba9-110">Zabezpieczenia programu Windows PowerShell Web Access jest restrykcyjna; Użytkownicy muszą otrzymać jawny dostęp do komputerów zdalnych przy użyciu reguł autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="56ba9-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="56ba9-111">Aby uzyskać więcej informacji na temat tworzenia reguł autoryzacji, zobacz [reguł autoryzacji i zabezpieczeń funkcje programu Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="56ba9-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="56ba9-112">Użytkownik nie ma autoryzowanego dostępu do komputera docelowego.</span><span class="sxs-lookup"><span data-stu-id="56ba9-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="56ba9-113">Jest to określane za pomocą list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="56ba9-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="56ba9-114">Aby uzyskać więcej informacji, zobacz [rejestrowania się w programie Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), lub Blog zespołu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56ba9-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="56ba9-115">Zdalne zarządzanie programu Windows PowerShell może nie być włączone na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="56ba9-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="56ba9-116">Sprawdź, czy zdalne zarządzanie jest włączone na komputerze, z którym użytkownik próbuje się połączyć.</span><span class="sxs-lookup"><span data-stu-id="56ba9-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="56ba9-117">Aby uzyskać więcej informacji, zobacz [jak skonfigurować komputer dla niego komunikację zdalną](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="56ba9-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="56ba9-118">Wewnętrzny błąd serwera</span><span class="sxs-lookup"><span data-stu-id="56ba9-118">Internal Server Error</span></span>

<span data-ttu-id="56ba9-119">Gdy użytkownicy próbują zalogować się do programu Windows PowerShell Web Access w oknie programu Internet Explorer, są one wyświetlane **wewnętrzny błąd serwera** strony, lub *programu Internet Explorer* przestaje odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="56ba9-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="56ba9-120">Ten problem dotyczy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="56ba9-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="56ba9-121">Możliwa przyczyna</span><span class="sxs-lookup"><span data-stu-id="56ba9-121">Possible cause</span></span>

<span data-ttu-id="56ba9-122">Taka sytuacja może wystąpić w przypadku użytkowników, którzy zalogowali się przy użyciu nazwy domeny zawierającej znaki w języku chińskim, lub jeśli nazwa serwera bramy zawiera co najmniej jeden znak w języku chińskim.</span><span class="sxs-lookup"><span data-stu-id="56ba9-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="56ba9-123">Obejście problemu</span><span class="sxs-lookup"><span data-stu-id="56ba9-123">Workaround</span></span>

1. [<span data-ttu-id="56ba9-124">Zainstaluj i uruchom program Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="56ba9-124">Install and run Internet Explorer 10</span></span>](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="56ba9-125">Zmień programu Internet Explorer **tryb dokumentu** ustawienie *IE10* standardów.</span><span class="sxs-lookup"><span data-stu-id="56ba9-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="56ba9-126">Naciśnij klawisz **F12** aby otworzyć konsolę narzędzia deweloperskie</span><span class="sxs-lookup"><span data-stu-id="56ba9-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="56ba9-127">W programie Internet Explorer 10 kliknij **tryb przeglądarki**, a następnie wybierz *programu Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="56ba9-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="56ba9-128">Kliknij przycisk **tryb dokumentu**, a następnie kliknij przycisk *IE10* standardów.</span><span class="sxs-lookup"><span data-stu-id="56ba9-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="56ba9-129">Naciśnij klawisz **F12** ponownie, aby zamknąć konsolę narzędzia deweloperskie.</span><span class="sxs-lookup"><span data-stu-id="56ba9-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="56ba9-130">Wyłącz konfigurację automatyczną serwera proxy w programie Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="56ba9-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="56ba9-131">Kliknij przycisk **narzędzia**, a następnie kliknij przycisk **Opcje internetowe**.</span><span class="sxs-lookup"><span data-stu-id="56ba9-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="56ba9-132">W **Opcje internetowe** na okna dialogowego **połączeń** , kliknij pozycję **ustawienia sieci LAN**.</span><span class="sxs-lookup"><span data-stu-id="56ba9-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="56ba9-133">Wyczyść **Automatycznie wykryj ustawienia** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="56ba9-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="56ba9-134">Kliknij przycisk **OK**, a następnie kliknij przycisk **OK** ponownie, aby zamknąć *Opcje internetowe* okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="56ba9-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="56ba9-135">Nie można nawiązać połączenia ze zdalnym komputerem grupy roboczej</span><span class="sxs-lookup"><span data-stu-id="56ba9-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="56ba9-136">Jeśli komputer docelowy jest członkiem grupy roboczej, aby podać nazwę użytkownika i zaloguj się do komputera należy użyć następującej składni: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="56ba9-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="56ba9-137">Nie można odnaleźć narzędzi do zarządzania serwerem sieci Web (IIS), nawet jeśli rola została zainstalowana</span><span class="sxs-lookup"><span data-stu-id="56ba9-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="56ba9-138">Po zainstalowaniu programu Windows PowerShell Web Access za pomocą `Install-WindowsFeature` polecenia cmdlet, o ile nie są zainstalowane narzędzia zarządzania `-IncludeManagementTools` do polecenia cmdlet zostanie dodany parametr.</span><span class="sxs-lookup"><span data-stu-id="56ba9-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="56ba9-139">Na przykład zobacz [do zainstalowania programu Windows PowerShell Web Access za pomocą poleceń cmdlet programu Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="56ba9-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="56ba9-140">Umożliwia dodanie konsoli Menedżer usług IIS i zarządzania usługami IIS w innych narzędzi, potrzebnych, przez wybranie narzędzi w **Kreatora dodawania ról i funkcji** sesji, która jest skierowana na serwer bramy.</span><span class="sxs-lookup"><span data-stu-id="56ba9-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="56ba9-141">Dodaj role i funkcje kreatora jest otwierany z Menedżera serwera.</span><span class="sxs-lookup"><span data-stu-id="56ba9-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="56ba9-142">Witryny sieci Web Windows PowerShell Web Access jest niedostępny</span><span class="sxs-lookup"><span data-stu-id="56ba9-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="56ba9-143">Jeśli Konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer (nazywana konfiguracją IE ESC), możesz dodać witrynę sieci Web Windows PowerShell Web Access do listy zaufanych witryn.</span><span class="sxs-lookup"><span data-stu-id="56ba9-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="56ba9-144">Jest mniej zalecane podejście, ze względu na zagrożenia bezpieczeństwa, aby wyłączyć konfigurację IE ESC.</span><span class="sxs-lookup"><span data-stu-id="56ba9-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="56ba9-145">Konfigurację IE ESC można wyłączyć na kafelku właściwości na stronie serwera lokalnego w Menedżerze serwera.</span><span class="sxs-lookup"><span data-stu-id="56ba9-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="56ba9-146">Wystąpił błąd autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="56ba9-146">An authorization failure occurred.</span></span> <span data-ttu-id="56ba9-147">Upewnij się, że masz uprawnienia do nawiązania połączenia z komputerem docelowym.</span><span class="sxs-lookup"><span data-stu-id="56ba9-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="56ba9-148">Powyżej komunikat o błędzie jest wyświetlany podczas próby nawiązania połączenia, gdy serwer bramy jest komputerem docelowym oraz należy w grupie roboczej.</span><span class="sxs-lookup"><span data-stu-id="56ba9-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="56ba9-149">Gdy serwer bramy jest również serwerem docelowym i jest w grupie roboczej, określ nazwę użytkownika, nazwę komputera i nazwę grupy użytkowników.</span><span class="sxs-lookup"><span data-stu-id="56ba9-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="56ba9-150">Nie należy używać pojedynczego znaku kropki (.) przez samego siebie do reprezentowania nazwy komputera.</span><span class="sxs-lookup"><span data-stu-id="56ba9-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="56ba9-151">Scenariusze i odpowiednie wartości</span><span class="sxs-lookup"><span data-stu-id="56ba9-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="56ba9-152">Wszystkich przypadkach</span><span class="sxs-lookup"><span data-stu-id="56ba9-152">All cases</span></span>

<span data-ttu-id="56ba9-153">Parametr</span><span class="sxs-lookup"><span data-stu-id="56ba9-153">Parameter</span></span> | <span data-ttu-id="56ba9-154">Wartość</span><span class="sxs-lookup"><span data-stu-id="56ba9-154">Value</span></span>
-- | --
<span data-ttu-id="56ba9-155">UserName</span><span class="sxs-lookup"><span data-stu-id="56ba9-155">UserName</span></span> | <span data-ttu-id="56ba9-156">Serwer\_nazwa\\użytkownika\_nazwy</span><span class="sxs-lookup"><span data-stu-id="56ba9-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="56ba9-157">Localhost\\użytkownika\_nazwy</span><span class="sxs-lookup"><span data-stu-id="56ba9-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="56ba9-158">. \\użytkownika\_nazwy</span><span class="sxs-lookup"><span data-stu-id="56ba9-158">.\\user\_name</span></span>
<span data-ttu-id="56ba9-159">Grupa_użytkowników</span><span class="sxs-lookup"><span data-stu-id="56ba9-159">UserGroup</span></span> | <span data-ttu-id="56ba9-160">Serwer\_nazwa\\użytkownika\_grupy</span><span class="sxs-lookup"><span data-stu-id="56ba9-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="56ba9-161">Localhost\\użytkownika\_grupy</span><span class="sxs-lookup"><span data-stu-id="56ba9-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="56ba9-162">. \\użytkownika\_grupy</span><span class="sxs-lookup"><span data-stu-id="56ba9-162">.\\user\_group</span></span>
<span data-ttu-id="56ba9-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="56ba9-163">ComputerGroup</span></span> | <span data-ttu-id="56ba9-164">Server\_name\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="56ba9-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="56ba9-165">Localhost\\komputera\_grupy</span><span class="sxs-lookup"><span data-stu-id="56ba9-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="56ba9-166">. \\komputera\_grupy</span><span class="sxs-lookup"><span data-stu-id="56ba9-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="56ba9-167">Serwer bramy znajduje się w domenie</span><span class="sxs-lookup"><span data-stu-id="56ba9-167">Gateway server is in a domain</span></span>

<span data-ttu-id="56ba9-168">Parametr</span><span class="sxs-lookup"><span data-stu-id="56ba9-168">Parameter</span></span> | <span data-ttu-id="56ba9-169">Wartość</span><span class="sxs-lookup"><span data-stu-id="56ba9-169">Value</span></span>
-- | --
<span data-ttu-id="56ba9-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="56ba9-170">ComputerName</span></span> | <span data-ttu-id="56ba9-171">W pełni kwalifikowana nazwa serwera bramy lub Localhost</span><span class="sxs-lookup"><span data-stu-id="56ba9-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="56ba9-172">Serwer bramy znajduje się w grupie roboczej</span><span class="sxs-lookup"><span data-stu-id="56ba9-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="56ba9-173">Parametr</span><span class="sxs-lookup"><span data-stu-id="56ba9-173">Parameter</span></span> | <span data-ttu-id="56ba9-174">Wartość</span><span class="sxs-lookup"><span data-stu-id="56ba9-174">Value</span></span>
-- | --
<span data-ttu-id="56ba9-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="56ba9-175">ComputerName</span></span> | <span data-ttu-id="56ba9-176">Nazwa serwera</span><span class="sxs-lookup"><span data-stu-id="56ba9-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="56ba9-177">Poświadczeń bramy</span><span class="sxs-lookup"><span data-stu-id="56ba9-177">Gateway credentials</span></span>

<span data-ttu-id="56ba9-178">Zaloguj się do serwera bramy jako komputera docelowego przy użyciu poświadczeń sformatowanych w jeden z następujących sposobów.</span><span class="sxs-lookup"><span data-stu-id="56ba9-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="56ba9-179">Serwer\_nazwa\\użytkownika\_nazwy</span><span class="sxs-lookup"><span data-stu-id="56ba9-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="56ba9-180">Localhost\\użytkownika\_nazwy</span><span class="sxs-lookup"><span data-stu-id="56ba9-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="56ba9-181">. \\użytkownika\_nazwy</span><span class="sxs-lookup"><span data-stu-id="56ba9-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="56ba9-182">Identyfikator zabezpieczeń (SID) jest wyświetlany w regule autoryzacji</span><span class="sxs-lookup"><span data-stu-id="56ba9-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="56ba9-183">Identyfikator zabezpieczeń (SID) jest wyświetlany w regule autoryzacji zamiast składni użytkownika\_nazwy i komputera\_nazwy.</span><span class="sxs-lookup"><span data-stu-id="56ba9-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="56ba9-184">Reguła nie jest już prawidłowa lub zapytanie usług domenowych Active Directory nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="56ba9-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="56ba9-185">Zazwyczaj reguły autoryzacji nie jest prawidłowa w sytuacji, gdy serwer bramy należał do grupy roboczej, ale później został przyłączony do domeny</span><span class="sxs-lookup"><span data-stu-id="56ba9-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="56ba9-186">Nie można zarejestrować się przy użyciu reguły jako adres IPv6 z domeną</span><span class="sxs-lookup"><span data-stu-id="56ba9-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="56ba9-187">Nie można zalogować się na komputerze docelowym, który został określony w regułach autoryzacji jako adres IPv6 z domeną.</span><span class="sxs-lookup"><span data-stu-id="56ba9-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="56ba9-188">Reguły autoryzacji nie obsługują adresów IPv6 w formie nazwy domeny.</span><span class="sxs-lookup"><span data-stu-id="56ba9-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="56ba9-189">Aby określić komputer docelowy przy użyciu adresu IPv6, należy użyć oryginalnego adresu IPv6 (zawierającego dwukropki) w regule autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="56ba9-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="56ba9-190">Zarówno domeny, jak i numeryczne adresy IPv6 (zawierające dwukropki) są obsługiwane jako nazwy komputera docelowego na stronie logowania programu Windows PowerShell Web Access, ale nie w ramach reguł autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="56ba9-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="56ba9-191">Aby uzyskać więcej informacji na temat adresów IPv6, zobacz [jak działa protokół IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="56ba9-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="56ba9-192">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56ba9-192">See Also</span></span>

- <span data-ttu-id="56ba9-193">[Reguły autoryzacji i funkcje zabezpieczeń programu Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="56ba9-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="56ba9-194">[Za pomocą konsoli programu PowerShell Windows opartych na sieci Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="56ba9-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="56ba9-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="56ba9-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)