---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie drugiego przeskoku w komunikacji zdalnej programu PowerShell
ms.openlocfilehash: 1b6e5ad53346324adc7be2d013e154c8600afa4f
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265590"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="51ee3-103">Wykonywanie drugiego przeskoku w komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="51ee3-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="51ee3-104">"Drugi problem przeskoku" odwołuje się do sytuacji podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="51ee3-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="51ee3-105">Użytkownik jest zalogowany do _Serwer_a_.</span><span class="sxs-lookup"><span data-stu-id="51ee3-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="51ee3-106">Z _Serwer_a_, Uruchom sesję zdalną programu PowerShell do nawiązania połączenia _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="51ee3-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="51ee3-107">Polecenie jest uruchamiane na _ServerB_ za pośrednictwem komunikacji zdalnej programu PowerShell sesji podejmie próbę uzyskania dostępu do zasobu na _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="51ee3-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="51ee3-108">Dostęp do zasobu na _ServerC_ odmowa, ponieważ poświadczenia użyte do utworzenia sesji komunikacji zdalnej programu PowerShell nie są przekazywane z _ServerB_ do _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="51ee3-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="51ee3-109">Istnieje kilka sposobów, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="51ee3-109">There are several ways to address this problem.</span></span> <span data-ttu-id="51ee3-110">W tym temacie wyjaśniono, kilka najbardziej popularnych rozwiązań problemu drugiego przeskoku.</span><span class="sxs-lookup"><span data-stu-id="51ee3-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="51ee3-111">Protokół CredSSP</span><span class="sxs-lookup"><span data-stu-id="51ee3-111">CredSSP</span></span>

