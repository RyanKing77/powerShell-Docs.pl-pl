---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a8904ac36f7fd9fe3c649ad4ca709a98c31b63c3
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094232"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="4c703-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4c703-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="4c703-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4c703-104">SYNOPSIS</span></span>

<span data-ttu-id="4c703-105">Dodaje nową regułę autoryzacji do zestawu reguł autoryzacji programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="4c703-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c703-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c703-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="4c703-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="4c703-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="4c703-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="4c703-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="4c703-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="4c703-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="4c703-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="4c703-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="4c703-111">OPIS</span><span class="sxs-lookup"><span data-stu-id="4c703-111">DESCRIPTION</span></span>

<span data-ttu-id="4c703-112">**Add-PswaAuthorizationRule** polecenie cmdlet dodaje nową regułę autoryzacji do zestawu reguł autoryzacji programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="4c703-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="4c703-113">Należy określić użytkowników, komputerów i punkty końcowe programu Windows PowerShell, dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="4c703-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="4c703-114">Można określić użytkowników i komputerów indywidualne konta użytkowników i nazwy komputerów lub za pomocą określania grup.</span><span class="sxs-lookup"><span data-stu-id="4c703-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="4c703-115">Na komputerze, który jest przyłączony do domeny usługi Active Directory polecenie cmdlet używa identyfikator zabezpieczeń (SID) komputera, aby utworzyć regułę.</span><span class="sxs-lookup"><span data-stu-id="4c703-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="4c703-116">Dzięki temu można używać krótką nazwę, w pełni kwalifikowaną nazwę domeny (FQDN) lub adres IP dla **nazwy komputera** pola na stronie logowania.</span><span class="sxs-lookup"><span data-stu-id="4c703-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="4c703-117">Na komputerze, który nie jest przyłączony do domeny usługi Active Directory polecenie cmdlet tworzy regułę przy użyciu nazwy komputera, dostarczone przez administratora.</span><span class="sxs-lookup"><span data-stu-id="4c703-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="4c703-118">Do pomyślnego połączenia z tą maszyną, użytkownik końcowy należy podać nazwę komputera, dokładnie tak, jak wygląda na to, w regule.</span><span class="sxs-lookup"><span data-stu-id="4c703-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="4c703-119">W przypadku wielu komputerów w ramach tej samej nazwie w sieci krótką nazwę może prowadzić do więcej niż jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4c703-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="4c703-120">Może to prowadzić do niejednoznaczności podczas nawiązywania połączenia.</span><span class="sxs-lookup"><span data-stu-id="4c703-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="4c703-121">Na przykład, jeśli istnieje reguła komputera grupy roboczej, o nazwie "*serwer1*" i nowy komputer o nazwie *server1.contoso.com* jest dołączony do sieci, zakończy się pomyślnie weryfikacji przy użyciu reguł autoryzacji i Windows PowerShell Web Access próbuje nawiązać połączenie z komputera o nazwie "*serwer1*".</span><span class="sxs-lookup"><span data-stu-id="4c703-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="4c703-122">Nie ma żadnej gwarancji, połączenie jest nawiązywane z określonej grupy roboczej komputera; Nie można ustanowić w grupie roboczej lub na komputerze domeny o nazwie "*serwer1*".</span><span class="sxs-lookup"><span data-stu-id="4c703-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="4c703-123">Aby ograniczyć niejednoznaczność, zalecane jest, użyj nazwy FQDN dla komputera docelowego, jeśli to możliwe utworzyć regułę autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="4c703-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="4c703-124">Reguły autoryzacji oceny podstawowego poświadczenia logowania użytkowników programu Windows PowerShell Web Access, a nie poświadczeń alternatywnych (drugi zestaw poświadczeń znaleziony w **opcjonalne ustawienia połączenia** sekcji Strona logowania).</span><span class="sxs-lookup"><span data-stu-id="4c703-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="4c703-125">Aby na przykład Zobacz przykład 6.</span><span class="sxs-lookup"><span data-stu-id="4c703-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="4c703-126">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c703-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="4c703-127">-ComputerGroupName \<ciągu\></span><span class="sxs-lookup"><span data-stu-id="4c703-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="4c703-128">Określa nazwę grupy komputerów w Active Directory Domain Services (AD DS) lub grupy lokalne, do których ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="4c703-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="4c703-129">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4c703-129">Aliases</span></span>                              | <span data-ttu-id="4c703-130">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-130">none</span></span>                                 |
| <span data-ttu-id="4c703-131">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4c703-131">Required?</span></span>                            | <span data-ttu-id="4c703-132">true</span><span class="sxs-lookup"><span data-stu-id="4c703-132">true</span></span>                                 |
| <span data-ttu-id="4c703-133">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4c703-133">Position?</span></span>                            | <span data-ttu-id="4c703-134">o nazwie</span><span class="sxs-lookup"><span data-stu-id="4c703-134">named</span></span>                                |
| <span data-ttu-id="4c703-135">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4c703-135">Default Value</span></span>                        | <span data-ttu-id="4c703-136">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-136">none</span></span>                                 |
| <span data-ttu-id="4c703-137">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4c703-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4c703-138">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4c703-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="4c703-139">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4c703-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4c703-140">false</span><span class="sxs-lookup"><span data-stu-id="4c703-140">false</span></span>                                |

