---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Wykonywanie drugiego przeskoku w komunikacji zdalnej programu PowerShell
ms.openlocfilehash: 06ca43e3e0524d89ec6f66f6553c4c75072beaf3
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320707"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="2c61b-103">Wykonywanie drugiego przeskoku w komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c61b-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="2c61b-104">"Drugi problem przeskoku" odwołuje się do sytuacji, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="2c61b-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="2c61b-105">Użytkownik jest zalogowany do _Serwer_a_.</span><span class="sxs-lookup"><span data-stu-id="2c61b-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="2c61b-106">Z _Serwer_a_, rozpocząć zdalną sesję programu PowerShell, aby nawiązać połączenie _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="2c61b-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="2c61b-107">Polecenie uruchamiane na _ServerB_ za pośrednictwem usługi komunikacji zdalnej programu PowerShell sesji próbuje uzyskać dostęp do zasobu na _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="2c61b-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="2c61b-108">Dostęp do zasobu na _ServerC_ odmowa, ponieważ poświadczenia użyte do utworzenia sesji komunikacji zdalnej programu PowerShell nie są przekazywane z _ServerB_ do _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="2c61b-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="2c61b-109">Istnieje kilka sposobów, aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="2c61b-109">There are several ways to address this problem.</span></span> <span data-ttu-id="2c61b-110">W tym temacie omówimy kilka najbardziej popularne rozwiązania do drugiego przeskoku problemu.</span><span class="sxs-lookup"><span data-stu-id="2c61b-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="2c61b-111">Protokół CredSSP</span><span class="sxs-lookup"><span data-stu-id="2c61b-111">CredSSP</span></span>