<span data-ttu-id="51ee3-112">Można użyć [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="51ee3-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="51ee3-113">CredSSP buforuje poświadczeń na serwerze zdalnym (_ServerB_), aby za jej pomocą otwiera do ataków kradzieży poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="51ee3-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="51ee3-114">W przypadku naruszenia zabezpieczeń komputera zdalnego atakujący ma dostęp do poświadczeń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="51ee3-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="51ee3-115">Domyślnie na komputerach klienta i serwera jest wyłączone uwierzytelnianie CredSSP.</span><span class="sxs-lookup"><span data-stu-id="51ee3-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="51ee3-116">Tylko w środowiskach najbardziej zaufany, należy włączyć uwierzytelnianie CredSSP.</span><span class="sxs-lookup"><span data-stu-id="51ee3-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="51ee3-117">Na przykład administrator domeny połączeniem z kontrolerem domeny, ponieważ kontroler domeny jest wysoce zaufanych.</span><span class="sxs-lookup"><span data-stu-id="51ee3-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="51ee3-118">Aby uzyskać więcej informacji na temat problemy z zabezpieczeniami w przypadku używania protokołu CredSSP dla komunikacji zdalnej programu PowerShell, zobacz [przypadkowemu sabotażu: Uważaj CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="51ee3-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="51ee3-119">Aby uzyskać więcej informacji dotyczących ataków kradzieży poświadczeń, zobacz [ataków Podręcznik Mitigating Pass--Hash (PtH) i inne kradzieży poświadczeń](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="51ee3-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="51ee3-120">Na przykład sposobu włączania i użyć protokołu CredSSP do komunikacji zdalnej programu PowerShell, zobacz [przy użyciu protokołu CredSSP, aby rozwiązać problem drugiego przeskoku](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="51ee3-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="51ee3-121">Zalety</span><span class="sxs-lookup"><span data-stu-id="51ee3-121">Pros</span></span>

- <span data-ttu-id="51ee3-122">Działa dla wszystkich serwerów z systemem Windows Server 2008 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="51ee3-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="51ee3-123">Wady</span><span class="sxs-lookup"><span data-stu-id="51ee3-123">Cons</span></span>

- <span data-ttu-id="51ee3-124">Ma luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="51ee3-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="51ee3-125">Wymaga konfiguracji ról klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="51ee3-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="51ee3-126">Delegowanie protokołu Kerberos (nieograniczonego)</span><span class="sxs-lookup"><span data-stu-id="51ee3-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="51ee3-127">Delegowanie protokołu Kerberos nieograniczonego można również używać do utworzyć drugi przeskok.</span><span class="sxs-lookup"><span data-stu-id="51ee3-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="51ee3-128">Jednak ta metoda sterowanie nie jest dostępne, z którym delegowane poświadczenia są używane.</span><span class="sxs-lookup"><span data-stu-id="51ee3-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="51ee3-129">**Uwaga:** Konta usługi Active Directory mających **konto jest poufne i nie może być delegowane** zestaw właściwości nie może być delegowane.</span><span class="sxs-lookup"><span data-stu-id="51ee3-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="51ee3-130">Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: Analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="51ee3-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="51ee3-131">Zalety</span><span class="sxs-lookup"><span data-stu-id="51ee3-131">Pros</span></span>

- <span data-ttu-id="51ee3-132">Wymaga nie kodowania.</span><span class="sxs-lookup"><span data-stu-id="51ee3-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="51ee3-133">Wady</span><span class="sxs-lookup"><span data-stu-id="51ee3-133">Cons</span></span>

- <span data-ttu-id="51ee3-134">Nie obsługuje drugi przeskok usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="51ee3-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="51ee3-135">Umożliwia sterowanie gdy używane są poświadczenia, tworząc luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="51ee3-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="51ee3-136">Ograniczone delegowanie protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="51ee3-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="51ee3-137">Starsze ograniczonego delegowania (nie opartych na zasobach) umożliwia utworzyć drugi przeskok.</span><span class="sxs-lookup"><span data-stu-id="51ee3-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="51ee3-138">Skonfiguruj ograniczone delegowanie protokołu Kerberos z opcją "Użyj dowolnego protokołu uwierzytelniania" Aby umożliwić przejścia protokołu.</span><span class="sxs-lookup"><span data-stu-id="51ee3-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="51ee3-139">Konta usługi Active Directory mających **konto jest poufne i nie może być delegowane** zestaw właściwości nie może być delegowane.</span><span class="sxs-lookup"><span data-stu-id="51ee3-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="51ee3-140">Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: Analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="51ee3-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="51ee3-141">Zalety</span><span class="sxs-lookup"><span data-stu-id="51ee3-141">Pros</span></span>

- <span data-ttu-id="51ee3-142">Wymaga nie kodowania</span><span class="sxs-lookup"><span data-stu-id="51ee3-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="51ee3-143">Wady</span><span class="sxs-lookup"><span data-stu-id="51ee3-143">Cons</span></span>

- <span data-ttu-id="51ee3-144">Nie obsługuje drugi przeskok usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="51ee3-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="51ee3-145">Musi być skonfigurowany w obiekcie Active Directory serwera zdalnego (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="51ee3-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="51ee3-146">Ograniczone do jednej domeny.</span><span class="sxs-lookup"><span data-stu-id="51ee3-146">Limited to one domain.</span></span> <span data-ttu-id="51ee3-147">Nie można dla wielu domen i lasów.</span><span class="sxs-lookup"><span data-stu-id="51ee3-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="51ee3-148">Wymaga uprawnień do aktualizowania obiektów oraz główne nazwy usług (SPN).</span><span class="sxs-lookup"><span data-stu-id="51ee3-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="51ee3-149">Oparte na zasobach ograniczonego delegowania protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="51ee3-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="51ee3-150">Przy użyciu Kerberos oparte na zasobach ograniczonego delegowania (wprowadzona w systemie Windows Server 2012), należy skonfigurować delegowanie poświadczeń na obiekt serwera, gdzie znajdują się zasoby.</span><span class="sxs-lookup"><span data-stu-id="51ee3-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="51ee3-151">W drugi przeskok opisane powyżej, należy skonfigurować _ServerC_ Aby określić, z której będzie akceptować delegowane poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="51ee3-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="51ee3-152">**Uwaga:** Konta usługi Active Directory mających **konto jest poufne i nie może być delegowane** zestaw właściwości nie może być delegowane.</span><span class="sxs-lookup"><span data-stu-id="51ee3-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="51ee3-153">Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: Analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="51ee3-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="51ee3-154">Zalety</span><span class="sxs-lookup"><span data-stu-id="51ee3-154">Pros</span></span>

- <span data-ttu-id="51ee3-155">Poświadczenia nie są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="51ee3-155">Credentials are not stored.</span></span>
- <span data-ttu-id="51ee3-156">Stosunkowo łatwa do skonfigurowania za pomocą poleceń cmdlet programu PowerShell — nie kodowania specjalne wymagane.</span><span class="sxs-lookup"><span data-stu-id="51ee3-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="51ee3-157">Brak dostępu specjalnego domeny jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="51ee3-157">No special domain access is required.</span></span>
- <span data-ttu-id="51ee3-158">Sprawdza się w domenach i lasach.</span><span class="sxs-lookup"><span data-stu-id="51ee3-158">Works across domains and forests.</span></span>
- <span data-ttu-id="51ee3-159">Kod programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51ee3-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="51ee3-160">Wady</span><span class="sxs-lookup"><span data-stu-id="51ee3-160">Cons</span></span>

- <span data-ttu-id="51ee3-161">Wymaga systemu Windows Server 2012 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="51ee3-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="51ee3-162">Nie obsługuje drugi przeskok usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="51ee3-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="51ee3-163">Wymaga uprawnień do aktualizowania obiektów oraz główne nazwy usług (SPN).</span><span class="sxs-lookup"><span data-stu-id="51ee3-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="51ee3-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="51ee3-164">Example</span></span>

<span data-ttu-id="51ee3-165">Przyjrzyjmy się PowerShell, na przykład, który konfiguruje zasobów na podstawie delegowania ograniczonego _ServerC_ umożliwia delegowane poświadczenia z _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="51ee3-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="51ee3-166">W tym przykładzie założono, że wszystkie serwery działają systemu Windows Server 2012 lub nowszym, i że istnieje co najmniej jeden kontroler domeny systemu Windows Server 2012 każdej domeny, do których serwerów należą.</span><span class="sxs-lookup"><span data-stu-id="51ee3-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="51ee3-167">Aby można było skonfigurować delegowanie ograniczone, należy dodać `RSAT-AD-PowerShell` funkcji do zainstalowania modułu środowiska PowerShell usługi Active Directory, a następnie zaimportuj ten moduł do sesji:</span><span class="sxs-lookup"><span data-stu-id="51ee3-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="51ee3-168">Kilka poleceń cmdlet dostępnych już **PrincipalsAllowedToDelegateToAccount** parametru:</span><span class="sxs-lookup"><span data-stu-id="51ee3-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="51ee3-169">**PrincipalsAllowedToDelegateToAccount** parametr ustawia atrybut obiektu usługi Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, który zawiera listy kontroli dostępu (ACL) który Określa konta, które ma uprawnienia do delegowania poświadczeń do skojarzonego konta (w tym przykładzie będzie konto komputera dla _serwera_).</span><span class="sxs-lookup"><span data-stu-id="51ee3-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="51ee3-170">Teraz Skonfigurujmy zmienne będą używane do reprezentowania serwerów:</span><span class="sxs-lookup"><span data-stu-id="51ee3-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="51ee3-171">Usługa WinRM (i w związku z tym obsługę zdalną środowiska PowerShell) domyślnie działa jako konto komputera.</span><span class="sxs-lookup"><span data-stu-id="51ee3-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="51ee3-172">Zobacz ten analizując **StartName** właściwość `winrm` usługi:</span><span class="sxs-lookup"><span data-stu-id="51ee3-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="51ee3-173">Aby uzyskać _ServerC_ aby umożliwić delegowanie w sesji komunikacji zdalnej programu PowerShell na _ServerB_, firma Microsoft będzie zezwalał na dostęp przez ustawienie **PrincipalsAllowedToDelegateToAccount** Parametr _ServerC_ do obiektu komputera z _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="51ee3-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="51ee3-174">Kerberos [Centrum dystrybucji kluczy (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) pamięci podręcznych odmowa prób dostępu (negatywną pamięć podręczną) przez 15 minut.</span><span class="sxs-lookup"><span data-stu-id="51ee3-174">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="51ee3-175">Jeśli _ServerB_ wcześniej próbowało uzyskać dostęp do _ServerC_, należy wyczyścić pamięć podręczną na _ServerB_ za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="51ee3-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="51ee3-176">Można także ponownie uruchom komputer lub zaczekaj co najmniej 15 minut, aby wyczyścić pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="51ee3-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="51ee3-177">Po wyczyszczeniu pamięci podręcznej, można pomyślnie uruchomić kod z _Serwer_a_ za pośrednictwem _ServerB_ do _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="51ee3-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="51ee3-178">W tym przykładzie `$using` zmiennej jest używane do obliczania `$ServerC` widoczne dla zmiennej _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="51ee3-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="51ee3-179">Aby uzyskać więcej informacji na temat `$using` zmiennych, zobacz [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="51ee3-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="51ee3-180">Aby umożliwić delegowanie poświadczeń w celu na wielu serwerach _ServerC_, ustaw wartość **PrincipalsAllowedToDelegateToAccount** parametru na _ServerC_ do tablicy:</span><span class="sxs-lookup"><span data-stu-id="51ee3-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="51ee3-181">Jeśli chcesz utworzyć drugi przeskok między domenami, Dodaj pełni kwalifikowaną nazwę domeny (FQDN) z kontrolerem domeny w domenie do której _ServerB_ należy:</span><span class="sxs-lookup"><span data-stu-id="51ee3-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="51ee3-182">Aby usunąć możliwość delegowania poświadczeń do ServerC, ustaw wartość **PrincipalsAllowedToDelegateToAccount** parametru _ServerC_ do `$null`:</span><span class="sxs-lookup"><span data-stu-id="51ee3-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="51ee3-183">Informacje o oparte na zasobach ograniczonego delegowania protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="51ee3-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="51ee3-184">Nowości w uwierzytelnianiu Kerberos</span><span class="sxs-lookup"><span data-stu-id="51ee3-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="51ee3-185">Jak Windows Server 2012 ułatwia słabe z protokołu Kerberos ograniczonego delegowania, część 1</span><span class="sxs-lookup"><span data-stu-id="51ee3-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="51ee3-186">Jak Windows Server 2012 ułatwia słabe z protokołu Kerberos ograniczonego delegowania, część 2</span><span class="sxs-lookup"><span data-stu-id="51ee3-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="51ee3-187">Opis protokołu Kerberos ograniczonego delegowania dla wdrożenia serwera Proxy aplikacji usługi Azure Active Directory przy użyciu zintegrowanego uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="51ee3-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="51ee3-188">[[MS-ADA2]: Active Directory schematu atrybutów M2.210 atrybutu msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="51ee3-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="51ee3-189">[[MS-SFU]: Rozszerzenia protokołu Kerberos: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="51ee3-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="51ee3-190">Zasobów na podstawie protokołu Kerberos ograniczonego delegowania</span><span class="sxs-lookup"><span data-stu-id="51ee3-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="51ee3-191">Administracja zdalna bez delegowania ograniczonego przy użyciu PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="51ee3-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="51ee3-192">PSSessionConfiguration przy użyciu funkcji RunAs</span><span class="sxs-lookup"><span data-stu-id="51ee3-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="51ee3-193">Możesz utworzyć konfigurację sesji na _ServerB_ i ustawić jej **RunAsCredential** parametru.</span><span class="sxs-lookup"><span data-stu-id="51ee3-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="51ee3-194">Aby dowiedzieć się, jak za pomocą PSSessionConfiguration i RunAs rozwiązać drugi przeskok, zobacz [innego rozwiązania do komunikacji zdalnej programu PowerShell z wieloma przeskokami](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="51ee3-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="51ee3-195">Zalety</span><span class="sxs-lookup"><span data-stu-id="51ee3-195">Pros</span></span>

- <span data-ttu-id="51ee3-196">Działa z dowolnym serwerem z WMF 3.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="51ee3-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="51ee3-197">Wady</span><span class="sxs-lookup"><span data-stu-id="51ee3-197">Cons</span></span>

- <span data-ttu-id="51ee3-198">Wymaga konfiguracji **PSSessionConfiguration** i **RunAs** na każdym serwerze pośredniego (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="51ee3-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="51ee3-199">Wymaga obsługi haseł, korzystając z domeny **RunAs** konta</span><span class="sxs-lookup"><span data-stu-id="51ee3-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="51ee3-200">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="51ee3-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="51ee3-201">JEA pozwala ograniczyć poleceń, jakie administrator można uruchomić sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51ee3-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="51ee3-202">Można go rozwiązać drugi przeskok.</span><span class="sxs-lookup"><span data-stu-id="51ee3-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="51ee3-203">Aby uzyskać informacje o JEA, zobacz [tylko tyle administracji](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="51ee3-203">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="51ee3-204">Zalety</span><span class="sxs-lookup"><span data-stu-id="51ee3-204">Pros</span></span>

- <span data-ttu-id="51ee3-205">Nie obsługi hasła korzystając z konta wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="51ee3-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="51ee3-206">Wady</span><span class="sxs-lookup"><span data-stu-id="51ee3-206">Cons</span></span>

- <span data-ttu-id="51ee3-207">Wymaga WMF 5.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="51ee3-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="51ee3-208">Wymaga konfiguracji na każdym serwerze pośredniego (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="51ee3-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="51ee3-209">Przekazywanie poświadczeń wewnątrz bloku skryptu Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="51ee3-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="51ee3-210">Można przekazać poświadczenia wewnątrz **ScriptBlock** parametru wywołania [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51ee3-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="51ee3-211">Zalety</span><span class="sxs-lookup"><span data-stu-id="51ee3-211">Pros</span></span>

- <span data-ttu-id="51ee3-212">Nie wymaga specjalnego serwera konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="51ee3-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="51ee3-213">Działa na każdym serwerze z programem WMF 2.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="51ee3-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="51ee3-214">Wady</span><span class="sxs-lookup"><span data-stu-id="51ee3-214">Cons</span></span>

- <span data-ttu-id="51ee3-215">Wymaga technikę nieodpowiednich kodu.</span><span class="sxs-lookup"><span data-stu-id="51ee3-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="51ee3-216">Jeśli uruchomiona WMF 2.0, wymaga innej składni przekazywanie argumentów do sesji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="51ee3-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="51ee3-217">Przykład</span><span class="sxs-lookup"><span data-stu-id="51ee3-217">Example</span></span>

<span data-ttu-id="51ee3-218">Poniższy przykład przedstawia sposób przekazywania poświadczeń w **Invoke-Command** bloku skryptu:</span><span class="sxs-lookup"><span data-stu-id="51ee3-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="51ee3-219">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51ee3-219">See also</span></span>

[<span data-ttu-id="51ee3-220">Zagadnienia dotyczące zabezpieczeń komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="51ee3-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