### <a name="-computername-string"></a><span data-ttu-id="4c703-141">-ComputerName \<ciągu\></span><span class="sxs-lookup"><span data-stu-id="4c703-141">-ComputerName \<String\></span></span>

<span data-ttu-id="4c703-142">Określa nazwę komputera, do której ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="4c703-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="4c703-143">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4c703-143">Aliases</span></span>                              | <span data-ttu-id="4c703-144">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-144">none</span></span>                                 |
| <span data-ttu-id="4c703-145">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4c703-145">Required?</span></span>                            | <span data-ttu-id="4c703-146">true</span><span class="sxs-lookup"><span data-stu-id="4c703-146">true</span></span>                                 |
| <span data-ttu-id="4c703-147">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4c703-147">Position?</span></span>                            | <span data-ttu-id="4c703-148">o nazwie</span><span class="sxs-lookup"><span data-stu-id="4c703-148">named</span></span>                                |
| <span data-ttu-id="4c703-149">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4c703-149">Default Value</span></span>                        | <span data-ttu-id="4c703-150">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-150">none</span></span>                                 |
| <span data-ttu-id="4c703-151">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4c703-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4c703-152">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4c703-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="4c703-153">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4c703-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4c703-154">false</span><span class="sxs-lookup"><span data-stu-id="4c703-154">false</span></span>                                |

### <a name="-configurationname-string"></a><span data-ttu-id="4c703-155">ConfigurationName — \<ciągu\></span><span class="sxs-lookup"><span data-stu-id="4c703-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="4c703-156">Określa nazwę konfiguracji sesji programu Windows PowerShell, nazywane również obszar działania, do której ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="4c703-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="4c703-157">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4c703-157">Aliases</span></span>                              | <span data-ttu-id="4c703-158">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-158">none</span></span>                                 |
| <span data-ttu-id="4c703-159">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4c703-159">Required?</span></span>                            | <span data-ttu-id="4c703-160">true</span><span class="sxs-lookup"><span data-stu-id="4c703-160">true</span></span>                                 |
| <span data-ttu-id="4c703-161">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4c703-161">Position?</span></span>                            | <span data-ttu-id="4c703-162">o nazwie</span><span class="sxs-lookup"><span data-stu-id="4c703-162">named</span></span>                                |
| <span data-ttu-id="4c703-163">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4c703-163">Default Value</span></span>                        | <span data-ttu-id="4c703-164">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-164">none</span></span>                                 |
| <span data-ttu-id="4c703-165">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4c703-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4c703-166">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4c703-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="4c703-167">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4c703-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4c703-168">false</span><span class="sxs-lookup"><span data-stu-id="4c703-168">false</span></span>                                |