<span data-ttu-id="2c61b-112">Możesz użyć [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="2c61b-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="2c61b-113">Protokół CredSSP buforuje poświadczeń na serwerze zdalnym (_ServerB_), więc za jego pomocą zostanie otwarty do ataków z kradzieżą poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="2c61b-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="2c61b-114">Jeśli komputer zdalny zostanie naruszony, osoba atakująca ma dostęp do poświadczeń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2c61b-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="2c61b-115">Protokół CredSSP jest domyślnie wyłączona, na komputerach klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="2c61b-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="2c61b-116">Tylko w środowiskach najbardziej zaufaną, należy włączyć uwierzytelnianie CredSSP.</span><span class="sxs-lookup"><span data-stu-id="2c61b-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="2c61b-117">Na przykład administrator domeny połączeniem z kontrolerem domeny, ponieważ kontroler domeny jest wysoce zaufanym.</span><span class="sxs-lookup"><span data-stu-id="2c61b-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="2c61b-118">Aby uzyskać więcej informacji na temat obawy związane z bezpieczeństwem w przypadku używania protokołu CredSSP dla komunikacji zdalnej programu PowerShell, zobacz [przypadkowym sabotażu: Uwaga CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="2c61b-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="2c61b-119">Aby uzyskać więcej informacji dotyczących ataków z kradzieżą poświadczeń, zobacz [ataków Mitigating Pass--Hash (PtH) i inne kradzieży poświadczeń](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="2c61b-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="2c61b-120">Na przykład sposobu włączania i protokół CredSSP na użytek komunikacji zdalnej programu PowerShell, zobacz [za pomocą protokołu CredSSP, aby rozwiązać problem drugiego przeskoku](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="2c61b-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="2c61b-121">Zalety</span><span class="sxs-lookup"><span data-stu-id="2c61b-121">Pros</span></span>

- <span data-ttu-id="2c61b-122">Działa na wszystkich serwerach z systemem Windows Server 2008 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="2c61b-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="2c61b-123">Wady</span><span class="sxs-lookup"><span data-stu-id="2c61b-123">Cons</span></span>

- <span data-ttu-id="2c61b-124">Ma luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="2c61b-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="2c61b-125">Wymaga konfiguracji klienta i serwera ról.</span><span class="sxs-lookup"><span data-stu-id="2c61b-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="2c61b-126">Delegowanie protokołu Kerberos (nieograniczonego)</span><span class="sxs-lookup"><span data-stu-id="2c61b-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="2c61b-127">Delegowanie protokołu Kerberos, nieograniczone mogą być również używane się drugiego przeskoku.</span><span class="sxs-lookup"><span data-stu-id="2c61b-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="2c61b-128">Jednak ta metoda zapewnia nie kontroli nad którym delegowane poświadczenia są używane.</span><span class="sxs-lookup"><span data-stu-id="2c61b-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="2c61b-129">**Uwaga:** kont usługi Active Directory, które mają **konto jest poufne i nie może być delegowane** ustawioną właściwość nie może być delegowane.</span><span class="sxs-lookup"><span data-stu-id="2c61b-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="2c61b-130">Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="2c61b-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="2c61b-131">Zalety</span><span class="sxs-lookup"><span data-stu-id="2c61b-131">Pros</span></span>

- <span data-ttu-id="2c61b-132">Wymaga bez kodowania.</span><span class="sxs-lookup"><span data-stu-id="2c61b-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="2c61b-133">Wady</span><span class="sxs-lookup"><span data-stu-id="2c61b-133">Cons</span></span>

- <span data-ttu-id="2c61b-134">Nie obsługuje drugiego przeskoku w przypadku usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="2c61b-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="2c61b-135">Zapewnia kontrolę której są używane poświadczenia, tworząc luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="2c61b-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="2c61b-136">Ograniczone delegowanie protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="2c61b-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="2c61b-137">Zapewnienie drugiego przeskoku, można użyć starszego ograniczonego delegowania (nie opartego na zasobach).</span><span class="sxs-lookup"><span data-stu-id="2c61b-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span>

><span data-ttu-id="2c61b-138">**Uwaga:** kont usługi Active Directory, które mają **konto jest poufne i nie może być delegowane** ustawioną właściwość nie może być delegowane.</span><span class="sxs-lookup"><span data-stu-id="2c61b-138">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="2c61b-139">Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="2c61b-139">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="2c61b-140">Zalety</span><span class="sxs-lookup"><span data-stu-id="2c61b-140">Pros</span></span>

- <span data-ttu-id="2c61b-141">Wymaga bez kodowania</span><span class="sxs-lookup"><span data-stu-id="2c61b-141">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="2c61b-142">Wady</span><span class="sxs-lookup"><span data-stu-id="2c61b-142">Cons</span></span>

- <span data-ttu-id="2c61b-143">Nie obsługuje drugiego przeskoku w przypadku usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="2c61b-143">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="2c61b-144">Musi być skonfigurowany w obiekcie Active Directory serwera zdalnego (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="2c61b-144">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="2c61b-145">Ograniczone do jednej domeny.</span><span class="sxs-lookup"><span data-stu-id="2c61b-145">Limited to one domain.</span></span> <span data-ttu-id="2c61b-146">Nie może przekraczać domen i lasów.</span><span class="sxs-lookup"><span data-stu-id="2c61b-146">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="2c61b-147">Wymaga uprawnień do aktualizowania obiektów oraz główne nazwy usług (SPN).</span><span class="sxs-lookup"><span data-stu-id="2c61b-147">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="2c61b-148">Oparte na zasobach ograniczonego delegowania protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="2c61b-148">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="2c61b-149">Przy użyciu protokołu Kerberos z opartego na zasobach ograniczonego delegowania (wprowadzona w systemie Windows Server 2012), skonfigurować delegowanie poświadczeń na obiekt serwera, gdzie znajdują się zasoby.</span><span class="sxs-lookup"><span data-stu-id="2c61b-149">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="2c61b-150">W drugim scenariuszu przeskoku opisanych powyżej, można skonfigurować _ServerC_ do określenia, z której będzie akceptować delegowane poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="2c61b-150">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="2c61b-151">**Uwaga:** kont usługi Active Directory, które mają **konto jest poufne i nie może być delegowane** ustawioną właściwość nie może być delegowane.</span><span class="sxs-lookup"><span data-stu-id="2c61b-151">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="2c61b-152">Aby uzyskać więcej informacji, zobacz [fokus zabezpieczeń: analizowanie "Konto jest poufne i nie może być delegowane" dla kont uprzywilejowanych](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) i [narzędzia uwierzytelniania Kerberos i ustawienia](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="2c61b-152">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="2c61b-153">Zalety</span><span class="sxs-lookup"><span data-stu-id="2c61b-153">Pros</span></span>

- <span data-ttu-id="2c61b-154">Poświadczenia nie są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="2c61b-154">Credentials are not stored.</span></span>
- <span data-ttu-id="2c61b-155">Stosunkowo łatwa do skonfigurowania za pomocą poleceń cmdlet programu PowerShell — nie specjalne jest wymagane tworzenie kodu.</span><span class="sxs-lookup"><span data-stu-id="2c61b-155">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="2c61b-156">Brak dostępu specjalnego domeny jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="2c61b-156">No special domain access is required.</span></span>
- <span data-ttu-id="2c61b-157">Działa na różnych domen i lasów.</span><span class="sxs-lookup"><span data-stu-id="2c61b-157">Works across domains and forests.</span></span>
- <span data-ttu-id="2c61b-158">Kod programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c61b-158">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="2c61b-159">Wady</span><span class="sxs-lookup"><span data-stu-id="2c61b-159">Cons</span></span>

- <span data-ttu-id="2c61b-160">Wymaga systemu Windows Server 2012 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="2c61b-160">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="2c61b-161">Nie obsługuje drugiego przeskoku w przypadku usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="2c61b-161">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="2c61b-162">Wymaga uprawnień do aktualizowania obiektów oraz główne nazwy usług (SPN).</span><span class="sxs-lookup"><span data-stu-id="2c61b-162">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="2c61b-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c61b-163">Example</span></span>

<span data-ttu-id="2c61b-164">Przyjrzyjmy się programu PowerShell, na przykład, który umożliwia skonfigurowanie zasobów na podstawie ograniczonego delegowania _ServerC_ umożliwia delegowane poświadczenia z _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="2c61b-164">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="2c61b-165">W tym przykładzie założono, że wszystkie serwery działają Windows Server 2012 lub nowszy, i że istnieje co najmniej jeden kontroler domeny systemu Windows Server 2012 każdej domeny, które dowolnego z serwerów należą.</span><span class="sxs-lookup"><span data-stu-id="2c61b-165">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="2c61b-166">Aby można było skonfigurować delegowanie ograniczone, należy dodać `RSAT-AD-PowerShell` funkcji do zainstalowania modułu środowiska PowerShell usługi Active Directory, a następnie zaimportuj ten moduł do sesji:</span><span class="sxs-lookup"><span data-stu-id="2c61b-166">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="2c61b-167">Teraz masz kilka dostępnych poleceń cmdlet **PrincipalsAllowedToDelegateToAccount** parametru:</span><span class="sxs-lookup"><span data-stu-id="2c61b-167">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="2c61b-168">**PrincipalsAllowedToDelegateToAccount** parametr ustawia atrybut obiektu usługi Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, który zawiera listy kontroli dostępu (ACL), Określa, które konta mają uprawnienia do delegowania poświadczeń do skojarzonego konta (w naszym przykładzie będzie konto komputera dla _serwera_).</span><span class="sxs-lookup"><span data-stu-id="2c61b-168">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="2c61b-169">Teraz Skonfigurujmy zmienne będą używane do reprezentowania serwerów:</span><span class="sxs-lookup"><span data-stu-id="2c61b-169">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="2c61b-170">Usługa WinRM (i w związku z tym komunikacji zdalnej programu PowerShell) jest domyślnie uruchamiany jako konto komputera.</span><span class="sxs-lookup"><span data-stu-id="2c61b-170">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="2c61b-171">Można to zobaczyć, analizując **StartName** właściwość `winrm` usługi:</span><span class="sxs-lookup"><span data-stu-id="2c61b-171">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="2c61b-172">Dla _ServerC_ aby umożliwić delegowanie sesji komunikacji zdalnej programu PowerShell na _ServerB_, firma Microsoft spowoduje przyznanie dostępu przez ustawienie **PrincipalsAllowedToDelegateToAccount** Parametr _ServerC_ do obiektu komputera _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="2c61b-172">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="2c61b-173">Kerberos [Centrum dystrybucji kluczy (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) pamięci podręcznych odmowa prób dostępu (negatywna pamięć podręczna) przez 15 minut.</span><span class="sxs-lookup"><span data-stu-id="2c61b-173">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="2c61b-174">Jeśli _ServerB_ wcześniej próbowało uzyskać dostęp do _ServerC_, należy wyczyścić pamięć podręczną na _ServerB_ za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="2c61b-174">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="2c61b-175">Można również ponowne uruchomienie komputera lub poczekaj co najmniej 15 minut, aby wyczyścić pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="2c61b-175">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="2c61b-176">Po wyczyszczeniu pamięci podręcznej, można pomyślnie uruchomić kod z _Serwer_a_ za pośrednictwem _ServerB_ do _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="2c61b-176">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="2c61b-177">W tym przykładzie `$using` zmienna jest używane do obliczania `$ServerC` widoczne dla zmiennej _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="2c61b-177">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="2c61b-178">Aby uzyskać więcej informacji na temat `$using` zmiennych, zobacz [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="2c61b-178">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="2c61b-179">Aby zezwolić na wiele serwerów delegować poświadczenia, aby _ServerC_, ustaw wartość **PrincipalsAllowedToDelegateToAccount** parametru _ServerC_ do tablicy:</span><span class="sxs-lookup"><span data-stu-id="2c61b-179">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="2c61b-180">Jeśli chcesz utworzyć drugiego przeskoku w domenach, Dodaj w pełni kwalifikowana nazwa domeny (FQDN) kontrolera domeny, domeny, do którego _ServerB_ należy:</span><span class="sxs-lookup"><span data-stu-id="2c61b-180">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="2c61b-181">Aby usunąć możliwość delegowania poświadczeń do ServerC, ustaw wartość **PrincipalsAllowedToDelegateToAccount** parametru _ServerC_ do `$null`:</span><span class="sxs-lookup"><span data-stu-id="2c61b-181">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="2c61b-182">Informacji na temat opartego na zasobach ograniczonego delegowania protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="2c61b-182">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="2c61b-183">What's New in uwierzytelnianie Kerberos</span><span class="sxs-lookup"><span data-stu-id="2c61b-183">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="2c61b-184">W jaki sposób system Windows Server 2012 ułatwia ból Kerberos ograniczone delegowanie, część 1</span><span class="sxs-lookup"><span data-stu-id="2c61b-184">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="2c61b-185">Jak system Windows Server 2012 ułatwia ból Kerberos ograniczone delegowanie, część 2</span><span class="sxs-lookup"><span data-stu-id="2c61b-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="2c61b-186">Opis protokołu Kerberos ograniczone delegowanie dla wdrożenia serwera Proxy aplikacji usługi Azure Active Directory przy użyciu uwierzytelniania zintegrowanego Windows</span><span class="sxs-lookup"><span data-stu-id="2c61b-186">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="2c61b-187">[[MS-ADA2]: Active Directory schematu atrybutów M2.210 atrybutu msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="2c61b-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="2c61b-188">[[MS-SFU]: rozszerzenia protokołu Kerberos: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="2c61b-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="2c61b-189">Zasób na podstawie protokołu Kerberos ograniczone delegowanie</span><span class="sxs-lookup"><span data-stu-id="2c61b-189">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="2c61b-190">Administracja zdalna bez ograniczone delegowanie przy użyciu PrincipalsAllowedToDelegateToAccount</span><span class="sxs-lookup"><span data-stu-id="2c61b-190">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="2c61b-191">PSSessionConfiguration przy użyciu funkcji RunAs</span><span class="sxs-lookup"><span data-stu-id="2c61b-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="2c61b-192">Można utworzyć konfiguracji sesji na _ServerB_ i ustaw jego **RunAsCredential** parametru.</span><span class="sxs-lookup"><span data-stu-id="2c61b-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="2c61b-193">Aby dowiedzieć się, jak przy użyciu PSSessionConfiguration i Uruchom jako, aby rozwiązać drugi problem przeskoków, zobacz [kolejnego rozwiązania do komunikacji zdalnej programu PowerShell z wieloma przeskokami](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="2c61b-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="2c61b-194">Zalety</span><span class="sxs-lookup"><span data-stu-id="2c61b-194">Pros</span></span>

- <span data-ttu-id="2c61b-195">Działa z każdym serwerem przy użyciu programu WMF 3.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="2c61b-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="2c61b-196">Wady</span><span class="sxs-lookup"><span data-stu-id="2c61b-196">Cons</span></span>

- <span data-ttu-id="2c61b-197">Wymaga konfiguracji **PSSessionConfiguration** i **RunAs** na każdym serwerze pośredni (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="2c61b-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="2c61b-198">Wymaga obsługi haseł, podczas korzystania z domeny **RunAs** konta</span><span class="sxs-lookup"><span data-stu-id="2c61b-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="2c61b-199">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="2c61b-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="2c61b-200">JEA pozwala ograniczyć jakie polecenia, które administrator może być uruchomiony w sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c61b-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="2c61b-201">Może służyć do problemu drugiego przeskoku.</span><span class="sxs-lookup"><span data-stu-id="2c61b-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="2c61b-202">Aby uzyskać informacji na temat technologii JEA, zobacz [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="2c61b-202">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="2c61b-203">Zalety</span><span class="sxs-lookup"><span data-stu-id="2c61b-203">Pros</span></span>

- <span data-ttu-id="2c61b-204">Nie obsługi haseł podczas korzystania z wirtualnego konta.</span><span class="sxs-lookup"><span data-stu-id="2c61b-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="2c61b-205">Wady</span><span class="sxs-lookup"><span data-stu-id="2c61b-205">Cons</span></span>

- <span data-ttu-id="2c61b-206">Wymaga programu WMF 5.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="2c61b-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="2c61b-207">Wymaga konfiguracji na każdym serwerze pośredni (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="2c61b-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="2c61b-208">Przekazywania poświadczeń wewnątrz bloku skryptu Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="2c61b-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="2c61b-209">Można przekazać poświadczenia wewnątrz **ScriptBlock** parametr wywołania [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c61b-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="2c61b-210">Zalety</span><span class="sxs-lookup"><span data-stu-id="2c61b-210">Pros</span></span>

- <span data-ttu-id="2c61b-211">Nie wymaga specjalnego serwera konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2c61b-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="2c61b-212">Działa na każdym serwerze z programem WMF 2.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="2c61b-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="2c61b-213">Wady</span><span class="sxs-lookup"><span data-stu-id="2c61b-213">Cons</span></span>

- <span data-ttu-id="2c61b-214">Wymaga technikę niewygodna kodu.</span><span class="sxs-lookup"><span data-stu-id="2c61b-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="2c61b-215">Jeśli z programem WMF 2.0, wymaga innej składni dotyczących przekazywania argumentów do sesji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="2c61b-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="2c61b-216">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c61b-216">Example</span></span>

<span data-ttu-id="2c61b-217">Poniższy przykład przedstawia sposób przekazywania poświadczeń w **Invoke-Command** blok skryptu:</span><span class="sxs-lookup"><span data-stu-id="2c61b-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="2c61b-218">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c61b-218">See also</span></span>

[<span data-ttu-id="2c61b-219">Zagadnienia dotyczące zabezpieczeń komunikacji zdalnej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c61b-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)