### <a name="-credential--pscredential"></a><span data-ttu-id="4c703-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="4c703-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="4c703-170">Określa **PSCredential** obiektu dla konta użytkownika, który chcesz użyć, aby zmienić reguły autoryzacji programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="4c703-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="4c703-171">Jeśli ten parametr nie zostanie dodany, polecenie cmdlet używa konta aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4c703-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="4c703-172">Aby uzyskać **PSCredential** obiektu, który jest wymagany, aby dodać reguły autoryzacji zdalnie, uruchom [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c703-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="4c703-173">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4c703-173">Aliases</span></span>                              | <span data-ttu-id="4c703-174">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-174">none</span></span>                                 |
| <span data-ttu-id="4c703-175">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4c703-175">Required?</span></span>                            | <span data-ttu-id="4c703-176">false</span><span class="sxs-lookup"><span data-stu-id="4c703-176">false</span></span>                                |
| <span data-ttu-id="4c703-177">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4c703-177">Position?</span></span>                            | <span data-ttu-id="4c703-178">o nazwie</span><span class="sxs-lookup"><span data-stu-id="4c703-178">named</span></span>                                |
| <span data-ttu-id="4c703-179">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4c703-179">Default Value</span></span>                        | <span data-ttu-id="4c703-180">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-180">none</span></span>                                 |
| <span data-ttu-id="4c703-181">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4c703-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4c703-182">false</span><span class="sxs-lookup"><span data-stu-id="4c703-182">false</span></span>                                |
| <span data-ttu-id="4c703-183">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4c703-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4c703-184">false</span><span class="sxs-lookup"><span data-stu-id="4c703-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="4c703-185">-Force</span><span class="sxs-lookup"><span data-stu-id="4c703-185">-Force</span></span>

<span data-ttu-id="4c703-186">Wymusza polecenia do uruchomienia bez monitowania o potwierdzenie przez użytkownika. \\</span><span class="sxs-lookup"><span data-stu-id="4c703-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="4c703-187">Ponadto on również monituje o potwierdzenie po wprowadzeniu nazwy komputera prostej lub krótki (takie jak nazwa, która nie jest nazwą domeny lub nie jest w pełni kwalifikowana).</span><span class="sxs-lookup"><span data-stu-id="4c703-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="4c703-188">Potwierdzenie jest wymagany ze względów bezpieczeństwa, dzięki czemu można użyć prostą nazwę, aby dodać komputer tylko wtedy, gdy komputer znajduje się w grupie roboczej.</span><span class="sxs-lookup"><span data-stu-id="4c703-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="4c703-189">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4c703-189">Aliases</span></span>                              | <span data-ttu-id="4c703-190">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-190">none</span></span>                                 |
| <span data-ttu-id="4c703-191">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4c703-191">Required?</span></span>                            | <span data-ttu-id="4c703-192">false</span><span class="sxs-lookup"><span data-stu-id="4c703-192">false</span></span>                                |
| <span data-ttu-id="4c703-193">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4c703-193">Position?</span></span>                            | <span data-ttu-id="4c703-194">o nazwie</span><span class="sxs-lookup"><span data-stu-id="4c703-194">named</span></span>                                |
| <span data-ttu-id="4c703-195">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4c703-195">Default Value</span></span>                        | <span data-ttu-id="4c703-196">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-196">none</span></span>                                 |
| <span data-ttu-id="4c703-197">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4c703-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4c703-198">false</span><span class="sxs-lookup"><span data-stu-id="4c703-198">false</span></span>                                |
| <span data-ttu-id="4c703-199">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4c703-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4c703-200">false</span><span class="sxs-lookup"><span data-stu-id="4c703-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="4c703-201">-RuleName \<ciągu\></span><span class="sxs-lookup"><span data-stu-id="4c703-201">-RuleName \<String\></span></span>

<span data-ttu-id="4c703-202">Określa przyjazną nazwę dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="4c703-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="4c703-203">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4c703-203">Aliases</span></span>                              | <span data-ttu-id="4c703-204">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-204">none</span></span>                                 |
| <span data-ttu-id="4c703-205">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4c703-205">Required?</span></span>                            | <span data-ttu-id="4c703-206">false</span><span class="sxs-lookup"><span data-stu-id="4c703-206">false</span></span>                                |
| <span data-ttu-id="4c703-207">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4c703-207">Position?</span></span>                            | <span data-ttu-id="4c703-208">o nazwie</span><span class="sxs-lookup"><span data-stu-id="4c703-208">named</span></span>                                |
| <span data-ttu-id="4c703-209">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4c703-209">Default Value</span></span>                        | <span data-ttu-id="4c703-210">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-210">none</span></span>                                 |
| <span data-ttu-id="4c703-211">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4c703-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4c703-212">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4c703-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="4c703-213">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4c703-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4c703-214">false</span><span class="sxs-lookup"><span data-stu-id="4c703-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="4c703-215">-UserGroupName \<ciągu\[\]\></span><span class="sxs-lookup"><span data-stu-id="4c703-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="4c703-216">Określa nazwę co najmniej jednej grupy użytkowników w usługach AD DS i grupy lokalne, do których ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="4c703-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="4c703-217">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4c703-217">Aliases</span></span>                              | <span data-ttu-id="4c703-218">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-218">none</span></span>                                 |
| <span data-ttu-id="4c703-219">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4c703-219">Required?</span></span>                            | <span data-ttu-id="4c703-220">true</span><span class="sxs-lookup"><span data-stu-id="4c703-220">true</span></span>                                 |
| <span data-ttu-id="4c703-221">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4c703-221">Position?</span></span>                            | <span data-ttu-id="4c703-222">o nazwie</span><span class="sxs-lookup"><span data-stu-id="4c703-222">named</span></span>                                |
| <span data-ttu-id="4c703-223">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4c703-223">Default Value</span></span>                        | <span data-ttu-id="4c703-224">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-224">none</span></span>                                 |
| <span data-ttu-id="4c703-225">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4c703-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4c703-226">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4c703-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="4c703-227">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4c703-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4c703-228">false</span><span class="sxs-lookup"><span data-stu-id="4c703-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="4c703-229">-UserName \<ciągu\[\]\></span><span class="sxs-lookup"><span data-stu-id="4c703-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="4c703-230">Określa co najmniej jednego użytkownika, do których ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="4c703-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="4c703-231">Nazwa użytkownika może mieć konto użytkownika lokalnego na komputerze bramy lub użytkownika w usługach AD DS.</span><span class="sxs-lookup"><span data-stu-id="4c703-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="4c703-232">Format jest `domain\user` lub `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="4c703-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="4c703-233">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4c703-233">Aliases</span></span>                              | <span data-ttu-id="4c703-234">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-234">none</span></span>                                 |
| <span data-ttu-id="4c703-235">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4c703-235">Required?</span></span>                            | <span data-ttu-id="4c703-236">true</span><span class="sxs-lookup"><span data-stu-id="4c703-236">true</span></span>                                 |
| <span data-ttu-id="4c703-237">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4c703-237">Position?</span></span>                            | <span data-ttu-id="4c703-238">1</span><span class="sxs-lookup"><span data-stu-id="4c703-238">1</span></span>                                    |
| <span data-ttu-id="4c703-239">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4c703-239">Default Value</span></span>                        | <span data-ttu-id="4c703-240">brak</span><span class="sxs-lookup"><span data-stu-id="4c703-240">none</span></span>                                 |
| <span data-ttu-id="4c703-241">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4c703-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4c703-242">Wartość true (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4c703-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="4c703-243">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4c703-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4c703-244">false</span><span class="sxs-lookup"><span data-stu-id="4c703-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="4c703-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="4c703-245">\<CommonParameters\></span></span>

<span data-ttu-id="4c703-246">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer oraz - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="4c703-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="4c703-247">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="4c703-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="4c703-248">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="4c703-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="4c703-249">Ciąg</span><span class="sxs-lookup"><span data-stu-id="4c703-249">String</span></span>

<span data-ttu-id="4c703-250">To polecenie cmdlet przyjmuje ciągiem lub tablicą ciągów jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="4c703-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="4c703-251">Ciąg\[\]</span><span class="sxs-lookup"><span data-stu-id="4c703-251">String\[\]</span></span>

<span data-ttu-id="4c703-252">To polecenie cmdlet przyjmuje ciągiem lub tablicą ciągów jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="4c703-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="4c703-253">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4c703-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4c703-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4c703-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="4c703-255">To polecenie cmdlet zwraca obiekt reguły autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="4c703-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="4c703-256">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="4c703-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="4c703-257">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="4c703-257">EXAMPLE 1</span></span>

<span data-ttu-id="4c703-258">W tym przykładzie daje dostęp do konfiguracji sesji _Punktkoncowypswa_, ograniczonym obszarem działania, na _srv2_ dla użytkowników w _SMAdmins_ grupy.</span><span class="sxs-lookup"><span data-stu-id="4c703-258">This example grants access to the session configuration _PSWAEndpoint_, a restricted runspace, on _srv2_ for users in the _SMAdmins_ group.</span></span>

> [!NOTE]
> <span data-ttu-id="4c703-259">Nazwa komputera musi być w pełni kwalifikowaną nazwę domeny (FQDN).</span><span class="sxs-lookup"><span data-stu-id="4c703-259">The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="4c703-260">Administratorzy zdefiniować konfigurację sesji z ograniczonym lub obszaru działania, czyli ograniczonym zakresem poleceń cmdlet i zadań, które użytkownicy końcowi mogą być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="4c703-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="4c703-261">Definiowanie ograniczonym obszarem działania można uniemożliwić użytkownikom uzyskanie dostępu do innych komputerów, które są nie w obszarze dozwolone działania Windows PowerShell® związku z tym oferują bardziej bezpiecznego połączenia.</span><span class="sxs-lookup"><span data-stu-id="4c703-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="4c703-262">Aby uzyskać więcej informacji na temat konfiguracji sesji, zobacz [informacje o konfiguracjach sesji](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) lub [instalacji i użyj Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="4c703-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="4c703-263">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="4c703-263">EXAMPLE 2</span></span>

<span data-ttu-id="4c703-264">W tym przykładzie daje dostęp do domyślnej konfiguracji sesji programu Windows PowerShell, `Microsoft.PowerShell`na *srv2* dla użytkowników w użytkowników o nazwie `contoso\user1`, `contoso\user2`, i `contoso\user3`.</span><span class="sxs-lookup"><span data-stu-id="4c703-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="4c703-265">To polecenie cmdlet tworzy trzy reguły (1 na osobę).</span><span class="sxs-lookup"><span data-stu-id="4c703-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="4c703-266">PRZYKŁAD 3</span><span class="sxs-lookup"><span data-stu-id="4c703-266">EXAMPLE 3</span></span>

<span data-ttu-id="4c703-267">W tym przykładzie pokazano, jak wprowadzanie wartości nazwy użytkownika przy użyciu potoku.</span><span class="sxs-lookup"><span data-stu-id="4c703-267">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="4c703-268">PRZYKŁAD 4</span><span class="sxs-lookup"><span data-stu-id="4c703-268">EXAMPLE 4</span></span>

<span data-ttu-id="4c703-269">Ten przykład ilustruje jak wszystkie parametry pobierają wartości z potoku, według nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="4c703-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="4c703-270">PRZYKŁAD 5</span><span class="sxs-lookup"><span data-stu-id="4c703-270">EXAMPLE 5</span></span>

<span data-ttu-id="4c703-271">Ten przykład dodaje regułę zezwalającą na użytkownika lokalnego o nazwie `PswaServer\ChrisLocal` dostęp do serwera o nazwie **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="4c703-271">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="4c703-272">W tym przykładzie przedstawiono scenariusz, w którym brama znajduje się w grupie roboczej i komputer docelowy znajduje się w domenie.</span><span class="sxs-lookup"><span data-stu-id="4c703-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="4c703-273">Reguła autoryzacji ma zastosowanie do użytkowników lokalnych skonfigurowanych na bramie.</span><span class="sxs-lookup"><span data-stu-id="4c703-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="4c703-274">W witrynie programu Windows PowerShell Web Access logowania w celu pomyślnego uwierzytelnienia użytkownik musi podać drugi zestaw poświadczeń w **opcjonalne ustawienia połączenia** obszaru.</span><span class="sxs-lookup"><span data-stu-id="4c703-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="4c703-275">Serwer bramy zastosuje ten dodatkowy zestaw poświadczeń do uwierzytelniania użytkownika na komputerze docelowym, a serwer o nazwie *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="4c703-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="4c703-276">PRZYKŁAD 6</span><span class="sxs-lookup"><span data-stu-id="4c703-276">EXAMPLE 6</span></span>

<span data-ttu-id="4c703-277">Ten przykład umożliwia wszystkim użytkownikom dostęp do wszystkich punktów końcowych na wszystkich komputerach.</span><span class="sxs-lookup"><span data-stu-id="4c703-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="4c703-278">Wyłącza to zasadniczo reguły autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="4c703-278">This essentially turns off authorization rules.</span></span>

> [!NOTE]
> <span data-ttu-id="4c703-279">Korzystanie z `*` znak symbolu wieloznacznego nie jest zalecane w przypadku wdrożeń z istotnymi dla zabezpieczeń i tylko powinny być traktowane jako dla środowisk testowych lub używane we wdrożeniach, których bezpieczeństwo może zostać złagodzone.</span><span class="sxs-lookup"><span data-stu-id="4c703-279">Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="4c703-280">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c703-280">See Also</span></span>

<span data-ttu-id="4c703-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="4c703-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="4c703-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="4c703-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="4c703-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="4c703-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="4c703-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="4c703-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="4c703-285">Dodawanie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="4c703-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="4c703-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="4c703-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="4c703-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="4c703-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)